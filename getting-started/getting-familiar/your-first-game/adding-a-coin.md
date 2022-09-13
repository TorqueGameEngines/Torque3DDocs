# Adding a Coin

Let's create some coins that we can pick up!

### Coin Shapes

First we need a datablock for the Coin objects, we'll use a simple `StaticShape` type of objects, create the file `data/CoinCollection/server/coin.datablock.tscript` with the following contents:

```csharp
datablock StaticShapeData( Coin ) {
    ShapeAsset = "Prototyping:TorusPrimitive_shape";
    category = "CoinCollectionObjects";
};
```

And as usual, remember to register the datablock in `data/CoinCollection/CoinCollection.tscript`:

```csharp
function CoinCollection::onCreateGameServer(%this) {
    %this.registerDatablock("./server/coin.datablock.tscript");
    %this.registerDatablock("./server/player.datablock.tscript");
}
```

Now open the Level Editor, and place a few coins, you do that by opening the Asset Editor![](<../../../.gitbook/assets/image (8).png>)

And then drag in the `Datablock` called coin inside `data/CoinCollection/server` ![](<../../../.gitbook/assets/image (2) (1).png>)

The Coins will show up in the Scene Tree, group them inside a `SimGroup` called `Coins`, right click the level object and select `Add SimGroup`:\
![](<../../../.gitbook/assets/image (10) (1).png>)\
And then just drag-and-drop the `StaticShape` objects into that folder:\
![](<../../../.gitbook/assets/image (9).png>)

A `SimGroup` is a collection of objects. If you delete a `Simgroup` all objects inside it will be deleted as well.

### Handle Collisions

We want our coins to have some logic, namely we want them to get picked up when the player runs into them. Let's create file called `data/CoinCollection/server/coin.tscript` and put the following function inside it:

```csharp
function Coin::onCollision(%this, %obj, %col, %vec, %len) {
    %obj.delete();
}
```

**Now what can we make of this?** For all static shapes that are using the datablock Coin, hence all our Coin objects, we define a function for the onCollision callback. The engine calls this callback when two objects collide. The parameters it gets is:

`%this` refers to the datablock.

`%obj` refers to the coin object.

`%col` refers to the object colliding with the coin.

`%vec` is the _inverse_ direction of the impact vector, which tells you the direction of the impact itself.

`%len` is the length of the impact vector, hence the force of the impact.

When an object collides with the coin, it deletes itself. That was pretty easy huh? This is one of the benefits of an event driven language, it can be incredibly easy to create something cool!

And let's exec it in `initServer` in the `data/CoinCollection/CoinCollection.tscript` file:&#x20;

```csharp
function CoinCollection::initServer(%this) {
    %this.queueExec("./server/coin.tscript");
    %this.queueExec("./server/gamemode.tscript");
}
```

Now run the level again and check that the coins disappear when the `Player` touches them
