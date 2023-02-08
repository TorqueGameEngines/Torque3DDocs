# SimGroup

In Torque3D, `SimGroup` objects are used to organize and manage collections of other objects in the game engine. They act as containers for other objects, allowing developers to group objects together and manipulate them like an array.

### What are SimGroup Objects?

`SimGroup` objects are special objects in Torque3D that act as a container for other objects. By creating a `SimGroup` object, developers can group together any number of other objects and manage them as a single entity. This allows for better organization of objects in the game engine and provides a convenient way to perform operations on groups of objects.

### Using SimGroup Objects

To use a `SimGroup` object, you first need to create an instance of the `SimGroup` class, either through script or through the World Editor. Once you have a `SimGroup` object, you can then add other objects to it as child objects.

To add a child object to a `SimGroup` object, you can use the `add` method, as follows:

```csharp
%group.add(%childObject);
```

where `%group` is the `SimGroup` object and `%childObject` is the object you want to add as a child.

To remove a child object from a `SimGroup`, you can use the `remove` method, as follows:

```csharp
%group.remove(%childObject);
```

where `%group` is the `SimGroup` object and `%childObject` is the child object you want to remove.

You can also use the `clear` method to remove all child objects from a `SimGroup` object:

```csharp
%group.clear();
```

### Benefits of Using SimGroup Objects

Using `SimGroup` objects in Torque3D provides several benefits, including:

* Improved organization of objects in the game engine.
* The ability to manipulate groups of objects as a single entity, making it easier to perform operations on multiple objects at once via utility functions like `callOnChildren().`
