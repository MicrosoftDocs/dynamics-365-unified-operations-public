---
title: Create a Modern POS extension package
description: Learn how to create a Modern POS (MPOS) extension package in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/25/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.custom: 
  - bap-template
---

# Create a Modern POS extension package

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/retail-sdk-deprecation-banner.md)]

This article explains how to create a Modern POS (MPOS) extension package in Microsoft Dynamics 365 Commerce.

To create the extension installer for a Modern POS extension, follow these steps:

1. In Microsoft Visual Studio 2017, create a new console application (.NET Core), and name it **ModernPos.Installer**.
1. Edit the .proj file, and change the target framework to the .NET Framework version 4.6.1, as shown in the following XML.

    ```Javascript
    <Project Sdk="Microsoft.NET.Sdk">
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>net461</TargetFramework>
        </PropertyGroup>
    </Project>
    ```

1. Delete the **Program.cs** file that was generated.
1. Add a reference to the **Microsoft.Dynamics.Commerce.Sdk.Installers.ModernPos** NuGet Package:

    1. In Solution Explorer, select and hold (or right-click) the project, and then select **Manage NuGet packages**.
    1. In the **NuGet Package Manager** window, on the **Browse** tab, search for **Microsoft.Dynamics.Commerce.Sdk.Installers.ModernPos**.
    1. Select the package, and then select **Install**.
    1. Select the version that matches your go-live version.

1. Add a reference to the **Modern POS** project that you created earlier:

    1. In Solution Explorer, select and hold (or right-click) the project, and then select **Add &gt; Reference**.
    1. In Reference Manager, on the **Projects** tab on the left, select the **Modern POS** project that you created earlier.
    1. After the project is added as reference, edit the csproj file and add `<ReferenceOutputAssembly>false</ReferenceOutputAssembly>` for the reference added.

1. **For offline channel database extension script projects only:** Add a reference from the Modern POS project to the channel database project:

    1. In Solution Explorer, select and hold (or right-click) the Modern POS project, and then select **Add &gt; Reference**.
    1. In Reference Manager, on the **Projects** tab on the left, select the channel database extension project that you created earlier.

1. Compile and build the project. The output of this project contains the Modern POS extension installer.
1. To manually install the extension, open Windows PowerShell in administrator mode, go to the extension installer folder, and run the **install** command.

    ```powershell
    PS C:\ModernPos.Installer\bin\Debug\net461> .\ModernPos.Installer.exe install
    ```

    To uninstall the extension, run the **uninstall** command.

    ```powershell
    PS C:\ModernPos.Installer\bin\Debug\net461> .\ModernPos.Installer.exe uninstall
    ```

    > [!NOTE]
    > Before you install the extension installer, install the sealed Modern POS.

1. After you finish installing the extension, close Modern POS if it's running. Then, to load the extension, open Modern POS by using the **Install/Update Modern POS** icon on the desktop. The extension's .appx file is installed. The previous steps copy the .appx file and other files to the correct location.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
