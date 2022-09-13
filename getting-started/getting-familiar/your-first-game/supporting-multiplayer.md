# Supporting multiplayer

In this tutorial, I have deliberately made some pit-falls that I have seen new developers falling in which prevents multiplayer gameplay from working.

So let's clean up in this mess, the first thing we want to address is the `$CoinsFound` global variable. We set it in the callback in `data/CoinCollection/server/coin.tscript` so how can we just use it directly in `data/CoinCollection/client/commands.tscript`? When we play in single-player mode the player and the host is the same process, this means we can use the global variable `$CoinsFound` in both client and server simultaneous. However this is an anti-pattern because this won't work for other clients in a multi-player scenario.

We can fix this using _dynamic variables_. TorqueScript has something called dynamic variables which is a very simple but very smart concept. Basically you can define any variable on any object by assigning it a value.

```csharp
%obj.somedynVar = 2;
echo(%obj.somedynVar); //outputs "2"
%obj.TSisSpecial = "Is it now?";
echo(%obj.TSisSpecial); //outputs "Is it now?"
echo(%obj.tsisspecial); //outputs "Is it now?"
//(TorqueScript is not case sensitive either by default..)
```

We can use this to keep track on how many coins each client has picked up!

Remove the `$CoinsFound` global, and change the `onCollision` callback  by adding `%col.client.coinsFound++;` instead in `data/CoinCollection/server/coin.tscript` so it looks like this:

```csharp
function Coin::onCollision(%this, %obj, %col, %vec, %len) {
    %emitterNode =  new ParticleEmitterNode(){
        datablock = CoinNode;
        emitter = CoinEmitter;
        position = %obj.getPosition();
    };
    %obj.delete();

    %col.client.coinsFound++; // Automatically starts at 0
    if (Coins.getCount() <= 0) {
        commandToClient(%col.client, 'ShowVictory', %col.client.coinsFound);
    }
}

```

However, there is still an issue here. We are currently showing the player that picks up the last coin that they won. We should show the one with most coins that they won and all others should be told they've lost. We can solve that by looping over the `ClientGroup` SimGroup. The ClientGroup is a collection of all the clients who have joined the game.&#x20;

So change the `onCollision` callback to the following:

```csharp
function Coin::onCollision(%this, %obj, %col, %vec, %len) {
    %emitterNode =  new ParticleEmitterNode(){
        datablock = CoinNode;
        emitter = CoinEmitter;
        position = %obj.getPosition();
    };
    %emitterNode.schedule(200, "delete");
    %obj.delete();

    %col.client.coinsFound++; // Automatically starts at 0
    if(Coins.getCount() <= 0)
    {
        %winnerClient = %col.client;
        foreach(%idxClient in ClientGroup)
        {
            // If we are looking at the current winner, skip forward
            if (%idxClient == %winnerClient) {
                continue;
            }
            
            // If the current client has more coins than the current winner
            if(%idxClient.coinsfound > %winnerClient.coinsfound) {
                // The current winner has lost
                commandToClient(%winnerClient, 'ShowDefeat', %winnerClient.coinsfound);
                // All hail the new winnner
                %winnerClient = %idxClient;
            } else {
                // Current client has lost, winner stays the same
                commandToClient(%idxClient, 'ShowDefeat', %idxClient.coinsfound);
            }
        }
        
        // %winnerClient has the highest number of coins!
        commandToClient(%winnerClient,
                'ShowVictory', %winnerClient.coinsFound);
    }
}
```

Now the last thing we need to do is to change the `data/CoinCollection/client/commands.tscript` file, first of all we want to add a `%score` parameter to the `clientCmdShowVictory` function:

```csharp
function clientCmdShowVictory(%score) {
    MessageBoxOK("You Win!",
            "Congratulation you found" SPC %score SPC "coins!",
            "disconnect();" );
}
```

And then we need to add another function for when we lose:

```csharp
function clientCmdShowDefeat(%score)
{
    MessageBoxOK("You Lost!",
            "You lost with" SPC %score SPC "coins",
            "disconnect();" );
}
```

Now your first multiplayer game should actually be working! Try opening two instances of Torque, in one of the instances you press **“play”** then you tick the **“host”** check box to the left of the `Go` button. In the other instance you press `join`, `"Query LAN"` select the server that comes forth and join the game. Now you can compete with yourself about collecting most coins! Even better, you can host a LAN and let all your friends play your coin collection game with you! Give it a cool name and brag about it a little!
