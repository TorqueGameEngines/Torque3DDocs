# Torque Project Manager

## What is the Torque Project Manager

The Torque Project Manager, or Project Manager, or PM, is a simple utility application built in Torque3D to help you manage your projects.

It does this by letting you manage builds of the engine, optional modules that can be installed in your projects, and the projects themselves. By default, you can point it at any engine builds, modules and projects you have on your computer's harddrive.&#x20;

If you have git installed, it can download and update engine builds and modules from the internet from a curated list, and if you have cmake installed, you can utilize source code builds of the engine to generate new projects instead of needing to only utilize precompiled binaries.

## Downloading the Project Manager

Naturally, the first step in working with Torque and the Project Manager is to download the PM. Fortunately it's easy to get. You can acquire a copy from the releases on the github repository for your respective platform here:

Once it's been downloaded, you can place it wherever you feel most comfortable on your machine. We would generally recommend having a sort of "gamedev" folder for organizing all your game development stuff, but ultimately what's most important is you putting it somewhere that works for you.

Once it's been installed, you can get cracking utilizing it immediately, but to maximize it's efficacy, we'll want to do some prepwork on your machine to make it a fully functional development environment

## Setting up your Development Environment

While this sounds intense, really it's just installing a few common programs that help you get and use builds of the engine, namely, git and cmake.

The PM utilizes both of these, as mentioned prior to fetch engine builds and modules from curated repositories, and generate compile-able engine builds, respectively. These aren't strictly necessary, and if you're comfortable with downloading and generating projects yourself without the PM doing it for you, then you're free to skip this step.

### git

Git can be most readily acquired from [here](https://git-scm.com/download/win). If you're on MacOS, and you have XCode and its dependencies installed, you're good to go. Certain distros of Linux will likewise already have git installed.

Once it's installed and you do the basic setup, this end of things is good to go enough for the Project Manager. If you want to do more advanced actions, use private repositories, or submit Pull Requests, you can see the more in-depth instructions for a Development Environment in the [Engine Section](broken-reference).

### Cmake

Cmake can be gotten from [here](https://cmake.org/download/). Cmake is used to generate and build projects that utilize an Engine Build that has the source code. For Engine Builds that utilize precompiled binaries, it isn't actually required.&#x20;

Like with the git section above, for more info on how to use Cmake in a more advanced capacity, you can find the more in-depth instructions in the [Engine Section](broken-reference).

## Getting Started

Once you launch the Torque Project Manager, you'll find a view like this:<img src="../../.gitbook/assets/image (2).png" alt="" data-size="original">

### Interface

While generally simple to navigate, we can do a quick go-over of the layout.

On the left side, at the top, you'll find the navigation 'breadcrumbs'. It'll show you what page you're on and the navigation stack if you're in sub-pages.

Below that is the primary navigation panel. The buttons are largely self explanatory, allowing you to quickly move page-to-page to let you get your work done.

To the right is the main panel, which will show the primary content of whatever page you're on. In the above screenshot, we're on the Engine Builds page.

Above that are the Action Buttons, which are contextual to the page you're on, as well as a search bar for filtering contents of the main panel.

### Engine Builds

Engine Builds are, as the name suggests for builds of the engine. To create projects, you must have a build of the engine to copy from. There are several builds listed by default which are pulled from the Torque3D website. You can also add new Engine Builds to the listing from git URLs or local directories on your computer.

There are two 'types' of Engine Builds:

#### Source

Denoted by the Source tag, these are Engine Builds that have the full source code with them. To utilize these you'll need Cmake and do the full generation and compile process.

#### Binary

Denoted by the Binary tag, these utilize precompiled binary files, and do not provide the source code. While these are less flexible, there are no additional setup steps needed. You can just create a project with them and immediately launch into the application and begin working.

By default, Engine Builds download to the /EngineBuilds/ directory in the Project Manager's folder. You can change the default download target in the Settings page.

Once you have a Engine Build downloaded, you can create a Project, but first we'll stop over in the Modules page.

### Modules

<img src="../../.gitbook/assets/image (6) (1).png" alt="" data-size="original">

For a full explination of what Modules(and the Assets they contain) are, you can check the Modules section of the documentation. But for the purposes of the Project Manager, Modules are self-contained chunks of content and code that are easily installed and managed for your projects.

Like Engine Builds, there are a number of default modules that are provided from the Torque3D website the Manager fetches info for. You can download any or all of them, as well as add new ones from local directories or git repositories.

Also like Engine Builds, they are by default downloaded to /Modules/ but this can be changed in the Settings.

Once you have downloaded modules, they are "Available", which will be important for when we go to make a project.

### Projects

![](<../../.gitbook/assets/image (4) (1).png>)

A project is, ultimately, your game. When creating a new one, you'll not only define the name and destination, but the Engine Build as well. If the build is a Source build, then you'll have additional prompts for for the Generator(what IDE/code platform Cmake uses to generate) as well as various Cmake flags.

Normally you can leave the flags as-is, but they do provide additional features and functions.

Likewise, if you've installed any Modules, you'll see a list of Available ones as well. While you can, at any time, install new Modules to an existing Project, you can quickly get a Project up to speed during creation by selecting some modules here. They will be installed as part of the setup process, making getting your game rolling even faster.

