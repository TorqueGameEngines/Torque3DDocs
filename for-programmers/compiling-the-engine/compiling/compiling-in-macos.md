# Compiling in MacOS

## Install prerequisites <a href="#toc0" id="toc0"></a>

In order to compile T3D, you'll need to install Xcode, which you can find in the app store.

### The generated files <a href="#toc4" id="toc4"></a>

If you browse to the location you asked CMake to put your binaries, you'll see something like the image below - a few files and directories and an xcode project.



### Compiling <a href="#toc5" id="toc5"></a>

To compile your project, open up the project, set the target project, and then build the project. The first time you build, you should use the install project, which will run scripts to copy the game template files into your game's directory for you, but after that you can just build the project with your app's name.

The engine executable will be generated in the project's game folder (i.e. My Projects/\<project name>/game/\<project name>.exe).
