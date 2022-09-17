# Adding some effects

The easiest way to make the game [POP](https://theoatmeal.com/comics/design\_hell) is to add some particle effects when we pick up the coins. Let's add the basic skeleton of a particle effect to the `data/CoinCollection/datablocks/coin.tscript` file:

```csharp
datablock ParticleData(CoinParticle : DefaultParticle)
{
};

datablock ParticleEmitterData(CoinEmitter : DefaultEmitter)
{
   particles = CoinParticle;
};

datablock ParticleEmitterNodeData(CoinNode  : DefaultEmitterNodeData)
{
   timeMultiple = 1.0;
};
```

As you can see we define two new **datablocks** in this file, a `ParticleEmitterDatablock` for creating a new _particle emitter_. _Particle emitters_ does not have a place in the world by themselves tho, they only emit particles they need a node to know where to emit particles from. Therefore we need a datablock for a _particle emitter node_ aswell. What you probably will notice here is when we define the name of the datablocks, we write a colon and then another name. **What does this mean?**

This means that our new datablock, inherits values from another datablock. It makes a copy of the other datablock and lets you edit the values which will only affect the new datablock.

**Another thing that is important to note**, is that `CoinEmitter` references `CoinParticle`. Which is why it is important that `CoinParticle` is defined before `CoinEmitter`.

### On-the-fly instancing <a href="#on-the-fly-instancing" id="on-the-fly-instancing"></a>

Lets put these new datablocks to good use. We want some visual feedback to tell us that we have picked up a coin.

To spawn a new Emitter we will use the `new` operator. It works like this:

```csharp
%emitterNode = new ParticleEmitterNode(){
   datablock = CoinNode;
   emitter = CoinEmitter;
};
```

Remember it is the node not emitter we want to spawn, then we set the emitter inside the “initialiser”. (What i call the initialiser is the variable definitions inside the two brackets { and }.)

This is where we define what datablock to use, the emitter and anything else we want to do with the newly created object.

We need to give this new object a position in the world. To get the position of an object you would call

```csharp
%obj.getPosition();
```

And to set the position of an object you would assign it, like this

```csharp
%obj.position = "x y z";
```

So now, let's utilise this to spawn emitters when we pickup coins, in `data/CoinCollection/server/coin.tscript` add the instancing to the `onCollision` callback:

```csharp
function Coin::onCollision(%this, %obj, %col, %vec, %len) {
    %emitterNode =  new ParticleEmitterNode(){
        datablock = CoinNode;
        emitter = CoinEmitter;
        position = %obj.getPosition();
    };
    %obj.delete();

    $CoinsFound++;
    if (Coins.getCount() <= 0) {
        commandToClient(%col.client, 'ShowVictory', $CoinsFound);
    }
}
```

### Schedules and cleanup <a href="#schedules-and-cleanup" id="schedules-and-cleanup"></a>

If you run into a couple of Coins, and it is all working properly, then if you open the world editor you will notice that the emitters is still there even tho they stopped emitting particles (given that you gave the `ParticleEmitter` a lifetime) if you didn’t you will see that they keep emitting particles.

We want to fix that! So I will introduce you to a very important feature in TorqueScript: schedules.

You can use a schedule to delete the emitter after some time.

The schedule syntax is:

```csharp
%obj.schedule(int timeMS, string method, string args...);
```

Or if you are not calling it on an object:

```csharp
schedule(int timeMS, int objectID, string method, string args...);
```

We can use this to delete the emitter after we spawn it:

```csharp
%emitterNode =  new ParticleEmitterNode(){
   datablock = CoinNode;
   emitter = CoinEmitter;
   position = obj.getPosition();
};
%emitterNode.schedule(200, "delete");
```

### Customising the effect

Let's start by filling out the `ParticleData` datablock

```csharp
datablock ParticleData(CoinParticle : DefaultParticle)
{
   lifetimeMS = 1000;
   gravityCoefficient = 0;
   dragCoefficient = "2";
   
   sizes[0] = 1;
   sizes[1] = 1;
   sizes[2] = 1;
   sizes[3] = 1;
};
```

The particles is the billboards we are emitting, these are all cosmetic values, I won't dive into them here.

```csharp
datablock ParticleEmitterData(CoinEmitter : DefaultEmitter)
{
   particles = CoinParticle;
   ejectionPeriodMS = 10;
   ejectionVelocity = 4.167;
   ejectionOffset = 0.625;
   thetaMax = 180;
   softnessDistance = 1;
};
```

{% hint style="info" %}
&#x20;I set the `softnessDistance` to 1. Softness distance refers to the concept of [soft particles](http://blog.wolfire.com/2010/04/Soft-Particles). It defaults to `1000`, so it is important to set this down to something reasonable, or else your particles will look transparent when the background is not kilometres away.
{% endhint %}

### &#x20;<a href="#on-the-fly-instancing" id="on-the-fly-instancing"></a>
