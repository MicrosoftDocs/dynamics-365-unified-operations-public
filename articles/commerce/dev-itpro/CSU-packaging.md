---
title: Create a Cloud Scale Unit extension package
description: This article describes how to create an extension package for Microsoft Dynamics 365 Commerce Cloud Scale Unit (CSU).
author: josaw1
ms.date: 02/17/2023
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-03-30
ms.dyn365.ops.version: AX 10.0.25
---

# Create a Cloud Scale Unit extension package

[!include [banner](../includes/banner.md)]

This article describes how to create an extension package for Microsoft Dynamics 365 Commerce Cloud Scale Unit (CSU). 

>[!NOTE]
>Removing Reply URLs or Service Principals will break operations related to AAD in Store Commerce in the browser.

A CSU extension package contains the extension code for the following components:

- Commerce runtime (CRT) and Headless Commerce application programming interfaces (APIs)
- Channel database extension scripts
- Payment connector
- Store Commerce for web

## Create a CSU package

To create a CSU package, choose one of the following options, and follow the steps.

### Option 1: Download the sample scale unit packaging project from GitHub

1. Clone or download the scale unit packaging project from [Dynamics365 Commerce ScaleUnit Samples](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit). Select the correct release branch version for your software development kit (SDK)/application release. For detailed information about how to clone a project, see [Download Retail SDK samples and reference packages from GitHub and NuGet](retail-sdk/sdk-github.md).
1. Add the extension CRT, Retail Server, channel database, Payment, and Store Commerce for web extension projects as a project reference to the scale unit packaging project.
1. If the CRT, Retail Server, or Payment extension depends on any assemblies or packages to run, include those assemblies as a project reference in the extension project. The packaging will include these assemblies in the **ext** folder. Don't add the dependent assemblies to the **CommerceRuntime.Ext.config** file, because that approach might cause runtime errors.
1. If you must include any configuration or setting values in the **CommerceRuntime.Ext.config** file, edit the scale unit packaging project file, and add the **CommerceRuntimeExtensionSettings** property, as shown in the following example.

    ```XML
    <CommerceRuntimeExtensionSettings Include="ext.YourKeyName">
        <Value>samplevalue</Value>
    </CommerceRuntimeExtensionSettings>
    ```

1. Build the scale unit project. The project will generate the **CloudScaleUnitExtensionPackage.zip** output package in the project bin output folder. The **CloudScaleUnitExtensionPackage.zip** package can then be uploaded to Microsoft Dynamics Lifecycle Services (LCS) and deployed to CSU. In the Visual Studio NuGet package manager, select the correct **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** NuGet version for your SDK/application version.

### Option 2: Create a new scale unit packaging project

1. Create a new C\# class library project where the target framework is .NET Standard 2.0.
1. Add the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** NuGet package as a dependency to the project. Select the correct **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** NuGet version for your SDK/application version.
1. Consume the **Microsoft.Dynamics.Commerce.Sdk.ScaleUnit** package from [https://pkgs.dev.azure.com/commerce-partner/Registry/\_packaging/dynamics365-commerce/nuget/v3/index.json](https://pkgs.dev.azure.com/commerce-partner/Registry/\_packaging/dynamics365-commerce/nuget/v3/index.json). You can add the package source location in the **nuget.config** file of your extension project file, as shown in the following example.

    ```xml
    <packageSources>
        <add key="dynamics365-commerce" value="https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json" />
        <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />
        </packageSources>
    ```

1. Add the extension CRT, Retail Server, channel database, Payment, and Store Commerce for web extension projects as a project reference to the CSU packaging project.
1. If the CRT, Retail Server, or Payment extension depends on any assemblies to run, include those assemblies as a project reference in the extension project. The packaging will include these assemblies in the **ext** folder. Don't add the dependent assemblies to the **CommerceRuntime.Ext.config** file, because that approach might cause runtime errors.
2. If you must include any configuration or setting values in the **CommerceRuntime.Ext.config** file, edit the CSU packaging project file, and add the **CommerceRuntimeExtensionSettings** property, as shown in the following example.
 
    ```XML
    <CommerceRuntimeExtensionSettings Include="ext.YourKeyName">
        <Value>samplevalue</Value>
    </CommerceRuntimeExtensionSettings>
    ```

1. Build the scale unit project. The project will generate the **CloudScaleUnitExtensionPackage.zip** output package in the project bin output folder. The **CloudScaleUnitExtensionPackage.zip** package can then be uploaded to LCS and deployed to CSU.

The CRT extension configuration file (**Web.Config**) is generated by the scale unit packaging project. You don't have to manually create the extension configuration files.

## Deploy the package to CSU

To deploy the package to CSU, follow these steps.

1. Sign in to [LCS](https://lcs.dynamics.com/v2), and open a project.
1. Select the **Menu** button (sometimes referred to as the hamburger menu or hamburger button), and then select **Asset library**.
1. Select **Commerce Cloud Scale Unit Extension** as the asset type, and then select the plus sign (**+**) button to upload the package.
1. Enter a name and description for the package, and then add the package file by selecting **Add file**.
1. After the upload is completed, select **Confirm** to complete the upload process.

    LCS validates the package. This validation will take a few minutes.

1. After the validation is completed, mark the package as **Release candidate**.
1. After the package is uploaded, you must deploy it to the environment. For more information, follow the steps in [Apply updates and extensions to Commerce Scale Unit (cloud)](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md).
