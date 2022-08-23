---
title: Create a Cloud POS extension package
description: This article explains how to create a Cloud POS extension package.
author: josaw1
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.dyn365.ops.version: AX 10.0.18
---

# Create a Cloud POS extension package

[!include [banner](../../../includes/banner.md)]

This article explains how to create a Cloud POS extension package. Depending on the Cloud POS deployment topology, Cloud POS can be deployed to either Cloud Scale Unit (CSU) or CSU – Self hosted.

## Packaging for CSU Cloud POS

The deployment package for CSU can be created by consuming the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** package.

Follow these steps to create the package.

1. In Microsoft Visual Studio 2017, create a new C\# class library project where the **Target framework** property is set to **.NET Standard 2.0**. Rename the project **ScaleUnit**.
2. Delete the **Class1.cs** file that was generated.
3. Add the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** NuGet package to the project as a dependency.
4. Select the version of the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** NuGet package that matches your SDK/application version. Use the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** package from `https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json`. You can add the package source location to the **nuget.config** file of your extension project file.
5. Add the **POS.Extension** project to the **ScaleUnit** project as a project reference.
6. Compile and build the project. The output of the project contains the CSU deployment package as a zip file.

> [!NOTE]
> If you have Commerce runtime (CRT) or Retail Server extensions, or a database extension, you must add all these extension projects to the **ScaleUnit** project as references. A combined deployment package is then generated that contains all your extensions.

To deploy the package, follow the steps in [Deploy the package to CSU](../retail-sdk/retail-sdk-packaging.md#deploy-the-package-to-csu).

## Packaging for CSU – Self hosted Cloud POS

The deployment package for CSU can be created by consuming the **Microsoft.Dynamics.Commerce.Sdk.Installers.ScaleUnit** package.

1. In Visual Studio 2017, create a new console application (.NET Core), and name it **ScaleUnit.Installer**.
2. Edit the .proj file, and change the target framework to the Microsoft .NET Framework version 4.6.1, as shown in the following XML.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>net461</TargetFramework>
        </PropertyGroup>
    </Project>
    ```

3. Delete the **Program.cs** file that was generated.
4. Add a reference to the Installer SDK NuGet Package.

    1. In Solution Explorer, select and hold (or right-click) the project, and then select **Manage NuGet packages**.
    2. In the **NuGet Package Manager** window, on the **Browse** tab, search for **Microsoft.Dynamics.Commerce.Sdk.Installers.ScaleUnit**.
    3. Select the package, and then select **Install**.
    4. Select the version that matches your go-live version.

5. Add a reference from the **ScaleUnit.Installer** project to the **POS.Extension** project that you created earlier.

    1. In Solution Explorer, select and hold (or right-click) the **ScaleUnit.Installer** project, select **Add**, and then select **Reference**.
    2. In Reference Manager, on the **Projects** tab on the left, select the **POS.Extension** project that you created earlier.

6. Add the **Extension.Config** file to the project.

    1. Select and hold (or right-click) the project, select **Add**, and then select **New Item**.
    2. Select **Application Configuration File**.
    3. Name the file **Extension.Config**, and add it.

7. Update the **Extension.Config** file with the CRT extensions, as shown in the following XML. If you don't have any CRT extensions, leave the **composition** section empty.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <commerceRuntimeExtensions>
        <composition>
            <add source="assembly" value="CommerceRuntime" />
        </composition>
    ```

8. Compile and build the project. The output of this project contains the .exe file for the **ScaleUnit** installer.
9. To manually install the extension, open Windows PowerShell in administrator mode, go to the extension installer folder, and run the **install** command.

    ```powershell
    PS C:\ModernPos.Installer\bin\Debug\net461> .\ScaleUnit.Installer.exe install
    ```

    To uninstall the extension, run the following command.

    ```powershell
    PS C:\ModernPos.Installer\bin\Debug\net461> .\ScaleUnit.Installer.exe
    ```

    > [!NOTE]
    > Before you install the extension installer, install the sealed **ScaleUnit** package. If you have CRT or Retail Server extensions, or a database extension, you must add all these extension projects to the **ScaleUnit.Installer** project as references. A combined deployment package is then generated that contains all your extensions.
    >
    > You can also create multiple Scale Unit installers, based on the extensions, and manage them separately. You don't have to combine all the extensions in one package.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
