---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2020-07-31"
slug: "change-windows10-alt-tab-navigation-back-to-classic-icons-instead-of-thumbnails"
tags:
- windows
title: "Change windows-10/11 Alt+Tab navigation back to classic icons instead of thumbnails"
---

In the registry editor, reach `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer`.

Add a new DWORD key: `AltTabSettings` and change its value to **1**.

Restart Explorer (Launch the Task Manager, find 'Windows Explorer' in the group 'Windows processes', right-click it and 'restart')

Now Alt+Tab should display only the application icons.

To revert back to the thumbnails, change the registry-key (AltTabSettings) value to **0**.

### Update (2022-02-03) - Get the classic Alt+Tab navigation using hotkeys:

In order to get the classic style Alt+Tab navigation without needing to edit the registry on Windows 10/11, try the following:

> Press & hold down any of the **Alt** keys > Press & release the other **Alt** key > Press **Tab** _(while keep the original Alt key pressed)_

This invokes the classic Alt+Tab navigation. It is a rather cumbersome way to invoke the classic style Alt+Tab navigation every time, as normally pressing Alt+Tab would still give you the standard Windows 10/11 style navigation among the open windows. So if you want to keep the classic style navigation, it would be better to use the Registry method explained earlier.
