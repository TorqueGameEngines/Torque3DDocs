# Porting a Legacy Project

## BaseGame Template <a href="#toc0" id="toc0"></a>

One of the major changes is the shift to the module-based BaseGame template as opposed to the preconfigured Full or Empty templates from before. While most changes won't impact a given project unless there was **heavy** modifications in a wide area of the scripts, some things - such as adopting the module system to help compartmentalize and organize your game's scripts and content - are important.

### Converting your game's content to a module <a href="#toc1" id="toc1"></a>

The big one, as mentioned, is converting your game's scripts and content to a module, or modules, for compartmentalization and organizational purposes.

#### Simple, naive conversion <a href="#toc2" id="toc2"></a>

The easiest way, but doesn't see much of a shift in organization or compartmentalization. The first thing you'll want to do is create a new folder in the data directory of the BaseGame template, calling it something relevent, and convenient. For our example's case, we'll call it MyGame.

**Setting up the module**

Inside it, you'll want to make 2 files: a \<ModuleName>.cs and a \<ModuleName>.module. The module file is a TAML file, but generally is XML.

Once those are made, the directory should look like this:

![](http://ghc-games.com/public/BaseGameUpdateTut01.png)

We'll want to make the \*.module file to look something like this:

```clike
<ModuleDefinition
    ModuleId="MyGame"
    VersionId="1"
    Description="This contains all of my game's scripts and content."
    ScriptFile="MyGame.cs"
    CreateFunction="onCreate"
    DestroyFunction="onDestroy"
    Dependencies="clientServer=1,ui=1"
    Group="Game">
</ModuleDefinition>
```

With the MyGame parts and description obviously changed to apply as needed. The script file similarly should be set up like this:

```clike
function MyGame::onCreate( %this )
{
}
 
function MyGame::onDestroy( %this )
{
}
```

Save the files, and the basics are in place. Important parts to note:

* ModuleID is the unique module name
* Version ID is the particular version number(which is usually used in dependencies checks)
* Description is the description
* ScriptFile is the name of the initialization script file
* CreateFunction is the function called in our initialization script file when the module is loaded. It's used to set up the common stuff for the module, such as loading datablocks, exec'ing scripts and guis, etc. It uses the ModuleID for the namespace.
* DestroyFunction is the function called when we unload the module, used for cleanup. Similarly used the ModuleID namespace.
* Dependencies is any modules we need to load before this one so we can use their functionality. It's done as \<ModuleID>=\<VersionNumber>. For multiple dependencies, it's separated by a comma. In our case, because we'll be loading datablocks and have client/server scripts, we'll want the clientServer module and ui module as dependencies so we can properly load everything up in a multiplayer context.
* Group is the group - if any - this module is a part of. This is a convenience feature that allows you to load and unload groups of modules at once automatically. The BaseGame template is designed to automatically load any modules in the Game group during initialization. This can be expanded upon or changed in the main.cs file.

**Porting the content to the module**

Obviously, we want to move our content over into our new module, so we'll do that now. While you can organize it in any way you want, a way that was done for the FPSGameplay and SpectatorGameplay modules(that replicate the gameplay of the full and empty templates, respectively) is organized like so:

![](http://ghc-games.com/public/BaseGameUpdateTut02.png)

* Art, unsurprisingly, would contain your art files - shapes, animations, textures, particles, skies, decals, etc
* Levels, naturally, contain the \*.mis files and any level-specific files such as the posteffect config, preview image, decals file, forest file and so on.
* Scripts contain anything script-based - gameplay scripts, guis, datablocks, etc
* Sounds are your sound files.

The FPSGameplay and EmptyGameplay modules structured the scripts folder as such:

* client - Any client-side specific scripts
* datablocks - Any files that contain your datablocks for all your objects
* gui - Any \*.gui files
* server - Any server-side specific scripts

It should be fairly self explanatory with that, but if you want a good comparison example, you can check the FPSGameplay module to compare, but this organization model should be relatively straightforward.

Ensure that your datablocks, gui files, level files, and script files' various paths have been updated to point to the respective folder inside the data/\<ModuleName>/ directory. This ensures that it's properly compartmentalized and contained in the module dir. Any content utilized from other modules should also be paired with adding that module's dependency to the module definition as mentioned above.

**Initializing the module's scripts and content**

Once you've moved your content over to the module folder, we'll want to initialize everything.

Following the FPSGameplay example - assuming you want to take advantage of the clientServer module's functionality, we'll want to make sure to initialize the client and server content appropriately.

Using the FPSGameplay initialization script file as an example, lets look at it:

```clike
function FPSGameplay::create( %this )
{
   //server scripts
   exec("./scripts/server/aiPlayer.cs");
   exec("./scripts/server/camera.cs");
   exec("./scripts/server/chat.cs");
   exec("./scripts/server/cheetah.cs");
   exec("./scripts/server/commands.cs");
   exec("./scripts/server/deathMatchGame.cs");
   exec("./scripts/server/health.cs");
   exec("./scripts/server/inventory.cs");
   exec("./scripts/server/item.cs");
   exec("./scripts/server/player.cs");
   exec("./scripts/server/projectile.cs");
   exec("./scripts/server/proximityMine.cs");
   exec("./scripts/server/radiusDamage.cs");
   exec("./scripts/server/shapeBase.cs");
   exec("./scripts/server/spawn.cs");
   exec("./scripts/server/teleporter.cs");
   exec("./scripts/server/triggers.cs");
   exec("./scripts/server/turret.cs");
   exec("./scripts/server/vehicle.cs");
   exec("./scripts/server/vehicleWheeled.cs");
   exec("./scripts/server/VolumetricFog.cs");
   exec("./scripts/server/weapon.cs");
 
   //add DBs
   if(isObject(DatablockFilesList))
   {
      for( %file = findFirstFile( "data/FPSGameplay/scripts/datablocks/*.cs.dso" );
      %file !$= "";
      %file = findNextFile( "data/FPSGameplay/scripts/datablocks/*.cs.dso" ))
      {
         // Only execute, if we don't have the source file.
         %csFileName = getSubStr( %file, 0, strlen( %file ) - 4 );
         if( !isFile( %csFileName ) )
            DatablockFilesList.add(%csFileName);
      }
 
      // Load all source material files.
      for( %file = findFirstFile( "data/FPSGameplay/scripts/datablocks/*.cs" );
      %file !$= "";
      %file = findNextFile( "data/FPSGameplay/scripts/datablocks/*.cs" ))
      {
         DatablockFilesList.add(%file);
      }
   }
 
   if(isObject(LevelFilesList))
   {
      for( %file = findFirstFile( "data/FPSGameplay/levels/*.mis" );
      %file !$= "";
      %file = findNextFile( "data/FPSGameplay/levels/*.mis" ))
      {
         LevelFilesList.add(%file);
      }
   }
 
   if (!$Server::Dedicated)
   {
      exec("data/FPSGameplay/scripts/client/gameProfiles.cs");
 
      //client scripts
      $KeybindPath = "data/FPSGameplay/scripts/client/default.keybinds.cs";
      exec($KeybindPath);
 
      %prefPath = getPrefpath();
      if(isFile(%prefPath @ "/keybinds.cs"))
         exec(%prefPath @ "/keybinds.cs");
 
      exec("data/FPSGameplay/scripts/client/inputCommands.cs");
 
      //guis
      exec("./scripts/gui/chatHud.gui");
      exec("./scripts/gui/playerList.gui");
      exec("./scripts/gui/playGui.gui");
 
      exec("./scripts/gui/playGui.cs");
 
      exec("data/FPSGameplay/scripts/client/message.cs");
      exec("data/FPSGameplay/scripts/client/chatHud.cs");
      exec("data/FPSGameplay/scripts/client/clientCommands.cs");
      exec("data/FPSGameplay/scripts/client/messageHud.cs");
      exec("data/FPSGameplay/scripts/client/playerList.cs");
   }
}
 
function FPSGameplay::destroy( %this )
{
 
}
```

As we can see, the first thing that happens is we exec our server scripts. This is done because unless you're fully separating the client and server side, a singleplayer game still sets up a server instance, so we'll need to exec the server-side scripts for all the gameplay stuff.\
It's done first, because in the event this is a dedicated server OR a client, we'll always need these scripts executed, but we may not need to execute the client-side scripts if we're a dedicated server.

Next, we'll iterate through our data/\<ModuleName>/scripts/datablocks folder - where we put all our datablock script files - and add them to DatablockFilesList.

This is where our utilization of the clientServer module comes in. This is an array that it set up in the initialization of the clientServer module, and is used to transmit datablocks to the client on connection. All modules can input datablocks into the array to ensure they all get properly transmitted to the client.\
As this is set up in the clientServer module, we have our dependency to the module so its always ready for us to use because we init after it.

Once we've iterated our datablock files and added them to that list, we want to iterate our data/\<ModuleName/levels folder to get any \*.mis files to add to the LevelFilesList. This is set up by the UI module, to give us a common list to add any level files from our modules and display that list on our ChooseLevel gui. Obviously, if you've got a different UI configuration, you may not need to do this, and can just reference the directory specifically if you don't have other level directories.

Next, we execute any client-side scripts. We filter this as being a client by checking that this process isn't running as a dedicated server - which means we'll be a client in some capacity. Then just exec the scripts, client preferences and any keybind files you set up for the client.

And you should be good! If your levels and datablocks have had their paths properly loaded, and you hooked the levels list to the UI, then calling StartGame(which is done in the UI module already, but needs to be done by any custom UI work you have) will kick off the creation of the game session!

#### Manually porting code <a href="#toc6" id="toc6"></a>

In the event your project's seen a good deal of custom work, obviously just piggybacking off the FPSGameplay or SpectatorGameplay modules for the baseline isn't sufficient, and you'll need to port your work.

However, given that a fair bit of trimming and re-organization was done to clean up the templates, trying to figure what functions moved where(and even worse, if they were renamed) it can be a bit of a slog to sort through - not insurmountable, but a timesink that we'd rather avoid. So, below is a master list of functions that were moved around, removed or renamed, as well as when other stuff like datablocks got moved around. This way, you can easily look up what's where and port over your custom modifications to the appropriate spot without having to track everything down yourself.

**Changes to functions in the template**

* /main.cs
  * createCanvas() moved to core/canvas.cs
  * isScriptFile() moved to core/helperFunctions.cs
  * onStart() empty function removed
  * parseArgs() empty function removed
* core/main.cs
  * onStart() replaced by direct execution, sidestepping the package initialization.
  * onExit deprecated
  * loadKeybindings() currently deprecated
  * parseArgs() moved to core/parseArgs.cs
* core/scripts/client/commands.cs
  * clientCmdSyncEditorGui => tools/worldEditor/scripts/cameraCommands.ed.cs

**Relocated Files**

| Original File Location                                            | New File Location                                                     |
| ----------------------------------------------------------------- | --------------------------------------------------------------------- |
| core/scripts/client/audio.cs                                      | core/audio.cs                                                         |
| core/scripts/client/audioAmbiences.cs                             | core/sfx/audioAmbiences.cs                                            |
| core/scripts/client/audioData.cs                                  | core/sfx/audioData.cs                                                 |
| core/scripts/client/audioDescriptioncs.cs                         | core/sfx/audioDescriptions.cs                                         |
| core/scripts/client/audioEnvironments.cs                          | core/sfx/audioEnvironments.cs                                         |
| core/scripts/client/audioStates.cs                                | core/sfx/audioStates.cs                                               |
| core/scripts/client/canvas.cs                                     | core/canvas.cs                                                        |
| core/scripts/client/centerPrint.cs                                | \[FPSGameplay Module]/scripts/client/centerPrint.cs                   |
| core/scripts/client/clouds.cs                                     | core/gfxData/clouds.cs                                                |
| core/scripts/client/commonMaterialData.cs                         | core/gfxData/commonMaterialData.cs                                    |
| core/scripts/client/cursor.cs                                     | core/cursor.cs                                                        |
| core/scripts/client/lighting.cs                                   | core/lighting.cs                                                      |
| core/scripts/client/message.cs                                    | \[FPSGameplay module]/scripts/client/message.cs                       |
| core/scripts/client/metrics.cs                                    | \[UI Module]/scripts/ui/profiler.gui                                  |
| core/scripts/client/postFx.cs                                     | core/postFx.cs                                                        |
| core/scripts/client/scatterSky.cs                                 | core/gfxData/scatterSky.cs                                            |
| core/scripts/client/shaders.cs                                    | core/gfxData/shaders.cs                                               |
| core/scripts/client/terrainBlock.cs                               | core/gfxData/terrainBlock.cs                                          |
| core/scripts/client/water.cs                                      | core/gfxData/water.cs                                                 |
| core/scripts/client/lighting/advanced/deferredShading.cs          | core/lighting/advanced/deferredShading.cs                             |
| core/scripts/client/lighting/advanced/depthViz.png                | tools/worldEditor/images/depthviz.png                                 |
| core/scripts/client/lighting/advanced/depthViz.png                | tools/worldEditor/images/depthviz.png                                 |
| core/scripts/client/lighting/advanced/init.cs                     | core/lighting/advanced/init.cs                                        |
| core/scripts/client/lighting/advanced/lightViz.cs                 | tools/worldEditor/scripts/lightViz.cs                                 |
| core/scripts/client/lighting/advanced/shaders.cs                  | core/lighting/advanced/shaders.cs                                     |
| core/scripts/client/lighting/advanced/shadowViz.cs                | tools/worldEditor/scripts/shadowViz.cs                                |
| core/scripts/client/lighting/advanced/shadowViz.gui               | tools/worldEditor/gui/shadowViz.gui                                   |
| core/scripts/client/lighting/basic/init.cs                        | core/lighting/advanced/init.cs                                        |
| core/scripts/client/lighting/basic/shadowFilter.cs                | core/lighting/basic/shadowFilter.cs                                   |
| core/scripts/client/lighting/shadowMaps/init.cs                   | core/lighting/shadowMaps/init.cs                                      |
| core/scripts/client/postFx/textures/caustics\_1.png               | core/images/caustics\_1.png                                           |
| core/scripts/client/postFx/textures/caustics\_2.png               | core/images/caustics\_2.png                                           |
| core/scripts/client/postFx/AreaMap33.dds                          | core/images/AreaMap33.dds                                             |
| core/scripts/client/postFx/caustics.cs                            | core/postFX/caustics.cs                                               |
| core/scripts/client/postFx/chromaticLens.cs                       | core/postFX/chromaticLens.cs                                          |
| core/scripts/client/postFx/default.postfxpreset.cs                | core/postFX/default.postfxpreset.cs                                   |
| core/scripts/client/postFx/dof.cs                                 | core/postFX/dof.cs                                                    |
| core/scripts/client/postFx/edgeAA.cs                              | core/postFX/edgeAA.cs                                                 |
| core/scripts/client/postFx/flash.cs                               | core/postFX/flash.cs                                                  |
| core/scripts/client/postFx/fog.cs                                 | core/postFX/fog.cs                                                    |
| core/scripts/client/postFx/fxaa.cs                                | core/postFX/fxaa.cs                                                   |
| core/scripts/client/postFx/GammaPostFX.cs                         | core/postFX/GammaPostFX.cs                                            |
| core/scripts/client/postFx/glow.cs                                | core/postFX/glow.cs                                                   |
| core/scripts/client/postFx/hdr.cs                                 | core/postFX/hdr.cs                                                    |
| core/scripts/client/postFx/lightRay.cs                            | core/postFX/lightRay.cs                                               |
| core/scripts/client/postFx/MLAA.cs                                | core/postFX/MLAA.cs                                                   |
| core/scripts/client/postFx/MotionBlurFx.cs                        | core/postFX/MotionBlurFx.cs                                           |
| core/scripts/client/postFx/noise.png                              | core/images/noise.png                                                 |
| core/scripts/client/postFx/null\_color\_ramp.png                  | core/images/null\_color\_ramp.cs                                      |
| core/scripts/client/postFx/ovrBarrelDistortion.cs                 | core/postFX/ovrBarrelDistortion.cs                                    |
| core/scripts/client/postFx/postFXManager.gui                      | core/postFX/postFXManager.gui                                         |
| core/scripts/client/postFx/postFXManager.gui.cs                   | core/postFX/postFXManager.gui.cs                                      |
| core/scripts/client/postFx/postFXManager.gui.settings.cs          | core/postFX/postFXManager.gui.settings.cs                             |
| core/scripts/client/postFx/postFXManager.persistance.cs           | core/postFX/postFXManager.persistance.cs                              |
| core/scripts/client/postFx/ssao.cs                                | core/postFX/ssao.cs                                                   |
| core/scripts/client/postFx/turbulence.cs                          | core/postFX/turbulence.cs                                             |
| core/scripts/client/postFx/vignette.cs                            | core/postFX/vignette.cs                                               |
| core/scripts/gui/messageBoxes/IODropdownDlg.ed.gui                | tools/gui/messageBoxes/IODropdownDlg.ed.gui                           |
| core/scripts/gui/messageBoxes/messageBox.ed.cs                    | tools/gui/messageBoxes/messageBox.ed.cs                               |
| core/scripts/gui/messageBoxes/messageBoxOK.ed.gui                 | tools/gui/messageBoxes/messageBoxOK.ed.gui                            |
| core/scripts/gui/messageBoxes/messageBoxOKBuy.ed.gui              | tools/gui/messageBoxes/messageBoxOKBuy.ed.gui                         |
| core/scripts/gui/messageBoxes/messageBoxOKCancel.ed.gui           | tools/gui/messageBoxes/messageBoxOKCancel.ed.gui                      |
| core/scripts/gui/messageBoxes/messageBoxOKCancelDetailsDlg.ed.gui | tools/gui/messageBoxes/messageBoxOKCancelDetailsDlg.ed.gui            |
| core/scripts/gui/messageBoxes/messageBoxOKYesNo.ed.gui            | tools/gui/messageBoxes/messageBoxOKYesNo.ed.gui                       |
| core/scripts/gui/messageBoxes/messageBoxOKYesNoCancel.ed.gui      | tools/gui/messageBoxes/messageBoxOKYesNoCancel.ed.gui                 |
| core/scripts/gui/messageBoxes/messagePopup.ed.gui                 | tools/gui/messageBoxes/messagePopup.ed.gui                            |
| core/scripts/gui/cursors.cs                                       | \[UI Module]scripts/cursors.cs                                        |
| core/scripts/gui/FileDialog.cs                                    | \[UI Module]/scripts/gui/FileDialog.cs                                |
| core/scripts/gui/FileDialog.gui                                   | \[UI Module]/scripts/gui/FileDialog.gui                               |
| core/scripts/gui/guiMusicPlayer.cs                                | \[UI Module]/scripts/gui/guiMusicPlayer.cs                            |
| core/scripts/gui/guiMusicPlayer.gui                               | \[UI Module]/scripts/gui/guiMusicPlayer.gui                           |
| core/scripts/gui/guiTreeViewCtrl.cs                               | \[UI Module]/scripts/gui/guiTreeViewCtrl.cs                           |
| core/scripts/gui/help.cs                                          | \[UI Module]/scripts/gui/help.cs                                      |
| core/scripts/server/audio.cs                                      | \[clientServer Module]/scripts/server/audio.cs                        |
| core/scripts/server/camera.cs                                     | \[FPSGameplay Module]/scripts/server/camera.cs                        |
| core/scripts/server/centerPrint.cs                                | \[FPSGameplay Module]/scripts/server/centerPrint.cs                   |
| core/scripts/server/clientConnection.cs                           | \[clientServer Module]/scripts/server/connectionToClient.cs           |
| core/scripts/server/defaults.cs                                   | \[clientServer Module]/scripts/server/defaults.cs                     |
| core/scripts/server/kickban.cs                                    | \[clientServer Module]/scripts/server/kickban.cs                      |
| core/scripts/server/levelInfo.cs                                  | \[clientServer Module]/scripts/server/levelInfo.cs                    |
| core/scripts/server/message.cs                                    | \[clientServer Module]/scripts/server/message.cs                      |
| core/scripts/server/missionDownload.cs                            | \[clientServer Module]/scripts/server/levelDownload.cs                |
| core/scripts/server/missionLoad.cs                                | \[clientServer Module]/scripts/server/levelLoad.cs                    |
| core/scripts/server/server.cs                                     | \[clientServer Module]/scripts/server/server.cs                       |
| core/scripts/server/spawn.cs                                      | \[FPSGameplay Module]/scripts/server/spawn.cs                         |
| scripts/client/audioData.cs                                       | \[FPSGameplay Module]/scripts/datablocks/audioData.cs                 |
| scripts/client/chatHud.cs                                         | \[FPSGameplay Module]/scripts/client/chatHud.cs                       |
| scripts/client/client.cs                                          | \[FPSGameplay Module]/scripts/client/clientCommands.cs                |
| scripts/client/default.bind.cs.cs                                 | \[FPSGameplay Module]/scripts/client/default.keybinds.cs              |
| scripts/client/messageHud.cs                                      | \[FPSGameplay Module]/scripts/client/messageHud.cs                    |
| scripts/client/missionDownload.cs                                 | \[clientServer Module]/scripts/client/levelDownload.cs                |
| scripts/client/playerList.cs                                      | \[FPSGameplay Module]/scripts/client/playerList.cs                    |
| scripts/client/serverConnection.cs                                | \[clientServer Module]/scripts/client/connectionToServer.cs           |
| scripts/client/messageHud.cs                                      | \[FPSGameplay Module]/scripts/client/messageHud.cs                    |
| scripts/gui/chooseLevelDlg.cs                                     | \[UI Module]/scripts/chooseLevelDlg.cs                                |
|                                                                   |                                                                       |
| scripts/gui/optionsDlg.cs                                         | \[UI Module]/scripts/optionsMenu.cs                                   |
| scripts/gui/playGui.cs                                            | \[FPSGameplay Module]/scripts/gui/playGui.cs                          |
| scripts/gui/startupGui.cs                                         | \[UI Module]/scripts/startupGui.cs                                    |
| scripts/server/aiPlayer.cs                                        | \[FPSGameplay Module]/scripts/server/aiPlayer.cs                      |
| scripts/server/camera.cs                                          | \[FPSGameplay Module]/scripts/server/camera.cs                        |
| scripts/server/cheetah.cs                                         | \[FPSGameplay Module]/scripts/server/cheetah.cs                       |
| scripts/server/commands.cs                                        | \[FPSGameplay Module]/scripts/server/commands.cs                      |
| scripts/server/gameDM.cs                                          | \[FPSGameplay Module]/scripts/server/deathMatchGame.cs                |
| scripts/server/health.cs                                          | \[FPSGameplay Module]/scripts/server/health.cs                        |
| scripts/server/inventory.cs                                       | \[FPSGameplay Module]/scripts/server/inventory.cs                     |
| scripts/server/item.cs                                            | \[FPSGameplay Module]/scripts/server/item.cs                          |
| scripts/server/physicsShape.cs                                    | \[FPSGameplay Module]/scripts/server/physicsShape.cs                  |
| scripts/server/player.cs                                          | \[FPSGameplay Module]/scripts/server/player.cs                        |
| scripts/server/projectile.cs                                      | \[FPSGameplay Module]/scripts/server/projectile.cs                    |
| scripts/server/proximityMine.cs                                   | \[FPSGameplay Module]/scripts/server/proximityMine.cs                 |
| scripts/server/radiusDamage.cs                                    | \[FPSGameplay Module]/scripts/server/radiusDamage.cs                  |
| scripts/server/shapeBase.cs                                       | \[FPSGameplay Module]/scripts/server/shapeBase.cs                     |
| scripts/server/teleporter.cs                                      | \[FPSGameplay Module]/scripts/server/teleporter.cs                    |
| scripts/server/triggers.cs                                        | \[FPSGameplay Module]/scripts/server/triggers.cs                      |
| scripts/server/turret.cs                                          | \[FPSGameplay Module]/scripts/server/turret.cs                        |
| scripts/server/vehicle.cs                                         | \[FPSGameplay Module]/scripts/server/vehicle.cs                       |
| scripts/server/vehicleWheeled.cs                                  | \[FPSGameplay Module]/scripts/server/vehicleWheeled.cs                |
| scripts/server/VolumetricFog.cs                                   | \[FPSGameplay Module]/scripts/server/VolumetricFog.cs                 |
| scripts/server/weapon.cs                                          | \[FPSGameplay Module]/scripts/server/weapon.cs                        |
| art/datablocks/vehicles/cheetaCar.cs                              | \[FPSGameplay Module]/scripts/datablocks/vehicles/cheetaCar.cs        |
| art/datablocks/weapons/grenadefx.cs                               | \[FPSGameplay Module]/scripts/datablocks/weapons/grenadefx.cs         |
| art/datablocks/weapons/Lurker.cs                                  | \[FPSGameplay Module]/scripts/datablocks/weapons/Lurker.cs            |
| art/datablocks/weapons/NewWeaponTemplate.cs                       | \[FPSGameplay Module]/scripts/datablocks/weapons/NewWeaponTemplate.cs |
| art/datablocks/weapons/ProxMine.cs                                | \[FPSGameplay Module]/scripts/datablocks/weapons/ProxMine.cs          |
| art/datablocks/weapons/rocketfx.cs                                | \[FPSGameplay Module]/scripts/datablocks/weapons/rocketfx.cs          |
| art/datablocks/weapons/Ryder.cs                                   | \[FPSGameplay Module]/scripts/datablocks/weapons/Ryder.cs             |
| art/datablocks/weapons/Turret.cs                                  | \[FPSGameplay Module]/scripts/datablocks/weapons/Turret.cs            |
| art/datablocks/aiPlayer.cs                                        | \[FPSGameplay Module]/scripts/datablocks/aiPlayer.cs                  |
| art/datablocks/audioProfiles.cs                                   | \[FPSGameplay Module]/scripts/datablocks/audioProfiles.cs             |
| art/datablocks/environment.cs                                     | \[FPSGameplay Module]/scripts/datablocks/environment.cs               |
| art/datablocks/health.cs                                          | \[FPSGameplay Module]/scripts/datablocks/health.cs                    |
| art/datablocks/lights.cs                                          | \[FPSGameplay Module]/scripts/datablocks/lights.cs                    |
| art/datablocks/managedDatablocks.cs                               | \[FPSGameplay Module]/scripts/datablocks/managedDatablocks.cs         |
| art/datablocks/particles.cs                                       | \[FPSGameplay Module]/scripts/datablocks/particles.cs                 |
| art/datablocks/physics.cs                                         | \[FPSGameplay Module]/scripts/datablocks/physics.cs                   |
| art/datablocks/player.cs                                          | \[FPSGameplay Module]/scripts/datablocks/player.cs                    |
| art/datablocks/rigidShape.cs                                      | \[FPSGameplay Module]/scripts/datablocks/rigidShape.cs                |
| art/datablocks/teleporter.cs                                      | \[FPSGameplay Module]/scripts/datablocks/teleporter.cs                |
| art/datablocks/triggers.cs                                        | \[FPSGameplay Module]/scripts/datablocks/triggers.cs                  |
| art/datablocks/weapon.cs                                          | \[FPSGameplay Module]/scripts/datablocks/weapon.cs                    |
| art/decals/Bullet Holes/BulletHole\_Glass.dds                     | \[FPSGameplay Module]/art/decals/Bullet Holes/BulletHole\_Glass.dds   |
| art/decals/Bullet Holes/BulletHole\_Walls.dds                     | \[FPSGameplay Module]/art/decals/Bullet Holes/BulletHole\_Walls.dds   |
| art/decals/bullet\_hole.png                                       | \[FPSGameplay Module]/art/decals/bullet\_hole.png                     |
| art/decals/defaultBlobShadow.png                                  | \[FPSGameplay Module]/art/decals/defaultBlobShadow.png                |
| art/decals/managedDecalData.cs                                    | \[FPSGameplay Module]/scripts/datablocks/managedDecalData.cs          |
| art/decals/materials.cs                                           | \[FPSGameplay Module]/art/decals/materials.cs                         |
| art/decals/rBlast.png                                             | \[FPSGameplay Module]/art/decals/rBlast.png                           |
| art/decals/scorch\_decal.png                                      | \[FPSGameplay Module]/art/decals/scorch\_decal.png                    |
| art/environment/precipitation/rain.png                            | \[FPSGameplay Module]/art/environment/precipitation/rain.png          |
| art/environment/precipitation/water\_splash.png                   | \[FPSGameplay Module]/art/environment/precipitation/water\_splash.png |
| art/environment/Fog\_Cube.cs                                      | \[FPSGameplay Module]/art/environment/Fog\_Cube.cs                    |
| art/environment/Fog\_Cube.DAE                                     | \[FPSGameplay Module]/art/environment/Fog\_Cube.DAE                   |
| art/environment/FogMod\_heavy.dds                                 | \[FPSGameplay Module]/art/environment/FogMod\_heavy.dds               |
| art/environment/FogMod\_light.dds                                 | \[FPSGameplay Module]/art/environment/FogMod\_light.dds               |
| art/environment/FogMod\_med.dds                                   | \[FPSGameplay Module]/art/environment/FogMod\_med.dds                 |
| art/environment/grass1.png                                        | \[FPSGameplay Module]/art/environment/grass1.png                      |
| art/environment/grass2.png                                        | \[FPSGameplay Module]/art/environment/grass2.png                      |
| art/environment/grass3.png                                        | \[FPSGameplay Module]/art/environment/grass3.png                      |
| art/environment/lightning.png                                     | \[FPSGameplay Module]/art/environment/lightning.png                   |
| art/environment/LightVolume\_Sphere.cs                            | \[FPSGameplay Module]/art/environment/LightVolume\_Sphere.cs          |
| art/environment/LightVolume\_Sphere.DAE                           | \[FPSGameplay Module]/art/environment/LightVolume\_Sphere.DAE         |
| art/environment/LightVolume\_Sphere.dts                           | \[FPSGameplay Module]/art/environment/LightVolume\_Sphere.dts         |
| art/environment/materials.cs                                      | \[FPSGameplay Module]/art/environment/materials.cs                    |
| art/environment/plant1.png                                        | \[FPSGameplay Module]/art/environment/plant1.png                      |
| art/gui/weaponHud/bino.png                                        | \[FPSGameplay Module]/art/gui/weaponHud/bino.png                      |
| art/gui/weaponHud/blank.png                                       | \[FPSGameplay Module]/art/gui/weaponHud/blank.png                     |
| art/gui/weaponHud/crossHair.png                                   | \[FPSGameplay Module]/art/gui/weaponHud/crossHair.png                 |
| art/gui/weaponHud/lurker.png                                      | \[FPSGameplay Module]/art/gui/weaponHud/lurker.png                    |
| art/gui/weaponHud/mine.png                                        | \[FPSGameplay Module]/art/gui/weaponHud/mine.png                      |
| art/gui/weaponHud/reticle\_rocketlauncher.png                     | \[FPSGameplay Module]/art/gui/weaponHud/reticle\_rocketlauncher.png   |
| art/gui/weaponHud/ryder.png                                       | \[FPSGameplay Module]/art/gui/weaponHud/ryder.png                     |
| art/gui/weaponHud/swarmer.png                                     | \[FPSGameplay Module]/art/gui/weaponHud/swarmer.png                   |
| art/gui/weaponHud/turret.png                                      | \[FPSGameplay Module]/art/gui/weaponHud/turret.png                    |
| art/gui/background.png                                            | \[FPSGameplay Module]/art/gui/background.png                          |
|                                                                   |                                                                       |
| art/gui/chatHud.gui                                               | \[FPSGameplay Module]/scripts/gui/chatHud.gui                         |
| art/gui/chooseLevelDlg.gui                                        | \[UI Module]/scripts/guis/chooseLevelDlg.gui                          |
| art/gui/damageBottom.png                                          | \[FPSGameplay Module]/art/gui/damageBottom.png                        |
| art/gui/damageFront.png                                           | \[FPSGameplay Module]/art/gui/damageFront.png                         |
| art/gui/damageLeft.png                                            | \[FPSGameplay Module]/art/gui/damageLeft.png                          |
| art/gui/damageRight.png                                           | \[FPSGameplay Module]/art/gui/damageRight.png                         |
| art/gui/damageTop.png                                             | \[FPSGameplay Module]/art/gui/damageTop.png                           |
| art/gui/hudfill.png                                               | \[FPSGameplay Module]/art/gui/hudfill.png                             |
| art/gui/hudlessGui.gui                                            | \[FPSGameplay Module]/scripts/gui/hudlessGui.gui                      |
| art/gui/joinServerDlg.gui                                         | \[UIModule]/scripts/gui/joinServerDlg.gui                             |
| art/gui/lagIcon.png                                               | \[UI Module]/art/lagIcon.png                                          |
| art/gui/loadingGui.gui                                            | \[FPSGameplay Module]/scripts/gui/loadingGui.gui                      |
| art/gui/mainMenuGui.gui                                           | \[UI Module]/scripts/guis/mainMenuGui.gui                             |
| art/gui/next-button\_d.png                                        | \[UI Module]/art/next-button\_d.png                                   |
| art/gui/next-button\_h.png                                        | \[UI Module]/art/next-button\_h.png                                   |
| art/gui/next-button\_n.png                                        | \[UI Module]/art/next-button\_n.png                                   |
| art/gui/no-preview.png                                            | \[UI Module]/art/no-preview.png                                       |
| art/gui/optionsDlg.gui                                            | \[UI Module]/scripts/guis/optionsMenu.gui                             |
| art/gui/playerList.gui                                            | \[FPSGameplay Module]/scripts/gui/playerList.gui                      |
| art/gui/playGui.gui                                               | \[FPSGameplay Module]/scripts/gui/playGui.gui                         |
| art/gui/previous-button\_d.png                                    | \[UI Module]/art/previous-button\_d.png                               |
| art/gui/previous-button\_h.png                                    | \[UI Module]/art/previous-button\_h.png                               |
| art/gui/previous-button\_n.png                                    | \[UI Module]/art/previous-button\_n.png                               |
| art/gui/remapDlg.gui                                              | \[UI Module]/scripts/guis/remapDlg.gui                                |
| art/gui/splash.png                                                | data/splash.png                                                       |
| art/gui/StartupGui.gui                                            | \[UI Module]/scripts/guis/StartupGui.gui                              |
| art/gui/Torque-3D-logo-w.png                                      | \[UI Module]/art/Torque-3D-logo-w.png                                 |
| art/gui/Torque-3D-logo.png                                        | \[UI Module]/art/Torque-3D-logo.png                                   |
| art/gui/Torque-3D-logo\_alt.png                                   | \[UI Module]/art/Torque-3D-logo\_alt.png                              |
| art/particles/bubble.png                                          | \[FPSGameplay Module]/art/particles/bubble.png                        |
| art/particles/droplet.png                                         | \[FPSGameplay Module]/art/particles/droplet.png                       |
| art/particles/Dust.png                                            | \[FPSGameplay Module]/art/particles/Dust.png                          |
| art/particles/dustParticle.png                                    | \[FPSGameplay Module]/art/particles/dustParticle.png                  |
| art/particles/ember.png                                           | \[FPSGameplay Module]/art/particles/ember.png                         |
| art/particles/fire.png                                            | \[FPSGameplay Module]/art/particles/fire.png                          |
| art/particles/fireball.png                                        | \[FPSGameplay Module]/art/particles/fireball.png                      |
| art/particles/firefly.png                                         | \[FPSGameplay Module]/art/particles/firefly.png                       |
| art/particles/flame.png                                           | \[FPSGameplay Module]/art/particles/flame.png                         |
| art/particles/flare.png                                           | \[FPSGameplay Module]/art/particles/flare.png                         |
| art/particles/impact.png                                          | \[FPSGameplay Module]/art/particles/impact.png                        |
| art/particles/managedParticleData.cs                              | \[FPSGameplay Module]/scripts/datablocks/managedParticleData.cs       |
| art/particles/managedEmitterData.cs                               | \[FPSGameplay Module]/scripts/datablocks/managedEmitterData.cs        |
| art/particles/millsplash01.png                                    | \[FPSGameplay Module]/art/particles/millsplash01.png                  |
| art/particles/ricochet.png                                        | \[FPSGameplay Module]/art/particles/ricochet.png                      |
| art/particles/smoke.png                                           | \[FPSGameplay Module]/art/particles/smoke.png                         |
| art/particles/spark.png                                           | \[FPSGameplay Module]/art/particles/spark.png                         |
| art/particles/spark\_wet.png                                      | \[FPSGameplay Module]/art/particles/spark\_wet.png                    |
| art/particles/Sparkparticle.png                                   | \[FPSGameplay Module]/art/particles/Sparkparticle.png                 |
| art/particles/splash.png                                          | \[FPSGameplay Module]/art/particles/splash.png                        |
| art/particles/steam.png                                           | \[FPSGameplay Module]/art/particles/steam.png                         |
| art/particles/Steak.png                                           | \[FPSGameplay Module]/art/particles/Streak.png                        |
| art/particles/wake.png                                            | \[FPSGameplay Module]/art/particles/wake.png                          |
| art/particles/waterDrip.png                                       | \[FPSGameplay Module]/art/particles/waterDrip.png                     |
| art/prefabs/fire.prefab                                           | \[FPSGameplay Module]/art/prefabs/fire.prefab                         |
| art/ribbons/materials.cs                                          | \[FPSGameplay Module]/art/particles/ribbons/materials.cs              |
| art/ribbons/ribbons.cs                                            | \[FPSGameplay Module]/scripts/datablocks/ribbons.cs                   |
| art/ribbons/ribTex.png                                            | \[FPSGameplay Module]/art/particles/ribbons/ribTex.png                |
| art/roads/defaultpath.png                                         | \[FPSGameplay Module]/art/roads/defaultpath.png                       |
| art/roads/defaultpath\_normal.png                                 | \[FPSGameplay Module]/art/roads/defaultpath\_normal.png               |
| art/roads/defaultRoadTextureOther.png                             | \[FPSGameplay Module]/art/roads/defaultRoadTextureOther.png           |
| art/roads/defaultRoadTextureTop.png                               | \[FPSGameplay Module]/art/roads/defaultRoadTextureTop.png             |
| art/roads/materials.cs                                            | \[FPSGameplay Module]/art/roads/materials.cs                          |
| art/shapes/actors/common/\*                                       | \[FPSGameplay Module]/art/shapes/actors/common/\*                     |
| art/shapes/actors/Soldier/Anims/\*                                | \[FPSGameplay Module]/art/shapes/actors/Soldier/Anims/\*              |
| art/shapes/actors/Soldier/FP/\*                                   | \[FPSGameplay Module]/art/shapes/actors/Soldier/FP/\*                 |
| art/shapes/Cheetah/\*                                             | \[FPSGameplay Module]/art/shapes/Cheetah/\*                           |
| art/shapes/cube/\*                                                | \[FPSGameplay Module]/art/shapes/cube/\*                              |
| art/shapes/groundCover/\*                                         | \[FPSGameplay Module]/art/shapes/groundCover/\*                       |
| art/shapes/items/kit/\*                                           | \[FPSGameplay Module]/art/shapes/items/kit/\*                         |
| art/shapes/items/patch/\*                                         | \[FPSGameplay Module]/art/shapes/items/patch/\*                       |
| art/shapes/rocks/\*                                               | \[FPSGameplay Module]/art/shapes/rocks/\*                             |
| art/shapes/station/\*                                             | \[FPSGameplay Module]/art/shapes/station/\*                           |
| art/shapes/teleporter/\*                                          | \[FPSGameplay Module]/art/shapes/teleporter/\*                        |
| art/shapes/trees/defaultTree/\*                                   | \[FPSGameplay Module]/art/shapes/trees/defaultTree/\*                 |
| art/shapes/weapons/Grenade/\*                                     | \[FPSGameplay Module]/art/shapes/weapons/Grenade/\*                   |
| art/shapes/weapons/Lurker/\*                                      | \[FPSGameplay Module]/art/shapes/weapons/Lurker/\*                    |
| art/shapes/weapons/ProxMine/PlayerAnims/\*                        | \[FPSGameplay Module]/art/shapes/weapons/ProxMine/PlayerAnims/\*      |
| art/shapes/weapons/ProxMine/\*                                    | \[FPSGameplay Module]/art/shapes/weapons/ProxMine/\*                  |
| art/shapes/weapons/Ryder/PlayerAnims/\*                           | \[FPSGameplay Module]/art/shapes/weapons/Ryder/PlayerAnims/\*         |
| art/shapes/weapons/Ryder/\*                                       | \[FPSGameplay Module]/art/shapes/weapons/Ryder/\*                     |
| art/shapes/weapons/shared/\*                                      | \[FPSGameplay Module]/art/shapes/weapons/shared/\*                    |
| art/shapes/weapons/Turret/PlayerAnims/\*                          | \[FPSGameplay Module]/art/shapes/weapons/Turret/PlayerAnims/\*        |
| art/shapes/weapons/Turret/\*                                      | \[FPSGameplay Module]/art/shapes/weapons/Turret/\*                    |
| art/skies/clouds/\*                                               | \[FPSGameplay Module]/art/skies/clouds/\*                             |
| art/skies/Desert\_Sky/cubemap/\*                                  | \[FPSGameplay Module]/art/skies/Desert\_Sky/cubemap/\*                |
| art/skies/Desert\_Sky/\*                                          | \[FPSGameplay Module]/art/skies/Desert\_Sky/\*                        |
| art/skies/night/\*                                                | \[FPSGameplay Module]/art/skies/night/\*                              |
| art/sound/cheetah/\*                                              | \[FPSGameplay Module]/sound/cheetah/\*                                |
| art/sound/environment/\*                                          | \[FPSGameplay Module]/sound/environment/\*                            |
| art/sound/turret/\*                                               | \[FPSGameplay Module]/sound/turret/\*                                 |
| art/sound/ui/\*                                                   | \[FPSGameplay Module]/sound/ui/\*                                     |
| art/sound/weapons/\*                                              | \[FPSGameplay Module]/sound/weapons/\*                                |
| art/sound/\*                                                      | \[FPSGameplay Module]/sound/\*                                        |
| art/terrains/Example/\*                                           | \[FPSGameplay Module]/art/terrains/Example/\*                         |
| art/terrains/\*                                                   | \[FPSGameplay Module]/art/terrains/\*                                 |
| art/water/\*                                                      | \[FPSGameplay Module]/art/water/\*                                    |

## Physically Based Rendering <a href="#toc9" id="toc9"></a>
