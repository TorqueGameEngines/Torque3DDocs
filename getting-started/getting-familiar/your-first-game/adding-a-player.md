# Adding a Player

In Torque3D we call the object that you are moving when you press keys the `ControlObject` and the `Player` is one instance of such a ControlObject. So, let's define a `PlayerData` datablock, place the following in the file `data/CoinCollection/server/player.datablock.tscript`:

```csharp
datablock PlayerData( CoinCollectorPlayer ) {
    // We want a third person game
    renderFirstPerson = false;

    // Third person shape
    ShapeAsset = "Prototyping:Playerbot_shape";

    // Set distance from camera to player
    cameraMaxDist = 3.0;
};
```

`datablock` this is very similar to a struct, basically in a datablock you define a set of default values which will get referenced by the spawned objects upon creation.

PlayerData`(` CoinCollectorPlayer `)` here we state that we want to create a datablock of the type PlayerData, for creating new Players. We call this new datablock CoinCollectorPlayer .

`renderFirstPerson` here we specify that we want the game to use a third person view when controlling this Player

`ShapeAsset` is a reference to the asset `Playerbot_shape`in the Prototyping module. We'll cover assets later in the tutorial.

`cameraMaxDist` defines the maximum distance from the Player shape to the `Camera` this will essentially allow us to zoom out a bit.

And we need to register this datablock, do this in the `onCreateGameServer` function in `data/CoinCollection/CoinCollection.tscript`:

```csharp
function CoinCollection::onCreateGameServer(%this) {
    %this.registerDatablock("./server/player.datablock.tscript");
}
```

We use the method  `registerDatablock` because the `core`module has a lot of clever logic about loading/unloading/updating datablocks which we can't take advantage of if we just use the `exec` function.

Now we have a `PlayerData` that we can use, but in order to actually use it, we have to create a `Player` instance whenever a player enters the game. We do that in `data/CoinCollection/server/gamemode.tscript`, first let's create a helper method that creates the `Player` using the `CoinCollectorPlayer` datablock and assigns it as the client's Control Object:

```csharp
function CoinCollectionGameMode::spawnControlObject(%this, %client) {
    // First spawn the actual Player object
    %player = spawnObject(Player, CoinCollectorPlayer);
    if (!isObject(%player)) {
        return;
    }
    MissionCleanup.add(%player);

    // Place it at the center of the world, this is a pretty simple "spawn placement"
    %spawnTransform = "0 0 1 0 0 0 0 0";
    %player.setTransform(%spawnTransform);
    
    // Couple the player to the client and set it as the control object
    %player.client = %client;
    %client.setControlObject(%player);
    %client.player = %player;

    // Tell the client that we expect it to be in third person
    %client.setFirstPerson(false);
}
```

Now that's just a helper method, in order to actually activate it we should call it from the `onClientEnterGame` function in that same file:

```csharp
function CoinCollectionGameMode::onClientEnterGame(%this, %client) {
    // Set the player name based on the client's connection data
    %client.setPlayerName(%client.connectData);

    // Call the helper function
    %this.spawnControlObject(%client);
}
```

Now, run the level again and see that you can move around and jump with your newly created `Player` object!
