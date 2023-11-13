---
title: CSS for Office UI Fabric Icons
date: 2023-11-11 23:15:00
categories: Styling-and-User-Interface CSS-Tricks
tags: m365 css office icon
---

You can provide an unified user experience to your users by using the same icons you can find in the Microsoft 365 environment.
The *Office UI Fabric Icons* set contains 2,313 icons, which is .  It might be a bit complicated using it the official way, here is some steps for a *custom* implementation (ie.: the way I was able to understand it and make it work).

# Download the CSS File
You can download the CSS file with these few steps:
1. Jump to the [Office UI Fabric Icons](https://uifabricicons.azurewebsites.net) page.
2. Click on the first icon in the page, and use CTRL+A to select all icons.
3. In the top menu bar, click on _Get subset_ and click _Ok_ to start preparing the package (the package will download automatically once it's ready).
4. On your computer, expand the Zip file.

The CSS file you need to include in your code is: `css/fabric-icons-inline.css` 
The _inline_ file is very useful because it includes the _FabricMDL2Icons_ font directly in the file, you don't need to maintain that extra file by yourself.

# How to use CSS Classes
In your code, use an `<i>` tag like this:
```html
<i class="ms-Icon ms-Icon--XYZ"></i>
``` 
You need to replace the `XYZ` with the Icon's Friendly Name.  

## Find the Icon's Friendly Name
Find the icon you wish to use in the the [Office UI Fabric Icons](https://uifabricicons.azurewebsites.net) page.  
Right-click on the icon and select _Copy Friendly Name_.

Use that name to compose the class Name `ms-Icon--?` (where `?` is the Friendly Name).


---

__Note__: Always keep a bookmark to the [Office UI Fabric Icons](https://uifabricicons.azurewebsites.net) page, so you can search for the icon you need.
