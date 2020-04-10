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

![include](banner.md)

## What’s changed in 10.0.11

-   Commerce SDK updated to Visual Studio 2017.
-   References updated to PackageReference (NuGet package reference).

## Retail SDK updated to support Visual Studio 2017

Retail SDK updated to VS 2017. From 10.0.11 all Retail SDK components (MPOS, CPOS, Commerce Runtime (CRT) RS, Proxy and Hardware station (HWS) can be built and compiled only in VS 2017, it will not work anymore in VS 2015.

## References updated to PackageReference

The Retail SDK reference libraries are updated to project PackageReference. All the SDK samples are updated to use the PackageReference model. All the SDK reference libraries are converted to NuGet packages, libraries are removed from the RetailSDK\\Reference folder. **All the NuGet packages can be found in the ..\\RetailSDK\\Code\\pkgs or ..\\RetailSDK\\pkgs**.

### Example

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" />
</ItemGroup>
```

## What’s impacted

- Extension built based on the older SDK needs to be migrated to the new SDK using VS 2017, no code change would be required and this steps is required only when you have extension and want to deploy a new merged package (Extension + OOB changes) with version 10.0.11 or greater.
- Hard reference in extension project must be migrated to PackageReference (NuGet reference).


### How to Migrate to the SDK for Visual Studio 2017

There arew two ways to migrate:
- Deploy a new development and build environment from LCS with VS 2017 template.
- Update extensions to VS 2017 in the development environent:
    - Install VS 2017 developer, professional or enterprise edition in the existing build and dev VM.
    - If manually install VS 2017, please also install the below prerequisites in the dev VM or else the compilation will fail with .NET SDK and runtime errors:
        + [https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-2.1.202-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-2.1.202-windows-x64-installer)
        + [https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-2.1.513-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-2.1.513-windows-x64-installer)
        + [https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-2.0.9-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-2.0.9-windows-x64-installer)
        + [https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-2.1.17-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-2.1.17-windows-x64-installer)
        + http://download.microsoft.com/download/6/D/8/6D8381B0-03C1-4BD2-AE65-30FF0A4C62DA/TS-2.2-dev14update3-20170321.1/TypeScript_Dev14Full.exe


## Build the OOB SDK:

-   Open the Developer command prompt for VS 2017 or msbuild 15.0 command prompt and build the OOB Retail SDK by running msbuild /t:rebuild from the root of the SDK folder where you can find the dirs.proj. (Mostly it will be RetailSDK\\dirs.proj or RetailSDK\\Code\\dirs.proj)

-   Merge your extension to the new SDK folder. Detailed documentation on how to merge extension with the new SDK can be found [here](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retailsdk-update).

-   After merging the extensions update all the hard-coded reference to PackageReferene using the NuGet packages.

**How to update the reference in the Commerce Runtime (CRT)extensions project:**

1.  Open the CRT extension project in VS 2017.

2.  Add local NuGet repository folder in the NuGet Package Manager.

    Note: All the SDK reference libraries are converted to NuGet packages, libraries are removed from the RetailSDK\\Reference folder. **All the NuGet packages can be found in the ..\\RetailSDK\\Code\\pkgs or ..\\RetailSDK\\pkgs**.

    To create a local NuGet repository follow the steps mentioned in this [documentation](https://docs.microsoft.com/en-us/nuget/consume-packages/install-use-packages-visual-studio#package-sources).

3.  To add the NuGet Package reference to the project, right click the Dependencies node in the project and select **Manage NuGet Packages**.

4.  In the NuGet Package Manager window add the required packages.

**Ex:** If the project need the Commerce runtime library reference add the Microsoft.Dynamics.Commerce.Runtime NuGet package.

After adding the NuGet package reference, the project file will be updated with the package reference.
```
<ItemGroup>
  <PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" />
</ItemGroup>
```
**Note:** PackageReference also support floating versions, update the version with floating version number. To know more details about the floating versions check this [documentation](https://docs.microsoft.com/en-us/nuget/concepts/dependency-resolution#floating-versions). With the floating version, extensions no need to update the reference with every update, NuGet will automatically resolve to the latest version.

Ex:

```
<PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" />

```

**Similarly update the reference for all the Retail server, Proxy and Hardware station extension project.**

**What’s not impacted:**

   -   It’s not required to change the extensions code written in previous version of SDK, only update of reference and recompilation is required with the new SDK.
   
   - Existing Azure DevOps pipeline set up for Retail SDK build will continue to work. If required in the MSBuild task step change the msbuild version to 15.0
