---
# required metadata

title: Migrate the Retail SDK from Visual Studio 2015 to Visual Studio 2017
description: This topic explains how to migrate the Retail SDK to Visual Studio 2017 and update the reference to NuGet.
author: mugunthanm 
manager: AnnBe
ms.date: 08/14/2020
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

[!include [banner](../../includes/banner.md)]

This topic explains what has changed in the 10.0.11 release of the Retail software development kit (SDK), how to migrate it to Visual Studio 2017, and how to update an extension project reference library to NuGet.

## What has changed in the 10.0.11 release

- The Retail SDK has been updated to Visual Studio 2017.
- References have been updated to PackageReference (NuGet package reference).

## Retail SDK updated to support Visual Studio 2017

The Retail SDK now runs on Visual Studio 2017. In release 10.0.11 and later, all Retail SDK components, including Modern POS (MPOS), Cloud POS (CPOS), the Commerce runtime (CRT), Retail Server, the proxy, and Hardware station (HWS), can be built and compiled only in Visual Studio 2017. You can't use Visual Studio 2015.

## References updated to PackageReference

The Retail SDK reference libraries use PackageReference. All the SDK samples use the PackageReference model. All the SDK reference libraries are converted to NuGet packages, and libraries are removed from the RetailSDK\\Reference folder. The NuGet packages are in the **..\\RetailSDK\\Code\\pkgs** or **..\\RetailSDK\\pkgs** folder. The following example shows the reference to **Microsoft.Dynamics.Commerce.Runtime**.

```xml
<ItemGroup>
    <PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" />
</ItemGroup>
```

## What is affected

- If you want to deploy a new merged package (that is, an extension and out-of-box changes) on version 10.0.11 or later, you must migrate your solution to the SDK on Visual Studio 2017. No code changes are required to migrate and build your solution.
- Hard-coded references in extension projects must be migrated to PackageReference (NuGet reference).

### Migrate to the SDK for Visual Studio 2017

There are two ways to migrate:

- Deploy a new development and build environment from Microsoft Dynamics Lifecycle Service (LCS), and manually install the Visual Studio 2017. LCS developer VM with Visual Studio 2017 will be available in a future release.
- Update extensions to Visual Studio 2017 in an existing development environment:

    - Install Visual Studio 2017 Community, Professional, or Enterprise edition on the existing build and development virtual machine (VM) with the following workloads:
    
        - .NET Desktop development
        - Universal Windows Platform development
        - ASP.NET and web development
        - Azure development
        - Node.js development
        - .NET Core cross-platform development
        - Mobile development with .NET (required for hybrid app development)
    
    - If you manually install Visual Studio 2017, install the following prerequisites on the development VM. If you don't install these prerequisites, compilation will fail, and .NET SDK and runtime errors will be generated:

        + [sdk-2.1.202-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-2.1.202-windows-x64-installer)
        + [sdk-2.1.513-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/sdk-2.1.513-windows-x64-installer)
        + [runtime-2.0.9-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-2.0.9-windows-x64-installer)
        + [runtime-2.1.17-windows-x64-installer](https://dotnet.microsoft.com/download/dotnet-core/thank-you/runtime-2.1.17-windows-x64-installer)
        + Install Typescript version 2.2.2. In Visual Studio, go to **Tools > Get Tools and Features**. Select the **Individual components** tab and select the **TypeScript 2.2 SDK from SDKs, libraries, and frameworks** section and install it. VS 2017 has Typescript 3.1 as default, please include 2.2.2 also because the POS app is built based on Typescript 2.2.2.

## Build the Retail SDK

Follow these steps to build the Retail SDK.

1. Open the Developer command prompt for Visual Studio 2017 or the MSBuild 15.0 command prompt. Build the out-of-box Retail SDK by running **msbuild /t:rebuild** from the root of the SDK folder (where you can find the dirs.proj file). The folder is **RetailSDK\\dirs.proj** or **RetailSDK\\Code\\dirs.proj** in most installations.
2. Merge your extension to the new SDK folder. For information about how to merge extension with the SDK, see [Upgrade the Retail channel extension to the latest Retail SDK](../retailsdk-update.md).
3. After the extensions have been merged, update all the hard-coded references to PackageReference by using the NuGet packages.

## Update the reference in the CRT and Retail Server extension projects

1. Open the CRT extension project in Visual Studio 2017.
2. In the NuGet Package Manager, add the local NuGet repository folder. For information about how to create a local NuGet repository, see [Install and manage packages in Visual Studio using the NuGet Package Manager](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio#package-sources).

    > [!NOTE]
    > All the SDK reference libraries are converted to NuGet packages, and libraries are removed from the RetailSDK\\Reference folder. The NuGet packages can be found in the **..\\RetailSDK\\Code\\pkgs** or **..\\RetailSDK\\pkgs** folder.

3. To add the NuGet package reference to the project, right-click the **Dependencies** node in the project, and then select **Manage NuGet Packages**.
4. In the NuGet Package Manager, add the required packages. For example, if the project requires the CRT library reference, add the **Microsoft.Dynamics.Commerce.Runtime** NuGet package. After the NuGet package reference is added, the project file will be updated with the package reference, as shown in the following example.

    ```xml
    <ItemGroup>
        <PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" />
    </ItemGroup>
    ```

> [!NOTE]
> PackageReference also supports floating versions, where the version is updated with the floating version number. For more information about floating versions, see [How NuGet resolves package dependencies](https://docs.microsoft.com/nuget/concepts/dependency-resolution#floating-versions). When the floating version is used, extensions no longer have to update the reference for every update, because NuGet will automatically resolve to the latest version. For example, the package reference might resemble **\<PackageReference Include="Microsoft.Dynamics.Commerce.Runtime" Version="9.21.x" /\>**.

In a similar way, update the references for all the Retail Server, proxy, and Hardware station extension projects. 

### Retail Server and Proxy extensions

Migrate the Retail Server and Proxy extensions to the new extension model released in version 10.0.12. Starting in version 10.0.12, the same Retail Server extension library can be used for offline use, no separate C# proxy library is needed, however a client typescript proxy is still required. For more information, see [Create a new Retail Server extension API](../retail-server-icontroller-extension.md). This step is recommended but not required, as the Retail Server and proxy extension libraries will continue to work until the old extension model is deprecated.

## What isn't affected

You don't have to change the extensions code that was written in previous versions of the Retail SDK. You must update references and recompile only for the new SDK.

If you have existing pipelines in Azure Pipelines not based on build machine agent that are set up for the Retail SDK build will continue to work. In the MSBuild task step, change the MSBuild version to 15.0, if this change is required.

Follow the steps to set up a build pipeline in Azure DevOps without using build VM and build agent from the build machine. For more information, see [Set up Commerce SDK build pipeline](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/retail-sdk/sdk-build-pipeline).

## Azure DevOps pipeline using build machine agent

The same build machine used for MSBuild  with the Azure DevOps pipeline can be used with SDK version 10.0.11. Perform the following steps on the build machine for the SDK:

1. Install Visual Studio 2017 on the build machine.
2. Optionally, run msbuild (msbuild version 15.0) from the developer command prompt for Visual Studio 2017 on the build machine. Open the developer command prompt for Visual Studio 2017 and navigate to the Retail SDK root folder. Type *msbuild dirs.proj* and make sure that the MSBuild completes successfully. 
3. On the build machine, add an environment variable for the MSBuild 15.0. Go to **System Properties > Environment Variables > System variables**. Select the **Path** variable, and then select **Edit**. In the **Edit environment variable** window, select **New** and add the path variable for MSBuild 15.0. Move it to the top of the list of PATH variables. For example, the path will be something like - C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild\15.0\Bin\. The path will change based on where you installed Visual Studio 2017. To get the path for MSBuild from the developer command prompt for Visual Studio 2017, type **where MSBuild**. 
- To validate the config information
  +  Open a regular "CMD" window (not the Visual Studio command prompt).
  +  Run **where MSBuild**.
  +  The first result in the list should be: C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild\15.0\Bin\MSBuild.exe.
         
4. Restart the Azure DevOps build agent on the build machine.
5. In Azure DevOps pipeline, change the MSBuild version to 15.0 or later.

If the build from Azure DevOps pipeline fails with a NuGet error, the Azure pipeline may not be not using MSBuild version 15.0 for NuGet restore or the extension projects are not upgraded to use the package reference model.
