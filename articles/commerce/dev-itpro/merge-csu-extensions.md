---
title: Merge Cloud Scale Unit extension packages for deployment
description: This article describes how to merge Microsoft Dynamics 365 Commerce Cloud Scale Unit (CSU) extension packages for deployment.
author: mugunthanm
ms.date: 06/01/2022
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

This article describes how to merge Microsoft Dynamics 365 Commerce Cloud Scale Unit (CSU) extension packages.

Extensions packages that independent software vendors (ISVs), partners, and customers generate for CSU must be merged into a single package before they are deployed to [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index). Currently, LCS doesn't support the deployment of multiple extension packages. The last extension package that is deployed will override the previous extension deployment.

There are multiple options for merging CSU extension packages. This article guides you through the process of merging them by generating a NuGet package for ISV CSU extensions.

> [!NOTE]
> Extension package merging isn't required for on-premises CSU deployments, Store Commerce, or shared Hardware Station. On-premises components support multiple extension deployments.

## Scenario

Both your tax ISV and your payment ISV gave you a CSU extension package, you have your own extension package, and you now want to deploy all the packages. Because LCS doesn't support the deployment of multiple packages, you must merge all the packages into one package.

### Merge the packages by generating a NuGet package for the ISV extensions

To merge the packages by generating a NuGet package for the ISV extensions, follow these steps.

1. Ask the ISVs to generate NuGet packages for their CSU extensions.
1. Consume the ISV NuGet packages in your CSU packaging project by adding them as references to the project.
1. Build your CSU packaging project. The output CSU extension package will have the extensions from the ISVs and your extensions.

### Generate a NuGet package for the ISVs extensions

If you have the ISV extension projects, follow these steps to generate the NuGet package. Alternatively, ask your ISVs to follow them.

1. Open the ISV extension CSU packaging project in Visual Studio Code or Visual Studio.
1. Edit the ISV CSU packaging project file, and add the following build property to [generate the NuGet package on build](/nuget/create-packages/creating-a-package-msbuild#automatically-generate-package-on-build) in addition generating to the CSU extension package.

    ```XML
    <GeneratePackageOnBuild>true</GeneratePackageOnBuild>
    ```

1. Get the CSU extension NuGet packages from your ISVs.

### Consume the NuGet package in your CSU extension package

To consume the NuGet package in your CSU extension package, follow these steps.

1. Before you consume the NuGet package from your ISV, set up the [package feed location](/nuget/hosting-packages/local-feeds) for your ISV CSU extension NuGet package in your **nuget.config** file by using the following XML.

    ```XML
    <packageSources>
        <add key="local" value="packages" />
    </packageSources>
    ```

1. Open your extension CSU packaging project in Visual Studio Code or Visual Studio.
1. Edit the project file, and add the CSU extension NuGet package that you received from your ISV as a reference in your CSU extension packaging project, as shown in the following example.

    ```XML
    <PackageReference Include="Contoso.Extension.Sample.Package" Version="2.0.*" />
    ```

    You can specify the exact package version, or you can use wildcards to pick up the updated version if it's available. If there are multiple ISV NuGet packages, repeat step 3 as required.

1. Build the CSU packaging project. The output CSU extension package will have the extensions from the ISVs and your extensions.

For more information about how to generate and deploy CSU extension packages, see [Create a Cloud Scale Unit extension package](csu-packaging.md).
