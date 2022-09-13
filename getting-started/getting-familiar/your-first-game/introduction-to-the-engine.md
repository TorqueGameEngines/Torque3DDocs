# Introduction To The Engine

### What is Torque 3D? <a href="#what-is-torque-3d" id="what-is-torque-3d"></a>

Torque is a game engine, it is not based on graphical drag ‘n’ drop elements like Unity thus it is not as easy to get into and understand. There is no ‘make game button’ in Torque; you need to have an understanding of how to code, so if you are an absolute beginner at programming and have never written even a simple program then this might not be the right guide to start with.

### What can Torque do out of the box? <a href="#what-can-torque-do-out-of-the-box" id="what-can-torque-do-out-of-the-box"></a>

Apart from the advanced deferred rendering model and the physics and all the other great stuff Torque can ‘do’. What you are thinking of here is more likely what can you do if you load up the engine and start walking around? Actually, T3D has a lot of gameplay features out of the box. You can try the FPS modules and you will be able to run around, shoot, throw mines etc without making a single change to the engine. There is a lot of FPS features built into the engine as well, including multiplayer support! So if you want to make a FPS you can probably (at first) treat the development as modding a game.

### What do I need to get started with developing for Torque? <a href="#what-do-i-need-to-get-started-with-developing-for-torque" id="what-do-i-need-to-get-started-with-developing-for-torque"></a>

#### Coding <a href="#coding" id="coding"></a>

_(The following steps is only necessary if you are not satisfied with just scripting and at some point want more than that. If you are only here for the scripting, the binary files in the repo will be enough.)_

**Before you** [download the repo](http://github.com/TorqueGameEngines/Torque3D) you should be sure to setup your environment correctly! **First** do you have an IDE (Integrated Development Environment)? No? If you are running Windows, you should go ahead and download [Visual Studio](https://visualstudio.microsoft.com/vs/). **Now**, you need to download the [Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk/) or else you can’t compile the engine. If you plan to use the extended physics plugins instead of the stock solution, you will need to enable Bullet (included in the download) or physX. If using physX, be aware you will need it's [SDK ](http://www.nvidia.com/object/physx\_downloads.html)as well.

#### Scripting <a href="#scripting" id="scripting"></a>

Nothing special is necessary in order to script with Torque3D, if the engine is running you should be good to go. However you might want an IDE for scripting, I suggest taking a look at either [Torsion](https://github.com/TorqueGameEngines/TorsionEditor/releases/tag/v1.1.392) or [IntelliJ Community](https://www.jetbrains.com/idea/download) with the [TorqueScript plugin](https://plugins.jetbrains.com/plugin/17218-torquescript-language-support).

### What is TorqueScript? <a href="#what-is-torquescript" id="what-is-torquescript"></a>

TorqueScript (TS) is a C-like language. It is very basic. There are no ‘types’ in TorqueScript, everything is handled as strings or ints. One of the most interesting things about scripting in TS is that it is event driven. The engine runs the game and sends the necessary callbacks to the script interface which in turn reacts to the events and vice versa.

A good way to think about it is that you'd probably create a `Projectile` class in C++ and from there you'd control it's trajectory, detect collisions, render the mesh etc.\
However, the creation of the projectile and figuring out what to do when it collides is handled quite well by script.
