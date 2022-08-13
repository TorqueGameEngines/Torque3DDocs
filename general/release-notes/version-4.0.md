# Version 4.0

* [GitHub release](https://github.com/TorqueGameEngines/Torque3D/releases/tag/v4.0)
* [Release announcement](http://forums.torque3d.org/viewtopic.php?f=15\&t=938)

## Notes <a href="#toc0" id="toc0"></a>

## Pull Requests Merged [source](https://github.com/TorqueGameEngines/Torque3D/tree/Release\_4\_0) <a href="#toc1" id="toc1"></a>

1. Alpha40/ts static cleanup #840
2. tsstatic aug cleanups #839
3. Re-enables reimport of assets #838
4. Cmake DEBUG/RELEASE flag standardization #837
5. targeted fix for #45 #836
6. pathshape cleanups and callbacks #835
7. soundAsset profile and description getter fixes #834
8. particle emission safeties #833
9. Update TORQUE\_GAME\_ENGINE\_VERSION\_STRING version number 4.0.0 #832
10. Misc FIxes 2022/07/24 #831
11. fix bounds box display #830
12. DBEditor callback fix for asset fields #828
13. Misc Fixes 2022/07/02 #827
14. make sure the volfog manager is dead before we kill scene #825
15. fix unspecified storage location mangle for new asset creation #824
16. fix a pair of taml typos #823
17. BugFix: Correct a missing asset for filling the background of the console #822
18. Misc Fixes 2022/06/20 #821
19. fix shape errorcodes #820
20. you want the higher number, not the lower #819
21. fix computeForwardProbes shadergen gl side #818
22. fix out of bounds reference in arrayobject #817
23. fix TORQUE\_TOOLS = off compilation #815
24. fix vectorlight visualizer varnames #814
25. Fix Misc ConvexShape Tooling Issues #813
26. BugFix: Remove the GCC Workaround #812
27. Misc Fixes 2022/06/09 #811
28. allow ambient light injection into ibl #809
29. Misc Fixes 2022/06/05 #808
30. Disconnect and Shutdown fixes #807
31. Uncomments networking lines that ensure client has the particle's textures #806
32. Sound Networking Fixes #805
33. Misc Fixes 2022/06/01 #804
34. proper player head rot clamp #802
35. constrain player mRot.z reguardless of translation #800
36. Misc Fixes for 2022/05/30 #799
37. Use screen space coordinates for mouse pointer position #798
38. BaseGame Template: Fix script assert on canceling game options changes #797
39. fix particle emitter asset browser spawning #796
40. lower min brushsize for forest to sub-meter levels #795
41. set convexshape to use a standard vertex type #794
42. fix on-RPC-command explosion sounds not playing the first time #793
43. BugFix: Correct MacOS not responding to various hotkeys #792
44. BugFix: Correct invalid fall-through behavior in sdlInputManager.cpp. #791
45. Misc Fixes for 2022/05/24 #790
46. Overhaul on CPU detection for Windows, Mac (x64/arm64) & Linux #789
47. Fixes issue where creating a new ForestItem wouldn't have it show in the ForestItemData dropdown on brushes until you restart. #788
48. Fix edgecase where empty string was not being explicitly set to 0 in … #787
49. Better allocator for TorqueScript temp conversions during interpretation #786
50. Adjustment: Update libsdl to address a bug in compilation on MacOS #785
51. fix sDefaultAmbience intialization. #783
52. Misc Fixes for 2022/05/10 #781
53. Implements a more standardized way to format usual UI pages by having the ability to utilize the UINavigation namespace for page stack navigation #780
54. Make the Console Sane Again #779
55. Fix weird ternary operator in torquescript regression #778
56. update assimp to 5.2.3 Bugfix-Release #777
57. Adds a conditional to the github workflow file so it only runs on the main repo #776
58. update sdl to release 2.0.22 #775
59. Github actions CI #774
60. Removes the BGRA inversion when displaying vertex colors on materials #773
61. Cleanup: Resolve several compiler warnings associated with TORQUE\_DEBUG #772
62. correct mac compilation #771
63. add .vs directory to gitignore #770
64. Misc Fixes 2022/04/23 #769
65. drop the prior requirement for a createcomposite to have a minimum of… #768
66. Fix TAML schema for array groups #767
67. requested feature: large number display #766
68. bump down saveScaledImage default to 256 #765
69. getAssetIdByFilename loaded state fix #764
70. Misc FIxes for 2022/04/09 #763
71. Updated readme with new links #762
72. Add funding/sponsor options for support #761
73. Fixes tooling of Forest Editor to be module-friendly #760
74. Misc Fixes 2022/04/05 #759
75. display the item to be spawned #758
76. Misc Fixes 2022/04/04 #757
77. Misc Fixes 2022/04/03 #756
78. Misc Fixes for terrain material editing, creation and usage #755
79. Fixes issue where nested callOnModules would thrash the queued exec lists from other invokes #754
80. Misc Fixes for 2022/03/27 #753
81. Misc Bugfixes for 2022/03/26 #752
82. update sdl to https://github.com/libsdl-org/SDL 22March 2022 #751
83. Misc tool fixes20220320 #750
84. Misc Tool and Asset Import fixes and improvements #748
85. extended callonModules hooks for baseline playgui #747
86. fix compilation flaws #746
87. Fixes handling of the setEditor commands so that the dropdown Editors menubar entry properly works #745
88. Fixes and cleans up various issues and error spam for core and tools folders #744
89. Changes the creation of new materials in the material editor process #743
90. Tweaks handling of "invisible" files #742
91. Adds a systemCommand console utility function #741
92. crashfix and projection fix for spotlights with cookies #740
93. point baseline fog color at the right target hen in deferred mode #738
94. ensure MissionCleanup exists before .mis load #737
95. Sky improvements #736 by marauder2k7 was merged on Mar 9
96. Fixes handling of loading non-DDS images to better handle pointer references with the GBitmap resources. #735
97. fix probe baking typo #734
98. Fixes saveScaledImage to handle DDS format files, since DDS's go through a separate resource loader #733
99. Misc importer improvements to handle importing in-place more predictably #732
100. Fixes some mishandled cases when preprocessing objects and functions for project import #731
101. Base UI module standardize pr #730
102. template mixins need this-> specified #729
103. doublesided material renderfix #728
104. Probe Bake Capturing flag toggle fix #727
105. Improves logical checks for the default value so it's more sane and stable #726
106. Rework of the Probes and Probe Bin #725
107. Shifts handling of material and terrain material definitions to be written into the asset definition taml file instead of having an extra loose file #723
108. clean up ambiguous reference #722
109. GuiBitmapCtrl named texture fixes. #721
110. Changes the -> syntax check from exclusively checking simgroups to checking simsets, allowing both to be used #720
111. Updated project importer #719
112. Sound Asset Fleshout #718
113. Improve tinyXml2 output formatting #717
114. Fixes creation of convex shapes via editor #715
115. Updates the handling of the baking of shape asset previews #714
116. Feature: VFS Security #713
117. fix ServerPlaySound #711
118. fix opengl device not returning the correct anisotropic value #709
119. BugFix: Correct a windows-only pathing issue in terrMaterial #708
120. WIP: BugFix: Correct 'make install' not working on MacOS #707
121. augments playSoundAsset #705
122. A clean implementation of Lukas' Fix side projection #684 PR with Az's addendum fix rolled in #704
123. BugFix: Fix a Windows ASAN reported allocation/deallocation mismatch error. #703
124. Fixes mapping of imposter images to be packed as part of the shape asset, and fixes paths to be formatted more sanely. #702
125. Fix console warning when calling void functions in console #701
126. Cleans up some core execution behavior #699
127. Removes the Library tabs from the World and GUI editors to avoid confusion #698
128. BugFix: Correct compilation for MacOS #696
129. Minor cmake corrections #694
130. fix metal sound entry for playerdata #692
131. use internalname for terrain layers #691
132. TSStatic::updateMaterials() crashfix #690
133. cleanups for sound assets #689
134. adds colorization to GuiBitmapButtonCtrl #688
135. Misc QOL and Bugfixes for 2021/11/26 #687
136. modular source work #686
137. BugFix: Correct data corruption potential in GuiInspectorField #685
138. BugFix: Correct the inability to build on MacOS #681
139. make use of folder properties in cmake #680
140. set cubemapsaver profile to one that preserves sizes #679
141. Fixed a leak with console stack in the interpreter. #678
142. Fix extension case handling when looking up assimp importer #
143. Optionally allow to treat script assert as warning #676
144. fix reported ASAN crash #675
145. Adjustment: Generalization of platformX86UNIX to platformPOSIX #674
146. Shifts utilization of gui elements in editors that point to 'normal' image assets to utilize generated previews instead. #673
147. Misc fixes2021114 #672
148. brdf handling corrections #671
149. Add Object Inheritence Acceptance Test #670
150. BugFix: Correct the vehicle types double-tapping onAdd and onRemove #669
151. Feature: Implement a TurretObjectType bit for typemasks #668
152. fix fbx importer lookup for setting formatScaleFactor #667
153. BugFix: Correct ASAN reported out of bounds reads in AssetImporter #666
154. fill out a %this variable for trigger callbacks #665
155. Better Architecture detection strategy if compiling on Apple Silicon #664
156. \[Tokenizer] BugFix: Correct a malloc/delete mismatch #663
157. Misc asset import QOL and bugfix changes #662
158. better handle old style references to named texture targets #661
159. new method tsstatic.getNodeTransform #660
160. \[TAML] BugFix: Correct a delete and new\[] mismatch in tamlWriteNode #659
161. imageasset array profile fixes #658
162. Updates asset importer and project importer to output to separate log files into tools/logs #657
163. BugFix: Correct Module deinitialization Ordering #656
164. BugFix: Correct an ASAN reported memory error caused by incorrect usage of \_\_sync\_fetch\_and\_add #655
165. BugFix: Correction for compiling on x86 Unix devices. #654
166. BugFix: Correct an invalid memory access error caused by the tab autocomplete #653
167. BugFix: Correct a crash in the variable inspector #652
168. BugFix: Correct an ASAN use-after-free Error in TSShapeEdit #651
169. BugFix: Correct an ASAN reported memory access error in GuiGameListMenuCtrl #649
170. BugFix: ARM Compilation #648
171. clean up more texture profile refs to kill spam #647
172. fix material scrolling #646
173. Misc QOL and Bugfixes for 2021/10/28 #645
174. Adjustment: Update Assimp version to 5.0.1. #644
175. BugFix: Don't assume a tooltip profile is going to be set when waking and sleeping #643
176. BugFix: Correct the usage of a local variable in a non-function scope #642
177. Feature: Properly detect ARM32/ARM64 in the CMake build process #641
178. Alpha40/ibl cleanups #640
179. typofix for impoerter #639
180. BugFix: Correct usage of mkdir in posixVolume.cpp #638
181. blatantly ganked from T2D; adds rotation as an option for drawbitmap #637
182. addsa material.setAnimflags(LAYER,TAGS STRING); method #636
183. BugFix: Address an error where deleting directories may result in an infinite loop #635
184. BugFix: Correct the inability to use function keys F1-F10 #634
185. BugFix: Allow the asset browser tree view to use a horizontal scroll bar #633
186. BugFix: Correct a crash caused by sfxProfile #632
187. adress gl spotlights disapearing for deferred #631
188. This one slipped through - nextToken can't use local variable for its… #630
189. BugFix: Correct GLSL Pathing Errors in Light Rays Shader #629
190. BugFix: Correct a case where creator categories may get populated Incorrectly #628
191. sound asset followups #627
192. BugFix: Correct a few memory leaks #626
193. BugFix: Correct a fatal error that may be thrown in case insensitive Unix IO #625
194. BugFix: Correct CMake errors on Windows #623
195. partial rollback of #620 to stop win-side pop ups #622
196. update lpng #621
197. BugFix: Clear several CMake warnings. #620
198. fix opengl cubemap display #619
199. BugFix: Correct the inability to spawn assorted objects #618
200. Adjustment: POSIX Case Insensitivty #617
201. Sound asset implements #616
202. OpenGL Memory Info Extensions #615
203. BugFix: Correct the SelectAssetPath Window not Listing any Paths #614
204. followups to #582 #613 by Azaezel was merged on Oct 11, 2021 1
205. Added more tests for torquescript #612 by JeffProgrammer was merged on Oct 9, 2021
206. Tweaks the MaterialAsset loading logic #611 by Areloch was merged on Oct 9, 2021
207. simplify callOnModules #610 by Azaezel was merged on Oct 8, 2021
208. BugFix: Correct a Windows compilation error in the endian swap code #609 by Ragora was merged on Oct 8, 2021
209. BugFix: Correct MSVC Compiler Warnings #608 by Ragora was merged on Oct 11, 2021 6
210. Adjustment: Utilize native compiler intrinsics for endian swapping when available #607 by Ragora was merged on Oct 7, 2021
211. \[Linux] BugFix: Free the mouse cursor when triggering SIGTRAP #606 by Ragora was merged on Oct 5, 2021
212. don't try and sort ribbon particles #605 by Azaezel was merged on Oct 8, 2021
213. BugFix: Clear a lot of warnings #604 by Ragora was merged on Oct 4, 2021
214. item->importStatus cleanup for asset importer #603 by Azaezel was merged on Oct 9, 2021
215. fix groundplane material reference in examplelevel #602 by Azaezel was merged on Oct 3, 2021
216. BugFix: Fix AL device listing #601 by Ragora was merged on Oct 3, 2021
217. BugFix: Correct tags in the asset browser not filtering correctly #600 by Ragora was merged on Oct 3, 2021
218. Add handling to RotationF's addRotation function to ensure formatted return #599 by Areloch was merged on Oct 3, 2021
219.
220.    uiCanvas keyboard mode callbacks. #598 by OTHGMars was merged on Oct 3, 2021

        Adjusted handling of field converts in the project importer to deal with fields that didn't contain quotation marks #597 by Areloch was merged on Sep 27, 2021
221. GuiGameListMenuCtrl Update #596 by OTHGMars was merged on Sep 25, 2021
222. inputTest Module Update #595 by OTHGMars was merged on Oct 3, 2021
223. Fix specific usage of Con::executef where it was not being assigned t… #594 by JeffProgrammer was merged on Sep 25, 2021
224. Material editor fixes from eval cleanup. #593 by JeffProgrammer was merged on Sep 25, 2021
225. BugFix: Correct an object spawning error #592 by Ragora was merged on Sep 24, 2021
226. BugFix: Fix a crash that sometimes occurs when groups of of objects are deleted #591 by Ragora was merged on Sep 24, 2021
227. BugFix: Correct the onAdd callback not being raised for Projectiles #590 by Ragora was merged on Sep 24, 2021
228. BugFix: Corrections to allow the Linux win console to work #589 by Ragora was merged on Sep 24, 2021
229. kill splashscreen on nonwindows #588 by Azaezel was merged on Sep 23, 2021
230. Allow local variables to be used in eval. #587 by JeffProgrammer was merged on Sep 20, 2021
231. particle cleanups #586 by Azaezel was merged on Sep 20, 2021
232. Misc QOL and Bugfixes 2021/09/19 #584 by Areloch was merged on Sep 19, 2021
233. \[OpenGL] BugFix: Correct shader errors being thrown during load #583 by Ragora was merged on Sep 19, 2021
234. BugFix: Correct function call Error that causes the engine to crash #581 by Ragora was merged on Sep 16, 2021
235. Converts precipitationData to use sound asset macros #579 by Areloch was merged on Sep 19, 2021 2
236. dedicated gfx device suppression #578 by Azaezel was merged on Sep 19, 2021
237. Reimplement object copy failures. #577 by JeffProgrammer was merged on Sep 13, 2021 1
238. Clean up more evals that have local variables are not working correctly. #576 by JeffProgrammer was merged on Sep 12, 2021
239.    Misc QOL and bugfixes for 2021/09/12 #575 by Areloch was merged on Sep 12, 2021

        Updates Prototyping module #574 by Areloch was merged on Sep 11, 2021
240. Fixes initial indexing of the tool palette widgets #573 by Areloch was merged on Sep 11, 2021
241. Fix local variable being eval'd in materialEditor #572 by JeffProgrammer was merged on Sep 11, 2021
242. Forgot to null out the datablock after being deleted when it fails to preload #571 by JeffProgrammer was merged on Sep 11, 2021
243. remove FMODex from Torque3D #570 by JeffProgrammer was merged on Sep 11, 2021 3
244. %guiContent importer compliance fix #569 by Areloch was merged on Sep 11, 2021
245. fix PhysicsShapeData upconvert entry #568 by Azaezel was merged on Sep 11, 2021
246. BugFix: Correct an error where the GUI editor cannot be opened #567 by Ragora was merged on Sep 11, 2021
247. don't try to generate mipmaps for images that aren't n^2 dureing prev… #566 by Azaezel was merged on Sep 10, 2021
248. Bugfix qol 20210909 #565 by Areloch was merged on Sep 11, 2021
249. macro cleanup #564 by Azaezel was merged on Sep 10, 2021
250. replace new with singleton to fix cannot re-declare object log file … #563 by Bloodknight was merged on Sep 8, 2021
251. followup to #531. fixes the same issue on mac #562 by Azaezel was merged on Sep 5, 2021
252. Sound asset initial rollin #561 by Areloch was merged on Sep 8, 2021
253. BugFix: Correct placement of the TORQUE\_NOINLINE statements #560 by Ragora was merged on Sep 1, 2021
254. Workaround: GCC Release mode Runtime Errors #559 by Ragora was merged on Sep 1, 2021 2
255. Misc Fixes and QOL improvements #558 by Areloch was merged on Sep 1, 2021
256. mini cleanups for ab #556 by Azaezel was merged on Sep 1, 2021
257. Update thread ids for 64bit support. #555 by JeffProgrammer was merged on Sep 1, 2021
258. account for the possiblity of \_set##name(StringTableEntry \_in entries somehow getting punted nulls #554 by Azaezel was merged on Aug 30, 2021
259. sanity check nodelist presence #553 by Azaezel was merged on Aug 29, 2021
260. ensure new (foo) lines being converted are valid according to findObj… #552 by Azaezel was merged on Aug 30, 2021
261. DiffuseRenderPassManager.addManager "cleanups" #551 by Azaezel was merged on Aug 30, 2021
262. Misc Quality of Life and Bug fixes #550 by Areloch was merged on Sep 1, 2021 6
263. be clear where we're referencing gbuffer render targets #549 by Azaezel was merged on Aug 28, 2021
264. kill off glowchan leftovers #548 by Azaezel was merged on Aug 28, 2021
265. fixes for copypastas that somehow slipped in #547 by Azaezel was merged on Aug 23, 2021
266. Converts most of AFX classes to utilize assets #546 by Areloch was merged on Aug 23, 2021
267. Enforces filename string case sensitivity for assets' internal filenames #545 by Areloch was merged on Aug 23, 2021
268. \[PLEASE TEST BEFORE MERGE] Mac font stuff #544 by JeffProgrammer was merged on Aug 27, 2021 1
269. MacOS fixes #543 by JeffProgrammer was merged on Aug 21, 2021
270. tooltip work #542 by Azaezel was merged on Aug 23, 2021
271. Fixes new emitter button bitmap to proper fieldname #540 by Areloch was merged on Aug 18, 2021
272. crash fixes #539 by Azaezel was merged on Aug 18, 2021
273. \[Shape Editor] BugFix: Correct a bad octahedron.dts reference when using the mount viewer. #535 by Ragora was merged on Aug 16, 2021
274. Importer sanitizing #534 by Areloch was merged on Aug 15, 2021
275. Bugfix linux release builds for Clang #533 by Ragora was merged on Aug 20, 2021 1
276. Linux BugFix: OpenAL Loading #532 by Ragora was merged on Aug 14, 2021 1
277. Asset Browser on Linux Fixes #531 by Ragora was merged on Aug 13, 2021
278. \[Material Editor] BugFix: Correct case sensitivity errors on the model previews when running on case sensitive systems (Ie. Linux). #530 by Ragora was merged on Aug 13, 2021
279. get the splash screen on linux to stop corrupting the main window #529 by Azaezel was merged on Aug 13, 2021 1
280. suppress deletion of temp material created by the editor #527 by Azaezel was merged on Aug 13, 2021
281. ensure the asset browser is executed prior to other pseudo-modules that may need bits #526 by Azaezel was merged on Aug 13, 2021
282. report if SDL\_CreateWindow is unable to create a window at all #523 by Azaezel was merged on Aug 10, 2021
283. bad constructor usage! bad! GCC no like! #522 by Azaezel was merged on Aug 10, 2021
284. give useful data when not finding a given shader var #521 by Azaezel was merged on Aug 10, 2021
285. Engine Asset Update #520 by Areloch was merged on Aug 9, 2021
286. Update TinyXML to TinyXML2 #517 by lukaspj was merged on Aug 9, 2021 5
287. partly address #502 #515 by Azaezel was merged on Jul 28, 2021
288. adress #510 - missing GFXFormatR11G11B10 macrohook #514 by Azaezel was merged on Jul 28, 2021
289. template index file review #513 by Azaezel was merged on Jul 28, 2021
290. adress #508 - fix postfxmanager default initialization #509 by Azaezel was merged on Jul 28, 2021
291. adress #501 - thread oversight. #507 by Azaezel was merged on Jul 28, 2021 3
292. adress #504 - typo leading to broken $origin reference #506 by Azaezel was merged on Jul 28, 2021
293. typofix in getScreenResolutionList #500 by Azaezel was merged on Jul 14, 2021
294. mac compilation and standarization fixes #499 by Azaezel was merged on Jul 5, 2021 3
295. Script extension assignment. #498 by OTHGMars was merged on Jun 27, 2021 6
296. particle emitter bounds box fix #497 by Azaezel was merged on Jul 14, 2021 3
297. Fix buffer overflow issue in StringUnit::getWords bug #496 by JeffProgrammer was merged on Jun 18, 2021
298.    TorqueScript Interpreter 2.0 C++ Script #495 by JeffProgrammer was merged on Sep 9, 2021 3

        Fix return value conversion when using SimObject::call() method #494 by just-bank was merged on Jun 15, 2021
299. shadowmap validator tweaks #493 by Azaezel was merged on Jun 22, 2021 1
300. report simset names for add/remove errors #492 by Azaezel was merged on Jun 22, 2021
301. augment bitstream write error reporting #491 by Azaezel was merged on Jun 22, 2021
302. connects staticshape::unmount to the parent chain so it can actually do so #490 by Azaezel was merged on Jun 22, 2021
303. expose a zip file password cmake config option #489 by Azaezel was merged on Jul 17, 2021 2
304. Window resolution options bug \[Mac] Test Needed #488 by OTHGMars was merged on May 17, 2021 1
305. Add support for Apple Silicon #487 by JeffProgrammer was merged on May 11, 2021 2
306. Update TORQUE\_GAME\_ENGINE version number to reflect current version 4.0 #486 by Jozor was merged on Apr 23, 2021
307. make string to char\* conversion automatic #485 by Azaezel was merged on Apr 22, 2021
308. form steve yorkshire: mat editor save extension fix #484 by Azaezel was merged on Apr 22, 2021 1
309. Updates the masterserver domain referenced in the default scripts, pointing it to the new torque3d master server #483 by Areloch was merged on Apr 22, 2021 1
310. add additional chars to the flatfile->asset->objectID name santizatio… #482 by Azaezel was merged on Apr 12, 2021
311. report which profile usages are conflicting (was,is) C++ QoL Enhancement #481 by Azaezel was merged on Apr 12, 2021
312. adds binary to decimal and vice versa methods QoL Enhancement Script #480 by Azaezel was merged on Apr 22, 2021
313. Implement Unit Test Suite for TorqueScript. C++ enhancement Script #479 by JeffProgrammer was merged on Apr 12, 2021 1
314. Fixes a resolution switching issue when the game uses **only** OpenGL… bug C++ Script #478 by Bloodknight was merged on Apr 22, 2021 8
315. Updates the torsion.in file to properly be configured to handle tscript extension C++ Script #477 by Areloch was merged on May 13, 2021 4
316. reset emissive to show 0,0,0,0 for local/vector lights in a manner th… #476 by Azaezel was merged on Mar 9, 2021
317. Adds import config settings for forcefully adding configurable suffixes for shapes, materials and images #475 by Areloch was merged on Mar 14, 2021
318. Fixes display of internal names on objects shown in guiTreeViewCtrl #474 by Areloch was merged on Mar 14, 2021 1
319. Misc. minor AB fixes #473 by Areloch was merged on Mar 14, 2021
320. Makes the DB creation process better jive with modules #472 by Areloch was merged on Mar 14, 2021
321. Adjusts Forest object creation and forest item data creation/management to work with asset/module workflows #471 by Areloch was merged on Mar 14, 2021
322. fix emissive #470 by Azaezel was merged on Feb 15, 2021
323. Missed a function where similar to previous was needed for the shape editor list fix to ensure it works both ways #468 by Areloch was merged on Feb 13, 2021
324. Fixes the constructor path compare logic in the shape editor so the lists can populate correctly. #467 by Areloch was merged on Feb 12, 2021
325. set prefab and makemesh origins to the biggest model #466 by Azaezel was merged on Feb 15, 2021 1
326. ribbon particle resource port #464 by Azaezel was merged on Feb 15, 2021
327. terrain brush dragging cleanups #463 by Azaezel was merged on Jan 28, 2021
328. Re-fixes terrain edit dragging without breaking paint actions #462 by Areloch was merged on Jan 27, 2021
329. Implements shape preview caching for shape assets #461 by Areloch was merged on Jan 27, 2021
330. re-fix file exclusivity, readd callonmodules variable extension #460 by Azaezel was merged on Jan 27, 2021
331. update openal-soft #459 by Azaezel was merged on Jan 27, 2021
332. Integrates object creator logic into the AB #458 by Areloch was merged on Jan 24, 2021
333. augment datablock file handling to include references with no suffixes #457 by Azaezel was merged on Jan 24, 2021 1
334. Fix for transparency in splash images #456 by zfbx was merged on Jan 27, 2021 1
335. version is not provided by current vendor api making it pointless to … #455 by zfbx was merged on Jan 27, 2021 1
336. Added fix for #365 from PR #367 - buffer overrun bug #454 by zfbx was merged on Jan 21, 2021
337. Corrects missed asset script file references in asset definitions when swapping to the tscript extension #453 by Areloch was merged on Jan 20, 2021
338. Add Discord badge to README #452 by lukaspj was merged on Jan 20, 2021
339. Fixes some minor errors on MacOS regarding compiling in clang #451 by Areloch was merged on Jan 14, 2021
340. provides a general Playgui\_onWake callback for modules #450 by Azaezel was merged on Feb 15, 2021 1
341.    Loading from zipped game directories. #449 by OTHGMars was merged on Jul 17, 2021 1

        general spawnspheres #448 by Azaezel was merged on Apr 22, 2021 1
342. Cmake allow non-source project directory #447 by Jozor was merged on Jan 10, 2021
343. add parameter handling to callonmodule callbacks. #446 by Azaezel was merged on Jan 9, 2021
344. revert #401 as while it does surpress hieght painting touching the ce… #443 by Azaezel was merged on Jan 5, 2021
345. Removed old fixed function code from GFX. #442 by rextimmy was merged on Jan 5, 2021 3
346. D3d11 texture lock #441 by rextimmy was merged on Jan 5, 2021
347. Improve terrain rendering, handle bug with no detail #438 by lukaspj was merged on Jan 4, 2021
348.
349.    ssetifies MeshRoad, Decal Road, and the material slot of GroundCover #436 by Areloch was merged on Jan 5, 2021

        Adjusts handling of C++ asset types #434 by Areloch was merged on Jan 2, 2021
350. moar asset errorhandling #433 by Azaezel was merged on Jan 2, 2021
351. sdl usage standards proposal 3 #432 by Azaezel was merged on Jan 2, 2021
352. mac fixes #430 by Azaezel was merged on Dec 31, 2020 1
353. High resolution timer fixes #429 by JeffProgrammer was merged on Dec 30, 2020
354. Consolidates and standardizes terrain creation between the editor, asset browser and creator panel #428 by Areloch was merged on Dec 29, 2020
355. membervar compile fix #426 by Azaezel was merged on Dec 28, 2020
356. Initial pass at implementing MaterialAsset macromagic utility functions #425 by Areloch was merged on Dec 29, 2020
357. Height based terrain texture blending #424 by lukaspj was merged on Jan 4, 2021 3 tasks done
358. OpenGL: Access viewtangent "DX" style for gbNormal in terrain textures #421 by lukaspj was merged on Dec 26, 2020 1
359. update sdl2 to release 2.0.14 #418 by Azaezel was merged on Dec 28, 2020
360. corrected and implemented a usage of shapeasset macros #417 by Azaezel was merged on Dec 28, 2020
361. Converts GroundPlane to utilize assets #415 by Areloch was merged on Dec 19, 2020
362. Misc various improvements for noted issues with the Asset Importer #414 by Areloch was merged on Dec 19, 2020
363. add validation flagging for server objects #413 by Azaezel was merged on Dec 28, 2020
364. Fixes a few bugs/issues on Linux #412 by Areloch was merged on Dec 15, 2020
365. asset pipe cleanups #409 by Azaezel was merged on Dec 19, 2020
366. Fixes for AA toggle and GFX Device reporting for options menu #408 by Areloch was merged on Dec 14, 2020
367. Wraps material animation floats to sane values. #407 by chaigler was merged on Dec 14, 2020
368. Parametrize script extension, default to 'tscript' enhancement #406 by lukaspj was merged on Jan 20, 2021 4
369. Correct bump map in waterObject.cpp being in sRGB space #403 by GoldenThumbs was merged on Dec 11, 2020
370. Fixing bug Terrain Editor bug #91 #401 by NoboKani was merged on Dec 8, 2020 1
371. Fixes logic that checks if a postFX was enabled so the PostFX Editor works properly #400 by Areloch was merged on Dec 7, 2020
372. Misc Editor and editor GUI fixups/improvements #399 by Areloch was merged on Dec 7, 2020
373. mMipCount was never being filled out. just use mPrefilterArray->getMi… #398 by Azaezel was merged on Dec 5, 2020
374. Removes unneeded redundant asserts when the functions already have range sanity checks #397 by Areloch was merged on Dec 4, 2020
375. Adds handling so the pause menu has a button to exit the editor as a quick shortcut #396 by Areloch was merged on Dec 3, 2020
376. WIP of marking active scene in the scenetree #395 by Areloch was merged on Dec 19, 2020
377. Fixes Datablock and Prefab DragnDrop behavior with the AB #394 by Areloch was merged on Dec 3, 2020
378. Adds ability to delete a module #393 by Areloch was merged on Dec 3, 2020
379. Cleanup of some log errors and spam with assets #392 by Areloch was merged on Dec 3, 2020
380. Better handling for finding modules by file path. Mainly used in asset importer #391 by Areloch was merged on Dec 3, 2020
381. variation on #387 that also introduces errorcodes #390 by Azaezel was merged on Dec 8, 2020
382. hooks up shapebase children breadcrumb #388 by Azaezel was merged on Dec 3, 2020
383. adress #385 #386 by Azaezel was merged on Nov 29, 2020
384. get shapeassetID read. TODO: find further flaws and unrem the filter #383 by Azaezel was merged on Nov 27, 2020
385. Pause Menu toggle fix #381 by Areloch was merged on Nov 21, 2020
386. light review (hdr and metalness vs direct lighting) #379 by Azaezel was merged on Nov 16, 2020
387. shader preprocessor fixes #378 by Azaezel was merged on Nov 11, 2020
388. mac compile fixes #377 by Azaezel was merged on Nov 7, 2020
389. be sure to executte defaults prior to clientprefs #376 by Azaezel was merged on Nov 11, 2020
390. Adds handling to the path manager so it can deal with both looping and non-looping paths #375 by Areloch was merged on Dec 21, 2020 5
391. Misc fixes to ensure that the default postFX save, load and editing process is valid #374 by Areloch was merged on Nov 1, 2020
392. get gl side HDR compiling, attempt clamp to keep bloom in range #373 by Azaezel was merged on Nov 3, 2020
393. Misc. probe bake/load fixups #372 by Areloch was merged on Oct 29, 2020
394. Adds a sanity check so asset names cannot start with a number #371 by Areloch was merged on Oct 25, 2020
395. Misc. BaseGame UI fixes #370 by Areloch was merged on Oct 28, 2020
396. Added date/timestamp option to console log #369 by zfbx was merged on Oct 24, 2020 2
397. fix #365 #367 by Azaezel was merged on Oct 21, 2020
398. Overhauls the handling of probes to utilize an active probe list #364 by Areloch was merged on Oct 19, 2020
399. Improves default suffix handling for asset importer on image assets under a material asset #363 by Areloch was merged on Oct 17, 2020
400. Basic prototyping module initial upload #362 by Areloch was merged on Oct 16, 2020
401. Updates some level asset functions and script handling #361 by Areloch was merged on Oct 17, 2020
402. clip ./ when doing pattern matching #360 by Azaezel was merged on Oct 12, 2020
403. Move slider to core and add opacity slider to console gui in BaseGame #359 by zfbx was merged on Oct 11, 2020
404. Updates macromagic to properly set up for init'ing when image assets are set in material and terrain materials #357 by Areloch was merged on Oct 17, 2020
405. sceneobject mountchain enable/disable collision aug #356 by Azaezel was merged on Oct 11, 2020
406. fix gl compilation #355 by Azaezel was merged on Oct 9, 2020
407. fix for empty r channel creation of composites crashing out #354 by Azaezel was merged on Oct 8, 2020
408. fix GCC compile #353 by Azaezel was merged on Oct 8, 2020
409. followup #352 by Azaezel was merged on Oct 5, 2020
410. replicate exec signatures for queueExec #351 by Azaezel was merged on Oct 5, 2020
411. EngineExportScope(){} _can't_ be initialized by default, aparantly #350 by Azaezel was merged on Oct 5, 2020
412. Fix paths in caustics shader bug Script #349 by lukaspj was merged on Oct 4, 2020
413. Use string.compare instead of String::compare when comparing strings bug C++ #348 by lukaspj was merged on Oct 3, 2020
414. fix terrain compilation #347 by Azaezel was merged on Oct 3, 2020
415. gl needs OUT\_col filled out to return anything #346 by Azaezel was merged on Oct 3, 2020
416. pathshape gravity suppression injection #345 by Azaezel was merged on Oct 3, 2020
417. Profile editor for the meshRoad object C++ enhancement Script #343 by lukaspj was merged on Oct 3, 2020 3
418. Replace uses of dStrCmp with new String::compare C++ QoL Enhancement #342 by lukaspj was merged on Oct 3, 2020 2
419. breakShape() - remove parts created with invalid object box . C++ QoL Enhancement #341 by lukaspj was merged on Oct 3, 2020 1
420. ForceFOV is not working on GuiTSControl. bug C++ help wanted question #339 by lukaspj was merged on Oct 28, 2020 3
421. extra option for terrain block to disable the update of the basetexture #337 by lukaspj was merged on Oct 3, 2020
422. Remove old and not needed torqueconfig files #336 by lukaspj was merged on Oct 3, 2020
423. SFX Player fixes #74 #334 by lukaspj was merged on Oct 3, 2020
424. Add NavMesh to World Editor #332 by lukaspj was merged on Oct 3, 2020
425. Temporary fix for the geometry feed in spotlights #329 by lukaspj was merged on Oct 3, 2020
426. Implementation of guiRenderTargetVizCtrl #328 by lukaspj was merged on Oct 3, 2020
427. Fix global variables not being able to be used inside of a foreach$ loop bug C++ #327 by lukaspj was merged on Oct 3, 2020 1
428. Feature/improve cinterface C++ help wanted QoL Enhancement #326 by lukaspj was merged on Nov 16, 2020 9
429. code review: #324 by Azaezel was merged on Oct 3, 2020
430. shift pbrconfig to ORM in keeping with the prepoderance of industry standards #323 by Azaezel was merged on Oct 3, 2020 1
431. minor cleanups: #321 by Azaezel was merged on Sep 27, 2020
432. memleak fix #320 by Azaezel was merged on Sep 25, 2020
433. Implements new shape fadeout and lighting fade/max lights/shadows pref options into the options menu #319 by Areloch was merged on Sep 26, 2020
434. Implements hook-look-up logic for shape assets to ShapeBaseData including autoimport handling #317 by Areloch was merged on Nov 27, 2020 1
435. Updated version of OTHGMars' updated window and resolution options modes. #316 by Areloch was merged on Sep 20, 2020
436. Various misc. tweaks and fixes targeting memleaks and crashes #315 by Areloch was merged on Sep 20, 2020
437. Fixes the hook-ins so when a shape asset is changed, tsstatics now are correctly triggered for a reload #314 by Areloch was merged on Sep 14, 2020
438. fix chooseleveldlg #313 by Azaezel was merged on Sep 12, 2020
439. Reorgs the layout and editing of PostFX with some supplemental level save/load changes #312 by Areloch was merged on Sep 11, 2020
440. Re-implements the dynamic cubemap mode option for reflection probes #311 by Areloch was merged on Sep 11, 2020
441. Misc asset browser/asset creation fixes #310 by Areloch was merged on Sep 10, 2020
442. new trigger features: triponce, tripcondition, and trippedby. #309 by Azaezel was merged on Oct 3, 2020
443. Misc fixes for Asset Browser navigation, scene asset utilization and editor settings #308 by Areloch was merged on Sep 10, 2020
444. Misc editor settings fixes and additions #307 by Areloch was merged on Aug 30, 2020
445. Misc Fixes for level saving and selecting asset paths #306 by Areloch was merged on Aug 30, 2020
446. Fixes logic when opening shapeEditor with a TSStatic selected #305 by Areloch was merged on Aug 28, 2020
447. Misc. Fixes and cleanup for lights #304 by Areloch was merged on Aug 28, 2020
448. Miscellaneous small issue fixes #303 by Areloch was merged on Aug 26, 2020
449. Integrates sound and shapeAnimation assets into the importer #302 by Areloch was merged on Aug 25, 2020
450. Material Asset import lookups and initial re-integration of sis files. #301 by Areloch was merged on Aug 24, 2020
451. Adds sorting to the settings class so when it saves out to file #300 by Areloch was merged on Aug 23, 2020
452. Level Asset Dependency handling and various level fixes #299 by Areloch was merged on Aug 21, 2020
453. fix for trigger::testobjects vector population #298 by Azaezel was merged on Aug 21, 2020
454. Adds a notes object that only displays in the editor #297 by Areloch was merged on Aug 17, 2020
455.
456.    ix compilation with shipping flag #295 by Azaezel was merged on Oct 3, 2020

        Adds a pref to dictate if local lights can cast shadows or not. #294 by Areloch was merged on Aug 16, 2020
457. Expands AB tooltips with file info #293 by Areloch was merged on Aug 16, 2020
458. Adds image variances for the menuGrid image #292 by Areloch was merged on Aug 16, 2020
459. Adds in the missing materials used for the Convex Proxies for triggers, zones, etc. #291 by Areloch was merged on Aug 16, 2020
460. Standardizes the tooltip profile colors to match the rest of the themeing stuff #290 by Areloch was merged on Aug 16, 2020
461. Adds logical check to skip animated statics when baking selection to mesh. #289 by Areloch was merged on Aug 16, 2020
462. Misc. Image Asset improvements #288 by Areloch was merged on Aug 13, 2020
463. More misc. fixes #287 by Areloch was merged on Aug 12, 2020
464. Updates SDL to 2.0.12 #286 by Areloch was merged on Aug 12, 2020
465. Followup commit to switch to engine conventions #285 by Pecon was merged on Aug 11, 2020
466. Basic Platform::openWebBrowser implementation for linux #284 by Pecon was merged on Aug 11, 2020
467. mouse display for keybinds #283 by Azaezel was merged on Jan 10, 2021
468. Even more misc asset fixes #280 by Areloch was merged on Aug 9, 2020
469. More various Asset Browser and importer fixes #279 by Areloch was merged on Aug 8, 2020
470. from @OTHGMars: AssetImporter type and path for material look-ups. #277 by Azaezel was merged on Aug 8, 2020
471. Queue exec order #276 by OTHGMars was merged on Aug 7, 2020
472. Fixes the backend logic for setting/creating 3DTextures in D3D11 #275 by Areloch was merged on Aug 12, 2020
473. Various fixes for both asset importing and some workflowy bits relating to assets stuffs #274 by Areloch was merged on Aug 7, 2020
474. Fix gamepad binds on non-windows. #273 by OTHGMars was merged on Aug 5, 2020
475. inputTest Module Initialization #272 by OTHGMars was merged on Aug 5, 2020
476. Alpha40 shader gen cleanups #271 by Azaezel was merged on Aug 4, 2020
477. Some cleanup and adjusting of local light fields and default settings. #270 by Areloch was merged on Aug 3, 2020
478. Adds additional light preferences #269 by Areloch was merged on Aug 3, 2020
479. Adds some console preference variables for object fade overriding on TSStatics #268 by Areloch was merged on Aug 3, 2020
480. ribbon shader variable order fix from @steve\_yorkshire #267 by Azaezel was merged on Aug 3, 2020
481. Adds a default value to the lodType of the asset importer #266 by Areloch was merged on Jul 30, 2020
482. proper variation on the datablock file list erasure #265 by Azaezel was merged on Jul 30, 2020
483. crashfix: const U32 numVerts = curEntry.vertBuffer-> is invalid for vectorlights #264 by Azaezel was merged on Jul 30, 2020
484. crashfix: decal report when missing the DB entry was malformed #263 by Azaezel was merged on Jul 30, 2020
485. fix reverb out of bound initializations #262 by Azaezel was merged on Jul 30, 2020
486. groundframe generation cleanup work #261 by Azaezel was merged on Oct 3, 2020
487. Moves the BaseUI module to utilize the queuedExec function #260 by Areloch was merged on Jul 26, 2020
488. Captures secondary window close events #259 by Areloch was merged on Jul 26, 2020 1
489. Updates the BaseGame UI theme #258 by Areloch was merged on Jul 26, 2020
490. Fix GCC9 complaints #257 by Bloodknight was merged on Jul 26, 2020
491. Fix GCC9 complaints #256 by Bloodknight was merged on Jul 22, 2020
492. Fixes issue with Drag-and-drop asset import action #255 by Areloch was merged on Jul 20, 2020
493. Moves the delta-based rounding function Verve used up into the engine #254 by Areloch was merged on Jul 18, 2020
494. from jeff and tim: review of lighting impacts #252 by Azaezel was merged on Jul 20, 2020
495. Added slider to consoleDlg for bg alpha (Needs refinement) #251 by zfbx was merged on Jul 27, 2020 3
496. from @rextimmy new isbackground shader feature. #250 by Azaezel was merged on Jul 14, 2020
497. Adds additional functions for inserting inspectorGroups #249 by Areloch was merged on Jul 14, 2020
498. cleanup singlechannel glowmask leftovers (we use a full rgb map now) #248 by Azaezel was merged on Jul 14, 2020
499. Various improvements, fixes and enhancements to Asset editor stuffs #247 by Areloch was merged on Jul 12, 2020
500. Various improvements, fixes and expansions for Asset Importing #246 by Areloch was merged on Jul 12, 2020
501. Minor additions to popup menus #245 by Areloch was merged on Jul 12, 2020
502. Adds logic to guiTextEditCtrl to have placeholder text when the control is empty. #244 by Areloch was merged on Jul 12, 2020
503. from @practicing01: trigger mounting #243 by Azaezel was merged on Jul 10, 2020
504. from practicing: aiplayer onstuck correction #242 by Azaezel was merged on Jul 10, 2020
505. comparison flaw in spotlight animation check. #241 by Azaezel was merged on Jul 8, 2020
506. fixed cpu detection on 64bit windows #240 by JeffProgrammer was merged on Jul 7, 2020 1
507. \#include "console/typeValidators.h" #239 by Azaezel was merged on Jul 5, 2020
508. fix cubemap capture for gl #238 by Azaezel was merged on Jul 5, 2020
509. safety check #237 by Azaezel was merged on Oct 9, 2020 1
510. client cleanups #236 by Azaezel was merged on Jul 26, 2020 1
511. Fix crash due to GuiEditCanvas::save() #235 by chaigler was merged on Jul 2, 2020 1
512. Implements missing \_captureBackBuffer method for GL gfx layer. #234 by chaigler was merged on Jul 2, 2020
513. Fix for crash in \_onZoningChanged methods when called by hidden objects. #233 by chaigler was merged on Jul 2, 2020
514. Reworks the terrain loader code to work with the assets. #229 by Areloch was merged on Jul 10, 2020
515. adress #116 and #179 (shaderside) #227 by Azaezel was merged on Jun 26, 2020 5
516. adress #225 #226 by Azaezel was merged on Jun 26, 2020
517. Removal of old font files from basegame template #223 by Bloodknight was merged on Jun 20, 2020
518. adress #221 crash surpress macromap #222 by Azaezel was merged on Jun 20, 2020
519. adress #16 - don't need to swizzle vert colors #218 by Azaezel was merged on Jun 19, 2020 2
520. groundcover requested augs #216 by Azaezel was merged on Jun 19, 2020
521. fixes for trigger onenter/onleave #215 by Azaezel was merged on Jun 26, 2020
522. adds an animspeed and animoffset to tsstatic instances #214 by Azaezel was merged on Jun 19, 2020
523. typofix in opengl terrain shadergen #213 by Azaezel was merged on Jun 19, 2020 1
524. export rounds LODs to the nearest power of 2 #212 by Azaezel was merged on Oct 3, 2020 2
525. Updated links, added info from torque3d.org #211 by zfbx was merged on Jun 20, 2020
526. adress #162 based on work by Chad Hall #210 by Azaezel was merged on Jun 20, 2020
527. adress #203 #209 by Azaezel was merged on Jun 20, 2020
528. Linux Slash compatability #208 by Bloodknight was merged on Jun 12, 2020
529. adress #205 #206 by Azaezel was merged on Jun 10, 2020 2
530. D3D-only compile fix DirectX #204 by Areloch was merged on Jun 12, 2020 1
531. implement copyResource, fix copyToBmp #202 by Azaezel was merged on Jun 20, 2020
532. Remove trailing whitespaces from simObject.cpp and fix pointer format #2382 by stsrc was merged on Apr 18, 2020 1
533. fixed texture call which reported as a missing image #2378 by zfbx was merged on Apr 18, 2020
534. Updates SDL to 2.0.10 #2369 by Areloch was merged on Sep 19, 2019
535. OpenAL efx fixes for macOS/Linux #2362 by rextimmy was merged on Aug 4, 2019 1
536. Modification of #2145 Improvement #2354 by Areloch was merged on Apr 20, 2019
537. adress #2344 #2352 by Azaezel was merged on Apr 6, 2019
538. Full template Scene conversion Bugfix Improvement #2345 by Areloch was merged on Apr 20, 2019
539. fix(es) for volumetric fog when dealing with dedicated servers. #2342 by Azaezel was merged on May 4, 2019
540. Makes the popups correctly operate anywhere in the space of the canvas Bugfix #2340 by Areloch was merged on Mar 31, 2019
541. Adds logic to temporarily disable collisions of mounted objects on Players Bugfix #2339 by Areloch was merged on Mar 31, 2019
542. Fixes some outstanding menubar problems. Bugfix #2338 by Areloch was merged on Mar 31, 2019
543. Fixes artifacts in Cloud Layer. Bugfix #2336 by wcbx was merged on Mar 31, 2019 1
544. rewrite of NavMeshUpdateAll/NavMeshUpdateAroundObject Bugfix Improvement #2335 by Azaezel was merged on Mar 31, 2019
545. Cleanup and minor tweaks to the core dir structure. Improvement #2334 by Areloch was merged on Mar 31, 2019
546. Fixes a crash that occurs on linux headless servers Bugfix #2332 by Bloodknight was merged on Mar 30, 2019
547. Set contrsaints for Player Z rotation Bugfix #2331 by Bloodknight was merged on Mar 31, 2019
548. Adds a filter for materials to never import when importing a shape New feature #2328 by Areloch was merged on May 4, 2019
549. Adds ability to skip loading of cached dts in enumColladaForImport New feature #2327 by Areloch was merged on Mar 30, 2019
550. Adds visualizers for various types of colorblindness Improvement New feature #2326 by Areloch was merged on Mar 30, 2019
551. Moves the path return from fileDialog through the returnBuffer Bugfix #2325 by Areloch was merged on Mar 30, 2019
552. Tweaks some object handling of guiTreeViewObj Improvement #2324 by Areloch was merged on May 4, 2019
553. Sanity check for calling getFieldValue Bugfix #2323 by Areloch was merged on Mar 30, 2019 2
554. Adds gui3DProjectionCtrl New feature #2322 by Areloch was merged on Mar 31, 2019
555. Updates TextEdit value when focus is lost. Improvement #2321 by Areloch was merged on Mar 30, 2019
556. Allows special inspectorFields to override their height Improvement #2320 by Areloch was merged on Mar 30, 2019
557. Initial implementation of the Scene object Improvement New feature #2319 by Areloch was merged on Mar 30, 2019 1
558. Tweaks to the Asset/Module info echo behavior to spam the console less. Improvement #2318 by Areloch was merged on Mar 30, 2019
559. Adds ability to set the split point of a guiSplitContainer #2317 by Areloch was merged on Mar 30, 2019
560. corrects a parity flaw between wireframe and non wireframe box display #2315 by Azaezel was merged on Mar 30, 2019
561. Switches to absolute position for mouse tracking. #2313 by OTHGMars was merged on Mar 31, 2019 1
562. Snap to terrain Z offset. #2311 by Bloodknight was merged on May 4, 2019
563. Vert color correction #2310 by Azaezel was merged on Mar 30, 2019
564. Remove redundant variables and clean up C4312 and C4305 warnings #2309 by suncaller was merged on Feb 20, 2019
565. nextfreemask does nothing for proximity mines as there are no subclas… #2307 by Azaezel was merged on Feb 21, 2019
566. corrects a copy-corruption flaw with GuiSwatchButtonCtrl::onMouseDragged #2305 by Azaezel was merged on Feb 20, 2019 1
567. Sdl joystick2 #2300 by OTHGMars was merged on Jan 21, 2019 1
568. Sqlite Console refactor, #2299 by Bloodknight was merged on Feb 20, 2019 1
569. Travis Compile #2298 by jmdejong was merged on Feb 1, 2019 1
570. Fix SDL Input::getKeyCode on software keyboard layouts #2296 by CouleeApps was merged on Jan 21, 2019 1
571. Add a .editorconfig file #2295 by Bloodknight was merged on Feb 20, 2019 1
572. Adds features to GuiInputCtrl #2294 by OTHGMars was merged on Jan 21, 2019 1
573. afxRenderHighlightMgr: account for hardware skinning #2292 by Azaezel was merged on Jan 21, 2019 1
574. corrects compilation errors on non-mac unix derivatives #2288 by Azaezel was merged on Jan 6, 2019 2
575. corrects compilation errors on mac #2287 by Azaezel was merged on Jan 9, 2019
576. Nfd update #2286 by Azaezel was merged on Feb 1, 2019 2
577. corrects a pair of conversions. one object oriented, one not. #2285 by Azaezel was merged on Dec 13, 2018
578. Fills in monitor functions in PlatformWindowManagerSDL #2284 by OTHGMars was merged on Dec 9, 2018
579. Adds handlers for sdl focus events. Final review Improvement #2283 by OTHGMars was merged on Dec 9, 2018 1
580. Fixes CanvasSizeChangeSignal and Canvas::onResize() under SDL Final review Improvement #2282 by OTHGMars was merged on Jan 6, 2019
581. OpenALEffects New feature #2281 by marauder2k7 was merged on Mar 30, 2019&#x20;
582. Approved Improved BitStream writeQuat/readQuat methods. Improvement #2277 by OTHGMars was merged on Oct 11, 2018
583. filter out pixel shader normalmap calcs when not in deferred mode. Bugfix Final review #2276 by Azaezel was merged on Dec 2, 2018
584. Adds Clamp to QuatF::dot() Bugfix #2275 by OTHGMars was merged on Oct 11, 2018
585. Core module-ification Improvement #2272 by Areloch was merged on Oct 12, 2018
586. micro patch to the nativefiledialogues library to mirror file type name #2270 by Azaezel was merged on Oct 12, 2018
587. alternative to #2268 : remove secondary profiling #2269 by Azaezel was merged on Sep 2, 2018
588. Network Code Fixes Improvement #2267 by calvinbalke13 was merged on Oct 12, 2018
589. Resolves #1721 - ScatterSky zOffset Bugfix #2266 by chaigler was merged on Jul 9, 2018
590. Fix for bug in GFXVideoMode::parseFromString() Bugfix #2265 by OTHGMars was merged on Jul 9, 2018
591. Resolves #740 - Remove redundant code in \_GFXInitGetInitialRes() Bugfix #2264 by chaigler was merged on Jul 9, 2018
592. member var conversion error that oddly didn't crop up till mac testing. Bugfix #2262 by Azaezel was merged on Jul 9, 2018
593. Changes TSStatic::castRayRendered to use passed texcoord argument. Bugfix #2259 by OTHGMars was merged on Sep 5, 2018
594. Fixes the front/back ortho views in the editors Bugfix #2258 by Areloch was merged on Dec 9, 2018
595. Particles should go downwind (while windCoefficient >0) Bugfix #2255 by pacomont was merged on Jul 12, 2018
596. SDL 2.0.8 Bugfix Improvement #2254 by rextimmy was merged on May 30, 2018
597. It's almost imposible to change direction of wind. Reseting mCurrentT… Bugfix #2252 by pacomont was merged on Jul 12, 2018
598. openal-soft updates Bugfix Improvement #2251 by rextimmy was merged on May 19, 2018
599. Fixes various incorrect popup menu behaviors. Bugfix Improvement #2250 by Areloch was merged on Sep 5, 2018
600. Updates PlatformCursorController to use full set of SDL cursors. Improvement #2249 by OTHGMars was merged on Sep 5, 2018
601. New cinterface #2248 by lukaspj was merged on Dec 9, 2018
602. Corrects a problem with the D3D11 texture lock/unlock mechanism #2247 by rextimmy was merged on Jul 12, 2018
603. Update CInterface #2246 by lukaspj was merged on Dec 9, 2018
604. Clean-up uses of ConsoleFunction etc. #2245 by lukaspj was merged on Dec 9, 2018
605. Higher resolution app icon #2243 by CouleeApps was merged on May 2, 2018
606. Interpreter Hotfix: Check for NULL on the thisObject before using it. #2242 by JeffProgrammer was merged on Apr 30, 2018
