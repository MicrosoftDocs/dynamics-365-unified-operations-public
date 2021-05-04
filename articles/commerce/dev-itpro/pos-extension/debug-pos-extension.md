---
title: Debugging POS extensions
description: This topic explains how to debug a POS extension.
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

[!include [banner](../../../includes/banner.md)]

This topic explains how to debug a POS extension. It applies to the Retail SDK, version 10.0.18 and later.

## Debugging Modern POS using Visual Studio 2017

Debug your extension by following these steps:

1. Install Sealed Modern POS on the development machine using the Sealed MPOS installer.
2. Install the UWP app by clicking the shortcut on the desktop.
3. In Visual Studio, build your Modern POS Extension Package Project (**jsproj**).
4. In Visual Studio, deploy your Modern POS Extension Package. Right-click the ModernPOS JavaScript project file in Solution Explorer and select **Deploy**.
5. Launch POS with the debugger attached, by following these steps:

    1. In the **Debug** menu, select **Other Debug Targets &gt; Debug Installed App Package**.
    2. Search for and Select **Commerce Modern POS**.
    3. Click **Start** to launch the application.

## Running and Debugging Cloud POS

### <a name="configure-cloud-pos"></a>Configuring the Cloud POS extension development environment

Run the following steps the first time that an extension package is developed on the machine or if the link is deleted. Create a directory symbolic link in the Cloud POS extensions directory to the extension package root directory.

1. Make sure that Cloud POS is deployed on your machine. If it isn't, use the CSU Self-Hosted installer to Deploy Cloud POS.
2. Open IIS. Open the **Run** menu (**Windows key + R**), and then type: **inetmgr**. Select **OK**.
3. Expand **Sites &gt; Select RetailCloudPos** and then right-click it and select **Explore**.
4. Select **File** and then select **Open Windows PowerShell as administrator**.
5. Open the Windows Command Prompt in the PowerShell Window by running the command `cmd .`.
6. Change the current directory to the extensions root directory by running the command `cd Extensions`.
7. Create a session variable with the name of your extension package by running the command `set ExtensionPackageName=Contoso.Pos.Developer.Samples`

    > [!NOTE]
    > Replace **Contoso.Pos.Developer.Samples** in the command above with the name of your POS extension package. The extension package name must match the name specified in the **ExtensionPackageDefinition** in the Commerce Runtime trigger extension that configures the POS extension package.

8. Create a session variable with the absolute path to your POS extension package project directory by running the command `set AbsolutePathToExtensionPackageProject=%FullPathToPOSExtensionProjectRootDirectory%`

    > [!NOTE]
    > Replace **%FullPathToPOSExtensionProjectRootDirectory%** with the absolute path to your POS Extension Package project.

    Example:

    ```powershell
    set AbsolutePathToExtensionPackageProject=K:\RetailCloudPos\WebRoot\Extensions\ Contoso.Pos.Developer.Samples
    ```

9. Create a link from the Extensions directory to the extension package project root directory by running the command:

    ```powershell
     mklink /D %ExtensionPackageName% %AbsolutePathToExtensionPackageProject%
    ```

10. Verify the whether the link folder for your extension package is created in the Cloud POS extension package directory looks like the image below.

## Debugging Cloud POS using Edge developer tools

1. Completed the steps in [Configuring the Cloud POS extension development environment](#configure-cloud-pos).
2. Build your Cloud POS extension project.
3. Navigate to the Cloud POS website in Edge.
4. Press F12 to launch the Edge developer tools.
5. Set up a workspace that points to the root directory of your Cloud POS Extension package. You only have to setup the workspace the first time.
6. Make sure that **JavaScript Source Mapping** is enabled.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
