# Mounting Shapes



#### Mounting

Objects in Torque may be mounted to other objects, such as a Player riding a WheeledVehicle or a weapon placed in the player's hands. Usually the object to be mounted has a node named _mountPoint_. For example, a weapon will be mounted in the player model's hand at node mount0. The mountPoint node is not essential however. If not present, the mounted object's origin is used as the mount point. Objects can be mounted from script at runtime, or in the Torque 3D Shape Editor.

```
function PlayerData::onAdd(%this, %obj)
{
   // put the crossbow in the player's hand
   %obj.mountImage(CrossBowImage, 0);
};
```

**See also**

* [Mounting objects in T3D Shape Editor](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/World%20Editor/Editors/ShapeEditor.html)
