---
title: Create a Store Commerce extension installer package
description: This article describes how to create a Microsoft Dynamics 365 Commerce Store Commerce extension installer package.
author: josaw1
ms.date: 10/29/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2022-03-30
ms.custom: 
  - bap-template
---

# Create a Store Commerce extension installer package

[!include [banner](../includes/banner.md)]

This article describes how to create a Microsoft Dynamics 365 Commerce Store Commerce extension installer package.

> [!NOTE]
> You can find the full code samples in the [Store Commerce Extension samples GitHub repository (repo)](https://github.com/microsoft/Dynamics365Commerce.InStore).

To create the extension installer for Store Commerce extension, follow these steps.

1. In Microsoft Visual Studio 2022, create a new .NET console application project named "StoreCommerce.ExtInstaller". For **Framework**, select **.NET 7.0 (Standard Term Support)**.
1. In the **.proj** file, change the target framework to the .NET Framework version 4.7.2, as shown in the following XML example.

    ```XML
    <Project Sdk="Microsoft.NET.Sdk">
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>net472</TargetFramework>
        </PropertyGroup>
    </Project>
    ```

1. Delete the **Program.cs** file that was generated.
1. Add a reference to the **Microsoft.Dynamics.Commerce.Sdk.Installers.StoreCommerce** NuGet package:

    1. In Solution Explorer, right-click the project, and then select **Manage NuGet packages**.
    1. In the **NuGet Package Manager** window, on the **Browse** tab, search for **Microsoft.Dynamics.Commerce.Sdk.Installers.StoreCommerce**.
    1. Select the package, and then select **Install**.
    1. Select the version that matches your go-live version.

1. Add a reference to the Store Commerce extension .csproj projects, Commerce runtime (CRT), and database script project extensions:

    1. In Solution Explorer, right-click the project, and then select **Add \> Reference**.
    1. In Reference Manager, on the **Projects** tab on the left, select the extension project that you created earlier.

1. Compile and build the project. The output of this project will contain the Store Commerce extension installer. When you select the **F5** key and build the project, the installer will automatically be deployed.
1. To manually install the extension, open Windows PowerShell in administrator mode, go to the extension installer folder, and run the following **install** command.

    ```PowerShell
    PS C:\StoreCommerce.ExtInstaller\bin\Debug\net472> .\ StoreCommerce.ExtInstaller.exe install
    ```

    > [!NOTE]
    > Before you install the extension installer, install the Store Commerce app.

    To uninstall the extension, run the following **uninstall** command.

    ```PowerShell
    PS C:\StoreCommerce.ExtInstaller\bin\Debug\net472> .\ StoreCommerce.ExtInstaller.exe uninstall
    ```

1. After you've finished installing the extension, close Store Commerce if it's running. Then, to load the extension, open Store Commerce by using the Store Commerce shortcut on the desktop.

> [!NOTE]
> Code signing isn't a strict requirement for the Store Commerce extension installer like it was for Modern POS (MPOS), but Microsoft recommends using code signing to verify the authenticity of any executable run on POS registers. You can configure your Azure DevOps pipeline to use the [Trusted Signing - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.TrustedSigning) task to digitally sign your files using a Trusted Signing certificate during an Azure Pipelines run.

## Sample code

```XML
<Project Sdk="Microsoft.NET.Sdk">
    <Import Project="..\CustomizationPackage.props " />
    <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFramework>net472</TargetFramework>
    </PropertyGroup>
    <ItemGroup>
        <PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Installers.StoreCommerce" Version="$(CommerceSdkPackagesVersion)" />
    </ItemGroup>
    <ItemGroup>
        <ProjectReference Include="..\CommerceRuntime\Contoso.GasStationSample.CommerceRuntime.csproj">
            <ReferenceOutputAssembly>false</ReferenceOutputAssembly>
        </ProjectReference>
        <ProjectReference Include="..\Pos\Contoso.GasStationSample.Pos.csproj">
            <ReferenceOutputAssembly>false</ReferenceOutputAssembly>
        </ProjectReference>
    </ItemGroup>
    <ItemGroup>
        <!-- Settings included in the CommerceRuntimeExtensionSettings item group will be added to the generated CommerceRuntime config file and available at runtime in the CommerceRuntime extension. -->
        <CommerceRuntimeExtensionSettings Include="ext.Contoso.GasolineItemId">
            <Value>gasoline</Value>
        </CommerceRuntimeExtensionSettings>
    </ItemGroup>
</Project>
```
