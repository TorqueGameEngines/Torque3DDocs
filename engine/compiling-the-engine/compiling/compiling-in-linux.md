# Compiling in Linux

## Using a virtual machine <a href="#toc0" id="toc0"></a>

If you don't have access to a Linux machine, or you prefer not to install libraries and software in your current Linux machine, building Torque inside a virtual machine is a great way to create binaries that you can redistribute. You can create your own virtual machine environment by following the steps on this page for Linux as usual, or you can use Vagrant to create reproducible VMs that you manage with the command-line. See [the Vagrant tutorial](http://wiki.torque3d.org/coder:compiling-using-vagrant) for more details.

## Prepare Linux for Torque <a href="#toc1" id="toc1"></a>

Prior to compiling Torque 3D under Linux, you will need to make sure you have the appropriate libraries and tools installed. The exact packages will depend on which Linux distribution you are using.

### Ubuntu <a href="#toc2" id="toc2"></a>

Confirmed compile on the following Versions:- 16.04\
Reported issues with Versions:- 16.10

#### Installing with apt-get <a href="#toc3" id="toc3"></a>

Binaries:

```
sudo apt-get install git build-essential nasm xorg-dev 
sudo apt-get install ninja-build gcc-multilib g++-multilib 
sudo apt-get install cmake cmake-qt-gui
```

Libraries:

```
sudo apt-get install libogg-dev libxft-dev libx11-dev libxxf86vm-dev 
sudo apt-get install libopenal-dev libfreetype6-dev libxcursor-dev 
sudo apt-get install libxinerama-dev libxi-dev libxrandr-dev 
sudo apt-get install libxss-dev libglu1-mesa-dev libgtk-3-dev
```

#### Additional Libraries <a href="#toc10" id="toc10"></a>

The file dialogs require GTK3 as well, so you will need to get the package for that if you do not already have it. The recommended command is this:

```
sudo apt-get install build-essential libgtk-3-dev
```

## Using git to download the source <a href="#toc11" id="toc11"></a>

If you followed the above instructions(or your distro already comes with git pre-installed) you can run git via the commandline by doing the following:

1. Make sure you're in the directory you want to clone the engine repository into, such as `"cd /home/gamedev/"`
2. clone the Torque 3D github repository\
   `git clone` [`https://github.com/GarageGames/Torque3D.git`](https://github.com/GarageGames/Torque3D.git) `Torque3D`
3. While usually you're going to just go with the default branch, you can change what branch you're working with via `git checkout <branchname>` with branch name being `Release_4_0`or `development`

## Compiling with CMake <a href="#toc12" id="toc12"></a>

### Generate build files with CMake <a href="#toc13" id="toc13"></a>

You can either use the CMake GUI to generate a new project or use CMake from the command-line. If you want to use the GUI, see the main guide for detailed instructions. Otherwise, continue on with the instructions below.

**Do note:** Many distros have out of date builds of cmake if you get them through the main update. Torque 3D requires at least version 3.1.4 to compile. If your version is older than that, even after updating, you can go to the cmake website and either get a precompiled binary to use, or the code if you wish to compile it yourself, [here.](https://cmake.org/download/)

First, make the directory the build files will live in:

```
mkdir -p /home/Torque3D/My\ Projects/LinuxTest/buildFiles/ubuntu
cd /home/Torque3D/My\ Projects/LinuxTest/buildFiles/ubuntu
```

\
note the \ in My Projects if you are typing by hand;

These directories start empty, but will be filled with template content soon. Now we can run CMake to configure the build we're going to make. The CMake command-line options let you enable various modules and options. We don't need any of them, fortunately, so we'll just specify the app name and build type:

```
cmake ../../../.. -DTORQUE_APP_NAME=LinuxTest -DCMAKE_BUILD_TYPE=Release
```

Take care to specify the same app name as the directory you created in the previous step, or your game will be placed in a different directory! CMake will detect the available compiler and other properties, and generate a Makefile in the current directory. If you'd prefer to use Ninja or one of CMake's other supported targets, you can use, for example,

```
cmake ../../../.. -G Ninja ...
```

The final output should look something like this:

```
-- Generating done
-- Build files have been written to: /torque/My Projects/LinuxTest/buildFiles/ubuntu
```

Don't worry about errors related to CMP0004 - they're caused by changes in behaviour with new versions of CMake and the SDL library, and are harmless. We're finally ready to build!

### Build from the command-line <a href="#toc14" id="toc14"></a>

Still in the same folder, run either make, ninja, or your build tool of preference.

The build may take some time, so go and frolic in the outdoors or something while you wait. When you return, you should see that the final executable was linked, and is now awaiting you in My\ Projects/LinuxTest/game.

### Copy template files <a href="#toc15" id="toc15"></a>

You can run make install to copy the template files from the template you specified into your project's folder.

### Build Using Code::Blocks (with cmakeGui) <a href="#toc16" id="toc16"></a>

[https://www.youtube.com/watch?v=ISbuSTgTQKI](https://www.youtube.com/watch?v=ISbuSTgTQKI)

### Build using Qt Creator <a href="#toc17" id="toc17"></a>

We need to configure qtCreator.

* Open editor
* MenuBar -> Tools -> Options
* Build & Run -> CMAKE
* Click on Prefered Ninja Generator
* Close Options.
* MenuBar -> File -> Open File or Project
* Go to Torque3D root path
* Select CMakeList.txt
* We need to configure project. Select your path for CMAKE cache.

```
/home/userName/Torque3D/My Projects/LinuxTest/buildFiles/CMAKE
```

* Click Configure Project
* After this we get the normal CMAKE error message

```
-- Configuring incomplete, errors occurred!
CMake Error at CMakeLists.txt:6 (message):
  Please set TORQUE_APP_NAME first
```

* We need to start CMAKE GUI to configure
* When finished, click Configuration button
* Return to qtCreator
* MenuBar -> Build -> Run CMake
* After this we have qtCreator configured for build
* If you have some problem, it's very important to delete CMakeLists.txt.user file on Torque3D root path.
* You need to use INSTALL project for copy Template files
* Go to Project view
* On Build Steps, Make: Ninja -> click Details
* You see a list of projects you can add to build
* Add INSTALL project
* Return to Edit view
* MenuBar-> Build -> Build All
* After the first build, is possible you prefer to deactivate Install project to avoid override your files.

**Note:** it has been reported that in Fedora, you may need to change the default 'Make: ninja' command to ninja-build for both 'Build Steps' and 'Clean Steps'.

### Compiling Dedicated/Server with the Project Generator <a href="#toc18" id="toc18"></a>

Torque 3D has a custom makefile generator known as the Project Manager, which is used to generate makefiles in Unix (or Visual Studio solutions in Windows). However, in Linux, the PG can only generate makefiles to build a dedicated server, not a full game client. Nevertheless, if you'd like to do that, simply:

* Change to your project's buildFiles/Make\_Ded directory.
* Enter the make clean command.
* Enter either the make debug or make release command depending on the type of build you wish to make.
* Go to your project's game/ directory.
* To start your game enter the following command (we'll use the name _LinuxTest_ as the example project name):

./LinuxTest -dedicated -mission "levels/Empty Terrain.mis"\
where the argument after the -mission switch is the path to the mission to load.

### Compiling with VSCode

