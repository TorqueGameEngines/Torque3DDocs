# SceneObject

In Torque3D, `SceneObject` is the base class for all objects that exist in a 3D scene. It provides a number of features and functions that can be used to create objects with specific behaviors and characteristics.

### What is a SceneObject?

A `SceneObject` is a type of object in Torque3D that represents a 3D object in a scene. It is the base class for all objects that exist in a scene and provides a number of features and functions for controlling the position, orientation, and other properties of objects.

### Features of SceneObjects

`SceneObject` objects have several key features, including:

* Position and orientation: The `SceneObject` class provides properties for controlling the position and orientation of objects in the scene. This allows you to control the position of objects relative to one another and determine how they are facing.
* Transformation: The `SceneObject` class provides functions for transforming objects in the scene, including translation, rotation, and scaling.
* Collision detection: The `SceneObject` class provides functionality for detecting collisions between objects in the scene. This allows you to create objects that can interact with one another in meaningful ways.
* A scene graph (in the Zones and Portals sections), allowing efficient and robust rendering of the game scene.
* Various helper functions, including functions to get bounding information and momentum/velocity.
* Lighting: SceneObjects can register dynamic lights at runtime (for special effects, such as from flame or a projectile, or from an explosion), or scene lighting such as the sun.

### Using SceneObjects

To use a `SceneObject` in Torque3D, you need to create an instance of the `SceneObject` class, either through script or through the Torque3D World Editor. While you cannot create a SceneObject directly, all spawnable object types are derived from SceneObject and can be used similarly. Once you have a `SceneObject` object, you can use its properties and functions to control its behavior and characteristics.

For example, to set the position of a `SceneObject` in the scene, you can use the `setPosition` method, as follows:

```perl
%object.setPosition(%x, %y, %z);
```

where `%object` is the `SceneObject` object, and `%x`, `%y`, and `%z` are the x, y, and z coordinates of the object's position.

To rotate a `SceneObject` in the scene, you can use the `rotation` variable, as follows:

```perl
%object.rotation = %x SPC %y SPC %z SPC %angle;
```

where `%object` is the `SceneObject` object, and `%x`, `%y`, and `%z` are the x, y, and z rotation axis for the object, and `%angle` is the applied angle on the axis.

