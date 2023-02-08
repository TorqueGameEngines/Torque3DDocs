# Datablocks

In Torque3D, `Datablocks` are a way to store data that can be shared among multiple instances of a class. They allow you to define common properties and behaviors that can be shared by multiple objects, making it easier to manage and maintain your objects in a scene and minimizing data duplication and networking overhead.

### What is a Datablock?

A `Datablock` is a type of object in Torque3D that stores data that can be shared by multiple instances of a class. They are defined as separate objects from the objects that use them, and they contain data that can be used by multiple instances of a class to define their properties and behaviors.

### Features of Datablocks

`Datablocks` have several key features, including:

* Reusability: `Datablocks` can be used by multiple instances of a class, which makes it easier to manage and maintain your objects in a scene. You can define a `Datablock` once, and then reuse it for multiple instances of a class, which saves time and reduces the risk of errors.
* Flexibility: `Datablocks` can be changed, and the changes will be reflected in all instances of a class that use the `Datablock`. This allows you to make global changes to the properties and behaviors of objects in your gane, without having to make changes to each object individually.
* Performance: By using `Datablocks`, you can reduce the amount of memory and processing power required to manage and maintain your objects in a scene.&#x20;
* Networking: Because `Datablocks` are sent from server to client, the game can be assured that the client has the same data as the server. Additionally, because they're sent during initial connection, it's data that doesn't need to be re-sent during normal network updates, keeping data transmission as low as possible.

### Using Datablocks

To use a `Datablock` in Torque3D, you need to create a `Datablock` object and define its properties. Then, you can reference the `Datablock` from multiple instances of a class to share its properties and behaviors.

For example, let's say you have a `Player` class, it has a variable, `health`,  that can be used for all instances of the `Player` class. To use this, you would create a `PlayerDatablock` object, and define the health property. Then, you would reference the `PlayerDatablock` from each instance of the `Player` class to share its health property.

```scss
datablock PlayerDatablock(PlayerDB)
{
   health = 100;
};

// Use the datablock for the player
%player = new Player() {
   datablock = PlayerDB;
};
```

In this example, the `PlayerDatablock` object is defined with a property named `health`, which is set to 100. The `Player` class references the `PlayerDatablock` by calling the `setDatablock` method and passing in the `PlayerDB` object.

For a breakdown of how to create your own classes utilizing datablocks, you can go to this page:

