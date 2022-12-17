# Compiling in Windows

To compile your project, open up the solution, right-click the INSTALL project, and click 'build'. You only need to do this the first time.

The INSTALL project not only compiles the engine, but also installs the BaseGame template files in your project.

![](../../../.gitbook/assets/install\_compile.png)

The engine executable will be generated in the project's game folder (i.e. My Projects/\<project name>/game/\<project name>.exe).

### Using the command-line <a href="#toc5" id="toc5"></a>

```
cd "C:\Torque3D\My Projects\Game\buildFiles\CMake"

cmake ^
  -G "Visual Studio 17" ^
  -T "v143" ^
  -DTORQUE_APP_NAME="MyGame" ^
  -DTORQUE_SFX_VORBIS=On ^
  -DTORQUE_THEORA=On ^
  -DCMAKE_BUILD_TYPE=Release ^
  C:\Torque3D

msbuild "MyGame.sln" /p:PlatformToolset=v143 /p:Configuration=Release
```

Change "Visual Studio 17" to the appropriate generator for your system and "MyGame" to your projectName
