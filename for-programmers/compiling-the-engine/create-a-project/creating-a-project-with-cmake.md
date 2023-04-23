# Creating a Project With CMake

To create a new project using Torque3D, you can use CMake's GUI application to configure and generate a project file. In this article, we will guide you through the process of setting up and generating a new project in Torque3D using CMake.

### Open CMake GUI

After installing CMake and cloning the Torque3D repository, you can open the CMake GUI application. This application allows you to configure and generate a project file for Torque3D.

### Set the Source and Build Directories

In the CMake GUI, you need to set the source and build directories. The source directory is the location of the Torque3D repository on your computer, and the build directory is where CMake will generate the project files. To set the directories, click the "Browse Source" and "Browse Build" buttons and select the appropriate folders.

<img src="../../../.gitbook/assets/image (4).png" alt="" data-size="original">

### Configure the Project

Once you have set the source and build directories, you can start the configuration process for the project by clicking the "Generate" button. This will bring up a dialog box where you can select the options you want to use for your project

![](<../../../.gitbook/assets/image (7).png>)

In most cases, the only thing you'll want to worry about at this step is making sure the correct generator is used. This is the program used to ultimately build the project, such as make, Visual Studio, XCode, etc.

Once you've got it selected, click "Finish".

It will do some work, and then throw an "error"

![](<../../../.gitbook/assets/image (35).png>)

Not to worry! All this means is you need to fill in the TORQUE\_APP\_NAME field before it can continue.

This will be your project name and will set some internal stuff in the engine, as well as define the application/executable name.

Once you've filled in the name, click "Generate" again and this time it'll run through the whole setup process. Once finished, you should see a lot of options listed in that center window area.

In this configuration box, you can select the build type (Debug or Release), or other options such as whether to enable physics or audio. You can also specify the location of any third-party libraries that you want to use with your project.

While the default configuration will work perfectly out of the box, some common optional settings that may be important ones for your project would be:

* TORQUE\_PHYSX: If on, will enable the use of nVidia's PhysX physics library
* TORQUE\_BULLET: If on, will enable the use of the Bullet physics library
* TORQUE\_NET\_CURL: An advanced setting, if enabled, will compile the engine with libCurl support, allowing your game to access web content.&#x20;
* TORQUE\_D3D11: If enabled, will have the engine support the DirectX 3D 11 rendering API (Only available on Windows)
* TORQUE\_OPENGL: If enabled, will have the engine support the OpenGL rendering API
* TORQUE\_SQLITE: If on, enables support for SQLite databases

When you're happy with the configuration, click the "Generate" button to generate the project files.

![](<../../../.gitbook/assets/image (33).png>)

### Build the Project

Once the project files have been generated, you can build the project by opening the build directory in your preferred development environment and compiling the code.&#x20;

![](<../../../.gitbook/assets/image (9).png>)

Depending on availability, you may be able to simply click the "Open Project" button and have the OS open the project file in your preferred IDE automatically.

You can quickly jump to your OS of choice to follow the compilation instructions here:

{% content-ref url="../compiling/compiling-in-windows.md" %}
[compiling-in-windows.md](../compiling/compiling-in-windows.md)
{% endcontent-ref %}

{% content-ref url="../compiling/compiling-in-macos.md" %}
[compiling-in-macos.md](../compiling/compiling-in-macos.md)
{% endcontent-ref %}

{% content-ref url="../compiling/compiling-in-linux.md" %}
[compiling-in-linux.md](../compiling/compiling-in-linux.md)
{% endcontent-ref %}
