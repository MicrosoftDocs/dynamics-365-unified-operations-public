---
title: Create a Store Commerce extension installer package
description: This topic describes how to create a Microsoft Dynamics 365 Commerce Store Commerce extension installer package.
author: mugunthanm
ms.date: 04/21/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Create a Store Commerce extension installer package

[!include [banner](../includes/banner.md)]

This topic describes how to create a Microsoft Dynamics 365 Commerce Store Commerce extension installer package.

> [!NOTE]
> You can find the full code samples in the [Store Commerce Extension samples GitHub repository (repo)](https://github.com/microsoft/Dynamics365Commerce.InStore).

To create the extension installer for Store Commerce extension, follow these steps.

1. In Microsoft Visual Studio 2017, create a new console application (.NET Core) that is named **StoreCommerce.ExtInstaller**.
1. In the **.proj** file, change the target framework to the .NET Framework version 4.6.1, as shown in the following XML example.

    ```XML
    <Project Sdk="Microsoft.NET.Sdk">
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>net461</TargetFramework>
        </PropertyGroup>
    </Project>
    ```

1. Delete the **Program.cs** file that was generated.
1. Add a reference to the **Microsoft.Dynamics.Commerce.Sdk.Installers.StoreCommerce** NuGet package:

    1. In Solution Explorer, select and hold (or right-click) the project, and then select **Manage NuGet packages**.
    1. In the **NuGet Package Manager** window, on the **Browse** tab, search for **Microsoft.Dynamics.Commerce.Sdk.Installers.StoreCommerce**.
    1. Select the package, and then select **Install**.
    1. Select the version that matches your go-live version.

1. Add a reference to the Store Commerce extension .csproj projects, Commerce runtime (CRT), and database script project extensions:

    1. In Solution Explorer, select and hold (or right-click) the project, and then select **Add \> Reference**.
    1. In Reference Manager, on the **Projects** tab on the left, select the extension project that you created earlier.

1. Compile and build the project. The output of this project will contain the Store Commerce extension installer. When you select the **F5** key and build the project, the installer will automatically be deployed.
1. To manually install the extension, open Windows PowerShell in administrator mode, go to the extension installer folder, and run the following **install** command.

    ```PowerShell
    PS C:\StoreCommerce.ExtInstaller\bin\Debug\net461> .\ StoreCommerce.ExtInstaller.exe install
    ```

    > [!NOTE]
    > Before you install the extension installer, install the Store Commerce app.

    To uninstall the extension, run the following **uninstall** command.

    ```PowerShell
    PS C:\StoreCommerce.ExtInstaller\bin\Debug\net461> .\ StoreCommerce.ExtInstaller.exe uninstall
    ```

1. After you've finished installing the extension, close Store Commerce if it's running. Then, to load the extension, open Store Commerce by using the Store Commerce shortcut on the desktop.

## Sample code

```XML
<Project Sdk="Microsoft.NET.Sdk">
    <Import Project="..\CustomizationPackage.props " />
    <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFramework>net461</TargetFramework>
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
