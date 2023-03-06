---
title: Security best practices for Store Commerce for web in shared environments
description: This article provides recommendations that can help secure Store Commerce for web in a shared environment.
author: josaw1
ms.date: 02/17/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.custom: 257674
ms.assetid: bd618e4b-ad09-483e-9440-f5d8d5e5af8a
---

# Security best practices for Store Commerce for web in shared environments

[!include [banner](../includes/banner.md)]

Store Commerce for web is a web application that runs in the context of a browser. This article provides recommendations that can help secure Store Commerce for web in a shared environment.

Store Commerce for web is a web application that runs in the context of a web browser. Therefore, it's vulnerable to attack when a user can run any script in the context of the web application. One requirement for such attacks is that the user must have physical access to the computer, either in person or by using Remote Desktop Connection. Vulnerability to attack is an existing issue in most browsers that provide developer tools, and that enable scripts to be run without sufficient privilege control. Because the web application will have little influence over its hosting environment, one way to mitigate security issues is to add defense-in-depth. The defense-in-depth can be built by taking advantage of the restrictive policies of both the browser and the operating system.

## Hardening instructions for a Store Commerce for web computer

>[!NOTE]
>Removing Reply URLs or Service Principals will break operations related to AAD in Store Commerce in the browser.

Here are some of the defense-in-depth recommendations for the operating system and/or browser that will have an activated instance of Store Commerce for web. The settings should be enabled or set by a high-privileged account for the operating system. Store Commerce for web should be used by a low-privileged account that can't override those settings. We recommend that you enable all the following settings. Otherwise, you could create a security loophole that will be prone to security exploitation.

- **Required** - Disable script execution in the browser's address bar.
- **Required** - Disable the browser's developer console.
- **Required** - Store Commerce for web should be accessed by a low-privileged user.
- **Required** - Set up group policies to enable a kiosk session.
- **Recommended** - Set up a proxy to access only websites included in a safe list.

## Disable script execution in the address bar of the browser that runs Store Commerce for web

### Internet Explorer - disable script execution

There is no option to disable script execution in the address bar in Internet Explorer. One alternative is to hide the address bar itself.

1. Create a shortcut for the Store Commerce for web URL, and copy it to each store worker's Microsoft Windows desktop.
2. Run **regedit.exe** to change the registry to disable the Internet Explorer address bar. \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Internet Explorer\\ToolBars\\Restrictions\] "NoNavBar"=dword:00000001

### Microsoft Edge - disable script execution

By design, Microsoft Edge prevents script execution in the address bar. Therefore, no action is required.

## Disable the developer console in the browser that runs Store Commerce for web

### Internet Explorer - disable the developer console

Use Group Policy Editor to enable the following group policy to disable the Internet Explorer developer console: \\Administrative Templates\\Windows Components\\Internet Explorer\\Toolbars\\Turn off Developer Tools="Enabled"

### Microsoft Edge - disable the developer console

Run **regedit.exe** to change the registry to disable the developer console. \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Policies\\Microsoft\\MicrosoftEdge\\F12\] "AllowDeveloperTools"=dword:00000000

## Store Commerce for web should be accessed by a low-privileged user

A point of sale (POS) user must be a non-administrative account that doesn't have privileges to change applied policies.

## Set up group policies to enable a kiosk session

We recommend that you apply the following restrictions for Store Commerce for web users:

- Restrict access to the file system.
- Restrict access to Control Panel.
- Restrict access to removable drives.
- Restrict access to shells that run commands.
- Restrict access to the registry.
- Restrict access to application management.

The following table lists the group policies to enable kiosk mode. The set of policies requires that you start your browser at the sign-in script. These policies can be adjusted to your requirements. You should always assess any security implications or talk to a specialist.

| Setting | State    | Comment | Path |
|---------|----------|---------|------|
| Enable screen saver             | Disabled | No      | \\Control Panel\\Personalization                                            |
| Allow DFS roots to be published | Disabled | No      | \\Shared Folders         |
| Allow shared folders to be published | Disabled | No      | \\Shared Folders         |
| Add Search Internet link to Start Menu | Disabled | No      | \\Start Menu and Taskbar |
| Show Quick Launch on Taskbar    | Disabled | No      | \\Start Menu and Taskbar |
| Show the Apps view automatically when the user goes to Start | Disabled | No      | \\Start Menu and Taskbar |
| Show "Run as different user" command on Start                | Disabled | No      | \\Start Menu and Taskbar |
| Add the Run command to the Start Menu  | Disabled | No      | \\Start Menu and Taskbar |
| Show Start on the display the user is using when they press the Windows logo key                                      | Disabled | No      | \\Start Menu and Taskbar |
| Show Windows Store apps on the taskbar | Disabled | No      | \\Start Menu and Taskbar |
| Turn off shell protocol protected mode | Disabled | No      | \\Windows Components\\File Explorer                                         |
| Turn on menu bar by default     | Disabled | No      | \\Windows Components\\Internet Explorer                                     |
| Turn on Script Execution        | Disabled | No      | \\Windows Components\\Windows PowerShell                                    |
| Hide the "Add a program from CD-ROM or floppy disk" option   | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Hide the "Add programs from Microsoft" option                | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Hide the "Add programs from your network" option             | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Hide Add New Programs page      | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Remove Add or Remove Programs   | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Hide the Set Program Access and Defaults page                | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Hide Change or Remove Programs page  | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Go directly to Components Wizard     | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Remove Support Information      | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Hide Add/Remove Windows Components page                      | Enabled  | No      | \\Control Panel\\Add or Remove Programs                                     |
| Disable the Display Control Panel    | Enabled  | No      | \\Control Panel\\Display |
| Hide Settings tab               | Enabled  | No      | \\Control Panel\\Display |
| Prevent changing color scheme   | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent changing theme          | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent changing visual style for windows and buttons        | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prohibit selection of visual style font size                 | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent changing color and appearance  | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent changing desktop background  | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent changing desktop icons  | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent changing mouse pointers | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent changing screen saver   | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent changing sounds         | Enabled  | No      | \\Control Panel\\Personalization                                            |
| Prevent addition of printers    | Enabled  | No      | \\Control Panel\\Printers                                                   |
| Prevent deletion of printers    | Enabled  | No      | \\Control Panel\\Printers                                                   |
| Hide "Set Program Access and Computer Defaults" page         | Enabled  | No      | \\Control Panel\\Programs                                                   |
| Hide "Get Programs" page        | Enabled  | No      | \\Control Panel\\Programs                                                   |
| Hide "Installed Updates" page   | Enabled  | No      | \\Control Panel\\Programs                                                   |
| Hide "Programs and Features" page    | Enabled  | No      | \\Control Panel\\Programs                                                   |
| Hide the Programs Control Panel | Enabled  | No      | \\Control Panel\\Programs                                                   |
| Hide "Windows Features"         | Enabled  | No      | \\Control Panel\\Programs                                                   |
| Hide "Windows Marketplace"      | Enabled  | No      | \\Control Panel\\Programs                                                   |
| Turn off automatic learning     | Enabled  | No      | \\Control Panel\\Regional and Language Options\\Handwriting personalization |
| Hide Regional and Language Options administrative options    | Enabled  | No      | \\Control Panel\\Regional and Language Options                              |
| Hide and disable all items on the desktop                    | Enabled  | No      | \\Desktop                |
| Remove the Desktop Cleanup Wizard    | Enabled  | No      | \\Desktop                |
| Hide Internet Explorer icon on desktop | Enabled  | No      | \\Desktop                |
| Remove Computer icon on the desktop  | Enabled  | No      | \\Desktop                |
| Remove My Documents icon on the desktop                      | Enabled  | No      | \\Desktop                |
| Hide Network Locations icon on desktop | Enabled  | No      | \\Desktop                |
| Remove Properties from the Computer icon context menu        | Enabled  | No      | \\Desktop                |
| Remove Properties from the Documents icon context menu       | Enabled  | No      | \\Desktop                |
| Do not add shares of recently opened documents to Network Locations                                                   | Enabled  | No      | \\Desktop                |
| Remove Recycle Bin icon from desktop | Enabled  | No      | \\Desktop                |
| Remove Properties from the Recycle Bin context menu          | Enabled  | No      | \\Desktop                |
| Do not save settings at exit    | Enabled  | No      | \\Desktop                |
| Turn off Aero Shake window minimizing mouse gesture          | Enabled  | No      | \\Desktop                |
| Prevent adding, dragging dropping and closing the Taskbar's toolbars                                                  |          |         | Enabled                  |
| Prohibit adjusting desktop toolbars  | Enabled  | No      | \\Desktop                |
| Force Start to be either full screen size or menu size       | Enabled  | No      | \\Start Menu and Taskbar |
| Go to the desktop instead of Start when signing in           | Enabled  | No      | \\Start Menu and Taskbar |
| Turn off personalized menus     | Enabled  | No      | \\Start Menu and Taskbar |
| Lock the Taskbar                | Enabled  | No      | \\Start Menu and Taskbar |
| Turn off notification area cleanup   | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Balloon Tips on Start Menu items                      | Enabled  | No      | \\Start Menu and Taskbar |
| Prevent users from customizing their Start Screen            | Enabled  | No      | \\Start Menu and Taskbar |
| Remove common program groups from Start Menu                 | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Favorites menu from Start Menu  | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Search link from Start Menu   | Enabled  | No      | \\Start Menu and Taskbar |
| Remove frequent programs list from the Start Menu            | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Games link from Start Menu    | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Help menu from Start Menu     | Enabled  | No      | \\Start Menu and Taskbar |
| Turn off user tracking          | Enabled  | No      | \\Start Menu and Taskbar |
| Remove All Programs list from the Start menu                 | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Network Connections from Start Menu                   | Enabled  | No      | \\Start Menu and Taskbar |
| Remove pinned programs list from the Start Menu              | Enabled  | No      | \\Start Menu and Taskbar |
| Do not keep history of recently opened documents             | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Recent Items menu from Start Menu                     | Enabled  | No      | \\Start Menu and Taskbar |
| Do not use the search-based method when resolving shell shortcuts  | Enabled  | No      | \\Start Menu and Taskbar |
| Do not use the tracking-based method when resolving shell shortcuts                                                   | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Run menu from Start Menu | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Default Programs link from the Start menu.            | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Documents icon from Start Menu  | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Music icon from Start Menu    | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Network icon from Start Menu  | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Pictures icon from Start Menu | Enabled  | No      | \\Start Menu and Taskbar |
| Do not search communications    | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Search Computer link     | Enabled  | No      | \\Start Menu and Taskbar |
| Remove See More Results / Search Everywhere link             | Enabled  | No      | \\Start Menu and Taskbar |
| Do not search for files         | Enabled  | No      | \\Start Menu and Taskbar |
| Do not search Internet          | Enabled  | No      | \\Start Menu and Taskbar |
| Do not search programs and Control Panel items               | Enabled  | No      | \\Start Menu and Taskbar |
| Remove programs on Settings menu     | Enabled  | No      | \\Start Menu and Taskbar |
| Prevent changes to Taskbar and Start Menu Settings           | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Downloads link from Start Menu  | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Homegroup link from Start Menu  | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Recorded TV link from Start Menu                      | Enabled  | No      | \\Start Menu and Taskbar |
| Remove user's folders from the Start Menu                    | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Videos link from Start Menu   | Enabled  | No      | \\Start Menu and Taskbar |
| Force classic Start Menu        | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Clock from the system notification area               | Enabled  | No      | \\Start Menu and Taskbar |
| Prevent grouping of taskbar items    | Enabled  | No      | \\Start Menu and Taskbar |
| Do not display any custom toolbars in the taskbar            | Enabled  | No      | \\Start Menu and Taskbar |
| Remove access to the context menus for the taskbar           | Enabled  | No      | \\Start Menu and Taskbar |
| Hide the notification area      | Enabled  | No      | \\Start Menu and Taskbar |
| Prevent users from uninstalling applications from Start      | Enabled  | No      | \\Start Menu and Taskbar |
| Remove user folder link from Start Menu                      | Enabled  | No      | \\Start Menu and Taskbar |
| Remove user name from Start Menu     | Enabled  | No      | \\Start Menu and Taskbar |
| Remove links and access to Windows Update                    | Enabled  | No      | \\Start Menu and Taskbar |
| Remove the "Undock PC" button from the Start Menu            | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Notifications and Action Center | Enabled  | No      | \\Start Menu and Taskbar |
| Disable showing balloon notifications as toasts.             | Enabled  | No      | \\Start Menu and Taskbar |
| Remove the Security and Maintenance icon                     | Enabled  | No      | \\Start Menu and Taskbar |
| Remove the networking icon      | Enabled  | No      | \\Start Menu and Taskbar |
| Remove the battery meter        | Enabled  | No      | \\Start Menu and Taskbar |
| Remove the volume control icon  | Enabled  | No      | \\Start Menu and Taskbar |
| Turn off feature advertisement balloon notifications         | Enabled  | No      | \\Start Menu and Taskbar |
| Do not allow pinning Store app to the Taskbar                | Enabled  | No      | \\Start Menu and Taskbar |
| Do not allow pinning items in Jump Lists                     | Enabled  | No      | \\Start Menu and Taskbar |
| Do not allow pinning programs to the Taskbar                 | Enabled  | No      | \\Start Menu and Taskbar |
| Do not display or track items in Jump Lists from remote locations  | Enabled  | No      | \\Start Menu and Taskbar |
| Turn off automatic promotion of notification icons to the taskbar  | Enabled  | No      | \\Start Menu and Taskbar |
| Lock all taskbar settings       | Enabled  | No      | \\Start Menu and Taskbar |
| Prevent users from adding or removing toolbars               | Enabled  | No      | \\Start Menu and Taskbar |
| Prevent users from rearranging toolbars                      | Enabled  | No      | \\Start Menu and Taskbar |
| Do not allow taskbars on more than one display               | Enabled  | No      | \\Start Menu and Taskbar |
| Turn off all balloon notifications   | Enabled  | No      | \\Start Menu and Taskbar |
| Remove pinned programs from the Taskbar                      | Enabled  | No      | \\Start Menu and Taskbar |
| Prevent users from moving taskbar to another screen dock location  | Enabled  | No      | \\Start Menu and Taskbar |
| Prevent users from resizing the taskbar                      | Enabled  | No      | \\Start Menu and Taskbar |
| Turn off taskbar thumbnails     | Enabled  | No      | \\Start Menu and Taskbar |
| Remove Task Manager             | Enabled  | No      | \\System\\Ctrl+Alt+Del Options                                              |
| Code signing for device drivers | Enabled  | No      | \\System\\Driver Installation                                               |
| Turn off Windows Update device driver search prompt          | Enabled  | No      | \\System\\Driver Installation                                               |
| Disallow selection of Custom Locales | Enabled  | No      | \\System\\Locale Services                                                   |
| Disallow changing of geographic location                     | Enabled  | No      | \\System\\Locale Services                                                   |
| Disallow user override of locale settings                    | Enabled  | No      | \\System\\Locale Services                                                   |
| CD and DVD: Deny read access    | Enabled  | No      | \\System\\Removable Storage Access                                          |
| CD and DVD: Deny write access   | Enabled  | No      | \\System\\Removable Storage Access                                          |
| Floppy Drives: Deny read access | Enabled  | No      | \\System\\Removable Storage Access                                          |
| Floppy Drives: Deny write access     | Enabled  | No      | \\System\\Removable Storage Access                                          |
| Removable Disks: Deny read access    | Enabled  | No      | \\System\\Removable Storage Access                                          |
| Removable Disks: Deny write access   | Enabled  | No      | \\System\\Removable Storage Access                                          |
| All Removable Storage classes: Deny all access               | Enabled  | No      | \\System\\Removable Storage Access                                          |
| Tape Drives: Deny read access   | Enabled  | No      | \\System\\Removable Storage Access                                          |
| Tape Drives: Deny write access  | Enabled  | No      | \\System\\Removable Storage Access                                          |
| WPD Devices: Deny read access   | Enabled  | No      | \\System\\Removable Storage Access                                          |
| WPD Devices: Deny write access  | Enabled  | No      | \\System\\Removable Storage Access                                          |
| Prevent access to the command prompt | Enabled  | No      | \\System                 |
| Prevent access to registry editing tools                     | Enabled  | No      | \\System                 |
| Prevent the wizard from running.     | Enabled  | No      | \\Windows Components\\Add features to Windows 10                            |
| Turn off Program Compatibility Assistant                     | Enabled  | No      | \\Windows Components\\Application Compatibility                             |
| Search, Share, Start, Devices and Settings don't appear when the mouse is pointing to the upper-right corner of the screen                                               | Enabled  | No      | \\Windows Components\\Edge UI                                               |
| Disable help tips               | Enabled  | No      | \\Windows Components\\Edge UI                                               |
| Turn off tracking of app usage  | Enabled  | No      | \\Windows Components\\Edge UI                                               |
| Do not show recent apps when the mouse is pointing to the upper-left corner of the screen                             | Enabled  | No      | \\Windows Components\\Edge UI                                               |
| Prevent users from replacing the Command Prompt with Windows PowerShell in the menu they see when they right-click the lower-left corner or press the Windows logo key+X | Enabled  | No      | \\Windows Components\\Edge UI                                               |
| Turn off switching between recent apps | Enabled  | No      | \\Windows Components\\Edge UI                                               |
| Turn on or off details pane     | Enabled  | No      | \\Windows Components\\File Explorer\\Explorer Frame Pane                    |
| Turn off Preview Pane           | Enabled  | No      | \\Windows Components\\File Explorer\\Explorer Frame Pane                    |
| Do not display the Welcome Center at user logon              | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Turn on Classic Shell           | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove CD Burning features      | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove DFS tab                  | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Hide these specified drives in My Computer                   | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| No Entire Network in Network Locations | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove File menu from File Explorer  | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Do not allow Folder Options to be opened from the Options button on the View tab of the ribbon | Enabled  | No      | \\Windows Components\\File Explorer      |
| Remove Hardware tab             | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Hide the Manage item on the File Explorer context menu       | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove Shared Documents from My Computer                     | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove "Map Network Drive" and "Disconnect Network Drive"    | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove the Search the Internet "Search again" link           | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove Security tab             | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove Search button from File Explorer                      | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Remove File Explorer's default context menu                  | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Prevent access to drives from My Computer                    | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Turn off Windows+X hotkeys      | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| No Computers Near Me in Network Locations                    | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Request credentials for network installations                | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Prevent users from adding files to the root of their Users Files folder.  | Enabled  | No      | \\Windows Components\\File Explorer                                         |
| Turn off Accelerators           | Enabled  | No      | \\Windows Components\\Internet Explorer\\Accelerators                       |
| File menu: Disable closing the browser and Explorer windows  | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| File menu: Disable Save As... menu option                    | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| File menu: Disable Save As Web Page Complete                 | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| File menu: Disable New menu option   | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| File menu: Disable Open menu option  | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Help menu: Remove 'Send Feedback' menu option                | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Help menu: Remove 'For Netscape Users' menu option           | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Help menu: Remove 'Tip of the Day' menu option               | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Help menu: Remove 'Tour' menu option | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Turn off Shortcut Menu          | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Hide Favorites menu             | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Disable Open in New Window menu option | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Turn off Print Menu             | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Turn off the ability to launch report site problems using a menu option   | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Disable Save this program to disk option                     | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Tools menu: Disable Internet Options... menu option          | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| View menu: Disable Full Screen menu option                   | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| View menu: Disable Source menu option  | Enabled  | No      | \\Windows Components\\Internet Explorer\\Browser menus                      |
| Turn off Developer Tools        | Enabled  | No      | \\Windows Components\\Internet Explorer\\Toolbars                           |
| Turn off toolbar upgrade tool   | Enabled  | No      | \\Windows Components\\Internet Explorer\\Toolbars                           |
| Hide the Command bar            | Enabled  | No      | \\Windows Components\\Internet Explorer\\Toolbars                           |
| Hide the status bar             | Enabled  | No      | \\Windows Components\\Internet Explorer\\Toolbars                           |
| Disable customizing browser toolbars | Enabled  | No      | \\Windows Components\\Internet Explorer\\Toolbars                           |
| Disable customizing browser toolbar buttons                  | Enabled  | No      | \\Windows Components\\Internet Explorer\\Toolbars                           |
| Turn off add-on performance notifications                    | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Do not allow users to enable or disable add-ons              | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing Advanced page settings                      | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off Favorites bar          | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Prevent per-user installation of ActiveX controls            | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off Reopen Last Browsing Session  | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off Tab Grouping           | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Prevent managing the phishing filter | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off Managing SmartScreen Filter for Internet Explorer 8 | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Prevent managing SmartScreen Filter  | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off the Security Settings Check feature                 | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Enforce full-screen mode        | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable Import/Export Settings wizard  | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Prevent Internet Explorer Search box from appearing          | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off Quick Tabs functionality    | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off tabbed browsing        | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing Automatic Configuration settings            | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing Temporary Internet files settings           | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing Calendar and Contact settings               | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing certificate settings  | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing default browser check | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing color settings | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing connection settings | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing font settings  | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing language settings   | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing link color settings | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing Messaging settings  | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Prevent managing pop-up exception list | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off pop-up management      | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing Profile Assistant settings                  | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Prevent changing proxy settings | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Disable changing ratings settings    | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off the auto-complete feature for web addresses         | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off suggestions for all user-installed providers        | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off the quick pick menu    | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Search: Disable Find Files via F3 within the browser         | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Search: Disable Search Customization | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off ability to pin sites in Internet Explorer on the desktop  | Enabled  | No      | \\Windows Components\\Internet Explorer                                     |
| Turn off the offer to update to the latest version of Windows      | Enabled  | No      | \\Windows Components\\Store                                                 |
| Turn off the Store application  | Enabled  | No      | \\Windows Components\\Store                                                 |
| Prohibit New Task Creation      | Enabled  | No      | \\Windows Components\\Task Scheduler                                        |

## Set up a proxy to access only websites included in a safe list

You can define a list of websites that a store worker (cashier) requires for normal operations, and set up an administrator-controlled proxy that has access only to these websites. Store Commerce for web requires access to the following websites:

- Store Commerce for web website
- Microsoft Azure Active Directory sign-in page
- Commerce Scale Unit website
- Bing Maps resources
- Media resources
- Credit Card Payment acceptance page (optional)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
