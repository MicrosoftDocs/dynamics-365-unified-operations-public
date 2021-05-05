---
title: Create a Cloud POS extension package 
description: This topic explains how to create Cloud POS extension package.
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

# Create Cloud POS extension package

[!include [banner](../../../includes/banner.md)]

This topic explains how to create Cloud POS extension package. Based on the Cloud POS deployment topology, the Cloud POS can be deployed to Cloud Scale unit (CSU) or Cloud Scale unit (CSU) – Self hosted.

## Packaging for Cloud Scale unit (CSU) CPOS

The deployment package for CSU can be created by consuming the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** package.

Follow these steps to create the package:

1. Open Visual Studio 2017, create a new C\# class library project with the **Target framework** set to **.NET Standard 2.0**, and rename the project to **ScaleUnit**.

2. Delete the generated **Class1.cs** file.

3. Add the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** NuGet package as a dependency to the project.

4. Select the version of the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** NuGet version to match your SDK/application version. Use the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** package from `https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json`. You can add the package source location to the **nuget.config** file of your extension project file.

5. Add the **POS.Extension** project as a project reference to the **ScaleUnit** project.

6. Compile and build the project. The output of this project contains the CSU deployment package as a zip file.

> [!NOTE]
> If you have Commerce Runtime, Retail Server, or a Database extension then you must include all these extension projects as references to the **ScaleUnit** project. Adding them generates a combined deployment package that contains all your extensions.

To deploy, follow the steps in [Deploy the package to CSU](../retail-sdk-packaging.md#deploy-the-package-to-csu).

## Packaging for Cloud Scale unit – Self hosted CPOS

The deployment package for CSU can be created by consuming the **Microsoft.Dynamics.Commerce.Sdk.Installers.ScaleUnit** package.

1. Open Visual Studio 2017, create a new console application (.NET Core), and name it **ScaleUnit.Installer**.

2. Edit the .proj file and change the **Target Framework** to **.NET Framework 4.6.1**. The Xml looks like this:

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>net461</TargetFramework>
        </PropertyGroup>
    </Project>
    ```

3. Delete the generated **Program.cs** file.

4. Add a reference to the Installer SDK NuGet Package

    1. Right-click the project in Solution Explorer and select **Manage NuGet packages**.
    2. Select the **Browse** tab in the NuGet Package Manager window.
    3. Search for **Microsoft.Dynamics.Commerce.Sdk.Installers.ScaleUnit**.
    4. Select the package and then select **Install**.
    5. Select the version that matches your go-live version.

5. Add a reference from the **ScaleUnit.Installer** project to the POS.Extension project created above.

    1. Right-click the **ScaleUnit.Installer** project in the Solution Explorer, select **Add** and then **Reference**.
    2. Select the **Projects** tab on the left side of the Reference Manager.
    3. Select the POS.Extension project created above.

6. Add the **Extension.Config** file to the project.

    1. Right-click the project and select **Add** and then **New Item**.
    2. Select **Application Configuration File**.
    3. Name file as **Extension.Config** and add it.

7. Update the **Extension.Config** file with the Commerce Runtime extensions. If you don’t have any Commerce Runtime extensions, leave the **composition** section empty. The Xml looks like this:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <commerceRuntimeExtensions>
        <composition>
            <add source="assembly" value="CommerceRuntime" />
          </composition>
    ```

8. Compile and build the project. The output of this project contains the **ScaleUnit** installer .exe file.

9. To manually install the extension, open PowerShell in administrator mode and navigate to the extension installer folder. Run the install command to install the extensions.

    ```powershell
    PS C:\ModernPos.Installer\bin\Debug\net461> .\ScaleUnit.Installer.exe install    
    ```

    To uninstall the extension:

    ```powershell
    PS C:\ModernPos.Installer\bin\Debug\net461> .\ ScaleUnit.Installer.exe 
    ```

    > [!NOTE]
    > Before installing the extension installer, install the sealed ScaleUnit. If you have Commerce Runtime, Retail Server, or a Database extension, then you must include all these extension projects as references to the **ScaleUnit.Installer** project. Adding the projects generates a combined deployment package that contains all your extensions.
    > You can also create multiple Scale unit installers by extensions and manage them separately. You don’t have to combine all the extensions in one package.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
