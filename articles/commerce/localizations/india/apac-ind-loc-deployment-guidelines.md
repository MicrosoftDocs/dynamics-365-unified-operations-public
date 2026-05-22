---
title: Deployment guidelines for cash registers for India
description: This article provides a deployment guide for the Microsoft Dynamics 365 Commerce localization for India.
author: EvgenyPopovMBS
ms.date: 02/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: India
ms.author: anupamar
ms.search.validFrom: 2018-01-31
ms.custom: 
  - bap-template
---
# Deployment guidelines for cash registers for India

[!include [banner](../../../finance/includes/banner.md)]

This article is a deployment guide that shows how to enable the requirements for Goods and Services Tax (GST) in the Microsoft Dynamics 365 Commerce app's localization for India. For more information about the localization for India, see [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md).

> [!WARNING]
> The steps described in this article apply only to the legacy implementation of the GST integration for India that is based on the [Retail software development kit (SDK)](../../dev-itpro/retail-sdk/retail-sdk-overview.md). Starting in Commerce version 10.0.34, the GST integration for India supports the [new independent packaging and extension model](../../dev-itpro/build-pipeline.md) and can be used with the Commerce SDK and the Store Commerce app. You can enable the functionality in the **Feature management** workspace in Commerce headquarters. For more details, see the [prerequisites for the GST integration for cash registers for India](apac-ind-cash-registers.md#prerequisites). If you're using Commerce version 10.0.33 or earlier and are migrating to Commerce version 10.0.34 or later, follow the steps in [Migrate to Commerce version 10.0.34 or later](#migrate-to-commerce-version-10034-or-later).

This functionality consists of extensions for the Commerce runtime (CRT) and point of sale (POS). To use this functionality, modify the configuration of the CRT extensions. You must also modify and build the POS projects. Use an unmodified Retail SDK to make the changes that are described in this article. Also, use a source control system such as Microsoft Visual Studio Online (VSO) where no files are changed yet. For information about how to install and use the Retail SDK, see the [Retail software development kit (SDK) architecture](../../dev-itpro/retail-sdk/retail-sdk-overview.md).

## Prerequisites

Make sure that the Visual C++ Redistributable Packages are present on the machine that you're running GST calculations on. For Cloud POS, and for Modern POS in online mode, this machine is Commerce Scale Unit. For Modern POS in offline mode, it's the Modern POS machine itself. For information about how to download the packages, see [Download the Visual C++ Redistributable Packages](https://www.microsoft.com/download/details.aspx?id=48145).

## Development environment

To set up a development environment so that you can test and extend the functionality, complete the following procedures.

### The CRT extension components

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **commerceruntime.ext.config**. You can find it in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**. You can find it under the local CRT client broker location.

1. Register the CRT change in the extension configuration file, as shown in the following example.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdIndia" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!IMPORTANT]
    > Keep the order of the extensions as shown in the preceding list.

    > [!WARNING]
    > Don't edit the **commerceruntime.config** and **CommerceRuntime.MPOSOffline.config** files. These files aren't intended for any customizations.

### The Commerce Scale Unit extension components

1. Open the **web.config** file in the root folder under the IIS Commerce Scale Unit site location.
1. Register the extensions in the **extensionComposition** section of the configuration file.

``` xml
<add source="assembly" value="Microsoft.Dynamics.Retail.RetailServer.TaxRegistrationIdIndia" />
```

### The ClientBroker extension components

1. Open **RetailProxy.MPOSOffline.ext.config** under the local CRT client broker location.
1. Register the Proxy extensions in the **extensionComposition** section of the configuration file.

``` xml
<add source="assembly" value="Microsoft.Dynamics.Commerce.RetailProxy.TaxRegistrationIdIndia" />
```

### The Modern POS extension components

To enable the Tax Registration ID extension, follow these steps:

1. Open the solution at **RetailSdk\POS\ModernPOS.sln**, and make sure that it compiles without errors. Also make sure that you can run Modern POS from Microsoft Visual Studio by using the Run command. (Don't customize Modern POS. You must enable User Account Control [UAC], and uninstall previously installed instances of Modern POS.)
1. Enable the extension in the **POS.Extensions\extensions.json** file by adding the following lines:

    ``` xml
    {
        "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

1. Build the solution.
1. Run Modern POS and test the functionality.

### The Cloud POS extension components

To enable the Tax Registration ID extension, follow these steps:

1. Open the solution at **RetailSdk\POS\CloudPOS.sln**, and make sure that it compiles without errors.
1. Enable the extension in **POS.Extensions\extensions.json** by adding the following lines:

    ``` xml
    {
        "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

1. Build the solution.
1. Run Cloud POS and test the functionality.

### Set up required parameters in Headquarters

For more information, see [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md).

## Production environment

Follow these steps to create deployable packages that contain components, and to apply the packages in a production environment.

1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\Assets** folder, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdIndia" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
    ```

    > [!IMPORTANT]
    > Keep the order of the extensions as shown in the preceding list.

1. In the **RetailProxy.MPOSOffline.ext.config** configuration file under the **RetailSdk\Assets** folder, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.RetailProxy.TaxRegistrationIdIndia" />
    ```

1. Update the web configuration file. In the **RetailSDK\Packages\RetailServer\Code\web.config** file, add the following lines to the **extensionComposition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Retail.RetailServer.TaxRegistrationIdIndia" />
    ```

1. Enable the Tax Registration ID POS extension by adding the following lines to the **RetailSDK\POS\Extensions\extensions.json** file:

    ``` xml
    {
        "baseUrl": "Microsoft/TaxRegistrationId.IN"
    }
    ```

1. Run **msbuild** for the whole Retail SDK to create deployable packages.
1. Apply the packages via LCS or manually. For more information, see [Create retail deployable packages](../../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Migrate to Commerce version 10.0.34 or later

If you're using Commerce version 10.0.33 or earlier and want to migrate to version 10.0.34 or later, complete the steps in this section. Follow the steps to correctly update your Commerce environment.

1. Update Commerce headquarters.
1. In the **Feature management** workspace, enable [India-specific features](apac-ind-cash-registers.md#prerequisites) and distribute the changes to channels.
1. Update Commerce runtime and exclude the following legacy India-specific extensions:
    - Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdIndia
    - Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
