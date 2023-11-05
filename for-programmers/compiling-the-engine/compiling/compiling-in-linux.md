# Compiling in Linux

## Using a virtual machine <a href="#toc0" id="toc0"></a>

If you don't have access to a Linux machine, or you prefer not to install libraries and software in your current Linux machine, building Torque inside a virtual machine is a great way to create binaries that you can redistribute. You can create your own virtual machine environment by following the steps on this page for Linux as usual, or you can use Vagrant to create reproducible VMs that you manage with the command-line. See [the Vagrant tutorial](http://wiki.torque3d.org/coder:compiling-using-vagrant) for more details.

### Build from the command-line <a href="#toc14" id="toc14"></a>

Still in the same folder, run either make, ninja, or your build tool of preference.

The build may take some time, so go and frolic in the outdoors or something while you wait. When you return, you should see that the final executable was linked, and is now awaiting you in My\ Projects/LinuxTest/game.

### Copy template files <a href="#toc15" id="toc15"></a>

You can run make install to copy the template files from the template you specified into your project's folder.

{% hint style="info" %}
Note, post 4.0.3 the CMake generation stepp will automatically install the template files for you, so you don't need to run the INSTALL project first. You can instead just compile the application project itself.
{% endhint %}

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
* You need to use INSTALL project for copy Template files. Note: post-4.0.3 the CMake generation will install the template files your you, so you can just use the application project itself.
* Go to Project view
* On Build Steps, Make: Ninja -> click Details
* You see a list of projects you can add to build
* Add INSTALL project
* Return to Edit view
* MenuBar-> Build -> Build All
* After the first build, is possible you prefer to deactivate Install project to avoid override your files.

**Note:** it has been reported that in Fedora, you may need to change the default 'Make: ninja' command to ninja-build for both 'Build Steps' and 'Clean Steps'.

### Compiling with VSCode

