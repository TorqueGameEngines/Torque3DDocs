# SimObject

The SimObject "Simulation Object" is the most basic class used in Torque and TorqueScript. It implements all of the functionality for an object to "exist" in both C++ and in script (in the [Console](../../for-programmers/major-components-of-the-engine/core/console.md)).  You'd generally always subclass SimObject rather than it's superclasses `ConsoleObject` and `EngineObject`.

![](<../../.gitbook/assets/image (3) (2).png>)

### Creating SimObjects

In TorqueScript, all you have to do when you create a new object is calling the `new` operator.

```csharp
$obj = new SimObject() {
    someDynamicVariable = "2.0";
};
```

However, this is actually a three-step process behind the scenes which becomes evident if you try to create a SimObject in C++.

```cpp
// Step 1 - Initialize the object
SimObject* obj = new SimObject();
// Step 2 - Apply the fields inside the initializer
obj->setFieldValue("someDynamicVariable", "2.0");
// Step 3 - Call "registerObject"
obj->registerObject();
```

Registering a SimObject performs these tasks:

* Marks the object as not cleared and not removed.
* Assigns the object a unique SimObjectID if it does not have one already.
* Adds the object to the global name and ID dictionaries so it can be found again.
* Calls the object's [onAdd()](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1a2b13eb492f78b31de4a8e4360e6fe43f) method. **Note:** [SimObject::onAdd()](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1a2b13eb492f78b31de4a8e4360e6fe43f) performs some important initialization steps. See [here](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1simobject\_subclassing) for details on how to properly subclass [SimObject](https://reference.torque3d.org/coding/class/classsimobject/).
* If [onAdd()](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1a2b13eb492f78b31de4a8e4360e6fe43f) fails (returns false), it calls [unregisterObject()](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1aab3f782f0b5ff644dc845fc0355c2cc8).
* Checks to make sure that the SimObject was properly initialized (and asserts if not).

Calling [registerObject()](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1a0c0706dac6f0fed254f6455bb16f75c8) and passing an ID or a name will cause the object to be assigned that name and/or ID before it is registered.

### Destroying SimObjects

There are a two ways a SimObject can die.

* First, the game can be shut down. This causes the root [simgroup.md](simgroup.md "mention") be unregistered and deleted. When a [simgroup.md](simgroup.md "mention") is unregistered, it unregisters all of its member SimObjects; this results in everything that has been registered with [Sim](https://reference.torque3d.org/coding/namespace/namespacesim/) being unregistered, as everything registered with [Sim](https://reference.torque3d.org/coding/namespace/namespacesim/) is in the root group.
* Second, you can manually kill it off, either by calling [unregisterObject()](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1aab3f782f0b5ff644dc845fc0355c2cc8) or by calling [deleteObject()](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1aa01c5c62196de8ca4d8c20e69a902bac).

When you unregister a SimObject, the following tasks are performed:

* The object is flagged as removed.
* Notifications are cleaned up.
* If the object is in a group, then it removes itself from the group.
* Delete notifications are sent out.
* Finally, the object removes itself from the [Sim](https://reference.torque3d.org/coding/namespace/namespacesim/) globals, and tells [Sim](https://reference.torque3d.org/coding/namespace/namespacesim/) to get rid of any pending events for it.

If you call [deleteObject()](https://reference.torque3d.org/coding/class/classsimobject/#classsimobject\_1aa01c5c62196de8ca4d8c20e69a902bac), all of the above tasks are performed, in addition to some sanity checking to make sure the object was previously added properly, and isn't in the process of being deleted. After the object is unregistered, it deallocates itself.

\
