---
title: Create a Modern POS extension package appx file
description: This topic explains how to create a Modern POS packaging project using Visual Studio 2017.
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

# Create a Modern POS extension package appx file

[!include [banner](../../includes/banner.md)]

The following steps show you how to create a Modern POS packaging project using Visual Studio 2017. These steps are only required if you are developing extensions for Modern POS. The Modern POS extension packaging project generates the [MSIX Windows app package](https://docs.microsoft.com/windows/msix/overview) that will extend the Modern POS app.

1. Create a new JavaScript Universal Windows Platform App project by following these steps:

    1. Right-click the solution in Solution explorer and select **Add** and then **New Project**. Find **Windows JavaScript** and select **Blank App (Universal Windows)**. Name the project **ModernPos**.
    2. Set **Target version** to **Windows 10, version 1809 (10.0; Build 17763)**.
    3. Set **Minimum version** to **Windows 10, version 1809 (10.0; Build 17763)**.

2. Delete these generated source folders and files:

    + **js** folder.
    + **css** folder.
    + **index.html** file.
    + **package.appxmanifest** file.

    > [!NOTE]
    > Don't delete the image file used as the logo for the app package (**images\\StoreLogo.png**) unless you include a replacement logo.

3. Edit the project and import the customization package **props** file created in the steps above.

    > [!NOTE]
    > Generating the **package.appxmanifest** file depends on the properties from the customization package **props** file. Make sure that you import it into the project.**

4. Add a reference to the POS SDK NuGet Package.

    1. Right-click the project Solution Explorer and select **Manage NuGet packages**.
    2. Select the **Browse** tab in the NuGet Package Manager window.
    3. Search for **Microsoft.Dynamics.Commerce.Sdk.Pos**.
    4. Select the package and select **Install**.

5. Update the solution configuration to target only **x86**.

    1. Right-click the project Solution Explorer and select **Properties**.
    2. Open the Configuration Manager.
    3. In the **Active solution platform** drop-down, select **Edit**.
    4. Remove all other platforms except for **x86**.

         ![Platform config](media/platform.png)

6. Edit the **jsproj** file to remove unsupported platform configurations.

    1. Save the project file.
    2. Unload the project using Solution Explorer.
    3. Right-click the project in Solution Explorer and select **Edit**.
    4. Delete the **ProjectConfiguration** includes for all platforms other than **x86**. The **ProjectConfigurations** should look like the following Xml:

        ```xml
        <ItemGroup Label="ProjectConfigurations">
            <ProjectConfiguration Include="Debug|x86">
                <Configuration>Debug</Configuration>
                <Platform>x86</Platform>
            </ProjectConfiguration>
            <ProjectConfiguration Include="Release|x86">
                <Configuration>Release</Configuration>
                <Platform>x86</Platform>
                <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
            </ProjectConfiguration>
        </ItemGroup>
        ```

    5. Reload the project.

7. Add a reference from the Modern POS **jsproj** to the **POS.Extension Package** project created above, by following these steps:

    1. Right-click the Modern POS project in Solution Explorer and select **Add** and then **Reference**.
    2. Select the **Projects** tab on the left side of the Reference Manager.
    3. Select the **POS Extension Package** project created above. When you select the project, Visual Studio asks you confirm the unsupported reference. Select **Yes**.

8. If your solution contains Commerce Runtime extension projects, then add project references to each of the Commerce Runtime extension projects in the solution.

    1. Right-click the Modern POS project in Solution Explorer. Select **Add** and then **Reference**.
    2. Select the **Projects** tab on the left side of the Reference Manager.
    3. Select the Commerce Runtime extension projects.

9. If your solution contains Hardware Station extension projects, then add project references to each of the Hardware Station extension projects in the solution.

    1. Right-click the Modern POS project in Solution Explorer. Select **Add** and then **Reference**.
    2. Select the **Projects** tab on the left side of the Reference Manager.
    3. Select the Hardware Station Extension projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
