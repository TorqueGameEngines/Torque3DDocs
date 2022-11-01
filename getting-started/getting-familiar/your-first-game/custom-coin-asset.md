# Custom coin asset

Let's say you have a model, that has been prepared for Torque, and some textures and now you want to use that instead of the boring torus primitive.

We will do a step-by step of how to import these files first download this zip file:

{% file src="../../../.gitbook/assets/korkCoin (1).zip" %}

And extract it into `data/CoinCollection/objects/korkCoin` such that you get the following four files inside that directory:

* data/CoinCollection/objects/korkCoin
  * korkCoin.fbx
  * korkCoin\_albedo.png
  * korkCoin\_n.png
  * korkCoin\_orm.png

Then open up the World Editor and find the Asset Browser:\
![](<../../../.gitbook/assets/image (1) (1) (1) (1).png>)\
Navigate to `data/CoinCollection/objects/korkCoin` and click on the exclamation mark:\
![](<../../../.gitbook/assets/image (5) (1).png>)

This will load all the files in as separate assets:\
![](<../../../.gitbook/assets/image (14).png>)

![](<../../../.gitbook/assets/image (13).png>)\
Now we need to tie them together, right-click the material asset and click on `Edit Asset`\


In the Material Editor, set the `Diffuse Map` to the albedo image asset, the `Normal Map` to the normal image asset and the `ORM Map` to the orm image asset.\
![](<../../../.gitbook/assets/image (11).png>)

Then click the save button, and confirm that everything looks right by dragging a "korkCoin\_shape" asset into the scene.

Finally, open up `data/CoinCollection/datablocks/coin.tscript` and change the `ShapeAsset` of your Coin datablock to this newly imported shape:

```csharp
datablock StaticShapeData( Coin ) {
    ShapeAsset = "CoinCollection:korkCoin_shape";
    category = "CoinCollectionObjects";
};
```

### Playing a simple animation

The `korkCoin.fbx` file has a simple animation built in. It simply rotates the coin around once. Let's play this on our coins. The animation is called `korkCoin|ambient`.

First open up `data/CoinCollection/objects/korkCoin/korkCoin.tscript` and add the following function to the end of the file:

```csharp
function korkCoinfbx::onLoad(%this)
{
    %this.setSequenceCyclic("korkCoin|ambient", "1");
}
```

This will make sure that our animation plays on a loop. \
Now we need to play this animation on all coins that are spawned, we can do that on the `onAdd` callback for each `Coin` in `data/CoinCollection/server/coin.tscript`:

```csharp
function Coin::onAdd(%this, %obj) {
    %obj.playThread( 0, "korkCoin|ambient" );
}
```

Remember here that `Coin` is the datablock, so the second parameter `%obj` is the actual Coin instance itself.&#x20;
