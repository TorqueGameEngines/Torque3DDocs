# What's the Torque3D Engine?

### What Is Torque 3D?

Torque 3D was created by **GarageGames** to make the development of games easier, faster, and more affordable. It is a professional Software Development Kit ("SDK") that will save you the effort required to build a rendering system, high speed multiplayer networking, real time editors, a scripting system, and much more.

\
As part of Torque 3D, you receive full access to 100% of our engine source code. This means that you can add to, alter, or optimize any component of the engine down to the lowest level C++ rendering calls. That being said, you don't need to be an experienced C++ programmer to use Torque 3D. In fact, **you do not need to know C++ at all.** Using TorqueScript and the collection of tools that are included with Torque 3D, you can build complete games (of many different genres) without ever touching a single line of C++ code.

\
To understand the basics of how the engine is setup and the tools available, a short reference is included below. Further sections in the documentation explain these tools in more depth.

\


### Minimum System Requirements

**OS:** Windows 7, MacOS Catalina, Ubuntu LTS or equivalent\
**Processor:** 1.6 GHz Processor or better\
**Memory:** 3GB RAM\
**Graphics:** DirectX 11+ or  OpenGL 4.3 supported\
**Hard Drive:** 3GB free disk space (less for binary only solutions)\


### The Engine

The engine handles all of the elements of a game that run in real time on your computer. The Torque 3D engine is written entirely in C++ and is fully accessible to you as a developer. This means you have access to the inner workings of the code to customize it for your needs. The end result is that Torque 3D allows developers to add functionality, increase optimization, and learn how everything works. Alternatively, you can build a game from scratch to release without delving into the source code. The choice of how to develop **your** game is up to you.

\
For example, if you wish to add MYSQL database functionality or integrate the Havok SDK to enhance your game, those paths are open to you. Another benefit of source code access is the ability to read through the comments and data structures to gain a better understanding of how the entire system is set up.

\
Do not be intimidated. This documentation will show you how to create games without touching the source code at all. There is no need to start working with the engine's C++ code until you feel comfortable. In the meantime, you can get going with Torque 3D right away!

\


### Project Manager

The first place to start using Torque 3D is the Project manager. This is the main application that downloads Torque3D and launches Torque Projects. The Project Manager is the central hub of T3D game development.

\
The Project Manager allows you to download existing Torque engines from the official repositories, or you can add your own fork or local folder as the engine build.&#x20;

\
One important part of the Project Manager is to Add or download Torque modules, which can be as large as full game templates and as small as a small graphics asset pack.

\
This allows you to create new projects based on Templates and Modules, which may also come in the form of Genre Kits. From inside the Project Manager, you can launch the demos that can be downloaded with the engine. The Project Manager also provides a direct link to access the documentation included with the engine.

\


### TorqueScript

Much of your game play logic, camera controls, and user interface will be written in TorqueScript. It is a powerful and flexible scripting language with syntax similar to C++. The key benefit of TorqueScript is that you do not need to be a code guru or know the nitty-gritty specifics of a particular language like C++. If you are already familiar with basic programming concepts, you will have a head start on building your own game.

\
Another benefit of using TorqueScript, as opposed to editing the engine's underlying C++ source code, is that you do not have to recompile your executable to see changes in your game. You simply create or modify a script, save, and then run the game from the Toolbox.

\
There are several TorqueScript [articles](https://web.archive.org/web/20200216204338/http://docs.garagegames.com/torque-3d/official/content/documentation/Scripting/Overview/Introduction.html) for new developers that will help you learn the syntax, functionality, and how to use the language with the engine and editors.

\


### Editors

Learning to work with Torque 3D editors is a large part of your initial experience. The key is to remember that the editors work in real-time and are **WYSIWYG** (**W**hat **Y**ou **S**ee **I**s **W**hat **Y**ou **G**et). When you use the editors to modify your level, you will see the changes immediately in the game.

\
**World Editor** - The World Editor is a tool that will help you assemble your game levels. With this tool, you will add and position terrain, game objects, models, environmental effects, lighting, and more.

\
**GUI Editor** - GUI stands for **G**raphical **U**ser **I**nterface. Some examples of GUIs include: splash screens, your main menu, options dialogs and in game Heads Up Displays ("HUDs"). With the GUI Editor, you can design and create your menus, player inventory system, health bars, loading screens, and so on.

\


### The Asset Pipeline

You would not have much of a game without models, textures, and other art assets. For Torque 3D, one of the preferred file format for 3D art assets is COLLADA, however Torque use the Open Asset Import Library so other formats such as FBX also work, many other formats have been less tested but many work for simple models quickly and easily.

\
For those of you familiar with previous Torque engines, you can still import DTS (static models) and DSQ (animation data) files for your 3D objects. This includes static shapes, players, buildings, and props. If you already have a library of DTS and DSQs, feel free to use them in Torque 3D. From this point on however we recommend you transition to the new formats for new art assets going forward.

\


### Conclusion

Now that you have read though this article, you are familiar with some of the most important aspects of Torque 3D. As you familiarize yourself with Torque 3D, you may also want to take a look at the various Torque [add-ons](https://web.archive.org/web/20200216204338/http://www.garagegames.com/products/browse) and [community resources ](https://web.archive.org/web/20200216204338/http://www.garagegames.com/community/resources)available on our site.
