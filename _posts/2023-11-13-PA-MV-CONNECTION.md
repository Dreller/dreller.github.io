---
title: Rename your Power Apps Connections
date: 2023-11-13 19:20:00
categories: PowerPlatform PowerApps
tags: m365 office power-platform power-apps vscode canvas
---

Did you know you can use [Visual Studio Code (VS Code)](https://code.visualstudio.com) to edit your Power Apps ?  Okay you can't edit your Screens, but at least, you can update some _under the hood_ things, such as Data Connection Display Names!
This is the main benefit for me.

Anyways, I had to find a way to deconstruct a Power App, and using VS Code was the easiest method.  Here is all you need to know to use VS Code to rename your Data Connections in a Power App.

## Setup your VS Code installation
You first need VS Code on your computer, with the [Power Platform Tools](https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.powerplatform-vscode) extension.

[Click here to get instructions from Microsoft Learn](https://learn.microsoft.com/en-us/power-pages/configure/vs-code-extension#install-visual-studio-code-extension).

## Download your app

```
pac canvas download --name APPLICATION-ID --environment ENVIRONMENT-ID
```

## Expand the files

```
pac canvas unpack --msapp "My App.msapp" --source "ABC"
```

## References
- **[pac canvas]**: Available commands for the `canvas` group.
