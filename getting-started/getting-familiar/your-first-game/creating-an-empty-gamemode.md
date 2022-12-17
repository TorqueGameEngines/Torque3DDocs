# Creating an empty gamemode

A gamemode is a feature provided by the `core` modules, as part of the normal level load and initialization process. It means you can attach a game mode to specific levels and then whenever you load that [level](../../../for-designers/scenes-and-levels/), the gamemode will be activated.

Before you dive into this part of the tutorial, make sure to create an empty level in the CoinCollection module. Open the [World Editor](../../launching-the-game/launching-the-editors.md), click on `File` in the top-left toolbar and choose `New Level` then click `Save Level` and make sure to place it in our CoinCollection module like this:

![](<../../../.gitbook/assets/image (7).png>)

### The game mode

We need to be able to initialise the game mode, create a new file in `data/CoinCollection/server/gamemode.tscript` with the following contents:

```csharp
function CoinCollectionGameMode::onCreateGame() {
    // Note: The Game object will be cleaned up by MissionCleanup.  
    // Therefore its lifetime is limited to that of the mission.
    new ScriptObject(CoinCollectionGameMode) {
    };

    return CoinCollectionGameMode;
}
```

This is a _static_ method and it is called from the `core` scripts.

Add the following piece of code to the end of `gamemode.tscript`:

```csharp
function CoinCollectionGameMode::onMissionStart(%this) {
    echo("CoinCollection mission has been loaded");
}
```

This does what it says on the tin, it's a method on the `CoinCollectionGameMode` object that is triggered when the mission starts, after the mission finish loading.

Since we added a new script file, we'll need to execute it, in the file `data/CoinCollection/CoinCollection.tscript` , change the function `initServer` to the following:&#x20;

```csharp
function CoinCollection::initServer(%this) {
    %this.queueExec("./server/gamemode.tscript");
}
```

Now, we need to associate our gamemode with the level. First select the scene object in the scene tree:\
![](<../../../.gitbook/assets/image (23).png>)

Then set the gameModeName of the scene object to `CoinCollectionGameMode`:

![](<../../../.gitbook/assets/image (4) (1).png>)

Remember to save your level.

Finally, go back to the main menu, click `Single Player`, choose your level and run it. Then look in the Console (tilde on US-layouts, for me it's the ½ key), and see if the message "CoinCollection mission has been loaded" is printed.

If it is, then awesome! Your gamemode is working! However, it's a rather boring game, you can't really move around in the game or do anything really.
