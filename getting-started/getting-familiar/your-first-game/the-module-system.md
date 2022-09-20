# The Module System

[Modules ](../../../knowledgebase/modules/)were introduced in Torque3D 4.0, by using modules you can easily isolate your changes in a dedicated package. Module system also gives you a nice way of load/unloading packages of scripts and distribute it for others to use.

Before we can begin writing our game scripts, we need to set up a module. The process is simple, create a new folder `data/CoinCollection` and inside that folder add two files.

**data/CoinCollection/CoinCollection.module**

```xml
<ModuleDefinition
    ModuleId="CoinCollection"
    VersionId="1"
    Description="Starter module for CoinCollection gameplay."
    scriptFile="CoinCollection"
    CreateFunction="onCreate"
    DestroyFunction="onDestroy"
    Group="Game"
    Dependencies="UI=1">
    <!-- UI dependency is needed for the Scoreboard later on -->
    <DeclaredAssets
        canSave="true"
        canSaveDynamicFields="true"
        Extension="asset.taml"
        Recurse="true" />
</ModuleDefinition>

```

Most of this, you don’t need to concern yourself with at this moment. It’s mainly metadata about the module. The most significant pieces right now is that the `Group` is set to `Game`, this means that it will be automatically by our `main.tscript` file, the game’s entrypoinnt.

Furthermore, the `scriptFile`, `DestroyFunction` and `CreateFunction` specify how our module is initialized. Let’s go ahead and add this file now:

**data/CoinCollection/CoinCollection.tscript**

```csharp
/// Module life-cycle

function CoinCollection::onCreate(%this) {
}

function CoinCollection::onDestroy(%this) {
}

/// Server life-cycle

function CoinCollection::initServer(%this) {
}

function CoinCollection::onCreateGameServer(%this) {
}

function CoinCollection::onDestroyGameServer(%this) {
}

/// Client life-cycle

function CoinCollection::initClient(%this) {
}

function CoinCollection::onCreateClientConnection(%this) {
}

function CoinCollection::onDestroyClientConnection(%this) {
}
```

This is all the life-cycle hooks we get for our module, the _Module life-cycle_ hooks are general for all modules, while the _Server_ and _Client life-cycle_ hooks are specific for `Game` modules.

{% hint style="info" %}
The primary difference between the `init` and the `on` callbacks is that e.g. `initServer` will only be called once, whereas `onCreateGameServer` will be called everytime a server is started.
{% endhint %}

That is actually the basis of creating a module, the next thing we will look at is how to create a specific gamemode and tie it into a level.
