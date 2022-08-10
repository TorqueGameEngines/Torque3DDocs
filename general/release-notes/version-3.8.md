# Version 3.8

* [GitHub release](https://github.com/GarageGames/Torque3D/releases/tag/v3.8)
* Release announcement
* Release candidate announcement

## Notes <a href="#toc0" id="toc0"></a>

* You'll need to regenerate projects thanks to Oculus file changes, even projects which don't use OR.
* One remaining issue that we tried to get wrapped up, but was unable to was native file dialogs.

There's a few niggling issues causing a crash somewhere with Areloch's implementation. There's a branch concerning it [here](https://github.com/Areloch/Torque3D/tree/NFD\_WIP) and if anyone can either tell him how to get Codeblocks to properly debug, or can figure out the crash themselves, it can PR'd right away and get a hotfix out to re-enable file dialogs for the Linux build.

## Issues closed [source](https://github.com/GarageGames/Torque3D/issues?q=milestone%3A3.8+is%3Aclosed) <a href="#toc1" id="toc1"></a>

[#1426](https://github.com/GarageGames/Torque3D/pull/1426) Backend correction for #1425\
[#1423](https://github.com/GarageGames/Torque3D/pull/1423) SDL Menubar accelerator fix\
[#1421](https://github.com/GarageGames/Torque3D/pull/1421) CMake NMake fix to place exe in game directory\
[#1418](https://github.com/GarageGames/Torque3D/pull/1418) Remove GL\_EXT\_gpu\_shader4\
[#1416](https://github.com/GarageGames/Torque3D/pull/1416) SDL Textbox bleedthrough inputs fix\
[#1411](https://github.com/GarageGames/Torque3D/pull/1411) void GuiTextEditCtrl::execConsoleCallback() reversion\
[#1410](https://github.com/GarageGames/Torque3D/pull/1410) Light animation brightness fix\
[#1409](https://github.com/GarageGames/Torque3D/pull/1409) U32 MRandomLCG::randI() was using longs\
[#1407](https://github.com/GarageGames/Torque3D/pull/1407) Companion PR to 1398\
[#1406](https://github.com/GarageGames/Torque3D/pull/1406) Monkey PR w/ mergefix\
[#1404](https://github.com/GarageGames/Torque3D/pull/1404) Companion PR to #719\
[#1402](https://github.com/GarageGames/Torque3D/pull/1402) Files caught by [https://github.com/GarageGames/Torque3D/pull/1401](https://github.com/GarageGames/Torque3D/pull/1401)\
[#1401](https://github.com/GarageGames/Torque3D/pull/1401) Adds a verifyCompatibility method to the Win32FileSystem to report case-sensitivity issues\
[#1377](https://github.com/GarageGames/Torque3D/pull/1377) From Dušan Jocić: convexDecomp vs2015+ compatibility patch\
[#1376](https://github.com/GarageGames/Torque3D/pull/1376) From Dušan Jocić: early out of treeview entries to prevent crashes\
[#1375](https://github.com/GarageGames/Torque3D/pull/1375) Redux of Winterleaf's PR 1001, with the suggested updated values\
[#1374](https://github.com/GarageGames/Torque3D/pull/1374) "AL: PSSM Cascade Viz" tool-button\
[#1373](https://github.com/GarageGames/Torque3D/pull/1373) Ribbons in the editors\
[#1371](https://github.com/GarageGames/Torque3D/pull/1371) Random VS warnings\
[#1370](https://github.com/GarageGames/Torque3D/pull/1370) Stop precipitation from processing ticks when it's hidden\
[#1369](https://github.com/GarageGames/Torque3D/pull/1369) Fix NaNs in Collada files\
[#1366](https://github.com/GarageGames/Torque3D/pull/1366) Overrides the default CMAKE\_INSTALL\_PREFIX\
[#1365](https://github.com/GarageGames/Torque3D/pull/1365) Removing pointless null-pointer tests for objects created with new\
[#1363](https://github.com/GarageGames/Torque3D/pull/1363) Allowplayerstep lets folks run up sharper angles than normal.\
[#1390](https://github.com/GarageGames/Torque3D/pull/1390) Case sensitivity fix for linux\
[#1388](https://github.com/GarageGames/Torque3D/pull/1388) SDL mouse wheel speed fix\
[#1387](https://github.com/GarageGames/Torque3D/pull/1387) Fixes the menubar functionality when using SDL\
[#1385](https://github.com/GarageGames/Torque3D/pull/1385) -wall leads to incredibly long compile times\
[#1383](https://github.com/GarageGames/Torque3D/pull/1383) SDL2 mouse wheel scrolling\
[#1382](https://github.com/GarageGames/Torque3D/pull/1382) Fatality Fix: need to account for 64 bit windows as well.\
[#1380](https://github.com/GarageGames/Torque3D/pull/1380) Partly addresses C4946 warnings\
[#1379](https://github.com/GarageGames/Torque3D/pull/1379) C4189 warning cleanups\
[#1378](https://github.com/GarageGames/Torque3D/pull/1378) Properly testing pointer vars aren't null before using them.\
[#1400](https://github.com/GarageGames/Torque3D/pull/1400) Case sensitivity script fixes\
[#1399](https://github.com/GarageGames/Torque3D/pull/1399) Adds a debug visualization mode for the active physics world\
[#1398](https://github.com/GarageGames/Torque3D/pull/1398) Update messageBox.ed.cs\
[#1397](https://github.com/GarageGames/Torque3D/pull/1397) From @LuisAntonRebollo -stops infinite loop on exit with SDL2+OGL on Win\
[#1396](https://github.com/GarageGames/Torque3D/pull/1396) Adds data to vector out of bounds reports\
[#1394](https://github.com/GarageGames/Torque3D/pull/1394) Release the mouse from window constraints when poping up a window prompt\
[#1392](https://github.com/GarageGames/Torque3D/pull/1392) Warning C4005: 'WIN32' : macro redefinition\
[#1391](https://github.com/GarageGames/Torque3D/pull/1391) Warning C4706: assignment within conditional expression\
[#1362](https://github.com/GarageGames/Torque3D/pull/1362) Removes fatal assertion on duplicated object collisions (meshroads, primarily)\
[#1361](https://github.com/GarageGames/Torque3D/pull/1361) Adds minimum displacement check prior to convexSweepTest to avoid NaNs\
[#1358](https://github.com/GarageGames/Torque3D/pull/1358) Reduces rotation transmission size\
[#1357](https://github.com/GarageGames/Torque3D/pull/1357) Followobject position caching\
[#1356](https://github.com/GarageGames/Torque3D/pull/1356) Convert un-modified function arguments to const references\
[#1354](https://github.com/GarageGames/Torque3D/pull/1354) Cleanup of ease functions operations\
[#1353](https://github.com/GarageGames/Torque3D/pull/1353) Utilize ++iter rather than iter++ to improve iterator performance\
[#1352](https://github.com/GarageGames/Torque3D/pull/1352) Unnecessarily repeated expressions\
[#1350](https://github.com/GarageGames/Torque3D/pull/1350) Fills in profiler timer fallback\
[#1346](https://github.com/GarageGames/Torque3D/pull/1346) Allow using ThreadPool synchronously\
[#1344](https://github.com/GarageGames/Torque3D/pull/1344) Fix -Wreorder warnings from ShapeBase\
[#1343](https://github.com/GarageGames/Torque3D/pull/1343) Fixed some random gcc's -Wreorder warnings\
[#1342](https://github.com/GarageGames/Torque3D/pull/1342) Offsetof is actually a standard thing nowadays it would seem\
[#1341](https://github.com/GarageGames/Torque3D/pull/1341) Fixed warning\
[#1339](https://github.com/GarageGames/Torque3D/pull/1339) Remove demo and trial checks\
[#1336](https://github.com/GarageGames/Torque3D/pull/1336) Fixed some minor compiler warnings on Linux\
[#1333](https://github.com/GarageGames/Torque3D/pull/1333) Plugging Memory Leaks\
[#1330](https://github.com/GarageGames/Torque3D/pull/1330) Basic fix for stereo rendering without a display device
