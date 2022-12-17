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

![](https://web.archive.org/web/20200207192111im\_/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Primer/images/materialMapping.png)

Target names are also important if the model is to support skin [swapping](https://web.archive.org/web/20200207192111fw\_/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Primer/torque\_art\_primer.html#SKINNING).

#### Material and Skin Swapping

There are two ways to change the Materials used by a model. The first is by remapping the Material object itself (ie. changing the 'mapTo' field). This will change the mapping for **all** models that use that material target. This is most easily done in the [Material Editor](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/World%20Editor/Editors/MaterialEditor.html); just select the shape and target to swap and choose a new Material using the Material Selector GUI ![](https://web.archive.org/web/20200207192111im\_/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Primer/images/material\_globe.png).

![](https://web.archive.org/web/20200207192111im\_/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Primer/images/material\_properties\_small.png)

Generally this is only done during level editing and is not the recommended way to dynamically change Materials on an object at runtime.

**Skinning**
