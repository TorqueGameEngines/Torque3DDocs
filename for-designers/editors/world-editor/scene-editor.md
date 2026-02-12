# Scene Editor

\
File Menu allows you to: Create, save, open, and close levels; Open, import, and export level data to/from other tools; Run your level to test it and exit the World Editor.

![../\_images/WEFileMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEFileMenu.jpg)

The Edit Menu allows you to: Control editor actions such as undo and redo; Cut, copy, paste, and delete objects you have selected; Select objects using a name pattern or by type filtering; Access dialogs to control various World Editor settings.

![../\_images/WEEditMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEEditMenu.jpg)

The View Menu: Opens the Visibility Layers dialog which toggles debug rendering modes; Toggle the visibility of other aspects of the editor.

![../\_images/WEViewMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEViewMenu.jpg)

The Object Menu allows you to: Manipulate a selected object’s settings by locking/unlocking it, hiding/showing the object, resetting its transforms, and so on.

![../\_images/WEObjectMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEObjectMenu.jpg)

The Drop Location sub-menu selection informs the World Editor where it should place newly created objects.

![../\_images/WEDropLocationMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEDropLocationMenu.jpg)

The Camera Menu allows you to choose your camera type, adjust its speed and motion, and drop it at certain locations.

![../\_images/WECameraMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WECameraMenu.jpg)

The World Camera sub-menu allows you to change the way the camera moves.

![../\_images/WEWorldCameraMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEWorldCameraMenu.jpg)

The Player Camera sub-menu allows you to switch between perspectives while moving around as a player.

![../\_images/WEPlayerCamera.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEPlayerCamera.jpg)

The Camera Speed sub-menu allows you to adjust how fast the camera moves.

![../\_images/WECameraSpeedMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WECameraSpeedMenu.jpg)

The Editors Menu allows you to select which set of editing tools is currently active in the World Editor.

![../\_images/WEEditorsMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEEditorsMenu.jpg)

The Lighting Menu allows you to switch between Advanced and Basic lighting modes, as well as perform level relights.

![../\_images/WELightingMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WELightingMenu.jpg)

Contains shortcuts to documentation and forums for Torque 3D.

![../\_images/WEHelpMenu.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEHelpMenu.jpg)

### Tools Bar

The Tools Bar is the best way to switch between tools. It is made of two components: Tool Settings (top bar) and Tools Selector (bottom bar).

![../\_images/ShortToolbar.jpg](https://torque-3d.readthedocs.io/en/latest/_images/ShortToolbar.jpg)

Tool Settings is made of up three sub-sections: the editor selector, camera settings, and Object Editor. The editor selector and camera setting will always be displayed. The Object Editor will display available settings for the currently selected tool. The Tools Selector will always display the same shortcuts for selecting tools.

This section focuses on the elements of Tool Settings.

The first three icons switch between the editor’s operating modes. Each icon represents a different editing mode and only one mode can be active at any time. There are three modes: World Editor, GUI Editor, and Game Mode. The World Editor is represented by the mountain icon. The GUI Editor is represented by the boxes icon. The Game Mode is represented by the arrow icon.

![../\_images/EditorIcons.jpg](https://torque-3d.readthedocs.io/en/latest/_images/EditorIcons.jpg)

World Editor mode provides tools for manipulating the “world” of your game including terrain, creatures, and so on.

GUI Editor mode provides tools for manipulating the Graphical User Interface (GUI) of your game such as health meters, cursors, and so on.

Play Game Mode runs your game and lets you play through it.

Note

When you use this icon to play your game the World Editor actually closes completely. To return to the World Editor you must press F11 or exit the game and relaunch the World Editor from the Toolbox.

Next to the editor selector, you will find the camera and visibility settings.

![../\_images/CameraIcons.jpg](https://torque-3d.readthedocs.io/en/latest/_images/CameraIcons.jpg)

The camera icon will let you choose your camera type. The drop-down menu next to it will let you switch between camera speeds. The eye icon is the visualization settings which toggle debug rendering modes for various graphical modules, such as normal mapping, wireframe, specular shading, etc. The icon that looks like a camera in a box will move your camera to whatever object you have selected, filling up your view with its boundaries.

![../\_images/WorldSettingsIcons.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WorldSettingsIcons.jpg)

The World Settings make up the rest of this bar when using the tools. The first icon lets you determine your snapping options (snapping to terrain, a bounding box of an object, which axis, etc.). The next icon toggles snapping to a grid. The magnet icon determines soft snapping to other objects. The numeric indicator determines the distance of the snap option.

The box icon with an arrow is a selection tool that allows you to select an object according to its bounding box. This makes selecting small, detailed objects much easier. The next icon that looks like a bullseye will change the selection target from the object center to the bounding box center. The small icon with arrows and mountains will change the object transform and the world transform.

The next two icons show descriptors in your scene. The first icon that looks like a box in a square will display object icons for the various objects in your scene. The second icon will show text descriptors for the objects in your scene.

The last two icons in the bar are prefab icons. The first icon lets you group selected items into a “prefab” (or prefabricated collection) of objects. The second icon will ungroup your prefab items.

### Tool Selector and Palette

![../\_images/ObjectEditorTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/ObjectEditorTool.jpg)

Object Editor

![../\_images/TerrainEditorTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/TerrainEditorTool.jpg)

Terrain Editor

![../\_images/TerrainPainterTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/TerrainPainterTool.jpg)

Terrain Painter

![../\_images/MaterialEditorTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/MaterialEditorTool.jpg)

Material Editor

![../\_images/SketchTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/SketchTool.jpg)

Sketch Tool

![../\_images/DatablockEditor1.jpg](https://torque-3d.readthedocs.io/en/latest/_images/DatablockEditor1.jpg)

Datablock Editor

![../\_images/DecalEditorTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/DecalEditorTool.jpg)

Decal Editor

![../\_images/ForestEditorTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/ForestEditorTool.jpg)

Forest Editor

![../\_images/MeshRoadTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/MeshRoadTool.jpg)

Mesh Road Tool

![../\_images/ParticleEditorTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/ParticleEditorTool.jpg)

Particle Editor

![../\_images/RiverTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/RiverTool.jpg)

River Tool

![../\_images/DecalRoadTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/DecalRoadTool.jpg)

Decal Road Tool

![../\_images/ShapeEditorTool.jpg](https://torque-3d.readthedocs.io/en/latest/_images/ShapeEditorTool.jpg)

Shape Editor

### Scene Tree

The Scene Tree panel is available while using the Object Editor tool. It is composed of two tabs: Scene and Library. The Scene tab contains a list of objects currently in your level. You can select specific objects to modify them.

![../\_images/SceneTree\_SceneTab.jpg](https://torque-3d.readthedocs.io/en/latest/_images/SceneTree_SceneTab.jpg)

Each object in the tree has an icon, unique ID, an object type, and a name. Whenever you click on an object in the tree, it is selected in the level and vice versa. Most of your objects can stand alone in the tree, but you can also use a SimGroup object to organize related entries.

At first glance, a SimGroup looks like a folder and acts much like one to help organize your tree. It does not physically exist in your level, but you can reference it by name or ID from script or the engine. This is handy for grouping several game objects you might need to iterate through and invoke an action on. Even if you do not use that feature, it is still a good idea to group similar objects under a SimGroup to help organize and better navigate your trees as some levels can grow to a large number of objects.

### Library Tab

The Library tab is what you will use to add objects to your level. Once an object has been added to your level, it will appear in the Scene tab (described above). There are four sub-categories on the Library tab, which are separated as sub-tabs: Scripted, Meshes, Level, and Prefabs. Each category contains objects that serve very specific purposes.

![../\_images/SceneTree\_LibraryTab.jpg](https://torque-3d.readthedocs.io/en/latest/_images/SceneTree_LibraryTab.jpg)

#### Scripted Tab

The first tab, Scripted, is automatically populated with game objects that have been created via script. For example, let’s say you have a ceiling fan object with an associated script which controls how and when the fan blades rotate. It would appear in the Scripted tab as follows:

![../\_images/ScriptedObject.jpg](https://torque-3d.readthedocs.io/en/latest/_images/ScriptedObject.jpg)

A discussion of scripting and how to associate scripts with an object is beyond the scope of this document. See the TorqueScript Tutorial for more information.

#### Meshes Tab

When you simply wish to add a 3D art asset, you will use the Meshes Tab. You can browse the various folders containing assets in your project’s “art” directory. From here you can add DTS, COLLADA, and DIF files.

![../\_images/MeshObject.jpg](https://torque-3d.readthedocs.io/en/latest/_images/MeshObject.jpg)

#### Level Tab

The Level Tab lists all the Torque 3D objects that can be used to populate your level. Objects are further divided into category folders. To view what is in a folder, double click it. To leave a folder and view the folder list, click the left pointing arrow icon. To move directly to another folder, select it from the drop down list.

![../\_images/LevelTab.jpg](https://torque-3d.readthedocs.io/en/latest/_images/LevelTab.jpg)

Each sub-category contains objects with similar themes:

![../\_images/LevelTab\_Environment.jpg](https://torque-3d.readthedocs.io/en/latest/_images/LevelTab_Environment.jpg)

* The Environment sub-category contains most of the objects you will add to your level, such as Terrain, Sun, Clouds, Waterblocks, and similar objects.
* The ExampleObjects sub-category contains example rendering classes created in C++.
* The Level sub-category contains objects that manage Time of Day, level boundaries, and similar objects.
* The System sub-category contains engine-level objects such as SimGroups.

#### Prefabs Tab

The prefab system allows you to group multiple objects together and combine them into a single file. This new object can then be repeatedly placed into your level as a whole, making it easier for you to add complex groups of objects with only a few mouse clicks. When you create a prefab from multiple selections, you will save it to a \*.prefab file using the group prefab icon. The World Editor will automatically load these files in the Prefabs tab.

![../\_images/PrefabsTab.jpg](https://torque-3d.readthedocs.io/en/latest/_images/PrefabsTab.jpg)

### Inspector

Whenever you add an object to a level, you will most likely start modifying them immediately. You can use the Inspector Panel to change the properties of an object

![../\_images/WEInspectorPanel.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WEInspectorPanel.jpg)

While there are a few shared property sections, most object types will have a unique set of properties. Editing is as simple as selecting an object in the level, locating a field that you want to change, such as “className” or “media”, then either editing the existing value or entering a value if no default value is given. There are different types of values such as strings, numbers, check boxes, vectors, and even values that require the use of a file browser or color picker.

### Options

The Options dialog is used to change your current session’s audio and video properties as well as mouse and keyboard control bindings. The Options dialog is accessed from the main menu by selecting Edit > Game Options...

![../\_images/OptionsDlg.jpg](https://torque-3d.readthedocs.io/en/latest/_images/OptionsDlg.jpg)

You will use the Graphics tab to adjust your game resolution, screen mode, detail levels, and so on. The Audio tab allows you to adjust your current game’s volume, both globally and channel specific.

### World Editor Settings

The World Editor Setting dialog is important to editing.

![../\_images/WorldEditorSettings.jpg](https://torque-3d.readthedocs.io/en/latest/_images/WorldEditorSettings.jpg)

Through this dialog, you can change various aspects of how your tools render and function. The top left section will control what is rendered on your object, such as its text (name/ID), handle, and selection box. You can also adjust the rendering of the editing plane in relation to the object.

The bottom left section contains the control settings for your manipulators (Translate, Rotate, and Scale tools). You can tweak the sensitivity of the manipulators for more precise or dramatic modifications.

Both sections on the right have settings that adjust visibility and selection methods for your gizmos. The Visible Distance is also an important value, as that adjusts how far into the distance you can see while editing the level.

### PostFX Manager

The PostFX Manager GUI allows level editors to control various post-processing effects. Select the _Enable PostFX_ checkbox to toggle PostFX on and off.

![../\_images/postfx\_toggle\_off.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_toggle_off.png)

Use the effect tabs to access the effect settings.

![../\_images/postfx\_tabs\_ssao.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_tabs_ssao.png)

PostFX settings can be saved to file and and loaded automatically with the level. To achieve this, simply save the settings with the same name as the level file. For example, for Burg.mis, save the PostFX settings in a file called Burg.postfxpreset.cs in the same folder as the level file.

![../\_images/postfx\_footer.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_footer.png)

#### SSAO

Screen space ambient occlusion (SSAO) is an approximation of true Ambient Occlusion. Enabling the effect will darken creases and surfaces that are close together. Outdoor areas with brighter ambient light will show the effect better.

![../\_images/postfx\_ssao\_general.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_ssao_general.png)QualityControls the number of ambient occlusion samples taken; higher quality is more expensive to compute.Overall StrengthControls the overall intensity/darkness of the effect (applied on top of near/far strength).Blur (Softness)Blur depth tolerance.Blur (Normal Maps)Blur normal tolerance.![../\_images/postfx\_ssao\_near.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_ssao_near.png)

SSAO parameters for pixels near to the camera (small depth values).

RadiusOcclusion radius.StrengthOcclusion intensity/darkness.Depth minMinimum screen depth at which to apply effect.Depth maxMaximum screen depth at which to apply effect.Toleranc&#x65;_&#x55;nuse&#x64;_&#x50;owe&#x72;_&#x55;nused_![../\_images/postfx\_ssao\_far.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_ssao_far.png)

SSAO parameters for pixels far away from the camera (large depth values).

RadiusOcclusion radius.StrengthOcclusion intensity/darkness.Depth minMinimum screen depth at which to apply effect.Depth maxMaximum screen depth at which to apply effect.Toleranc&#x65;_&#x55;nuse&#x64;_&#x50;owe&#x72;_&#x55;nused_

#### HDR

Control several High Dynamic Range (HDR) effects including Bloom and Tone mapping.

![../\_images/postfx\_hdr\_bright.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_hdr_bright.png)Tone Mapping ContrastAmount of interpolation between the scene and the tone mapped scene.Key ValueThe tone mapping middle grey or exposure value used to adjust the overall “balance” of the image.Minimum LuminenceThe minimum luninace value to allow when tone mapping the scene. Is particularly useful if your scene very dark or has a black ambient color in places.White CutoffThe lowest luminance value which is mapped to white. This is usually set to the highest visible luminance in your scene. By setting this to smaller values you get a contrast enhancement.Brightness Adapt RateThe rate of adaptation from the previous and new average scene luminance.![../\_images/postfx\_hdr\_bloom.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_hdr_bloom.png)Bright Pass ThresholdThe threshold luminace value for pixels which are considered “bright” and need to be bloomed.Blur multiplier/mean/Std DevThese control the gaussian blur of the bright pass for the bloom effect.![../\_images/postfx\_hdr\_effects.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_hdr_effects.png)Enable color shiftEnables a scene tinting/blue shift based on the selected color, for a cinematic desaturated night effect.

#### Light Rays

This effect creates radial light scattering (also known as god rays). It works best when the scene contains a very bright light, but even in the example above you should be able to see some scattering occuring around the crystal.

![../\_images/postfx\_rays.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_rays.png)BrightnessIntensity of the light ray effect.

#### DOF

Depth of Field (DOF) simulates a camera lens, and blurs pixels based on depth from the focal point. DOF is commonly used when zooming in with a weapon.

![../\_images/postfx\_dof\_general.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_dof_general.png)Enable DOFEnable/disable the DOF effect.Enable Auto FocusDetermines how the focal depth is calculated. When auto-focus is disabled, focal depth is set manually by calling DOFPostEffect::setFocalDist. When auto-focus is enabled, focal depth is calculated automatically by performing a raycast at the screen-center.![../\_images/postfx\_dof\_focus.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_dof_focus.png)Near/Far Blur MaxSets maximum blur for pixels closer/further than the focal distance.Focus Range (Min/Max)The min and max range parameters control how much area around the focal distance is completely in focus.Blur Curve Near/FarControls the gradient of the near/far blurring curve. A small number causes bluriness to increase gradually at distances closer/further than the focal distance. A large number causes bluriness to increase quickly.

#### Sharpness

![../\_images/postfx\_sharpness.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_sharpness.png)

#### Nightvision

![../\_images/postfx\_night\_bright.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_night_bright.png) ![../\_images/postfx\_night\_distort.png](https://torque-3d.readthedocs.io/en/latest/_images/postfx_night_distort.png)

### Manipulators

The last World Editor visual we will describe is the gizmo. A gizmo is a three dimensional rendering of an object’s transforms. While using the Object Editor tool, you can use a gizmo to adjust an object’s location, rotation, and scale without having to manually input number values in the Inspector Panel.

Each gizmo has a unique appearance to notify you of what you are adjusting based upon the tool that you are using.

#### Move Tool Gizmo

When you wish to move an object from one place to another, you will use the Move Tool. This is represented by a gizmo with arrows pointing toward different axes.

You can grab an arrow to move the object along an axis, or grab a space between two arrows to move it in both directions.

![../\_images/TranslateGizmo.jpg](https://torque-3d.readthedocs.io/en/latest/_images/TranslateGizmo.jpg)

If you look carefully, you should see letters at the end of each arrow. These correspond to Torque 3D’s world coordinate system. The engine utilizes the right-handed (or positive) Cartesian coordinate system, where Z is up (top), X is side (right), and Y is front (forward). This applies to the rest of the gizmos.

#### Scaling Tool Gizmo

The Scaling Tool is represented by a gizmo that looks similar to the Translate gizmo. Instead of arrows, there are blocks at the end of the gizmo lines. Dragging one of the boxes in a direction will shrink or grow your object, depending on which direction you move.

![../\_images/ScaleGizmo.jpg](https://torque-3d.readthedocs.io/en/latest/_images/ScaleGizmo.jpg)

#### Rotation Tool Gizmo

While using the Rotation Tool, the orientation gizmo will be rendered. This gizmo looks and acts much differently than the previous two. Instead of straight lines, multiple circles will surround your object.

![../\_images/RotateGizmo.jpg](https://torque-3d.readthedocs.io/en/latest/_images/RotateGizmo.jpg)

Dragging the red circle in a direction will rotate the object along the X-Axis. Green rotates around the Y-Axis. Blue rotates around the Z-axis. The off color circles allow you to rotate an object along multiple axes.
