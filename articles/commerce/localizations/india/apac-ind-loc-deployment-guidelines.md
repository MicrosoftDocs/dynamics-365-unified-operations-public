---
title: Deployment guidelines for cash registers for India
description: This article is a deployment guide for the Commerce localization for India.
author: EvgenyPopovMBS
ms.date: 04/13/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: India
ms.author: josaw
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: 7.3.1
ms.search.industry: Retail
---
# Deployment guidelines for cash registers for India

[!include [banner](../../../finance/includes/banner.md)]

This article is a deployment guide that shows how to enable the requirements for Goods and Services Tax (GST) in the Dynamics 365 Commerce app's localization for India. For more information about the localization for India, see [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md).

> [!WARNING]
> The steps described in this article are applicable only to the legacy implementation of the GST integration for India that is based on the [Retail software development kit (SDK)](../../dev-itpro/retail-sdk/retail-sdk-overview.md). Starting in Commerce version 10.0.34, the GST integration for India supports the [new independent packaging and extension model](../../dev-itpro/build-pipeline.md) and can be used with the Commerce SDK and the Store Commerce app. The functionality can be enabled in the **Feature management** workspace in Commerce headquarters. For more details, see the [prerequisites for the GST integration for cash registers for India](apac-ind-cash-registers.md#prerequisites). If you are using Commerce version 10.0.33 or earlier and are migrating to Commerce version 10.0.34 or later, follow the steps in [Migrate to Commerce version 10.0.34 or later](#migrate-to-commerce-version-10034-or-later).

This functionality consists of extensions for the Commerce runtime (CRT) and point of sale (POS). To use this functionality, modify the configuration of the CRT extensions. You must also modify and build the POS projects. We recommend that use you an unmodified Retail SDK to make the changes that are described in this article. We also recommend that you use a source control system such as Microsoft Visual Studio Online (VSO) where no files have been changed yet. For information about how to install and use the Retail SDK, see the [Retail software development kit (SDK) architecture](../../dev-itpro/retail-sdk/retail-sdk-overview.md).

## Prerequisites

Make sure that the Visual C++ Redistributable Packages are present on the machine that you're running GST calculations on. For Cloud POS, and for Modern POS in online mode, this machine is Commerce Scale Unit. For Modern POS in offline mode, it's the Modern POS machine itself. For information about how to download the packages, see [Download the Visual C++ Redistributable Packages](https://www.microsoft.com/download/details.aspx?id=48145).

## Development environment

To set up a development environment so that you can test and extend the functionality, complete the following procedures.

### The CRT extension components

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file, as shown in the following example.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdIndia" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!IMPORTANT]
    > Keep the order of the extensions as shown above.

    > [!WARNING]
    > Do not edit the **commerceruntime.config** and **CommerceRuntime.MPOSOffline.config** files. These files aren't intended for any customizations.

### The Commerce Scale Unit extension components

1. Open the **web.config** file in the root folder under the IIS Commerce Scale Unit site location.
2. Register the extensions in the **extensionComposition** section of the configuration file.

``` xml
<add source="assembly" value="Microsoft.Dynamics.Retail.RetailServer.TaxRegistrationIdIndia" />
```

### The ClientBroker extension components

1. Open **RetailProxy.MPOSOffline.ext.config** under the local CRT client broker location.
2. Register the Proxy extensions in the **extensionComposition** section of the configuration file.

``` xml
<add source="assembly" value="Microsoft.Dynamics.Commerce.RetailProxy.TaxRegistrationIdIndia" />
```

### The Modern POS extension components

To enable the Tax Registration ID extension, follow these steps.

1. Open the solution at **RetailSdk\POS\ModernPOS.sln**, and make sure that it can be compiled without errors. Also make sure that Modern POS can be run from Microsoft Visual Studio using the Run command. (Modern POS must not be customized. You must enable User Account Control [UAC], and uninstall previously installed instances of Modern POS.)
2. Enable the extension in the **POS.Extensions\extensions.json** file by adding the following lines:

    ``` xml
    {
        "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

3. Build the solution.
4. Run Modern POS and test the functionality.

### The Cloud POS extension components

To enable the Tax Registration ID extension, follow these steps.

1. Open the solution at **RetailSdk\POS\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Enable the extension in **POS.Extensions\extensions.json** by adding the following lines:

    ``` xml
    {
        "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

3. Build the solution.
4. Run Cloud POS and test the functionality.

### Set up required parameters in Headquarters

For more information, see [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md).

## Production environment

Follow these steps to create deployable packages that contain components, and to apply the packages in a production environment.

1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdIndia" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!IMPORTANT]
    > Keep the order of the extensions as shown above.

2. In the **RetailProxy.MPOSOffline.ext.config** configuration file under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.RetailProxy.TaxRegistrationIdIndia" />
    ```

3. Update the web configuration file. In the **RetailSDK\Packages\RetailServer\Code\web.config** file, add the following lines to the **extensionComposition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Retail.RetailServer.TaxRegistrationIdIndia" />
    ```

4. Enable the Tax Registration ID POS extension by adding the following lines to the **RetailSDK\POS\Extensions\extensions.json** file:

    ``` xml
    {
        "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

5. Run **msbuild** for the whole Retail SDK to create deployable packages.
6. Apply the packages via LCS or manually. For more information, see [Create retail deployable packages](../../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Migrate to Commerce version 10.0.34 or later

The steps described in this section are required if you are using Commerce version 10.0.33 or earlier and are migrating to version 10.0.34 or later. Follow the steps below to correctly update your Commerce environment.

1. Update Commerce headquarters.
1. In the **Feature management** workspace, enable [India-specific features](apac-ind-cash-registers.md#prerequisites) and distribute the changes to channels.
1. Update Commerce runtime and exclude the following legacy India-specific extensions:
    - Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdIndia
    - Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
