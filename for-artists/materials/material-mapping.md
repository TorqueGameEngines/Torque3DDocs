# Material Mapping

In Torque, Materials (note capital _M_) are TorqueScript objects that define properties used when rendering a surface. Each Material object is mapped to a single material (note lowercase _m_) target. These targets are the names of the materials defined in the model itself (DTS, DAE etc), and are usually the same as the material names in the application that exported the model.

For example, a model containing a single material target _soldier_ might have a Material defined as follows:

```
singleton Material( Mat_Soldier )          // Object name is arbitrary (though must be unique)
{
   mapTo = "soldier";                      // This is the material target name
   diffuseMap[0] = "soldier_armor.jpg";    // Texture name is arbitrary
};
```

For Materials that consist of only a diffuse texture, the Material object definition can be omitted entirely and Torque will automatically create and map a simple Material. For this to work, the diffuse texture must be in the same folder as the model, and must have the same name as the material target. In this case, the diffuse texture would have to be named _soldier_.png (extension is not important, only the base filename).

Torque's Material system requires artists to be careful when naming materials in their modeling application prior to export; any models that share the same material target names will also share the same script Materials.

![](../../.gitbook/assets/materialMapping.png)

Target names are also important if the model is to support skin [swapping](material-mapping.md#material-and-skin-swapping).

#### Material and Skin Swapping

There are two ways to change the Materials used by a model. The first is by remapping the Material object itself (ie. changing the 'mapTo' field). This will change the mapping for **all** models that use that material target. This is most easily done in the [Material Editor](../../for-designers/editors/world-editor/material-editor.md); just select the shape and target to swap and choose a new Material using the Material Selector GUI ![](https://web.archive.org/web/20200207192111im_/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Primer/images/material_globe.png).

![](../../.gitbook/assets/material_properties_small.png)

Generally this is only done during level editing and is not the recommended way to dynamically change Materials on an object at runtime.

**Skinning**

The second way to change Materials is to use _skinning_. Changing the skin of an object essentially renames its material targets (on a per-object basis) - allowing each instance of the same model to use different Materials. Reskinning an object replaces the old skin name at the start of each material target with the new skin name

For example, a character model contains 3 materials: _base\_head_, _base\_body_, and _face_. The script Materials might be defined as follows:

```cs
singleton Material( Mat_Base_Head )
{
   mapTo = "base_head";
   diffuseMap[0] = "base_head_D.dds";
   normalMap[0] = "head_N.dds";

   specular[0] = "0.9 0.9 0.9 1";
   specularPower[0] = 10;
};

singleton Material( Mat_Base_Body )
{
   mapTo = "base_body";
   diffuseMap[0] = "base_body_D.dds";
   normalMap[0] = "body_N.dds";

   specular[0] = "0.9 0.9 0.9 1";
   specularPower[0] = 10;
};

singleton Material( Mat_Face )
{
   mapTo = "face";
   diffuseMap[0] = "face_D.dds";
   normalMap[0] = "face_N.dds";

   specular[0] = "0.9 0.9 0.9 1";
   specularPower[0] = 5;
};
```

Note that the 'mapTo' fields of the script Materials match the model material names. The initial 'old' skin name is "base"; material targets that support skinning should use this as the start of the material name (followed by an underscore or period) in the modeling app prior to export. When a new skin name is applied, it replaces the old skin name in all of the shape material targets with the new skin name. For example, calling:

```cs
%obj.setSkinName( "blue" );
```

Would change the material target names for this instance of the model as shown below:

```
base_head => blue_head
base_body => blue_body
face      => face
```

Note that the _face_ material target was not changed since it did **not** start with the old skin name "base". Most importantly, only the object for which setSkinName was invoked will use the new Materials - all other objects that use the same model (or any model that shares the target names) are not affected.

With this knowledge, we can now define the Materials used to reskin this model.

```cs
// 'blue' skin materials
singleton Material( Mat_Blue_Head : Mat_Base_Head )
{
   mapTo = "blue_head";
   diffuseMap[0] = "blue_head_D.dds";
};

singleton Material( Mat_Blue_Body : Mat_Base_Body )
{
   mapTo = "blue_body";
   diffuseMap[0] = "blue_body_D.dds";
};

// 'red' skin materials
singleton Material( Mat_Red_Body : Mat_Base_Body )
{
   mapTo = "red_body";
   diffuseMap[0] = "red_body_D.dds";
};
```

In this example each skinned Material extends the base Material so that all fields are the same except those that are explicitly set. This is not essential, but is a good way to keep common properties synchronized. It should also be noted that the target is only renamed if there is an existing Material that maps to the new name, or if a diffuse texture with the new name exists in the model folder (for automatic diffuse-only Materials as discussed above). If neither of these conditions exist the target is not renamed. So calling:

```cs
%obj.setSkinName( "red" );
```

Would change the material target names again:

```
blue_head => red_head
blue_body => blue_body
face      => face
```

Note that the _blue\_body_ target was not renamed because no Material was defined that mapped to _red\_body_.

Skinning is available to all TSStatic or ShapeBase derived ojects, and you can even specify a skin when mounting an image (ShapeBaseImageData) to a ShapeBase derived object via `%obj.mountImage()`. The last applied skin name is available by calling _getSkinName_ or via the _skin_ field. Skin changes can also be made within the World Editor by editing the _skin_ field of an object directly, and are therefore persistent (saved to the mission file).

Material targets that do not start with the default "base" name can also support skinning. Simply specify the old skin name to use when calling _setSkinName_ or setting the _skin_ field. For instance, we could change the _face_ material target in the previous example by doing:

```cs
%obj.skin = "face=happy_face";    // "face" target renamed to "happy_face"
```

Multiple skin updates can also be applied at the same time by separating them with a semicolon. For example:

```cs
%obj.setSkinName( "base=blue;face=happy_face" );
```

Note that since only the most recently applied skin update is stored in the _skin_ field, models that require several material target changes (eg. to separately change the armor, skin and face Materials of a character) should apply them all at once using the semicolon delimited format shown above rather than successive calls to _setSkinName_. Otherwise when the mission is saved or new clients join the server, only the most recently applied skin update would be used.
