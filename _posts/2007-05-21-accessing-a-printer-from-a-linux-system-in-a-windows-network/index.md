---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-05-21"
slug: "accessing-a-printer-from-a-linux-system-in-a-windows-network"
tags:
- linux
title: "Accessing a printer from a Linux system in a Windows network"
---

## Add a new Printer

**System** > **Administration** > **Printing** > **'Add a Printer'**

Printer Type: **Network Printer - Windows Printer (SMB)**

- Don't enter any login info when the dialog boxes prompt. 
- Wait for all of them to appear and Cancel them all. 
- Then select the host to which the printer is connected. 
- Then a dialog box pops up prompting for login info. 
- Don't do anything for the username field. Just enter the password of the host. The Username and Password fields will be filled in.
- Then select the printer from the Printer's dropdown menu.
- Now be sure to clear the Username and Password fields!

In step 2, select the appropriate manufacturer name and model. (The suggested Driver will automatically be selected. Keep it. Proceed forward.)

In step 3, leave the Description and Location fields empty. 

Click Apply. Done!
