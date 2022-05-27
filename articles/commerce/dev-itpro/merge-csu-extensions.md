---
title: Merge Cloud Scale Unit extension packages for deployment
description: This topic describes how to merge Microsoft Dynamics 365 Commerce Cloud Scale Unit (CSU) extension packages for deployment.
author: mugunthanm
ms.date: 05/27/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Merge Cloud Scale Unit extension packages for deployment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes how to merge Microsoft Dynamics 365 Commerce Cloud Scale Unit (CSU) extension packages.

Extensions packages generated for CSU from independent software vendors (ISVs), partners, and customers must be merged into a single package before deploying to [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index). Currently, LCS doesn’t support deploying multiple extension packages. The last deployed extension package will override the previous extension deployment.

There are multiple options to merge a CSU extension package. In this topic we'll walk through how to merge CSU extension packages by generating a NuGet package for the ISV CSU extensions.

> [!NOTE]
> Extension package merging is not required for on-premises CSU deployments, Store Commerce, or shared Hardware Station. On-premises components supports multiple extension deployments.

## Scenario

Your tax ISV and payment ISV each gave you a CSU extension package, you have your own extension package, and now want to deploy all these packages.
Since LCS doesn't support deploying multiple packages, you must merge all of these packages into one package.

### Merge the packages by generating a NuGet package for the ISV extension

To merge the packages by generating a NuGet package for the ISV extension, follow these steps.

1. For the ISV extensions, ask the ISVs to generate NuGet packages for their CSU extensions.
1. Consume the ISV NuGet packages in your CSU packaging project by adding them as references to the project.
1. Build your CSU packaging project. The output CSU extension package will have the extensions from the ISVs and your extensions.

### Generate NuGet package for the ISVs extensions

If you have the ISV extension projects, to generate the NuGet package follow these steps (or ask your ISV to follow them).

1. Open the ISV extension CSU packaging project using Visual Studio Code or Visual Studio.
1. Edit the ISV CSU packaging project file and add the following build property to [generate the NuGet package on build](/nuget/create-packages/creating-a-package-msbuild#automatically-generate-package-on-build) in addition to the CSU extension package.

    ```XML
    <GeneratePackageOnBuild>true</GeneratePackageOnBuild>
    ```
        
1. Get the CSU extension NuGet package from your ISVs.

### Consume the NuGet package in your CSU extension package

To consume the NuGet package in your CSU extension package, follow these steps.

1. Before consuming the NuGet package from your ISV, set up the [package feed location](/nuget/hosting-packages/local-feeds) for your ISV CSU extension NuGet package in your **nuget.config** file using the following XML:

    ```XML
    <packageSources>
          <add key="local" value="packages" />
    </packageSources>
    ```

1. Open your extension CSU packaging project using Visual Studio Code or Visual Studio.
1. Edit the project file and add the CSU extension NuGet package received from your ISV as a reference in your CSU extension packaging project, as shown in the following example:

    ```XML
    <PackageReference Include="Contoso.Extension.Sample.Package" Version="2.0.*” />
    ```
    You can specify the exact package version or use wildcards to pick up the updated version if available. If there are multiple ISV NuGet packages, repeat step 3 as required.

1. Build the CSU packaging project. The output CSU extension package will have the extensions from the ISVs and your extensions.

For more information on CSU extension package generation and deployment, see [Create a Cloud Scale Unit extension package](csu-packaging.md).
