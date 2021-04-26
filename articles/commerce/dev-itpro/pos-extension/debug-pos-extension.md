---
title: Debugging POS extensions
description: This topic explains how to debug POS extension.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# Debugging POS extensions

[!include [banner](../../includes/banner.md)]

This topic explains how to debug POS extension, this topic applies to Retail software development kit (SDK) version 10.0.18 and later.

## Debugging Modern POS from Visual Studio 2017

1. Install Sealed Modern POS on the development machine using the Sealed MPOS installer. Install the UWP app by clicking the shortcut on the desktop.
2. Build your Modern POS Extension Package Project (jsproj)
3. Deploy your Modern POS Extension Package. Right click the ModernPOS JavaScript project file and select deploy.
4. Launch POS with the debugger attached.

    1. Using the “Debug” Menu select “Other Debug Targets” > “Debug Installed App Package…”
    2. Search for and Select “Commerce Modern POS”
    3. Click “Start” to launch the application.

## Running and Debugging Cloud POS

### Configuring the Cloud POS Extension Development Environment

The steps detailed below must be run the first time that an extension package is developed on the machine or if the link is deleted. Create a directory symbolic link in the Cloud POS extensions directory to the extension package root directory.

1. Ensure that Cloud POS is deployed on your machine. If not, use the CSU Self-Hosted installer to Deploy Cloud POS
2. Open IIS. Open the Run menu (Windows key + R), type: "inetmgr", press OK
3. Expand the Sites > Select RetailCloudPos and then right click it and click "Explore”.
4. Click File then "Open Windows PowerShell as administrator”.
5. Open Windows Command Prompt in the PowerShell Window by running the command "cmd ."
6. Change the current directory to the extensions root directory by running the command "cd Extensions"
7. Create a session variable with the name of your extension package by running the command "set ExtensionPackageName=Contoso.Pos.Developer.Samples"

    > [!NOTE]
    > Replace "Contoso.Pos.Developer.Samples" in the command above with the name of your POS extension package. The Extension package name must match the name specified in the ExtensionPackageDefinition in the Commerce Runtime trigger Extension that configures the POS extension package.

8. Create a session variable with the absolute path to your POS extension package project directory by running the command "set AbsolutePathToExtensionPackageProject=%FullPathToPOSExtensionProjectRootDirectory%"

    > [!NOTE]
    > Replace "%FullPathToPOSExtensionProjectRootDirectory%" with the absolute path to your POS Extension Package project.

    Example:

    ```cmd
    set AbsolutePathToExtensionPackageProject=K:\RetailCloudPos\WebRoot\Extensions\ Contoso.Pos.Developer.Samples
    ```

9. Create a link from the Extensions directory to the extension package project root directory by running the command:

    ```dos
     mklink /D %ExtensionPackageName% %AbsolutePathToExtensionPackageProject%
    ```

10. Verify the whether the link folder for your extension package is created in the Cloud POS extension package directory looks like the image below.

## Debugging Cloud POS Using Edge Dev Tools

1. Ensure that you have completed the steps in the “Configuring the Cloud POS Extension Development Environment”.
2. Build your Cloud POS Extension Project
3. Navigate to the Cloud POS Website
4. Press F12 to launch the Edge Dev Tools
5. Set up a workspace that points to the root directory of your Cloud POS Extension package (First Time Only)
6. Ensure that you have JavaScript Source Mapping Enabled.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
