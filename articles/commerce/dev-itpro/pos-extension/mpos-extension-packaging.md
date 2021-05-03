---
# required metadata

title: Modern POS extension package 
description: This topic explains how to Create Modern POS extension package.
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

# Create a Modern POS extension package 

[!include [banner](../includes/banner.md)]

To create the extension installer for the Modern POS, follow the below steps:

1.  Open the Visual studio 2017 and create a new console application (.NET Core), name it as ModernPos.Installer.

2.  Edit the proj file and change the Target Framework to .NET Framework 4.6.1.

3.  Delete the generated Program.cs file.

```Javascript

Ex: 
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net461</TargetFramework>
  </PropertyGroup>
</Project>

```

4.  Add a reference to the POS SDK NuGet Package

    1.  Right click the project in the solution explore and select "Manage NuGet packages"

    2.  Select the "Browse" tab in the NuGet Package Manager window

    3.  Search for "Microsoft.Dynamics.Commerce.Sdk.Installers.ModernPos"

    4.  Select the package and click Install, select the version that matches your go-live version.

5.  Add a reference from the ModernPos project to the ModernPos.Installer project created above.

    1.  Right click the Modern POS project in the Solution Explorer and click Add -&gt; Reference.

    2.  Select the "Projects" tab on the left side of the Reference Manager.

    3.  Select the ModernPos.Installer project created above.

6.  \[Offline Channel database extension script project only\] Add a reference from the ModernPos project to the Channel database project.

    1.  Right click the Modern POS project in the Solution Explorer and click Add -&gt; Reference.

    2.  Select the "Projects" tab on the left side of the Reference Manager.

    3.  Select the Channel database extension project created above.

7.  Compile and build the project.

8.  The output of this project will contain the Modern POS extension installer.

9.  To manually install the extension, open PowerShell in administrator mode and navigate to the extension installer folder and run the install command to install the extensions.

    Ex: PS C:\\ModernPos.Installer\\bin\\Debug\\net461&gt; .\\**ModernPos.Installer.exe install**

    To uninstall: PS C:\\ModernPos.Installer\\bin\\Debug\\net461&gt; .\\**ModernPos.Installer.exe** uninstall

    Note: Before installing the extension installer, install the sealed Modern POS first.

10. After installing the extension, close the Modern POS if its running and launch Modern POS from the Install/Update Modern POS desktop shortcut icon to load the extension. The extension appx will be installed after clicking the Install/Update Modern POS desktop icon. The previous step copies the appx and files to the right location, the appx will be installed by launching the MPOS from Install/Update Modern POS desktop shortcut icon.
