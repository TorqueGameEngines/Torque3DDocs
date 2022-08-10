# Version 3.10

* [GitHub release](https://github.com/GarageGames/Torque3D/releases/tag/3.10)
* [Release announcement](http://forums.torque3d.org/viewtopic.php?f=15\&t=938)

## Notes <a href="#toc0" id="toc0"></a>

## Pull Requests Merged [source](https://github.com/GarageGames/Torque3D/issues?q=milestone%3A3.10+is%3Aclosed) <a href="#toc1" id="toc1"></a>

More to add

[#1688](https://github.com/GarageGames/Torque3D/pull/1688) Basic OpenVR Support code\
[#1690](https://github.com/GarageGames/Torque3D/pull/1690) fix create datablock for physicsshapes.\
[#1692](https://github.com/GarageGames/Torque3D/pull/1692) CMake support for VS\_STARTUP\_PROJECT\
[#1695](https://github.com/GarageGames/Torque3D/pull/1695) Tidy up unnecessary #define\
[#1705](https://github.com/GarageGames/Torque3D/pull/1705) 3.9 fix: corrects improperly applied specularpower\
[#1706](https://github.com/GarageGames/Torque3D/pull/1706) Tweaks the detail textures for the terrain\
[#1710](https://github.com/GarageGames/Torque3D/pull/1710) adresses #1704: partial reversion to 3.8 specs regarding layer blending.\
[#1711](https://github.com/GarageGames/Torque3D/pull/1711) Hardware Skinning Support\
[#1713](https://github.com/GarageGames/Torque3D/pull/1713) adresses C4189 warnings\
[#1714](https://github.com/GarageGames/Torque3D/pull/1714) addresses C4101 warnings ('identifier' : unreferenced local variable)\
[#1715](https://github.com/GarageGames/Torque3D/pull/1715) Change back "enabled" values to lowercase\
[#1716](https://github.com/GarageGames/Torque3D/pull/1716) changes "Rotation" instead of "rotation" #1702\
[#1717](https://github.com/GarageGames/Torque3D/pull/1717) fixes footsteps missing when no impactSoundId\
[#1718](https://github.com/GarageGames/Torque3D/pull/1718) file name reporting for 'sampler not defined' and rtParams error reports.\
[#1719](https://github.com/GarageGames/Torque3D/pull/1719) dx9 samplernames for fixed function replication shaders\
[#1720](https://github.com/GarageGames/Torque3D/pull/1720) navmesh file load error-fix\
[#1725](https://github.com/GarageGames/Torque3D/pull/1725) Fix to include a needed include for the accumulation volume stuffs\
[#1726](https://github.com/GarageGames/Torque3D/pull/1726) added path @dottools\
[#1730](https://github.com/GarageGames/Torque3D/pull/1730) accutex was left out of the copy constructor for TSRenderState.\
[#1732](https://github.com/GarageGames/Torque3D/pull/1732) vec3 variants for toLinear and toGamma\
[#1743](https://github.com/GarageGames/Torque3D/pull/1743) replace fix #1736 for add physicShape datablock from the editor\
[#1749](https://github.com/GarageGames/Torque3D/pull/1749) adds toLinear and toGamma helper functions for ColorF, uses the former in adjusting lights.\
[#1750](https://github.com/GarageGames/Torque3D/pull/1750) short term LOD correction\
[#1754](https://github.com/GarageGames/Torque3D/pull/1754) Removes the unnecessary include of altbase in nativefiledialogs\
[#1755](https://github.com/GarageGames/Torque3D/pull/1755) Implements the splash screen window to the SDL platform stuff.\
[#1756](https://github.com/GarageGames/Torque3D/pull/1756) Fix load with DTS shapes introduced with HW skinning changes\
[#1761](https://github.com/GarageGames/Torque3D/pull/1761) Intrinsicsfix\
[#1762](https://github.com/GarageGames/Torque3D/pull/1762) lightbuffer (aka brightness and shadow) always comes last as a mul\
[#1763](https://github.com/GarageGames/Torque3D/pull/1763) banding: conforms misbehaving postfx to the hdr buffer format\
[#1764](https://github.com/GarageGames/Torque3D/pull/1764) linearizes fog color\
[#1765](https://github.com/GarageGames/Torque3D/pull/1765) Correctly copy mipmap sub resources for DX11 cubemap.\
[#1766](https://github.com/GarageGames/Torque3D/pull/1766) Replace Epoxy with Glad\
[#1768](https://github.com/GarageGames/Torque3D/pull/1768) Added a missed a preprocessor for when not using openVR.\
[#1769](https://github.com/GarageGames/Torque3D/pull/1769) Fixes the Toggle Children Lock and Toggle Children Hidden options\
[#1770](https://github.com/GarageGames/Torque3D/pull/1770) Makes sure the key modifiers are passed along with mouse actions.\
[#1772](https://github.com/GarageGames/Torque3D/pull/1772) Fix crash when saving NavMesh file without Links\
[#1773](https://github.com/GarageGames/Torque3D/pull/1773) GuiInspector's findByObject method fix.\
[#1774](https://github.com/GarageGames/Torque3D/pull/1774) embeds blendtotal into the low bit for the normal|depth buffer\
[#1777](https://github.com/GarageGames/Torque3D/pull/1777) Update libogg to 1.3.2\
[#1778](https://github.com/GarageGames/Torque3D/pull/1778) Libpng update to 1.6.25 (fixes x64 crashing on exit)\
[#1779](https://github.com/GarageGames/Torque3D/pull/1779) Revert TORQUE\_CPU\_X64 changes to oggTheoraDecoder\
[#1780](https://github.com/GarageGames/Torque3D/pull/1780) .gitignore to exclude cmake generated config\_types for libogg\
[#1782](https://github.com/GarageGames/Torque3D/pull/1782) Fixes AbstractPolyList::addBox(). Complete each face with missing 2nd triangle.\
[#1784](https://github.com/GarageGames/Torque3D/pull/1784) Gui speedometer hud\
[#1785](https://github.com/GarageGames/Torque3D/pull/1785) MacOS platform support\
[#1786](https://github.com/GarageGames/Torque3D/pull/1786) Reduce the amount of blocks of memory DataChunker uses\
[#1787](https://github.com/GarageGames/Torque3D/pull/1787) Fix redundant memcpy in swizzle ToBuffer method\
[#1790](https://github.com/GarageGames/Torque3D/pull/1790) GuitHealthBarHud flip fill\
[#1795](https://github.com/GarageGames/Torque3D/pull/1795) ai: distance needs to be returned as a float.\
[#1796](https://github.com/GarageGames/Torque3D/pull/1796) retooled circular ease methods\
[#1798](https://github.com/GarageGames/Torque3D/pull/1798) clang: format\_token string format correction\
[#1799](https://github.com/GarageGames/Torque3D/pull/1799) clang catch: pragma note. (no longer needed)\
[#1800](https://github.com/GarageGames/Torque3D/pull/1800) clang reports: unclear || + && and &+| mixes\
[#1801](https://github.com/GarageGames/Torque3D/pull/1801) clang: register type modifier deprecated\
[#1802](https://github.com/GarageGames/Torque3D/pull/1802) unused variable cleanup\
[#1803](https://github.com/GarageGames/Torque3D/pull/1803) clang: trailing else\
[#1804](https://github.com/GarageGames/Torque3D/pull/1804) clang: unsigned>0 checks\
[#1805](https://github.com/GarageGames/Torque3D/pull/1805) clang: constructor initialization order\
[#1806](https://github.com/GarageGames/Torque3D/pull/1806) more unused variable cleanups\
[#1807](https://github.com/GarageGames/Torque3D/pull/1807) clang catch: boxBase's getPlanePointIndex method wasn't returning values in all cases.\
[#1808](https://github.com/GarageGames/Torque3D/pull/1808) clang: consistent callbacks\
[#1809](https://github.com/GarageGames/Torque3D/pull/1809) refactor: spacing on function call parameters\
[#1810](https://github.com/GarageGames/Torque3D/pull/1810) Force enums using unsigned values to actually hard type to U32\
[#1811](https://github.com/GarageGames/Torque3D/pull/1811) filters false flags from clang compilation\
[#1812](https://github.com/GarageGames/Torque3D/pull/1812) clang: The unit test suite doesn't play nice with -wundef\
[#1813](https://github.com/GarageGames/Torque3D/pull/1813) clang catch: garbage in line directives\
[#1814](https://github.com/GarageGames/Torque3D/pull/1814) garbage char in string\
[#1816](https://github.com/GarageGames/Torque3D/pull/1816) OpenAL-soft for windows\
[#1817](https://github.com/GarageGames/Torque3D/pull/1817) Preliminary IPV6 Support\
[#1818](https://github.com/GarageGames/Torque3D/pull/1818) Fixes up some erroneous behavior with Simgroup parentage.\
[#1819](https://github.com/GarageGames/Torque3D/pull/1819) Fixes prefabs in root dirs having extra folders in creator.\
[#1820](https://github.com/GarageGames/Torque3D/pull/1820) Updates SDL to 2.0.5\
[#1821](https://github.com/GarageGames/Torque3D/pull/1821) Sanity check for if the GuiPlatformGenericMenuBar class\
[#1822](https://github.com/GarageGames/Torque3D/pull/1822) Corrects the specular handling as per Richard's suggestion in #1783\
[#1824](https://github.com/GarageGames/Torque3D/pull/1824) Hides the light's dynamic refresh rate field in the editor\
[#1828](https://github.com/GarageGames/Torque3D/pull/1828) fix issue #696\
[#1829](https://github.com/GarageGames/Torque3D/pull/1829) Adding depth option to the texture of guiOffscreenCanvas\
[#1830](https://github.com/GarageGames/Torque3D/pull/1830) Fix for NavPath is not updated when navMesh has change.\
[#1831](https://github.com/GarageGames/Torque3D/pull/1831) fix ColladaExporter\
[#1834](https://github.com/GarageGames/Torque3D/pull/1834) Also adds a sanity check in the event a splash image isn't found.\
[#1835](https://github.com/GarageGames/Torque3D/pull/1835) Adds some helpful utility math functions.\
[#1836](https://github.com/GarageGames/Torque3D/pull/1836) motion based updates for shadow caching\
[#1838](https://github.com/GarageGames/Torque3D/pull/1838) re-enable face culling for the terrain\
[#1839](https://github.com/GarageGames/Torque3D/pull/1839) directional coloration for pathnodes,\
[#1840](https://github.com/GarageGames/Torque3D/pull/1840) FIELD\_ComponentInspectors inspector hook up\
[#1843](https://github.com/GarageGames/Torque3D/pull/1843) Update version.h\
[#1846](https://github.com/GarageGames/Torque3D/pull/1846) Fix SDL/Mac report going into the background\
[#1847](https://github.com/GarageGames/Torque3D/pull/1847) factoring in tangentW causes parallax to swap specular highlight directions.\
[#1848](https://github.com/GarageGames/Torque3D/pull/1848) \[workaround] pinches parallax steps so the 0-1 range has minimal artifacting\
[#1850](https://github.com/GarageGames/Torque3D/pull/1850) Change VS to use the default fp:precise\
[#1851](https://github.com/GarageGames/Torque3D/pull/1851) remove dml file\
[#1852](https://github.com/GarageGames/Torque3D/pull/1852) Adds some bake-to-collada functions\
[#1854](https://github.com/GarageGames/Torque3D/pull/1854) fix SDL text events from generating a \~ key when opening the console\
[#1855](https://github.com/GarageGames/Torque3D/pull/1855) Updated recast to 1.5.1\
[#1856](https://github.com/GarageGames/Torque3D/pull/1856) uts bitangent direction determinant back\
[#1858](https://github.com/GarageGames/Torque3D/pull/1858) flips dx11, opengl, and sdl2 on by default now that those are no long…\
[#1859](https://github.com/GarageGames/Torque3D/pull/1859) Multiple canvas support for GL and DX11\
[#1868](https://github.com/GarageGames/Torque3D/pull/1868) GL::Workaround::noCompressedNPoTTextures profile is no longer used\
[#1874](https://github.com/GarageGames/Torque3D/pull/1874) readme update\
[#1876](https://github.com/GarageGames/Torque3D/pull/1876) Fixes Bullet not supporting holes in terrain.\
[#1877](https://github.com/GarageGames/Torque3D/pull/1877) Default port fix\
[#1878](https://github.com/GarageGames/Torque3D/pull/1878) Fixes window icons with SDL\
[#1879](https://github.com/GarageGames/Torque3D/pull/1879) colorPicker/swatch srgb display.\
[#1882](https://github.com/GarageGames/Torque3D/pull/1882) OpenGL vsync fixes.\
[#1883](https://github.com/GarageGames/Torque3D/pull/1883) DX11 updates\
[#1885](https://github.com/GarageGames/Torque3D/pull/1885) update libvorbis 135\
[#1886](https://github.com/GarageGames/Torque3D/pull/1886) looks like getsockname needs a slightly different signature for crossplat support\
[#1887](https://github.com/GarageGames/Torque3D/pull/1887) HDR review: remove from reflections, kill depth check, order of ops\
[#1888](https://github.com/GarageGames/Torque3D/pull/1888) brings empty up to date for core and shader dirs\
[#1889](https://github.com/GarageGames/Torque3D/pull/1889) Bullet 2.85 update\
[#1890](https://github.com/GarageGames/Torque3D/pull/1890) added torque SimView tool\
[#1891](https://github.com/GarageGames/Torque3D/pull/1891) D3D11 shadermodel version fix\
[#1894](https://github.com/GarageGames/Torque3D/pull/1894) enable video recording\
[#1895](https://github.com/GarageGames/Torque3D/pull/1895) Unused preDemoRecord()\
[#1896](https://github.com/GarageGames/Torque3D/pull/1896) PhysicsShapeData examples\
[#1897](https://github.com/GarageGames/Torque3D/pull/1897) Physx3.3 updates\
[#1898](https://github.com/GarageGames/Torque3D/pull/1898) PhysicsShape applyTorque function\
[#1899](https://github.com/GarageGames/Torque3D/pull/1899) Physx 2.8 removal\
[#1901](https://github.com/GarageGames/Torque3D/pull/1901) Physics timing\
[#1903](https://github.com/GarageGames/Torque3D/pull/1903) PhysicsShape applyForce function\
[#1904](https://github.com/GarageGames/Torque3D/pull/1904) Fix net tests\
[#1907](https://github.com/GarageGames/Torque3D/pull/1907) OSX de-deprecation (profiler and macFileIO)\
[#1908](https://github.com/GarageGames/Torque3D/pull/1908) Removed deprecated use of register keyword from the TorqueScript lexer/parser\
[#1915](https://github.com/GarageGames/Torque3D/pull/1915) Fixed semaphore struct to class\
[#1916](https://github.com/GarageGames/Torque3D/pull/1916) SFX Variance Overflow\
[#1919](https://github.com/GarageGames/Torque3D/pull/1919) Fixed StaticShape onUnmount\
[#1920](https://github.com/GarageGames/Torque3D/pull/1920) Variadic console templates\
[#1921](https://github.com/GarageGames/Torque3D/pull/1921) address #1914\
[#1922](https://github.com/GarageGames/Torque3D/pull/1922) Optionally include a CMake configurations file from the project directory\
[#1923](https://github.com/GarageGames/Torque3D/pull/1923) String table empty string\
[#1925](https://github.com/GarageGames/Torque3D/pull/1925) Sdl update fix\
[#1926](https://github.com/GarageGames/Torque3D/pull/1926) Call the correct system rename\
[#1928](https://github.com/GarageGames/Torque3D/pull/1928) Cleanup when deactivating light manager instead of reinitializing\
[#1929](https://github.com/GarageGames/Torque3D/pull/1929) Make RenderPassManager call Parent::InitPersistFields\
[#1930](https://github.com/GarageGames/Torque3D/pull/1930) Texture crash\
[#1931](https://github.com/GarageGames/Torque3D/pull/1931) Fixes some issues with lightning\
[#1932](https://github.com/GarageGames/Torque3D/pull/1932) Cleans up a few cmake options and flags\
[#1933](https://github.com/GarageGames/Torque3D/pull/1933) Fixes editor handling of menubars when opening/closing.\
[#1934](https://github.com/GarageGames/Torque3D/pull/1934) SDL Menubar accelerator fix\
[#1935](https://github.com/GarageGames/Torque3D/pull/1935) Adds a check to the record movie call\
[#1937](https://github.com/GarageGames/Torque3D/pull/1937) fix warningFlashes() of lightning class\
[#1938](https://github.com/GarageGames/Torque3D/pull/1938) added strikeObject lightning feature\
[#1939](https://github.com/GarageGames/Torque3D/pull/1939) Hotfix to re-add the prior static function fix in platformNet\
[#1942](https://github.com/GarageGames/Torque3D/pull/1942) Fixes some issues with forest editor.
