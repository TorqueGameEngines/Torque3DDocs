# Version 4.0

* [GitHub release](https://github.com/TorqueGameEngines/Torque3D/releases/tag/v4.0)
* Release announcement

## Notes <a href="#toc0" id="toc0"></a>

* Switched engine over to utilize Assets and Modules
* Switched lighting and materials to utilize PBR rendering
* Made BaseGame template the main/only template
* Added Assimp shape importer library
* Added Legacy Project Importer
* Updated to D3D11 from D3D9
* Updated GL to be 4.0
* Updated TorqueScript compiler for better performance

## Pull Requests Merged [source](https://github.com/TorqueGameEngines/Torque3D/tree/Release\_4\_0) <a href="#toc1" id="toc1"></a>

* Alpha40/ts static cleanup #840
* tsstatic aug cleanups #839
* Re-enables reimport of assets #838
* Cmake DEBUG/RELEASE flag standardization #837
* targeted fix for #45 #836
* pathshape cleanups and callbacks #835
* soundAsset profile and description getter fixes #834
* particle emission safeties #833
* Update TORQUE\_GAME\_ENGINE\_VERSION\_STRING version number 4.0.0 #832
* Misc FIxes 2022/07/24 #831
* fix bounds box display #830
* DBEditor callback fix for asset fields #828
* Misc Fixes 2022/07/02 #827
* make sure the volfog manager is dead before we kill scene #825
* fix unspecified storage location mangle for new asset creation #824
* fix a pair of taml typos #823
* BugFix: Correct a missing asset for filling the background of the console #822
* Misc Fixes 2022/06/20 #821
* fix shape errorcodes #820
* you want the higher number, not the lower #819
* fix computeForwardProbes shadergen gl side #818
* fix out of bounds reference in arrayobject #817
* fix TORQUE\_TOOLS = off compilation #815
* fix vectorlight visualizer varnames #814
* Fix Misc ConvexShape Tooling Issues #813
* BugFix: Remove the GCC Workaround #812
* Misc Fixes 2022/06/09 #811
* allow ambient light injection into ibl #809
* Misc Fixes 2022/06/05 #808
* Disconnect and Shutdown fixes #807
* Uncomments networking lines that ensure client has the particle's textures #806
* Sound Networking Fixes #805
* Misc Fixes 2022/06/01 #804
* proper player head rot clamp #802
* constrain player mRot.z reguardless of translation #800
* Misc Fixes for 2022/05/30 #799
* Use screen space coordinates for mouse pointer position #798
* BaseGame Template: Fix script assert on canceling game options changes #797
* fix particle emitter asset browser spawning #796
* lower min brushsize for forest to sub-meter levels #795
* set convexshape to use a standard vertex type #794
* fix on-RPC-command explosion sounds not playing the first time #793
* BugFix: Correct MacOS not responding to various hotkeys #792
* BugFix: Correct invalid fall-through behavior in sdlInputManager.cpp. #791
* Misc Fixes for 2022/05/24 #790
* Overhaul on CPU detection for Windows, Mac (x64/arm64) & Linux #789
* Fixes issue where creating a new ForestItem wouldn't have it show in the ForestItemData dropdown on brushes until you restart. #788
* Fix edgecase where empty string was not being explicitly set to 0 in … #787
* Better allocator for TorqueScript temp conversions during interpretation #786
* Adjustment: Update libsdl to address a bug in compilation on MacOS #785
* fix sDefaultAmbience intialization. #783
* Misc Fixes for 2022/05/10 #781
* Implements a more standardized way to format usual UI pages by having the ability to utilize the UINavigation namespace for page stack navigation #780
* Make the Console Sane Again #779
* Fix weird ternary operator in torquescript regression #778
* update assimp to 5.2.3 Bugfix-Release #777
* Adds a conditional to the github workflow file so it only runs on the main repo #776
* update sdl to release 2.0.22 #775
* Github actions CI #774
* Removes the BGRA inversion when displaying vertex colors on materials #773
* Cleanup: Resolve several compiler warnings associated with TORQUE\_DEBUG #772
* correct mac compilation #771
* add .vs directory to gitignore #770
* Misc Fixes 2022/04/23 #769
* drop the prior requirement for a createcomposite to have a minimum of… #768
* Fix TAML schema for array groups #767
* requested feature: large number display #766
* bump down saveScaledImage default to 256 #765
* getAssetIdByFilename loaded state fix #764
* Misc FIxes for 2022/04/09 #763
* Updated readme with new links #762
* Add funding/sponsor options for support #761
* Fixes tooling of Forest Editor to be module-friendly #760
* Misc Fixes 2022/04/05 #759
* display the item to be spawned #758
* Misc Fixes 2022/04/04 #757
* Misc Fixes 2022/04/03 #756
* Misc Fixes for terrain material editing, creation and usage #755
* Fixes issue where nested callOnModules would thrash the queued exec lists from other invokes #754
* Misc Fixes for 2022/03/27 #753
* Misc Bugfixes for 2022/03/26 #752
* update sdl to https://github.com/libsdl-org/SDL 22March 2022 #751
* Misc tool fixes20220320 #750
* Misc Tool and Asset Import fixes and improvements #748
* extended callonModules hooks for baseline playgui #747
* fix compilation flaws #746
* Fixes handling of the setEditor commands so that the dropdown Editors menubar entry properly works #745
* Fixes and cleans up various issues and error spam for core and tools folders #744
* Changes the creation of new materials in the material editor process #743
* Tweaks handling of "invisible" files #742
* Adds a systemCommand console utility function #741
* crashfix and projection fix for spotlights with cookies #740
* point baseline fog color at the right target hen in deferred mode #738
* ensure MissionCleanup exists before .mis load #737
* Sky improvements #736 by marauder2k7 was merged on Mar 9
* Fixes handling of loading non-DDS images to better handle pointer references with the GBitmap resources. #735
* fix probe baking typo #734
* Fixes saveScaledImage to handle DDS format files, since DDS's go through a separate resource loader #733
* Misc importer improvements to handle importing in-place more predictably #732
* Fixes some mishandled cases when preprocessing objects and functions for project import #731
* Base UI module standardize pr #730
* template mixins need this-> specified #729
* doublesided material renderfix #728
* Probe Bake Capturing flag toggle fix #727
* Improves logical checks for the default value so it's more sane and stable #726
* Rework of the Probes and Probe Bin #725
* Shifts handling of material and terrain material definitions to be written into the asset definition taml file instead of having an extra loose file #723
* clean up ambiguous reference #722
* GuiBitmapCtrl named texture fixes. #721
* Changes the -> syntax check from exclusively checking simgroups to checking simsets, allowing both to be used #720
* Updated project importer #719
* Sound Asset Fleshout #718
* Improve tinyXml2 output formatting #717
* Fixes creation of convex shapes via editor #715
* Updates the handling of the baking of shape asset previews #714
* Feature: VFS Security #713
* fix ServerPlaySound #711
* fix opengl device not returning the correct anisotropic value #709
* BugFix: Correct a windows-only pathing issue in terrMaterial #708
* WIP: BugFix: Correct 'make install' not working on MacOS #707
* augments playSoundAsset #705
* A clean implementation of Lukas' Fix side projection #684 PR with Az's addendum fix rolled in #704
* BugFix: Fix a Windows ASAN reported allocation/deallocation mismatch error. #703
* Fixes mapping of imposter images to be packed as part of the shape asset, and fixes paths to be formatted more sanely. #702
* Fix console warning when calling void functions in console #701
* Cleans up some core execution behavior #699
* Removes the Library tabs from the World and GUI editors to avoid confusion #698
* BugFix: Correct compilation for MacOS #696
* Minor cmake corrections #694
* fix metal sound entry for playerdata #692
* use internalname for terrain layers #691
* TSStatic::updateMaterials() crashfix #690
* cleanups for sound assets #689
* adds colorization to GuiBitmapButtonCtrl #688
* Misc QOL and Bugfixes for 2021/11/26 #687
* modular source work #686
* BugFix: Correct data corruption potential in GuiInspectorField #685
* BugFix: Correct the inability to build on MacOS #681
* make use of folder properties in cmake #680
* set cubemapsaver profile to one that preserves sizes #679
* Fixed a leak with console stack in the interpreter. #678
* Fix extension case handling when looking up assimp importer #
* Optionally allow to treat script assert as warning #676
* fix reported ASAN crash #675
* Adjustment: Generalization of platformX86UNIX to platformPOSIX #674
* Shifts utilization of gui elements in editors that point to 'normal' image assets to utilize generated previews instead. #673
* Misc fixes2021114 #672
* brdf handling corrections #671
* Add Object Inheritence Acceptance Test #670
* BugFix: Correct the vehicle types double-tapping onAdd and onRemove #669
* Feature: Implement a TurretObjectType bit for typemasks #668
* fix fbx importer lookup for setting formatScaleFactor #667
* BugFix: Correct ASAN reported out of bounds reads in AssetImporter #666
* fill out a %this variable for trigger callbacks #665
* Better Architecture detection strategy if compiling on Apple Silicon #664
* \[Tokenizer] BugFix: Correct a malloc/delete mismatch #663
* Misc asset import QOL and bugfix changes #662
* better handle old style references to named texture targets #661
* new method tsstatic.getNodeTransform #660
* \[TAML] BugFix: Correct a delete and new\[] mismatch in tamlWriteNode #659
* imageasset array profile fixes #658
* Updates asset importer and project importer to output to separate log files into tools/logs #657
* BugFix: Correct Module deinitialization Ordering #656
* BugFix: Correct an ASAN reported memory error caused by incorrect usage of \_\_sync\_fetch\_and\_add #655
* BugFix: Correction for compiling on x86 Unix devices. #654
* BugFix: Correct an invalid memory access error caused by the tab autocomplete #653
* BugFix: Correct a crash in the variable inspector #652
* BugFix: Correct an ASAN use-after-free Error in TSShapeEdit #651
* BugFix: Correct an ASAN reported memory access error in GuiGameListMenuCtrl #649
* BugFix: ARM Compilation #648
* clean up more texture profile refs to kill spam #647
* fix material scrolling #646
* Misc QOL and Bugfixes for 2021/10/28 #645
* Adjustment: Update Assimp version to 5.0.1. #644
* BugFix: Don't assume a tooltip profile is going to be set when waking and sleeping #643
* BugFix: Correct the usage of a local variable in a non-function scope #642
* Feature: Properly detect ARM32/ARM64 in the CMake build process #641
* Alpha40/ibl cleanups #640
* typofix for impoerter #639
* BugFix: Correct usage of mkdir in posixVolume.cpp #638
* blatantly ganked from T2D; adds rotation as an option for drawbitmap #637
* addsa material.setAnimflags(LAYER,TAGS STRING); method #636
* BugFix: Address an error where deleting directories may result in an infinite loop #635
* BugFix: Correct the inability to use function keys F1-F10 #634
* BugFix: Allow the asset browser tree view to use a horizontal scroll bar #633
* BugFix: Correct a crash caused by sfxProfile #632
* adress gl spotlights disapearing for deferred #631
* This one slipped through - nextToken can't use local variable for its… #630
* BugFix: Correct GLSL Pathing Errors in Light Rays Shader #629
* BugFix: Correct a case where creator categories may get populated Incorrectly #628
* sound asset followups #627
* BugFix: Correct a few memory leaks #626
* BugFix: Correct a fatal error that may be thrown in case insensitive Unix IO #625
* BugFix: Correct CMake errors on Windows #623
* partial rollback of #620 to stop win-side pop ups #622
* update lpng #621
* BugFix: Clear several CMake warnings. #620
* fix opengl cubemap display #619
* BugFix: Correct the inability to spawn assorted objects #618
* Adjustment: POSIX Case Insensitivty #617
* Sound asset implements #616
* OpenGL Memory Info Extensions #615
* BugFix: Correct the SelectAssetPath Window not Listing any Paths #614
* followups to #582 #613
* Added more tests for torquescript #612
* Tweaks the MaterialAsset loading logic #611
* simplify callOnModules #610
* BugFix: Correct a Windows compilation error in the endian swap code #609
* BugFix: Correct MSVC Compiler Warnings #608
* Adjustment: Utilize native compiler intrinsics for endian swapping when available #607
* \[Linux] BugFix: Free the mouse cursor when triggering SIGTRAP #606
* don't try and sort ribbon particles #605
* BugFix: Clear a lot of warnings #604
* item->importStatus cleanup for asset importer #603
* fix groundplane material reference in examplelevel #602
* BugFix: Fix AL device listing #601
* BugFix: Correct tags in the asset browser not filtering correctly #600
* Add handling to RotationF's addRotation function to ensure formatted return #599
* uiCanvas keyboard mode callbacks. #598
* Adjusted handling of field converts in the project importer to deal with fields that didn't contain quotation marks #597
* GuiGameListMenuCtrl Update #596
* inputTest Module Update #595
* Fix specific usage of Con::executef where it was not being assigned t… #594
* Material editor fixes from eval cleanup. #593
* BugFix: Correct an object spawning error #592
* BugFix: Fix a crash that sometimes occurs when groups of of objects are deleted #591
* BugFix: Correct the onAdd callback not being raised for Projectiles #590
* BugFix: Corrections to allow the Linux win console to work #589
* kill splashscreen on nonwindows #588
* Allow local variables to be used in eval. #587
* particle cleanups #586
* Misc QOL and Bugfixes 2021/09/19 #584
* \[OpenGL] BugFix: Correct shader errors being thrown during load #583
* BugFix: Correct function call Error that causes the engine to crash #581
* Converts precipitationData to use sound asset macros #579
* dedicated gfx device suppression #578
* Reimplement object copy failures. #577
* Clean up more evals that have local variables are not working correctly. #576
* Misc QOL and bugfixes for 2021/09/12 #575
* Updates Prototyping module #574
* Fixes initial indexing of the tool palette widgets #573
* Fix local variable being eval'd in materialEditor #572
* Forgot to null out the datablock after being deleted when it fails to preload #571
* remove FMODex from Torque3D #570
* %guiContent importer compliance fix #569
* fix PhysicsShapeData upconvert entry #568
* BugFix: Correct an error where the GUI editor cannot be opened #567
* don't try to generate mipmaps for images that aren't n^2 dureing prev… #566
* Bugfix qol 20210909 #565
* macro cleanup #564
* replace new with singleton to fix cannot re-declare object log file … #563
* followup to #531. fixes the same issue on mac #562
* Sound asset initial rollin #561
* BugFix: Correct placement of the TORQUE\_NOINLINE statements #560
* Workaround: GCC Release mode Runtime Errors #559
* Misc Fixes and QOL improvements #558
* mini cleanups for ab #556
* Update thread ids for 64bit support. #555
* account for the possiblity of \_set##name(StringTableEntry \_in entries somehow getting punted nulls #554
* sanity check nodelist presence #553
* ensure new (foo) lines being converted are valid according to findObj… #552
* DiffuseRenderPassManager.addManager "cleanups" #551
* Misc Quality of Life and Bug fixes #550
* be clear where we're referencing gbuffer render targets #549
* kill off glowchan leftovers #548
* fixes for copypastas that somehow slipped in #547
* Converts most of AFX classes to utilize assets #546
* Enforces filename string case sensitivity for assets' internal filenames #545
* \[PLEASE TEST BEFORE MERGE] Mac font stuff #544
* MacOS fixes #543
* tooltip work #542
* Fixes new emitter button bitmap to proper fieldname #540
* crash fixes #539
* \[Shape Editor] BugFix: Correct a bad octahedron.dts reference when using the mount viewer. #535
* Importer sanitizing #534
* Bugfix linux release builds for Clang #533
* Linux BugFix: OpenAL Loading #532
* Asset Browser on Linux Fixes #531
* \[Material Editor] BugFix: Correct case sensitivity errors on the model previews when running on case sensitive systems (Ie. Linux). #530
* get the splash screen on linux to stop corrupting the main window #529
* suppress deletion of temp material created by the editor #527
* ensure the asset browser is executed prior to other pseudo-modules that may need bits #526
* report if SDL\_CreateWindow is unable to create a window at all #523
* bad constructor usage! bad! GCC no like! #522
* give useful data when not finding a given shader var #521
* Engine Asset Update #520
* Update TinyXML to TinyXML2 #517
* partly address #502 #515
* adress #510 - missing GFXFormatR11G11B10 macrohook #514
* template index file review #513
* adress #508 - fix postfxmanager default initialization #509
* adress #501 - thread oversight. #507
* adress #504 - typo leading to broken $origin reference #506
* typofix in getScreenResolutionList #500
* mac compilation and standarization fixes #499
* Script extension assignment. #498
* particle emitter bounds box fix #497
* Fix buffer overflow issue in StringUnit::getWords bug #496
*   TorqueScript Interpreter 2.0 C++ Script #495

    Fix return value conversion when using SimObject::call() method #494
* shadowmap validator tweaks #493
* report simset names for add/remove errors #492
* augment bitstream write error reporting #491
* connects staticshape::unmount to the parent chain so it can actually do so #490
* expose a zip file password cmake config option #489
* Window resolution options bug \[Mac] Test Needed #488
* Add support for Apple Silicon #487
* Update TORQUE\_GAME\_ENGINE version number to reflect current version 4.0 #486
* make string to char\* conversion automatic #485
* form steve yorkshire: mat editor save extension fix #484
* Updates the masterserver domain referenced in the default scripts, pointing it to the new torque3d master server #483
* add additional chars to the flatfile->asset->objectID name santizatio… #482
* report which profile usages are conflicting (was,is) C++ QoL Enhancement #481
* adds binary to decimal and vice versa methods QoL Enhancement Script #480
* Implement Unit Test Suite for TorqueScript. C++ enhancement Script #479
* Fixes a resolution switching issue when the game uses **only** OpenGL… bug C++ Script #478
* Updates the torsion.in file to properly be configured to handle tscript extension C++ Script #477
* reset emissive to show 0,0,0,0 for local/vector lights in a manner th… #476
* Adds import config settings for forcefully adding configurable suffixes for shapes, materials and images #475
* Fixes display of internal names on objects shown in guiTreeViewCtrl #474
* Misc. minor AB fixes #473
* Makes the DB creation process better jive with modules #472
* Adjusts Forest object creation and forest item data creation/management to work with asset/module workflows #471
* fix emissive #470
* Missed a function where similar to previous was needed for the shape editor list fix to ensure it works both ways #468
* Fixes the constructor path compare logic in the shape editor so the lists can populate correctly. #467
* set prefab and makemesh origins to the biggest model #466
* ribbon particle resource port #464
* terrain brush dragging cleanups #463
* Re-fixes terrain edit dragging without breaking paint actions #462
* Implements shape preview caching for shape assets #461
* re-fix file exclusivity, readd callonmodules variable extension #460
* update openal-soft #459
* Integrates object creator logic into the AB #458
* augment datablock file handling to include references with no suffixes #457
* Fix for transparency in splash images #456
* version is not provided by current vendor api making it pointless to … #455
* Added fix for #365 from PR #367 - buffer overrun bug #454
* Corrects missed asset script file references in asset definitions when swapping to the tscript extension #453
* Add Discord badge to README #452
* Fixes some minor errors on MacOS regarding compiling in clang #451
* provides a general Playgui\_onWake callback for modules #450
*   Loading from zipped game directories. #449

    general spawnspheres #448
* Cmake allow non-source project directory #447
* add parameter handling to callonmodule callbacks. #446
* revert #401 as while it does surpress hieght painting touching the ce… #443
* Removed old fixed function code from GFX. #442
* D3d11 texture lock #441
* Improve terrain rendering, handle bug with no detail #438
* Assetifies MeshRoad, Decal Road, and the material slot of GroundCover #436
* Adjusts handling of C++ asset types #434
* moar asset errorhandling #433
* sdl usage standards proposal 3 #432
* mac fixes #430
* High resolution timer fixes #429
* Consolidates and standardizes terrain creation between the editor, asset browser and creator panel #428
* membervar compile fix #426
* Initial pass at implementing MaterialAsset macromagic utility functions #425
* Height based terrain texture blending #424
* OpenGL: Access viewtangent "DX" style for gbNormal in terrain textures #421
* update sdl2 to release 2.0.14 #418
* corrected and implemented a usage of shapeasset macros #417
* Converts GroundPlane to utilize assets #415
* Misc various improvements for noted issues with the Asset Importer #414
* add validation flagging for server objects #413
* Fixes a few bugs/issues on Linux #412
* asset pipe cleanups #409
* Fixes for AA toggle and GFX Device reporting for options menu #408
* Wraps material animation floats to sane values. #407
* Parametrize script extension, default to 'tscript' enhancement #406
* Correct bump map in waterObject.cpp being in sRGB space #403
* Fixing bug Terrain Editor bug #91 #401
* Fixes logic that checks if a postFX was enabled so the PostFX Editor works properly #400
* Misc Editor and editor GUI fixups/improvements #399
* mMipCount was never being filled out. just use mPrefilterArray->getMi… #398
* Removes unneeded redundant asserts when the functions already have range sanity checks #397
* Adds handling so the pause menu has a button to exit the editor as a quick shortcut #396
* WIP of marking active scene in the scenetree #395
* Fixes Datablock and Prefab DragnDrop behavior with the AB #394
* Adds ability to delete a module #393
* Cleanup of some log errors and spam with assets #392
* Better handling for finding modules by file path. Mainly used in asset importer #391
* variation on #387 that also introduces errorcodes #390
* hooks up shapebase children breadcrumb #388
* adress #385 #386
* get shapeassetID read. TODO: find further flaws and unrem the filter #383
* Pause Menu toggle fix #381
* light review (hdr and metalness vs direct lighting) #379
* shader preprocessor fixes #378
* mac compile fixes #377
* be sure to executte defaults prior to clientprefs #376
* Adds handling to the path manager so it can deal with both looping and non-looping paths #375
* Misc fixes to ensure that the default postFX save, load and editing process is valid #374
* get gl side HDR compiling, attempt clamp to keep bloom in range #373
* Misc. probe bake/load fixups #372
* Adds a sanity check so asset names cannot start with a number #371
* Misc. BaseGame UI fixes #370
* Added date/timestamp option to console log #369
* fix #365 #367
* Overhauls the handling of probes to utilize an active probe list #364
* Improves default suffix handling for asset importer on image assets under a material asset #363
* Basic prototyping module initial upload #362
* Updates some level asset functions and script handling #361
* clip ./ when doing pattern matching #360
* Move slider to core and add opacity slider to console gui in BaseGame #359
* Updates macromagic to properly set up for init'ing when image assets are set in material and terrain materials #357
* sceneobject mountchain enable/disable collision aug #356
* fix gl compilation #355
* fix for empty r channel creation of composites crashing out #354
* fix GCC compile #353
* followup #352
* replicate exec signatures for queueExec #351
* EngineExportScope(){} _can't_ be initialized by default, aparantly #350
* Fix paths in caustics shader bug Script #349
* Use string.compare instead of String::compare when comparing strings bug C++ #348
* fix terrain compilation #347
* gl needs OUT\_col filled out to return anything #346
* pathshape gravity suppression injection #345
* Profile editor for the meshRoad object C++ enhancement Script #343
* Replace uses of dStrCmp with new String::compare C++ QoL Enhancement #342
* breakShape() - remove parts created with invalid object box . C++ QoL Enhancement #341
* ForceFOV is not working on GuiTSControl. bug C++ help wanted question #339
* extra option for terrain block to disable the update of the basetexture #337
* Remove old and not needed torqueconfig files #336
* SFX Player fixes #74 #334
* Add NavMesh to World Editor #332
* Temporary fix for the geometry feed in spotlights #329
* Implementation of guiRenderTargetVizCtrl #328
* Fix global variables not being able to be used inside of a foreach$ loop bug C++ #327
* Feature/improve cinterface C++ help wanted QoL Enhancement #326
* code review: #324
* shift pbrconfig to ORM in keeping with the prepoderance of industry standards #323
* minor cleanups: #321
* memleak fix #320
* Implements new shape fadeout and lighting fade/max lights/shadows pref options into the options menu #319
* Implements hook-look-up logic for shape assets to ShapeBaseData including autoimport handling #317
* Updated version of OTHGMars' updated window and resolution options modes. #316
* Various misc. tweaks and fixes targeting memleaks and crashes #315
* Fixes the hook-ins so when a shape asset is changed, tsstatics now are correctly triggered for a reload #314
* fix chooseleveldlg #313
* Reorgs the layout and editing of PostFX with some supplemental level save/load changes #312
* Re-implements the dynamic cubemap mode option for reflection probes #311
* Misc asset browser/asset creation fixes #310
* new trigger features: triponce, tripcondition, and trippedby. #309
* Misc fixes for Asset Browser navigation, scene asset utilization and editor settings #308
* Misc editor settings fixes and additions #307
* Misc Fixes for level saving and selecting asset paths #306
* Fixes logic when opening shapeEditor with a TSStatic selected #305
* Misc. Fixes and cleanup for lights #304
* Miscellaneous small issue fixes #303
* Integrates sound and shapeAnimation assets into the importer #302
* Material Asset import lookups and initial re-integration of sis files. #301
* Adds sorting to the settings class so when it saves out to file #300
* Level Asset Dependency handling and various level fixes #299
* fix for trigger::testobjects vector population #298
* Adds a notes object that only displays in the editor #297
* Fix compilation with shipping flag #295
* Adds a pref to dictate if local lights can cast shadows or not. #294
* Expands AB tooltips with file info #293
* Adds image variances for the menuGrid image #292
* Adds in the missing materials used for the Convex Proxies for triggers, zones, etc. #291
* Standardizes the tooltip profile colors to match the rest of the themeing stuff #290
* Adds logical check to skip animated statics when baking selection to mesh. #289
* Misc. Image Asset improvements #288
* More misc. fixes #287
* Updates SDL to 2.0.12 #286
* Followup commit to switch to engine conventions #285
* Basic Platform::openWebBrowser implementation for linux #284
* mouse display for keybinds #283
* Even more misc asset fixes #280
* More various Asset Browser and importer fixes #279
* from @OTHGMars: AssetImporter type and path for material look-ups. #277
* Queue exec order #276
* Fixes the backend logic for setting/creating 3DTextures in D3D11 #275
* Various fixes for both asset importing and some workflowy bits relating to assets stuffs #274
* Fix gamepad binds on non-windows. #273
* inputTest Module Initialization #272
* Alpha40 shader gen cleanups #271
* Some cleanup and adjusting of local light fields and default settings. #270
* Adds additional light preferences #269
* Adds some console preference variables for object fade overriding on TSStatics #268
* ribbon shader variable order fix from @steve\_yorkshire #267
* Adds a default value to the lodType of the asset importer #266
* proper variation on the datablock file list erasure #265
* crashfix: const U32 numVerts = curEntry.vertBuffer-> is invalid for vectorlights #264
* crashfix: decal report when missing the DB entry was malformed #263
* fix reverb out of bound initializations #262
* groundframe generation cleanup work #261
* Moves the BaseUI module to utilize the queuedExec function #260
* Captures secondary window close events #259
* Updates the BaseGame UI theme #258
* Fix GCC9 complaints #257
* Fix GCC9 complaints #256
* Fixes issue with Drag-and-drop asset import action #255
* Moves the delta-based rounding function Verve used up into the engine #254
* from jeff and tim: review of lighting impacts #252
* Added slider to consoleDlg for bg alpha (Needs refinement) #251
* from @rextimmy new isbackground shader feature. #250
* Adds additional functions for inserting inspectorGroups #249
* cleanup singlechannel glowmask leftovers (we use a full rgb map now) #248
* Various improvements, fixes and enhancements to Asset editor stuffs #247
* Various improvements, fixes and expansions for Asset Importing #246
* Minor additions to popup menus #245
* Adds logic to guiTextEditCtrl to have placeholder text when the control is empty. #244
* from @practicing01: trigger mounting #243 by Azaezel was merged on Jul 10, 2020
* from practicing: aiplayer onstuck correction #242 by Azaezel was merged on Jul 10, 2020
* comparison flaw in spotlight animation check. #241 by Azaezel was merged on Jul 8, 2020
* fixed cpu detection on 64bit windows #240 by JeffProgrammer was merged on Jul 7, 2020 1
* \#include "console/typeValidators.h" #239 by Azaezel was merged on Jul 5, 2020
* fix cubemap capture for gl #238 by Azaezel was merged on Jul 5, 2020
* safety check #237 by Azaezel was merged on Oct 9, 2020 1
* client cleanups #236 by Azaezel was merged on Jul 26, 2020 1
* Fix crash due to GuiEditCanvas::save() #235
* Implements missing \_captureBackBuffer method for GL gfx layer. #234
* Fix for crash in \_onZoningChanged methods when called by hidden objects. #233
* Reworks the terrain loader code to work with the assets. #229
* adress #116 and #179 (shaderside) #227
* adress #225 #226
* Removal of old font files from basegame template #223
* adress #221 crash surpress macromap #222
* adress #16 - don't need to swizzle vert colors #218
* groundcover requested augs #216
* fixes for trigger onenter/onleave #215
* adds an animspeed and animoffset to tsstatic instances #214
* typofix in opengl terrain shadergen #213
* export rounds LODs to the nearest power of 2 #212
* Updated links, added info from torque3d.org #211
* adress #162 based on work by Chad Hall #210
* adress #203 #209
* Linux Slash compatability #208
* adress #205 #206
* D3D-only compile fix DirectX #204
* implement copyResource, fix copyToBmp #202
* Remove trailing whitespaces from simObject.cpp and fix pointer format #2382
* fixed texture call which reported as a missing image #2378
* Updates SDL to 2.0.10 #23699
* OpenAL efx fixes for macOS/Linux #2362
* Modification of #2145 Improvement #2354
* adress #2344 #2352
* Full template Scene conversion Bugfix Improvement #2345
* fix(es) for volumetric fog when dealing with dedicated servers. #2342
* Makes the popups correctly operate anywhere in the space of the canvas Bugfix #2340
* Adds logic to temporarily disable collisions of mounted objects on Players Bugfix #2339
* Fixes some outstanding menubar problems. Bugfix #2338
* Fixes artifacts in Cloud Layer. Bugfix #2336
* rewrite of NavMeshUpdateAll/NavMeshUpdateAroundObject Bugfix Improvement #2335
* Cleanup and minor tweaks to the core dir structure. Improvement #2334
* Fixes a crash that occurs on linux headless servers Bugfix #2332
* Set contrsaints for Player Z rotation Bugfix #2331
* Adds a filter for materials to never import when importing a shape New feature #2328
* Adds ability to skip loading of cached dts in enumColladaForImport New feature #2327
* Adds visualizers for various types of colorblindness Improvement New feature #2326
* Moves the path return from fileDialog through the returnBuffer Bugfix #2325
* Tweaks some object handling of guiTreeViewObj Improvement #2324
* Sanity check for calling getFieldValue Bugfix #2323
* Adds gui3DProjectionCtrl New feature #2322
* Updates TextEdit value when focus is lost. Improvement #2321
* Allows special inspectorFields to override their height Improvement #2320
* Initial implementation of the Scene object Improvement New feature #2319
* Tweaks to the Asset/Module info echo behavior to spam the console less. Improvement #2318
* Adds ability to set the split point of a guiSplitContainer #2317
* corrects a parity flaw between wireframe and non wireframe box display #2315
* Switches to absolute position for mouse tracking. #2313
* Snap to terrain Z offset. #2311
* Vert color correction #2310
* Remove redundant variables and clean up C4312 and C4305 warnings #2309
* nextfreemask does nothing for proximity mines as there are no subclas… #2307
* corrects a copy-corruption flaw with GuiSwatchButtonCtrl::onMouseDragged #2305
* Sdl joystick2 #2300
* Sqlite Console refactor, #2299
* Travis Compile #2298
* Fix SDL Input::getKeyCode on software keyboard layouts #2296
* Add a .editorconfig file #2295
* Adds features to GuiInputCtrl #2294
* afxRenderHighlightMgr: account for hardware skinning #2292
* corrects compilation errors on non-mac unix derivatives #2288
* corrects compilation errors on mac #2287
* Nfd update #2286
* corrects a pair of conversions. one object oriented, one not. #2285
* Fills in monitor functions in PlatformWindowManagerSDL #2284
* Adds handlers for sdl focus events. Final review Improvement #228
* Fixes CanvasSizeChangeSignal and Canvas::onResize() under SDL Final review Improvement #2282
* OpenALEffects New feature #2281
* Approved Improved BitStream writeQuat/readQuat methods. Improvement #2277
* filter out pixel shader normalmap calcs when not in deferred mode. Bugfix Final review #2276
* Adds Clamp to QuatF::dot() Bugfix #2275
* Core module-ification Improvement #2272
* micro patch to the nativefiledialogues library to mirror file type name #2270
* alternative to #2268 : remove secondary profiling #2269
* Network Code Fixes Improvement #2267
* Resolves #1721 - ScatterSky zOffset Bugfix #2266
* Fix for bug in GFXVideoMode::parseFromString() Bugfix #2265
* Resolves #740 - Remove redundant code in \_GFXInitGetInitialRes() Bugfix #2264
* member var conversion error that oddly didn't crop up till mac testing. Bugfix #2262
* Changes TSStatic::castRayRendered to use passed texcoord argument. Bugfix #2259
* Fixes the front/back ortho views in the editors Bugfix #2258
* Particles should go downwind (while windCoefficient >0) Bugfix #2255
* SDL 2.0.8 Bugfix Improvement #2254
* It's almost imposible to change direction of wind. Reseting mCurrentT… Bugfix #2252
* openal-soft updates Bugfix Improvement #2251
* Fixes various incorrect popup menu behaviors. Bugfix Improvement #2250
* Updates PlatformCursorController to use full set of SDL cursors. Improvement #2249
* New cinterface #2248
* Corrects a problem with the D3D11 texture lock/unlock mechanism #2247
* Update CInterface #2246
* Clean-up uses of ConsoleFunction etc. #2245
* Higher resolution app icon #2243
* Interpreter Hotfix: Check for NULL on the thisObject before using it. #2242
