---
title: Modern POS extension package 
description: This topic explains how to create a Modern POS extension package.
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

# Create a Modern POS extension package

[!include [banner](../includes/banner.md)]

To create the extension installer for a Modern POS extension, follow these steps:

1. Open Visual studio 2017, create a new console application (.NET Core), and name it **ModernPos.Installer**.

2. Edit the **.proj** file and change the **Target Framework** to **.NET Framework 4.6.1**. The Xml is shown here:

    ```Javascript
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFramework>net461</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

3. Delete the generated **Program.cs** file.

4. Add a reference to the Retail SDK with POS extension NuGet Package.

    1. Right-click the project in Solution Explorer and select **Manage NuGet packages**.
    2. Select the **Browse** tab in the NuGet Package Manager window.
    3. Search for **Microsoft.Dynamics.Commerce.Sdk.Installers.ModernPos**.
    4. Select the package and then select **Install**.
    5. select the version that matches your go-live version.

5. Add a reference from your Modern POS project to the **ModernPos.Installer** project created above.

    1. Right-click the Modern POS project in Solution Explorer and select **Add -&gt; Reference**.
    2. Select the **Projects** tab on the left side of the Reference Manager.
    3. Select the **ModernPos.Installer** project created above.

6. For \[Offline channel database extension script projects only\]: add a reference from the Modern Pos project to the Channel database project.

    1. Right-click the Modern POS project in Solution Explorer and select **Add -&gt; Reference**.
    2. Select the **Projects** tab on the left side of the Reference Manager.
    3. Select the Channel database extension project created above.

7. Compile and build the project. The output of this project contains the Modern POS extension installer.

8. To manually install the extension, open PowerShell in administrator mode and navigate to the extension installer folder. Run the install command to install the extensions.

    ```powershell
    PS C:\ModernPos.Installer\bin\Debug\net461> .\**ModernPos.Installer.exe install**
    ```

    To uninstall the extension:

    ```powershell
    PS C:\ModernPos.Installer\bin\Debug\net461> .\**ModernPos.Installer.exe** uninstall
    ```

    > [!NOTE]
    > Before installing the extension installer, install the sealed Modern POS first.

9. After installing the extension, close Modern POS if it's running. Launch Modern POS from the **Install/Update Modern POS** desktop shortcut icon to load the extension. The extension .appx file will be installed after clicking the desktop icon. The previous steps copy the .appx and files to the correct location.
