---
title: Merge Cloud Scale Unit Extensions packages
description: This document explains how to merge Commerce cloud Scale Unit (CSU) extensions.
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

# Merge Cloud Scale Unit Extensions packages from ISVs, partners, or Customers for cloud deployments

[!include [banner](../includes/banner.md)]

This document explains how to merge Commerce cloud Scale Unit (CSU) extensions deployed to CSU from [Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index).
Extension packages generated for Commerce cloud Scale Unit (CSU) from ISVs, partners and customers must be merged into single package before deploying to LCS, Currently the LCS doesn’t support deploying multiple extension packages, the last deployed extension package will override the previous extension deployment.

There are multiple options to merge the CSU extension package, in this document we will walkthrough how to merge the CSU extensions by generating NuGet package for the ISVs CSU extensions.

> [!NOTE]
> Extension package merge is not required for On-premises Scale Unit deployments and Store Commerce, Shared Hardware Station. On-premises components supports multiple extension deployments.

### Scenario:
Your Tax ISV and Payment ISV gave you a CSU extension package, and you have your own extension package and now you want to deploy all these packages.
Since LCS doesn’t support deploying multiple packages, you must merge all these packages into one package.

## Merge the packages by generating NuGet package for the ISV extension
1.	For the ISV extensions, ask the ISVs to generate NuGet package for their CSU extensions
2.	Consume the ISVs NuGet packages in your Scale Unit packaging project by adding it as references to the project.
3.	Build your Scale Unit packaging project. The output CSU extension package generated will have the extensions from the ISVs and your extensions.

## Detailed steps:
**Generate NuGet package for the ISVs extensions**

If you have the ISV extension projects, then you can perform the steps below or ask your ISV to follow the below steps to generate the NuGet package.
1.	Open the ISVs extension Scale Unit packaging project using Visual Studio Code or Visual Studio
2.	Edit the ISVs Scale Unit packaging project file and add the below build property to [generate the NuGet package on build]( https://docs.microsoft.com/en-us/nuget/create-packages/creating-a-package-msbuild#automatically-generate-package-on-build) in addition to the Scale Unit extension package.

        ```
        <GeneratePackageOnBuild>true</GeneratePackageOnBuild>
        ```

3.	Get the CSU extension NuGet package from your ISVs.

### Consume the NuGet package in your CSU extension package
Before consuming the NuGet package from your ISV, set up the [package feed location]( https://docs.microsoft.com/en-us/nuget/hosting-packages/local-feeds)  for your ISV CSU extension NuGet package in your nuget.config file
    ```
    <packageSources>
          <add key="local" value="packages" />
      </packageSources>
    ```
1.	Open your extension Scale Unit packaging project using Visual Studio Code or Visual Studio
2.	Edit the project file and add the CSU extension NuGet package received from your ISV as reference to your Scale Unit extension packaging project 

    ```
    <PackageReference Include="Contoso.Extension.Sample.Package" Version="2.0.*” />
    ```
    You can specify the exact package version or use wildcards to pick up the updated version if available. 

3.	Build the Scale Unit packaging project. The output CSU extension package generated will have the extensions from the ISVs and your extensions.

For more information on CSU extension package generation and deployment refer [Create a Cloud Scale Unit extension package]( https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/csu-packaging)
