---
# required metadata

title: Create a Modern POS extension appx file
description: This topic explains how to create a Modern POS packaging project using Visual Studio 2017.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18

---

# Create a Modern POS extension appx file 

[!include [banner](../../includes/banner.md)]

The steps below describe how to create a Modern POS packaging project using Visual Studio 2017. These steps are only required if you are developing extensions for Modern POS. The Modern POS extension packaging project is responsible for generating the Universal Windows Platform Modification package (MSIX) that will extend the Modern POS App.

1.  Create a new JavaScript Universal Windows Platform App Project and name the project as ModernPos:

    1.  Right click the solution in the Solution explorer and click Add -&gt; New Project...

         1.  Search for "Windows JavaScript" and select "Blank App (Universal Windows)"

            <img src="media/image9.png" alt="Graphical user interface, application Description automatically generated" width="480" height="360" />

         2.  Set the Target Version and Minimum version as shown below.

        ![Version](media/MinimumVersion.png)

2.  Delete Generated Source Files

       1.  Delete the "js" and "css" folders, the index.html and the package.appxmanifest file.

        **Note:** Don't delete the image file used as the logo for the app package (images\\StoreLogo.png) unless you content include a replacement logo

3.  Edit the project and import the customization package props file created in the steps above.

    **Note: Generating the package.appxmanifest depends on the properties from the customization package props file. Please make sure the project has imported it.**

4.  Add a reference to the POS SDK NuGet Package

    1.  Right click the project in the solution explore and select "Manage NuGet packages"

    2.  Select the "Browse" tab in the NuGet Package Manager window

    3.  Search for "Microsoft.Dynamics.Commerce.Sdk.Pos"

    4.  Select the package and click Install.

5.  Update the solution configuration to only target x86

    1.  Right click the solution in the Solution Explorer and select "Properties"

    2.  Open the Configuration Manager

    3.  In the "Active solution platform" drop down select Edit

    4.  Remove all other platforms except for "x86"

         ![Platform config](media/Platform.png)

6.  Edit the jsproj file to remove unsupported platform configurations.

    1.  Ensure the project file is saved and unload the project using the Solution Explorer

    2.  Right click the project file in the Solution Explorer and click Edit

    3.  Delete the **ProjectConfiguration** includes for all platforms other than x86

        1.  This should result in a ProjectConfigurations section that looks like the one below:

        ![Project config](media/ProjectConfig.png)


    4.  Reload the project.

7.  Add a reference from the Modern POS jsproj to the POS.Extension Package project created above.

    1.  Right click the Modern POS project in the Solution Explorer and click Add -&gt; Reference.

    2.  Select the "Projects" tab on the left side of the Reference Manager.

    3.  Select the POS Extension Package project created above.

> Note: Visual Studio will warn about an unsupported reference. Select "Yes" to add the reference anyway.

![Reference error](media/ReferenceManager.png)

8.  If your solution contains Commerce Runtime extension projects then add project references to each of the Commerce Runtime extension projects in the solution.

    1.  Right click the Modern POS project in the Solution Explorer and click Add -&gt; Reference

    2.  Select the "Projects" tab on the left side of the Reference Manager.

    3.  Select the Commerce Runtime extension projects.

9.  If your solution contains Hardware Station extension projects then add project references to each of the Hardware Station extension projects in the solution.

    1.  Right click the Modern POS project in the Solution Explorer and click Add -&gt; Reference

    2.  Select the "Projects" tab on the left side of the Reference Manager.

    3.  Select the Hardware Station Extension projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
