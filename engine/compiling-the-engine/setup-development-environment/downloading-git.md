---
description: >-
  This page explains the steps to acquire, install and set up git for version
  control with the Torque game engine
---

# Git

## Where to get

Git can be most readily acquired from here:

{% embed url="https://git-scm.com/download" %}

## Platform-Specifics

### Windows

If you've installed Git for Windows and utilized the basic settings, you're good to go.

### Mac OSX

If you're on MacOS, and you have XCode and its dependencies installed, you'll already have git installed. You can still download git from the site to ensure you have up to date versions, but for normal operations, the XCode-packed version is perfectly sufficient.

### Linux

Certain distros of Linux will likewise already have git installed. If you are unsure, you can either download it from above to ensure you have the latest, or if you're working off Ubuntu/Debian, you can run the following command to ensure you've got the latest:

```
sudo apt-get install git-all
```

## GUI Clients

GUI Clients can make working with git significantly easier than doing it all by hand with the command line. Here are some options:

<details>

<summary>TortiseGit (Windows Only)</summary>

Acquirable [here](https://tortoisegit.org/download/) tortisegit is powerful due to a simple interface that can integrate into the Windows shell. Meaning that you can do git actions directly from the RMB shell menu, like so:

![](<../../../.gitbook/assets/image (13).png>)

This can drastically improve iteration time.

It also can integrate in other external tools, such as [WinMerge](https://winmerge.org/downloads/?lang=en) for diff comparisons.

</details>

<details>

<summary>Github Desktop</summary>

Github can be acquired [here.](https://desktop.github.com)

Github Desktop is convenient because, as per the name, github has integrations directly with it. If you have Desktop installed, then it's possible for you to initiate a clone or pull directly from the github interface:

![](<../../../.gitbook/assets/image (6).png>)

</details>

<details>

<summary>GitKraken</summary>

GitKraken can be acquired [here.](https://www.gitkraken.com/download)

It has paid and free tiers, and offers a bunch of potentially useful features to help with project/repository management.

</details>
