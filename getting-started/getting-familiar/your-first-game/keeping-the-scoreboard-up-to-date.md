# Keeping the scoreboard up-to-date

In order to update scoreboard we need to do two things:

1. Write the logic for updating the UI
2. Adding hooks to trigger this logic where necessary

### Writing the client-side logic

We want to be able to add/update a player in the scoreboard when they join and remove a player when they leave.

In `data/CoinCollection/client/gui/scoreBoard.tscript` add the following section to the bottom:

```csharp
//-----------------------------------------------------------------------------
// ScoreBoardGUI data handler methods
//-----------------------------------------------------------------------------

function ScoreBoardGUI::upsertPlayer(%this, %clientID, %name, %score, %kills, %deaths) {
    %text = StripMLControlChars(%name);
    if (%score !$= "null")
        %text = setField(%text, 1, %score);
    %text = setField(%text, 2, %kills);
    %text = setField(%text, 3, %deaths);

    // Update or add the player to the control
    if (ScoreBoardGUIList.getRowNumById(%clientId) == -1)
        ScoreBoardGUIList.addRow(%clientId, %text);
    else ScoreBoardGUIList.setRowById(%clientId, %text);

    // Sorts by score
    ScoreBoardGUIList.sortNumerical(1, false);
    ScoreBoardGUIList.clearSelection();
}

function ScoreBoardGUI::removePlayer(%this, %clientId) {
    PlayerListGuiList.removeRowById(%clientId);
}
```

So lets see what this does.  The `upsertPlayer` function first creates a new variable `%text` which stores name, score, kills and deaths with columns seperated by tabs. **Then** we check if there is already stored a row with that id. If not, then we add a new row else we update the row with that id. **Finally** we sort the list by column 1 (the second column because it starts at 0).&#x20;

The `removePlayer` function simply removes the row with the player's ID.

In order to trigger these two functions we will use the network message system. Let's add the client-side listeners right away in the top of the `scoreBoard.tscript` file:

```csharp
//-----------------------------------------------------------------------------
// Callbacks
//-----------------------------------------------------------------------------
addMessageCallback('MsgClientWelcome', SBGUIWelcome);
addMessageCallback('MsgClientJoin', SBGUIPlayerJoined);
addMessageCallback('MsgClientDrop', SBGUIPlayerLeft);
addMessageCallback('MsgClientScoreChanged', SBGUIScoreChanged);

function SBGUIWelcome(%msgType, %msgString, %clientName, %clientId,
        %isAI, %isAdmin, %isSuperAdmin) {
    ScoreBoardGUI.clear();
    ScoreBoardGUI.upsertPlayer(%clientId, detag(%clientName), 0, 0, 0);
}

function SBGUIPlayerJoined(%msgType, %msgString, %clientName,
        %clientId, %score, %kills,
        %deaths, %isAI, %isAdmin, %isSuperAdmin) {
    ScoreBoardGUI.upsertPlayer(%clientId, detag(%clientName), %score, %kills, %deaths);
}

function SBGUIPlayerLeft(%msgType, %msgString, %clientName, %clientId) {
    ScoreBoardGUI.removePlayer(%clientId);
}

function SBGUIScoreChanged(%msgType, %msgString, %clientName,
        %clientId, %score, %kills, %deaths) {
    ScoreBoardGUI.upsertPlayer(%clientId, detag(%clientName), %score, %kills, %deaths);
}
```

### Adding the hooks on the server

We have four different callbacks we need to implement. Let's start with the callback `MsgClientScoreChanged`, we will trigger that one whenever we pick up a coin. In `data/CoinCollection/server/coin.tscript` add:

```csharp
messageAll('MsgClientScoreChanged', -1, getTaggedString(%col.client.playername),
    %col.client, %col.client.coinsFound,
    %col.client.kills, %col.client.deaths);
```

Right after:

```csharp
%col.client.coinsFound++; // Automatically starts at 0
```

The three other hooks should happen whenever a client enters or leaves the game. So let's open up `data/CoinCollection/gamemode.tscript` and change `onClientEnterGame` and add `onClientLeaveGame` :

```csharp
function CoinCollectionGameMode::onClientEnterGame(%this, %client) {
    //Set the player name based on the client's connection data
    %client.setPlayerName(%client.connectData);

    %this.spawnControlObject(%client);

    // Welcome the client
    messageClient(
            %client, 'MsgClientWelcome',
                    "\c2Welcome to the Torque demo app %1.",
                    getTaggedString(%client.playername),
                    %client,
                    %client.isAiControlled()
            );

    // Inform the client about everyone else
    foreach(%other in ClientGroup) {
        if (%other == %client) {
            continue;
        }

        messageClient(%client, 'MsgClientJoin', -1,
                    getTaggedString(%other.playername),
                    %other, %other.coinsFound,
                    %other.kills, %other.deaths);
    }

    // Inform everyone else about the client
    messageAllExcept(
            %client,
                    "-1",
                    'MsgClientJoin',
                    "\c1 % 1 joined the game.",
                    getTaggedString(%client.playername),
                    %client,
                    %client.coinsFound,
                    %client.kills, %client.deaths,
                    %client.isAiControlled()
            );
}

function CoinCollectionGameMode::onClientLeaveGame(%this, %client) {
    // Inform everyone that the client left
    messageAllExcept(
            %client,
                    "-1",
                    'MsgClientDrop',
                    "\c1 % 1 left the game.",
                    %client,
                    %client.isAiControlled()
            );
}

```
