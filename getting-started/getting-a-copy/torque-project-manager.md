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

The PM utilizes both of these, as mentioned prior to fetch engine builds and modules from curated repositories, and generate compileable engine builds, respectively. These aren't strictly necessary, and if you're comfortable with downloading and generating projects yourself without the PM doing it for you, then you're free to skip this step.
