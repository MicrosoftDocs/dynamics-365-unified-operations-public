---
# required metadata

title: Migrate the Retail SDK from Visual Studio 2015 to Visual Studio 2017
description: This topic explains how to migrate the Retail SDK to Visual Studio 2017 and update the reference to NuGet.
author: mugunthanm 
manager: AnnBe
ms.date: 04/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-04-10
ms.dyn365.ops.version: 10.0.11
---

# Migrate the Retail SDK from Visual Studio 2015 to Visual Studio 2017

This topic explains what’s changed in the Retail SDK 10.0.11 release, how to migrate to Visual Studio 2017, and how to update an extension project reference library to NuGet.

[!include [banner](../../includes/banner.md)]

## What’s changed in 10.0.11

- Commerce SDK updated to Visual Studio 2017.
- References updated to PackageReference (NuGet package reference).

## Retail SDK updated to support Visual Studio 2017

Retail SDK now runs on Visual Studio 2017. With release 10.0.11 and later, all Retail SDK components, including MPOS, CPOS, Commerce Runtime (CRT) RS, Proxy, and Hardware station (HWS), can be built and compiled only in Visual Studio 2017. You can't use Visual Studio 2015.

## References updated to PackageReference

The Retail SDK reference libraries project PackageReference. All the SDK samples use the PackageReference model. All the SDK reference libraries are converted to NuGet packages, libraries are removed from the RetailSDK\\Reference folder. The NuGet packages are in the **..\\RetailSDK\\Code\\pkgs or ..\\RetailSDK\\pkgs** folder. The following example shows the reference to **Microsoft.Dynamics.Commerce.Runtime**:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" />
</ItemGroup>
```

## What’s affected

- If you want to deploy a new merged package, that is, an extension and out-of-box changes, on version 10.0.11 or later, then you must migrate your solution to the SDK on Visual Studio 2017. No code changes are required to migrate and build your solution.
- Hard-coded references in extension projects must be migrated to PackageReference (NuGet reference).

### How to Migrate to the SDK for Visual Studio 2017

There are two ways to migrate:
- Deploy a new development and build environment from LCS, and use the Visual Studio 2017 template.
- Update extensions to Visual Studio 2017 in the development environment:
    - Install Visual Studio 2017 Community, Professional, or Enterprise edition in the existing build and development VM.
    - If you manually install Visual Studio 2017, install the following prerequisites in the development VM. If you don't install these prerequisites, then compilation will fail, generating .NET SDK and runtime errors:
        + [sdk-2.1.202-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-2.1.202-windows-x64-installer)
        + [sdk-2.1.513-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-2.1.513-windows-x64-installer)
        + [runtime-2.0.9-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-2.0.9-windows-x64-installer)
        + [runtime-2.1.17-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-2.1.17-windows-x64-installer)
        + [TypeScript_Dev14Full](https://download.microsoft.com/download/6/D/8/6D8381B0-03C1-4BD2-AE65-30FF0A4C62DA/TS-2.2-dev14update3-20170321.1/TypeScript_Dev14Full.exe)


## Build the Retail SDK

Follow these steps to build the Retail SDK:

1. Open the Developer command prompt for Visual Studio 2017 or the msbuild 15.0 command prompt. Build the out-of-box Retail SDK by running `msbuild /t:rebuild` from the root of the SDK folder (where you can find the dirs.proj file). The folder is  **RetailSDK\\dirs.proj** or **RetailSDK\\Code\\dirs.proj** in most installations.
2. Merge your extension to the new SDK folder. For information about how to merge extension with the SDK, [Upgrade the Retail channel extension to the latest Retail SDK](../retailsdk-update.md).
3. After merging the extensions, update all the hard-coded reference to PackageReferene using the NuGet packages.

## How to update the reference in the Commerce Runtime (CRT) extensions project

1. Open the CRT extension project in Visual Studio 2017.
2. Add the local NuGet repository folder in the NuGet Package Manager. For information about how to create a local NuGet repository, see [Install and manage packages in Visual Studio using the NuGet Package Manager](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio#package-sources). 

    > [!NOTE]
    > All the SDK reference libraries are converted to NuGet packages, and libraries are removed from the **RetailSDK\\Reference** folder. The NuGet packages can be found in the **..\\RetailSDK\\Code\\pkgs** or **..\\RetailSDK\\pkgs** folder.

3. To add the NuGet Package reference to the project, right-click the **Dependencies** node in the project and select **Manage NuGet Packages**.
4.  In the NuGet Package Manager window, add the required packages. For example, if the project needs the Commerce runtime library reference, then add the **Microsoft.Dynamics.Commerce.Runtime** NuGet package. After adding the NuGet package reference, the project file will be updated with the package reference, as shown in the following example:
    ```xml
    <ItemGroup>
      <PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" />
    </ItemGroup>
    ```

> [!NOTE]
> PackageReference also supports floating versions, updating the version with floating version number. For more information about floating versions, see [How NuGet resolves package dependencies](https://docs.microsoft.com/nuget/concepts/dependency-resolution#floating-versions). With the floating version, extensions no longer need to update the reference with every update, because NuGet will automatically resolve to the latest version. For example, the PackageReference would look like `<PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" />`.

Similarly, you would update the references for all the Retail server, Proxy, and Hardware station extension projects.

## What’s not affected

You don't have to change the extensions code written in previous versions of the Retail SDK, updating references and recompiling is required only with the new SDK.
   
Existing Azure Pipelines set up for Retail SDK build will continue to work. If required in the MSBuild task step, change the msbuild version to 15.0.
