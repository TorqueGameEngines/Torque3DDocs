# Version 3.6

* [GitHub release](https://github.com/GarageGames/Torque3D/releases/tag/v3.6)
* [Pre-release blog](http://www.garagegames.com/community/blogs/view/22828)

## Notes <a href="#toc0" id="toc0"></a>

* Add a call to closeSplashWindow somewhere if you don't want it sticking around in the background. Template main.cs files now do this.
* If you manage Project Generator modules, the Generator class has been renamed T3D\_Generator.
* If you were relying on Projectile impact decals being aligned vertically, sorry, but they will now rotate randomly on placement. We thought this was better default behavior.
* Player now makes use of PlayerData::swimForce while submerged, where previously it ignored this value and used only runForce.
* ShapeBase::Thread::sound and associated functions have been removed because they were not actually used. If you made them useful in your own code, we apologise for any merge conflicts.

## Issues closed [source](https://github.com/GarageGames/Torque3D/issues?q=closed%3A2014-03-11..2014-10-03+sort%3Aupdated-desc) <a href="#toc1" id="toc1"></a>

* [#808](https://github.com/GarageGames/Torque3D/pull/808) Version 3.6
* [#807](https://github.com/GarageGames/Torque3D/pull/807) Added Outpost testing level by Azaezel
* [#795](https://github.com/GarageGames/Torque3D/pull/795) Support for Windows x64 builds
* [#737](https://github.com/GarageGames/Torque3D/pull/737) Query Stall Prevention
* [#723](https://github.com/GarageGames/Torque3D/pull/723) Light ray cleanup
* [#772](https://github.com/GarageGames/Torque3D/pull/772) Outpost testbed.
* [#775](https://github.com/GarageGames/Torque3D/pull/775) player triggers.
* [#728](https://github.com/GarageGames/Torque3D/issues/728) Port existing unit tests to googletest
* [#796](https://github.com/GarageGames/Torque3D/pull/796) Bump version numbers
* [#801](https://github.com/GarageGames/Torque3D/pull/801) Googletest tests
* [#233](https://github.com/GarageGames/Torque3D/issues/233) Editor crashes when painting a forest in the scene in debug mode physx on stock T3D
* [#689](https://github.com/GarageGames/Torque3D/pull/689) Physx 2.8 actor release fix
* [#794](https://github.com/GarageGames/Torque3D/pull/794) Euler to quat reversion
* [#781](https://github.com/GarageGames/Torque3D/pull/781) Removed annoying warning
* [#763](https://github.com/GarageGames/Torque3D/pull/763) - Added check in tsMesh::createTangents to check size of incoming normal…
* [#739](https://github.com/GarageGames/Torque3D/pull/739) Fix Vehicle crash on change Datablock's shape.
* [#779](https://github.com/GarageGames/Torque3D/pull/779) Fixed Vehicle crash on changing datablock shape in editor for #189
* [#722](https://github.com/GarageGames/Torque3D/pull/722) implicit truncation warning cleanup.
* [#616](https://github.com/GarageGames/Torque3D/pull/616) Fix WaterObject TODO: Retrieve sampler numbers from parameter handles, see r22631.
* [#800](https://github.com/GarageGames/Torque3D/pull/800) Fix compiler warnings with CMAKE and TORQUE\_DISABLE\_MEMORY\_MANAGER.
* [#559](https://github.com/GarageGames/Torque3D/pull/559) Torque3D x64
* [#791](https://github.com/GarageGames/Torque3D/pull/791) Bumped minimum CMake version
* [#792](https://github.com/GarageGames/Torque3D/pull/792) Link against librt
* [#776](https://github.com/GarageGames/Torque3D/pull/776) Simplify compiler ast
* [#81](https://github.com/GarageGames/Torque3D/pull/81) Improve Console Function Calls
* [#658](https://github.com/GarageGames/Torque3D/pull/658) Add send queue to TCPObject
* [#716](https://github.com/GarageGames/Torque3D/issues/716) EventManager is actually case-sensitive
* [#789](https://github.com/GarageGames/Torque3D/pull/789) Make mSubscribers case-insensitive
* [#682](https://github.com/GarageGames/Torque3D/pull/682) Extended onend sequence
* [#459](https://github.com/GarageGames/Torque3D/issues/459) Non-Cyclic animations don't propagate to new clients.
* [#780](https://github.com/GarageGames/Torque3D/pull/780) Fixed ShapeBase animation networking
* [#783](https://github.com/GarageGames/Torque3D/issues/783) chat under GNU/Linux does not catch all typing focus
* [#754](https://github.com/GarageGames/Torque3D/pull/754) requested correction
* [#769](https://github.com/GarageGames/Torque3D/pull/769) Adds material definitions for groundcover referencing.
* [#717](https://github.com/GarageGames/Torque3D/pull/717) Make NavPath::alwaysRender work the same as NavMesh::alwaysRender
* [#773](https://github.com/GarageGames/Torque3D/pull/773) Removed ShapeBase::Thread::sound
* [#645](https://github.com/GarageGames/Torque3D/pull/645) Ridgidshape update forces
* [#649](https://github.com/GarageGames/Torque3D/pull/649) Ai player utility
* [#650](https://github.com/GarageGames/Torque3D/pull/650) Ejection offset variance defaults
* [#742](https://github.com/GarageGames/Torque3D/pull/742) Improving CMake build system for power users
* [#641](https://github.com/GarageGames/Torque3D/pull/641) Projectile decal
* [#554](https://github.com/GarageGames/Torque3D/pull/554) Fixed some warnings L4 on the VS2012.
* [#766](https://github.com/GarageGames/Torque3D/pull/766) Deferred Shading
* [#747](https://github.com/GarageGames/Torque3D/pull/747) WaterObject loose reflection.
* [#567](https://github.com/GarageGames/Torque3D/pull/567) Natural (without 2-km limitations) heights of terrain.
* [#760](https://github.com/GarageGames/Torque3D/pull/760) Fixed thread statics
* [#636](https://github.com/GarageGames/Torque3D/pull/636) Fix cmake mayor
* [#755](https://github.com/GarageGames/Torque3D/pull/755) Fix splashscreen
* [#735](https://github.com/GarageGames/Torque3D/pull/735) Splash screen fix
* [#756](https://github.com/GarageGames/Torque3D/pull/756) Load new DLL first so existing projects don't see odd behavior
* [#621](https://github.com/GarageGames/Torque3D/pull/621) Update GLSL Shadergen.
* [#590](https://github.com/GarageGames/Torque3D/pull/590) cmake - version 2
* [#603](https://github.com/GarageGames/Torque3D/pull/603) simple alteration to allow for negative damage (repair).
* [#416](https://github.com/GarageGames/Torque3D/pull/416) error splitting mesh and image filenames
* [#662](https://github.com/GarageGames/Torque3D/pull/662) Fixes #625 - Cmake missing modules
* [#647](https://github.com/GarageGames/Torque3D/pull/647) Debris collision
* [#659](https://github.com/GarageGames/Torque3D/pull/659) Bouncy bullets
* [#495](https://github.com/GarageGames/Torque3D/pull/495) action tactics template
* [#605](https://github.com/GarageGames/Torque3D/pull/605) Player hitboxes
* [#548](https://github.com/GarageGames/Torque3D/pull/548) More fixes
* [#601](https://github.com/GarageGames/Torque3D/pull/601) Rename enum GFXTextureProfile::None for avoid conficts on Linux.
* [#612](https://github.com/GarageGames/Torque3D/pull/612) Platform type consistency
* [#738](https://github.com/GarageGames/Torque3D/pull/738) Add GG(c) and MIT license to CMake files.
* [#727](https://github.com/GarageGames/Torque3D/issues/727) Add MIT header to all CMake files
* [#661](https://github.com/GarageGames/Torque3D/pull/661) Grenade decal
* [#665](https://github.com/GarageGames/Torque3D/pull/665) Support for large lists of shape formats.
* [#455](https://github.com/GarageGames/Torque3D/pull/455) Platform type consistency
* [#600](https://github.com/GarageGames/Torque3D/pull/600) Rename Status enum for avoid conficts on Linux.
* [#732](https://github.com/GarageGames/Torque3D/pull/732) Revert #540
* [#729](https://github.com/GarageGames/Torque3D/pull/729) Fix #224 Memory corruption on Precipitation::destroySplash.
* [#224](https://github.com/GarageGames/Torque3D/issues/224) modifyStorm bug in precipitation.cpp
* [#731](https://github.com/GarageGames/Torque3D/pull/731) Fix CMake testing module.
* [#544](https://github.com/GarageGames/Torque3D/pull/544) Update bundled PHP to 5.5.6
* [#542](https://github.com/GarageGames/Torque3D/pull/542) Update to latest smarty to fix problems with PHP 5
* [#595](https://github.com/GarageGames/Torque3D/issues/595) Move unit tests to their own module
* [#626](https://github.com/GarageGames/Torque3D/issues/626) Use gtest framework for unit tests
* [#706](https://github.com/GarageGames/Torque3D/pull/706) Add Google test library
* [#698](https://github.com/GarageGames/Torque3D/pull/698) Append ' DLL' to DLL name to fix linker times
* [#72](https://github.com/GarageGames/Torque3D/issues/72) Long linker times on Torque3D.dll (VS2010)
* [#558](https://github.com/GarageGames/Torque3D/pull/558) Fixed errors vs2013
* [#718](https://github.com/GarageGames/Torque3D/pull/718) Fixed Euler to Quaternion conversion
* [#164](https://github.com/GarageGames/Torque3D/issues/164) Euler to Quaternion conversion is incorrect
* [#277](https://github.com/GarageGames/Torque3D/issues/277) Bug in GFXDrawUtil::draw2DSquare
* [#724](https://github.com/GarageGames/Torque3D/pull/724) Allow drawing 2D squares with 0 rotation angle
* [#201](https://github.com/GarageGames/Torque3D/issues/201) Engine - Bad quad UV mapping (THREED-1482)
* [#697](https://github.com/GarageGames/Torque3D/pull/697) Added string functions from T2D
* [#711](https://github.com/GarageGames/Torque3D/pull/711) Make use of PlayerData::swimForce
* [#570](https://github.com/GarageGames/Torque3D/pull/570) Fixed Box3F::overlap
* [#425](https://github.com/GarageGames/Torque3D/pull/425) fixed memory checking in volume
* [#687](https://github.com/GarageGames/Torque3D/pull/687) Add coverage option to procedural terrain generator
* [#597](https://github.com/GarageGames/Torque3D/pull/597) Fix VS2008
* [#674](https://github.com/GarageGames/Torque3D/pull/674) Fix SignalBase constructor shenanigans
* [#699](https://github.com/GarageGames/Torque3D/pull/699) Prevent call to dStrlen(NULL)
* [#632](https://github.com/GarageGames/Torque3D/pull/632) Added a better example of using Explosion in a client/server fashion
* [#715](https://github.com/GarageGames/Torque3D/pull/715) Fix to allow parallax mapping with dxtnm textures via the red channel.
* [#475](https://github.com/GarageGames/Torque3D/pull/475) A few fixes for generating projects on \*nix platform.
* [#538](https://github.com/GarageGames/Torque3D/pull/538) Tangent Basis Cleanup
* [#563](https://github.com/GarageGames/Torque3D/pull/563) Fixed issue #256: "$pref::TS::smallestVisiblePixelSize doesn't work".
* [#580](https://github.com/GarageGames/Torque3D/pull/580) fixes problems for newer php version
* [#547](https://github.com/GarageGames/Torque3D/pull/547) Fix potential crashes
* [#593](https://github.com/GarageGames/Torque3D/pull/593) Added build status icon to README.
* [#556](https://github.com/GarageGames/Torque3D/pull/556) When setting the field on a GuiInspectorField, check if the field is null before setting the docs
* [#675](https://github.com/GarageGames/Torque3D/pull/675) Fix assertfatal/TORQUE\_UNUSED release performance
* [#676](https://github.com/GarageGames/Torque3D/pull/676) Fix dedicated Linux build.
* [#609](https://github.com/GarageGames/Torque3D/pull/609) Case-sensitive fixes on template script files for Linux.
* [#465](https://github.com/GarageGames/Torque3D/pull/465) Fix bug in HTTPObject (Fixed)
* [#568](https://github.com/GarageGames/Torque3D/pull/568) clipping the lighting result via ciel was causing banding issues with sp…
* [#543](https://github.com/GarageGames/Torque3D/pull/543) PHP 5.5 doesn't want us to use the class name "Generator"
* [#596](https://github.com/GarageGames/Torque3D/pull/596) VS2013 compatibility patch.
* [#630](https://github.com/GarageGames/Torque3D/pull/630) FIX RenderMeshExample not having a material on mission start…
* [#631](https://github.com/GarageGames/Torque3D/pull/631) FIX RenderMeshExample not having a material on mission start even if one…
* [#629](https://github.com/GarageGames/Torque3D/pull/629) FIX RenderMeshExample not having a material on mission start…
* [#540](https://github.com/GarageGames/Torque3D/pull/540) Added a default keyboard layout for launching the game.
* [#614](https://github.com/GarageGames/Torque3D/pull/614) Removed unnecessary parameter in a simObject getter method
* [#635](https://github.com/GarageGames/Torque3D/pull/635) Various engine fixes
* [#670](https://github.com/GarageGames/Torque3D/pull/670) Fix Dereference of null pointer on String::operator+=
* [#671](https://github.com/GarageGames/Torque3D/pull/671) Fix cmake dependencies
* [#591](https://github.com/GarageGames/Torque3D/pull/591) revised #568. abs and max.
* [#581](https://github.com/GarageGames/Torque3D/pull/581) Visual Studio 2012 32Bit Level 4 Warning fixes
* [#569](https://github.com/GarageGames/Torque3D/pull/569) Added the script Utils::landing() for the simplest work with a level
* [#602](https://github.com/GarageGames/Torque3D/pull/602) removes non-functional shield and invincibility functionality.
* [#561](https://github.com/GarageGames/Torque3D/pull/561) Corrected docs for scripts in the group FileSystem: fileBase() and fileName().
* [#594](https://github.com/GarageGames/Torque3D/pull/594) Increased stability Torque3D: unit-tests running without a crash.
* [#599](https://github.com/GarageGames/Torque3D/issues/599) Errors during global ThreadPool destruction.
* [#634](https://github.com/GarageGames/Torque3D/pull/634) Commit to add "Coverage" option to procedural terrain generator
* [#562](https://github.com/GarageGames/Torque3D/pull/562) Unit tests without crashes.
* [#613](https://github.com/GarageGames/Torque3D/pull/613) T2D style 'Stock colors'
* [#646](https://github.com/GarageGames/Torque3D/pull/646) Ejection offest variance defaults
* [#583](https://github.com/GarageGames/Torque3D/pull/583) windows 64 bit basics
* [#673](https://github.com/GarageGames/Torque3D/issues/673) SignalBase constructor causes warnings in GCC
* [#681](https://github.com/GarageGames/Torque3D/pull/681) Fix CMake linux dedicated on gcc and Clang
* [#582](https://github.com/GarageGames/Torque3D/pull/582) RenderInstType default constructor improvements
* [#666](https://github.com/GarageGames/Torque3D/pull/666) CMake linux fixes
* [#557](https://github.com/GarageGames/Torque3D/pull/557) Add a 'Coverage' option to the procedural terrain generator
* [#669](https://github.com/GarageGames/Torque3D/pull/669) Fix ALDeviceList::GetDeviceVersion incorrect check of valid pointer.
* [#668](https://github.com/GarageGames/Torque3D/pull/668) Fix for avoid a zero division on \_StringTable::resize.
* [#617](https://github.com/GarageGames/Torque3D/pull/617) Fix ScatterSkyVertex::color declaration.
* [#551](https://github.com/GarageGames/Torque3D/pull/551) Minor fixes
* [#628](https://github.com/GarageGames/Torque3D/pull/628) Fix crash on exit T3D when build with CMake.
* [#566](https://github.com/GarageGames/Torque3D/pull/566) Action for solder edges of nearest terrains.
* [#633](https://github.com/GarageGames/Torque3D/pull/633) Coverage option for procedural terrain painter
* [#604](https://github.com/GarageGames/Torque3D/pull/604) Particle Accumulation on Damage (Yet another one-liner)
* [#652](https://github.com/GarageGames/Torque3D/pull/652) Use fixed buffer size variable for allocating return buffer
* [#688](https://github.com/GarageGames/Torque3D/pull/688) Vehicle gamepad fix for full template.
* [#367](https://github.com/GarageGames/Torque3D/issues/367) Vehicle out of control when entering with a gamepad.
* [#672](https://github.com/GarageGames/Torque3D/pull/672) Cmake improvements
* [#638](https://github.com/GarageGames/Torque3D/pull/638) Fix for avoid a zero division on \_StringTable::resize.
* [#640](https://github.com/GarageGames/Torque3D/pull/640) Fix ALDeviceList::GetDeviceVersion incorrect check of valid pointer.
* [#639](https://github.com/GarageGames/Torque3D/pull/639) Fix Dereference of null pointer on String::operator+=
* [#610](https://github.com/GarageGames/Torque3D/pull/610) Changes to Templates GLSL files for OpenGL
* [#619](https://github.com/GarageGames/Torque3D/pull/619) Add GFXShader::init with support for ordered vector of sampler names for shader.
* [#625](https://github.com/GarageGames/Torque3D/issues/625) CMake has no option for Rift, Hydra or Recast
* [#660](https://github.com/GarageGames/Torque3D/issues/660) Grenade Launcher Projectile Missing Decal
* [#656](https://github.com/GarageGames/Torque3D/issues/656) Missing parameter in FixedSizeVector
* [#627](https://github.com/GarageGames/Torque3D/issues/627) Explosion is not networked properly
* [#624](https://github.com/GarageGames/Torque3D/issues/624) CMake generates solutions in project root
* [#437](https://github.com/GarageGames/Torque3D/issues/437) Ground Cover Material Issue
* [#615](https://github.com/GarageGames/Torque3D/pull/615) Fixed the crash when using glow material on billboard groundcover
* [#598](https://github.com/GarageGames/Torque3D/pull/598) Issue 437
* [#493](https://github.com/GarageGames/Torque3D/issues/493) Ubuntu 64 compile Error
* [#79](https://github.com/GarageGames/Torque3D/issues/79) Add TorqueScript Prefab methods
* [#143](https://github.com/GarageGames/Torque3D/issues/143) ClientMissionCleanup not found
* [#553](https://github.com/GarageGames/Torque3D/pull/553) Added method Vector::reverse().
* [#586](https://github.com/GarageGames/Torque3D/pull/586) CMake Buildsystem Basics
* [#578](https://github.com/GarageGames/Torque3D/pull/578) improved gitignore for VS2012
* [#589](https://github.com/GarageGames/Torque3D/pull/589) further cleanup for error splitting mesh and image filenames #416
* [#584](https://github.com/GarageGames/Torque3D/pull/584) Copy of PR #551 changed to target development.
* [#577](https://github.com/GarageGames/Torque3D/pull/577) main working on unicode systems
* [#473](https://github.com/GarageGames/Torque3D/issues/473) PHP class name clash with Generator class.
* [#428](https://github.com/GarageGames/Torque3D/issues/428) Sprinting is not a pose
* [#546](https://github.com/GarageGames/Torque3D/pull/546) Minor cleanups
* [#256](https://github.com/GarageGames/Torque3D/issues/256) $pref::TS::smallestVisiblePixelSize doesn't work
