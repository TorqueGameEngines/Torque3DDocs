# Custom coin asset

Let's say you have a model, that has been prepared for Torque, and some textures and now you want to use that instead of the boring torus primitive.

We will do a step-by step of how to import these files first download this zip file:

{% file src="../../../.gitbook/assets/korkCoin.zip" %}

And extract it into `data/CoinCollection/objects/korkCoin` such that you get the following four files inside that directory:

* data/CoinCollection/objects/korkCoin
  * korkCoin.fbx
  * korkCoin\_albedo.png
  * korkCoin\_n.png
  * korkCoin\_r.png

Then open up the World Editor and find the Asset Browser:\
![](<../../../.gitbook/assets/image (1).png>)\
Navigate to `data/CoinCollection/objects/korkCoin` and click on the exclamation mark:\
![](<../../../.gitbook/assets/image (5).png>)

This will load all the files in as separate assets:\
![](<../../../.gitbook/assets/image (12).png>)

Now we need to tie them together, right-click the material asset and click on `Edit Asset`\
![](../../../.gitbook/assets/image.png)

In the Material Editor, set the `Diffuse Map` to the albedo image asset, the `Normal Map` to the normal image asset and the `ORM Map` to the roughness image asset.\
![](<../../../.gitbook/assets/image (6).png>)

Then click the save button, and confirm that everything looks right by dragging a "korkCoin\_shape" asset into the scene.

Finally, open up `data/CoinCollection/server/coin.datablock.tscript` and change the `ShapeAsset` of your Coin datablock to this newly imported shape:

```csharp
datablock StaticShapeData( Coin ) {
    ShapeAsset = "CoinCollection:korkCoin_shape";
    category = "CoinCollectionObjects";
};
```
