# Version 3.7

* [GitHub release](https://github.com/GarageGames/Torque3D/releases/tag/v3.7)
* [Release announcement](http://www.garagegames.com/community/blogs/view/22988)
* [Release candidate announcement](http://www.garagegames.com/community/blogs/view/22963)

## Notes <a href="#toc0" id="toc0"></a>

* Most uses of ConsoleMethod have been changed to use DefineEngineMethod. The old macros haven't been removed, and are in fact still used for variadic script functions, which aren't currently possible with the DefineEngineMethod macros. But be warned that there are a lot of changes in this area, which may cause conflicts if you've modified any of the console methods.
* James Urquhart's major console function call refactor has finally found its way in, which has meant significant refactoring to the way TorqueScript works under the hood, including new wrappers for console types. This has introduced some subtle bugs we've managed to find, but if you're relying on custom console methods and behaviour, we urge you to double-check those and make sure they still behave exactly as expected.
* [A bug](https://github.com/GarageGames/Torque3D/issues/164) in quaternion math has been fixed, but you might find that code relying on the broken behaviour needs to be changed.
* There's a new version of the SimDictionary based on the C++11 STL hashmap. You'll find a commented-out #define in torqueConfig.h which you can enable if you like. According to the contributors, it's worth doing if you have a lot of SimObjects about at the same time.
* The projects.xml file is now part of the main repo, instead of being part of the Project Manager repo. Just so you know, and don't go looking for it there.
* isObject is now stricter about what's actually an object. Where before, the string "3.14" would be cast to the integer "3" and resolved to object ID 3, the whole string is now validated first, and if it's not a valid integer, it won't count as an object ID. (Note that the method still also accepts object names as usual.) This logic expands to other types of object resolution as well - so "3.14".getClassName() now won't work.

## Issues closed [source](https://github.com/GarageGames/Torque3D/issues?q=milestone%3A3.7+is%3Aclosed) <a href="#toc1" id="toc1"></a>

* [#1327](https://github.com/GarageGames/Torque3D/pull/1327) GFXGLDevice setShader fix.
* [#1326](https://github.com/GarageGames/Torque3D/pull/1326) GFXGLDevice setShader fix
* [#1324](https://github.com/GarageGames/Torque3D/pull/1324) Fixed a issue with the terrain blending having hard-edges.
* [#1321](https://github.com/GarageGames/Torque3D/pull/1321) No need for server-only aps to generate visible textures.
* [#1316](https://github.com/GarageGames/Torque3D/pull/1316) Fix for rendering particles to the glow buffer
* [#1315](https://github.com/GarageGames/Torque3D/issues/1315) particle glow bug
* [#1316](https://github.com/GarageGames/Torque3D/pull/1316) Fix for rendering particles to the glow buffer
* [#1292](https://github.com/GarageGames/Torque3D/issues/1292) Editor ribbon cannot be expanded once collapsed
* [#1303](https://github.com/GarageGames/Torque3D/pull/1303) Add workaround for issue #1292
* [#1302](https://github.com/GarageGames/Torque3D/issues/1302) Vignette PostFX does not save
* [#1305](https://github.com/GarageGames/Torque3D/pull/1305) Apply vignette settings properly for #1302
* [#1313](https://github.com/GarageGames/Torque3D/pull/1313) Added toolbar expand button images.
* [#1301](https://github.com/GarageGames/Torque3D/pull/1301) setExtent now takes Strings instead of leaving args as pointers.
* [#1287](https://github.com/GarageGames/Torque3D/issues/1287) Forest in Outpost level not appearing in Ubuntu
* [#1307](https://github.com/GarageGames/Torque3D/pull/1307) tsForestItemData: default to no bounds instead of crazy bounds
* [#1310](https://github.com/GarageGames/Torque3D/pull/1310) Corrected another filename case
* [#1309](https://github.com/GarageGames/Torque3D/pull/1309) Add more info to fatal assert in SceneContainer
* [#1308](https://github.com/GarageGames/Torque3D/pull/1308) Case-sensitive filenames for Linux
* [#1270](https://github.com/GarageGames/Torque3D/pull/1270) terrain texturecache prior functionality preservation
* [#1294](https://github.com/GarageGames/Torque3D/pull/1294) opengl crashfix: cannot self-multiply a uniform. use a temp-variable.
* [#1277](https://github.com/GarageGames/Torque3D/issues/1277) Level save with populated forest results in "FileStream::open::empty filename"
* [#1290](https://github.com/GarageGames/Torque3D/pull/1290) Patch to fix no-sound in Linux
* [#920](https://github.com/GarageGames/Torque3D/pull/920) Fix for fuzzy borders between textures
* [#1289](https://github.com/GarageGames/Torque3D/issues/1289) Dedicated server crashes
* [#1298](https://github.com/GarageGames/Torque3D/pull/1298) Remove value constructors for ConsoleValueRef & fix callbacks
* [#1290](https://github.com/GarageGames/Torque3D/pull/1290) Patch to fix no-sound in Linux
* [#1289](https://github.com/GarageGames/Torque3D/issues/1289) Dedicated server crashes
* [#1288](https://github.com/GarageGames/Torque3D/pull/1288) Issue 1277
* [#1283](https://github.com/GarageGames/Torque3D/pull/1283) corrects getrandom to behave as documented.
* [#1279](https://github.com/GarageGames/Torque3D/pull/1279) Fixes issue #1277
* [#1278](https://github.com/GarageGames/Torque3D/pull/1278) Tweak Vagrant
* [#1277](https://github.com/GarageGames/Torque3D/issues/1277) Level save with populated forest results in "FileStream::open::empty filename"
* [#1269](https://github.com/GarageGames/Torque3D/pull/1269) Added missing VS2012 template files to Empty template
* [#1268](https://github.com/GarageGames/Torque3D/pull/1268) Removed main.cs.in files
* [#1252](https://github.com/GarageGames/Torque3D/pull/1252) Fix bug on DefineConsoleMethod GuiCanvas::setVideoMode.
* [#1250](https://github.com/GarageGames/Torque3D/issues/1250) fullscreen alt+tab erorrs
* [#1246](https://github.com/GarageGames/Torque3D/pull/1246) Fix GuiTreeViewCtrl::getParentItem incorrent use in ShapeEditor script files.
* [#1245](https://github.com/GarageGames/Torque3D/pull/1245) Fix GLSL include when file is empty.
* [#1244](https://github.com/GarageGames/Torque3D/pull/1244) Fix waterBasicP.glsl for HDR.
* [#1243](https://github.com/GarageGames/Torque3D/pull/1243) Simplify readme
* [#1242](https://github.com/GarageGames/Torque3D/pull/1242) Fix Linux rpath.
* [#1241](https://github.com/GarageGames/Torque3D/pull/1241) vignette\_final
* [#1238](https://github.com/GarageGames/Torque3D/pull/1238) [https://github.com/GarageGames/Torque3D/issues/770](https://github.com/GarageGames/Torque3D/issues/770) resolution
* [#1236](https://github.com/GarageGames/Torque3D/pull/1236) Revert recent style cleanup changes
* [#1234](https://github.com/GarageGames/Torque3D/pull/1234) typofix for void ColladaAppMesh::lockMesh
* [#1232](https://github.com/GarageGames/Torque3D/issues/1232) Level Output crash (development branch)
* [#1230](https://github.com/GarageGames/Torque3D/pull/1230) removal of un-implemented ShockwaveData entries from explosion.
* [#1227](https://github.com/GarageGames/Torque3D/pull/1227) Con::executef trampoline had mismatched argc values for the high end
* [#1226](https://github.com/GarageGames/Torque3D/pull/1226) fix preprocessor directive
* [#1225](https://github.com/GarageGames/Torque3D/pull/1225) Vignette updated for OpenGL
* [#1223](https://github.com/GarageGames/Torque3D/pull/1223) DeferredBumpFeat order of operations corrections
* [#1220](https://github.com/GarageGames/Torque3D/pull/1220) Fix #396
* [#1218](https://github.com/GarageGames/Torque3D/pull/1218) Revert "PR for issue #748"
* [#1216](https://github.com/GarageGames/Torque3D/pull/1216) Fix VS2008 again again
* [#1215](https://github.com/GarageGames/Torque3D/pull/1215) Default to background navmesh builds
* [#1214](https://github.com/GarageGames/Torque3D/pull/1214) Fix some issues flagged by cppcheck
* [#1212](https://github.com/GarageGames/Torque3D/pull/1212) Fixed SDL related header includes for linux
* [#1204](https://github.com/GarageGames/Torque3D/pull/1204) little typo
* [#1203](https://github.com/GarageGames/Torque3D/pull/1203) Fix shadows on Basic Lighting.
* [#1202](https://github.com/GarageGames/Torque3D/pull/1202) proper fix for [https://github.com/GarageGames/Torque3D/issues/1197](https://github.com/GarageGames/Torque3D/issues/1197)
* [#1200](https://github.com/GarageGames/Torque3D/pull/1200) Fix for minidump support
* [#1199](https://github.com/GarageGames/Torque3D/pull/1199) Added NULL check in function findItemByName.
* [#1198](https://github.com/GarageGames/Torque3D/pull/1198) Fix Bullet compilation.
* [#1197](https://github.com/GarageGames/Torque3D/issues/1197) unit tests for matrixf\_X\_matrixF causing non-compilation.
* [#1196](https://github.com/GarageGames/Torque3D/pull/1196) return the result value of scrollVisible
* [#1195](https://github.com/GarageGames/Torque3D/issues/1195) Projects from 3.6 do not work with 3.7 executable
* [#1192](https://github.com/GarageGames/Torque3D/issues/1192) MiniDump support doesnt get defined when checked off in the project manager
* [#1191](https://github.com/GarageGames/Torque3D/issues/1191) #define TORQUE\_RELEASE doesnt get defined for release builds
* [#1190](https://github.com/GarageGames/Torque3D/pull/1190) nvidia nsight debugger support.
* [#1183](https://github.com/GarageGames/Torque3D/pull/1183) Documentation
* [#1181](https://github.com/GarageGames/Torque3D/issues/1181) Crash 3.6.3 GUI Editor Locks Up
* [#1180](https://github.com/GarageGames/Torque3D/pull/1180) Add math control state functions for intel
* [#1176](https://github.com/GarageGames/Torque3D/pull/1176) Fix VS2008 again
* [#1175](https://github.com/GarageGames/Torque3D/pull/1175) feedback for \*which\* namespace is already linked.
* [#1171](https://github.com/GarageGames/Torque3D/pull/1171) extra entry in DefineConsoleFunction( queryMasterServer
* [#1170](https://github.com/GarageGames/Torque3D/pull/1170) Fix VS2008
* [#1169](https://github.com/GarageGames/Torque3D/pull/1169) Add Vagrant config
* [#1167](https://github.com/GarageGames/Torque3D/pull/1167) Remove default web deployment
* [#1165](https://github.com/GarageGames/Torque3D/pull/1165) Fix for console stack
* [#1164](https://github.com/GarageGames/Torque3D/pull/1164) Remove some dead code from OpenGL shadergen.
* [#1161](https://github.com/GarageGames/Torque3D/pull/1161) More x64 fixes - 2
* [#1159](https://github.com/GarageGames/Torque3D/pull/1159) Include navigation and testing modules by default
* [#1157](https://github.com/GarageGames/Torque3D/pull/1157) Show the canvas immediately in unix because the splash doesn't work
* [#1156](https://github.com/GarageGames/Torque3D/pull/1156) Fix issue 396
* [#1149](https://github.com/GarageGames/Torque3D/pull/1149) More x64 fixes
* [#1145](https://github.com/GarageGames/Torque3D/pull/1145) Make CMake project load all .cmake files from the module folder Updated.
* [#1141](https://github.com/GarageGames/Torque3D/pull/1141) Changed type to NetSocket
* [#1140](https://github.com/GarageGames/Torque3D/pull/1140) ambient normal on GLSL
* [#1137](https://github.com/GarageGames/Torque3D/pull/1137) Fix changes to moveSelection API
* [#1136](https://github.com/GarageGames/Torque3D/issues/1136) Bullet build is broken by linux changes
* [#1135](https://github.com/GarageGames/Torque3D/issues/1135) Object editor lod alteration fails
* [#1134](https://github.com/GarageGames/Torque3D/issues/1134) Pull Request #1026 broke the console stack
* [#1133](https://github.com/GarageGames/Torque3D/pull/1133) Rename netTest.cpp to netExamples.cpp
* [#1131](https://github.com/GarageGames/Torque3D/issues/1131) Two netTest.CPP files write to same place
* [#1130](https://github.com/GarageGames/Torque3D/pull/1130) Remove a get\* OpenGL function causing CPU-GPU sync point.
* [#1128](https://github.com/GarageGames/Torque3D/pull/1128) cloudlayer hdr packing
* [#1127](https://github.com/GarageGames/Torque3D/issues/1127) OpenGL Basic Lighting rendering issues
* [#1124](https://github.com/GarageGames/Torque3D/pull/1124) Forest wind emitter
* [#1121](https://github.com/GarageGames/Torque3D/pull/1121) Fix buffer overflows
* [#1119](https://github.com/GarageGames/Torque3D/pull/1119) OpenGL fix - fixed a crash when you activate Alpha Threshold checkbox wi…
* [#1118](https://github.com/GarageGames/Torque3D/pull/1118) fix #1117
* [#1117](https://github.com/GarageGames/Torque3D/issues/1117) OpenGL bug - removing diffuse from a skybox cause shadergen error
* [#1115](https://github.com/GarageGames/Torque3D/pull/1115) Jeff faust fix also on openGL.
* [#1100](https://github.com/GarageGames/Torque3D/pull/1100) Fixed define bug for OpenGL shadergen.
* [#1098](https://github.com/GarageGames/Torque3D/issues/1098) OpenGL basic lighting no shadows on player
* [#1097](https://github.com/GarageGames/Torque3D/issues/1097) GUI Editor moveSelection
* [#1096](https://github.com/GarageGames/Torque3D/pull/1096) Fix include guards
* [#1093](https://github.com/GarageGames/Torque3D/pull/1093) Fix setExtent
* [#1092](https://github.com/GarageGames/Torque3D/pull/1092) Walkabout navigation editor
* [#1090](https://github.com/GarageGames/Torque3D/pull/1090) Anonymous functions
* [#1089](https://github.com/GarageGames/Torque3D/pull/1089) Add profiler regions for StringTable functions
* [#1085](https://github.com/GarageGames/Torque3D/pull/1085) cubemap Mip retrieval-DX
* [#1084](https://github.com/GarageGames/Torque3D/pull/1084) OpenGL: Add project define for GLEW with php generator.
* [#1083](https://github.com/GarageGames/Torque3D/pull/1083) Fix/walkaround for OpenGL on Intel
* [#1082](https://github.com/GarageGames/Torque3D/issues/1082) OpenGL debug crash on Intel HD4000
* [#1081](https://github.com/GarageGames/Torque3D/pull/1081) Added OpenGL to projects.xml
* [#1080](https://github.com/GarageGames/Torque3D/pull/1080) Use a strong reference instead of more manual reference counting
* [#1077](https://github.com/GarageGames/Torque3D/pull/1077) Fix persistent underwater effect.
* [#1074](https://github.com/GarageGames/Torque3D/pull/1074) cleaned up variant of Accumulation volumes #768
* [#1072](https://github.com/GarageGames/Torque3D/pull/1072) Make more use of DefineConsoleMethod
* [#1067](https://github.com/GarageGames/Torque3D/pull/1067) bugfix #1066
* [#1065](https://github.com/GarageGames/Torque3D/pull/1065) winTime month fix
* [#1064](https://github.com/GarageGames/Torque3D/pull/1064) CMake fixes
* [#1061](https://github.com/GarageGames/Torque3D/pull/1061) Glow particles
* [#1056](https://github.com/GarageGames/Torque3D/pull/1056) mipmap support on OpenGL cubemap
* [#1055](https://github.com/GarageGames/Torque3D/pull/1055) Fix ShaderGen cubemap feature.
* [#1054](https://github.com/GarageGames/Torque3D/pull/1054) Style cleanup
* [#1053](https://github.com/GarageGames/Torque3D/issues/1053) development - opengl cubemap display wrong on scaled objects
* [#1049](https://github.com/GarageGames/Torque3D/pull/1049) Add VS2012 support to projectgenerator
* [#1048](https://github.com/GarageGames/Torque3D/pull/1048) missing texture format.
* [#1040](https://github.com/GarageGames/Torque3D/pull/1040) Fix spaces in TSStatic fied names.
* [#1035](https://github.com/GarageGames/Torque3D/pull/1035) Memfixes
* [#1030](https://github.com/GarageGames/Torque3D/pull/1030) Volumetric Fog Resource by Richard Marrevee.
* [#1029](https://github.com/GarageGames/Torque3D/pull/1029) Intel graphics bugfix
* [#1027](https://github.com/GarageGames/Torque3D/pull/1027) Allow normals on shadowed surfaces
* [#1026](https://github.com/GarageGames/Torque3D/pull/1026) Fix issue where console stack values were getting overwritten
* [#1025](https://github.com/GarageGames/Torque3D/pull/1025) Fix AMD render problem with missed meshes.
* [#1023](https://github.com/GarageGames/Torque3D/issues/1023) soft snapping makes systematic crash on x64
* [#1020](https://github.com/GarageGames/Torque3D/pull/1020) SimDictionary improvement
* [#1018](https://github.com/GarageGames/Torque3D/pull/1018) Ghost scoping
* [#1014](https://github.com/GarageGames/Torque3D/pull/1014) vSync on opengl
* [#1013](https://github.com/GarageGames/Torque3D/pull/1013) Fix testimg ppm
* [#1011](https://github.com/GarageGames/Torque3D/pull/1011) Fix GLCircularVolatileBuffer incorrect binding.
* [#1007](https://github.com/GarageGames/Torque3D/pull/1007) Added scriptable move triggers for AIPlayers. Fixes an issue where AIPla…
* [#1006](https://github.com/GarageGames/Torque3D/pull/1006) Fix lighting errors when all lights are disabled.
* [#1005](https://github.com/GarageGames/Torque3D/pull/1005) Revert terrain opengl
* [#1004](https://github.com/GarageGames/Torque3D/pull/1004) Fixed a crash and memory leak on the ribbon code
* [#1003](https://github.com/GarageGames/Torque3D/pull/1003) Ribbon port for opengl
* [#1002](https://github.com/GarageGames/Torque3D/pull/1002) Z Offset for Scattersky to fix the rendering issue at high altitudes.
* [#1000](https://github.com/GarageGames/Torque3D/pull/1000) FMod switching DLLS if 64 bit.
* [#999](https://github.com/GarageGames/Torque3D/pull/999) Fix so it compiles correctly on Visual Studio 2013
* [#998](https://github.com/GarageGames/Torque3D/pull/998) Fixed issue where physx3 cpu dispatcher was created multiple times
* [#997](https://github.com/GarageGames/Torque3D/pull/997) This just adds some console spam if the PostEffect Texture isn't found. …
* [#996](https://github.com/GarageGames/Torque3D/pull/996) Added support for AMD Chips
* [#995](https://github.com/GarageGames/Torque3D/pull/995) Just cleaned up some code
* [#991](https://github.com/GarageGames/Torque3D/pull/991) Bit Alignment of variables in serverQuery.cpp
* [#981](https://github.com/GarageGames/Torque3D/pull/981) Fix x64 builds.
* [#980](https://github.com/GarageGames/Torque3D/pull/980) opengl error reporting formatting
* [#977](https://github.com/GarageGames/Torque3D/pull/977) Support for physx3 in projects.xml
* [#976](https://github.com/GarageGames/Torque3D/issues/976) Parameters to callback being overwritten by method call inside callback
* [#974](https://github.com/GarageGames/Torque3D/pull/974) re-orders sound device provider wieghting
* [#971](https://github.com/GarageGames/Torque3D/pull/971) turret tracking correction, again
* [#970](https://github.com/GarageGames/Torque3D/pull/970) clamp value fix on vorbis decoding
* [#969](https://github.com/GarageGames/Torque3D/pull/969) Improved God Ray PostFX
* [#967](https://github.com/GarageGames/Torque3D/pull/967) Add support for rendering particles to the glow buffer
* [#955](https://github.com/GarageGames/Torque3D/pull/955) Eval return issue 953 and trace buffer 952
* [#923](https://github.com/GarageGames/Torque3D/pull/923) turret tracking correction
* [#922](https://github.com/GarageGames/Torque3D/pull/922) Make HTTPObject::post work
* [#921](https://github.com/GarageGames/Torque3D/pull/921) Remove warning
* [#920](https://github.com/GarageGames/Torque3D/pull/920) Fix for fuzzy borders between textures
* [#919](https://github.com/GarageGames/Torque3D/pull/919) BaseTexFormat was not networked properly.
* [#918](https://github.com/GarageGames/Torque3D/issues/918) HTTPObject's post method doesn't work
* [#917](https://github.com/GarageGames/Torque3D/pull/917) Fix bug where console stack was incorrectly used to print audio devices
* [#916](https://github.com/GarageGames/Torque3D/issues/916) Re-enable MixedParticleRendering warning.
* [#915](https://github.com/GarageGames/Torque3D/issues/915) sfxGetAvailableDevices breaks after console changes
* [#910](https://github.com/GarageGames/Torque3D/pull/910) Added Alpha LOD to tsStatic objects.
* [#908](https://github.com/GarageGames/Torque3D/pull/908) This adds limiting the ghost data to a specific area around the client.
* [#905](https://github.com/GarageGames/Torque3D/issues/905) Lens flare effect rendering over objects
* [#903](https://github.com/GarageGames/Torque3D/pull/903) WaypointTeam never worked and if you look at the code you can see its no…
* [#902](https://github.com/GarageGames/Torque3D/pull/902) Cleaning up and streamlining Types.h,
* [#896](https://github.com/GarageGames/Torque3D/pull/896) Dev forest wind emitter improvement
* [#895](https://github.com/GarageGames/Torque3D/pull/895) So the problem is that when your inside the sphere it won't render so it…
* [#894](https://github.com/GarageGames/Torque3D/pull/894) Added Sanity Check for out of memory
* [#892](https://github.com/GarageGames/Torque3D/pull/892) Improvements to SimDictionary for when you have a large number of object…
* [#890](https://github.com/GarageGames/Torque3D/pull/890) Minor Improvement to depthSortList.cpp
* [#889](https://github.com/GarageGames/Torque3D/pull/889) Improvements to the math in mEase
* [#887](https://github.com/GarageGames/Torque3D/pull/887) Replaced a ton of ConsoleMethods with the DefineConsoleMethod Macro.
* [#886](https://github.com/GarageGames/Torque3D/pull/886) Reduce minimum tab width in PostFX manager
* [#882](https://github.com/GarageGames/Torque3D/issues/882) Update README and Github wiki
* [#877](https://github.com/GarageGames/Torque3D/pull/877) Revert "Euler to quat reversion"
* [#876](https://github.com/GarageGames/Torque3D/issues/876) Turret uses quaternion and euler angles incorrectly
* [#871](https://github.com/GarageGames/Torque3D/pull/871) Added a setPosition function
* [#869](https://github.com/GarageGames/Torque3D/pull/869) Fix omissions in astNodes.cpp
* [#853](https://github.com/GarageGames/Torque3D/issues/853) Fix console func refactor
* [#845](https://github.com/GarageGames/Torque3D/pull/845) dynamic cubemapped statics
* [#843](https://github.com/GarageGames/Torque3D/pull/843) Added projects.xml from Project Manager
* [#842](https://github.com/GarageGames/Torque3D/pull/842) jamesu's console function refactor
* [#841](https://github.com/GarageGames/Torque3D/issues/841) Underwater fog/caustics/turbulence effects don't disappear when they should
* [#832](https://github.com/GarageGames/Torque3D/issues/832) Move projects.xml here from project manager repo
* [#829](https://github.com/GarageGames/Torque3D/pull/829) Add console function to link namespaces
* [#828](https://github.com/GarageGames/Torque3D/issues/828) Provide direct script access to namespace functions
* [#827](https://github.com/GarageGames/Torque3D/pull/827) Make CMake project load all .cmake files from the module folder
* [#816](https://github.com/GarageGames/Torque3D/issues/816) CMake does not name debug executables with \_DEBUG
* [#806](https://github.com/GarageGames/Torque3D/issues/806) PostFX presets do not reset between missions
* [#793](https://github.com/GarageGames/Torque3D/pull/793) Terrain basetex formats
* [#788](https://github.com/GarageGames/Torque3D/pull/788) Allow return status to be specified using quitWithStatus
* [#784](https://github.com/GarageGames/Torque3D/issues/784) NavMesh scale does not make sense in script
* [#774](https://github.com/GarageGames/Torque3D/issues/774) TorqueScript anonymous functions
* [#770](https://github.com/GarageGames/Torque3D/issues/770) Fatal error-Shader quality lowest with lighting quality above lowest
* [#768](https://github.com/GarageGames/Torque3D/pull/768) Accumulation volumes
* [#761](https://github.com/GarageGames/Torque3D/pull/761) -added Vignette PostFx
* [#751](https://github.com/GarageGames/Torque3D/issues/751) Script API: no setPosition
* [#749](https://github.com/GarageGames/Torque3D/pull/749) Re-enable Mixed particle rendering
* [#744](https://github.com/GarageGames/Torque3D/pull/744) Ribbon implementation
* [#726](https://github.com/GarageGames/Torque3D/pull/726) Sahara
* [#721](https://github.com/GarageGames/Torque3D/pull/721) deprecated functionality. T3D handles this in the reflector class.
* [#715](https://github.com/GarageGames/Torque3D/pull/715) Fix to allow parallax mapping with dxtnm textures via the red channel.
* [#705](https://github.com/GarageGames/Torque3D/pull/705) Fix for unexpected behavior described in issue #704
* [#704](https://github.com/GarageGames/Torque3D/issues/704) Return values from TS functions not handled correctly.
* [#690](https://github.com/GarageGames/Torque3D/pull/690) Bullet Physics Library 2.82 update
* [#685](https://github.com/GarageGames/Torque3D/pull/685) Physx3 Physics Plugin
* [#667](https://github.com/GarageGames/Torque3D/issues/667) MeshRoad does not collide with physics objects
* [#664](https://github.com/GarageGames/Torque3D/pull/664) Consoleargfix
* [#663](https://github.com/GarageGames/Torque3D/issues/663) "Unused" TS arguments being optimised out
* [#658](https://github.com/GarageGames/Torque3D/pull/658) Add send queue to TCPObject
* [#637](https://github.com/GarageGames/Torque3D/issues/637) Change all member vars to use mMemberName naming
* [#623](https://github.com/GarageGames/Torque3D/issues/623) CMake generated solution has ALL\_BUILD as startup project
* [#592](https://github.com/GarageGames/Torque3D/pull/592) TorqueScript unit test
* [#587](https://github.com/GarageGames/Torque3D/issues/587) Add OpenGL 3.2 renderer
* [#479](https://github.com/GarageGames/Torque3D/issues/479) Custom GUI Profile/Files issue
* [#396](https://github.com/GarageGames/Torque3D/issues/396) Using LF (\n) instead of CRLF (\r\n) causes some parsing errors.
* [#199](https://github.com/GarageGames/Torque3D/issues/199) GuiObjectView camera transform and object orbit distance problem.
* [#164](https://github.com/GarageGames/Torque3D/issues/164) Euler to Quaternion conversion is incorrect
* [#148](https://github.com/GarageGames/Torque3D/pull/148) Prevented looking up incorrect object handles
* [#81](https://github.com/GarageGames/Torque3D/pull/81) Improve Console Function Calls

## OpenGL issues closed [source](https://github.com/GarageGames/Torque3D/issues?q=milestone%3AOpenGL3+is%3Aclosed) <a href="#toc2" id="toc2"></a>

* [#990](https://github.com/GarageGames/Torque3D/pull/990) Fix CI server.
* [#989](https://github.com/GarageGames/Torque3D/pull/989) Fix OpenGL changes formating.
* [#988](https://github.com/GarageGames/Torque3D/pull/988) Clean GLSL fragment shader out.
* [#986](https://github.com/GarageGames/Torque3D/pull/986) Fix GLSL out fragment shader color.
* [#985](https://github.com/GarageGames/Torque3D/pull/985) Clean PlaneReflector member variables declaration.
* [#984](https://github.com/GarageGames/Torque3D/pull/984) const U64 maxValPerChannel = (U64)1 \&lt;\&lt; mBitsPerChannel;
* [#983](https://github.com/GarageGames/Torque3D/pull/983) DeferredMinnaert feautre was missing samplernames
* [#982](https://github.com/GarageGames/Torque3D/pull/982) Fix PHP ProjectGenerator for OpenGL.
* [#965](https://github.com/GarageGames/Torque3D/pull/965) Added OpenGL module with some additions to the project generator
* [#962](https://github.com/GarageGames/Torque3D/pull/962) Fix OpenGL new terrain blend
* [#961](https://github.com/GarageGames/Torque3D/pull/961) Fix OpenGL fullscreen on win32
* [#940](https://github.com/GarageGames/Torque3D/pull/940) Add/Activate OpenGL render.
* [#939](https://github.com/GarageGames/Torque3D/pull/939) Templates changes for OpenGL shaders.
* [#938](https://github.com/GarageGames/Torque3D/pull/938) Remove old/unused OpenGL files.
* [#937](https://github.com/GarageGames/Torque3D/pull/937) Increase FrameBuffer size for use on OpenGL.
* [#936](https://github.com/GarageGames/Torque3D/pull/936) GLEW library for OpenGL.
* [#935](https://github.com/GarageGames/Torque3D/pull/935) Fix imposter capture on OpenGL.
* [#934](https://github.com/GarageGames/Torque3D/pull/934) Changes on PostFX for OpenGL.
* [#933](https://github.com/GarageGames/Torque3D/pull/933) Changes on ShaderGen for generate GLSL shaders.
* [#932](https://github.com/GarageGames/Torque3D/pull/932) Reduce innecesary changes on Render Target textures.
* [#931](https://github.com/GarageGames/Torque3D/pull/931) Set correct terrain layer texture format.
* [#930](https://github.com/GarageGames/Torque3D/pull/930) Separate OpenGL code from Linux or Mac.
* [#929](https://github.com/GarageGames/Torque3D/pull/929) Remove unnecesary code for handle OpenGL.
* [#928](https://github.com/GarageGames/Torque3D/pull/928) Change RenderParticleMgr for use sampler names
* [#927](https://github.com/GarageGames/Torque3D/pull/927) Add GFXDevice::setupGenericShader for fix render on non FFP.
* [#926](https://github.com/GarageGames/Torque3D/pull/926) Fix PrimBuild with non Fixed Function Pipeline.
* [#925](https://github.com/GarageGames/Torque3D/pull/925) Add sampler names to ShaderData
* [#924](https://github.com/GarageGames/Torque3D/pull/924) Remove GFXDevice::disableShader
* [#622](https://github.com/GarageGames/Torque3D/pull/622) Handle texel-pixel offset with diferents graphics APIs.
* [#621](https://github.com/GarageGames/Torque3D/pull/621) Update GLSL Shadergen.
* [#620](https://github.com/GarageGames/Torque3D/pull/620) Add RenderPassData::mSamplerNames for OpenGL code. Not used on DX9.
* [#619](https://github.com/GarageGames/Torque3D/pull/619) Add GFXShader::init with support for ordered vector of sampler names for shader.
* [#618](https://github.com/GarageGames/Torque3D/pull/618) Use shader data for get sampler register in CloudLayer and BasicClouds.
* [#617](https://github.com/GarageGames/Torque3D/pull/617) Fix ScatterSkyVertex::color declaration.
* [#616](https://github.com/GarageGames/Torque3D/pull/616) Fix WaterObject TODO: Retrieve sampler numbers from parameter handles, see r22631.
* [#611](https://github.com/GarageGames/Torque3D/pull/611) Add sampler names to Templates ShaderData declarations necesary for OpenGL.
* [#610](https://github.com/GarageGames/Torque3D/pull/610) Changes to Templates GLSL files for OpenGL
* [#608](https://github.com/GarageGames/Torque3D/pull/608) Use GFXDevice::setupGenericShaders for support non Fixed Fuction Pipelines.
