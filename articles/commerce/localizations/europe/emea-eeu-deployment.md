---
title: Deployment guidelines for Advance Invoice report printing for Czech Republic, Hungary, and Poland
description: Learn how to build extensions of the Microsoft Dynamics 365 Commerce components to enable printing advance invoices from POS in Czech Republic, Hungary, and Poland.
author: josaw1
ms.date: 02/26/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Eastern Europe
ms.author: josaw
ms.search.validFrom: 2018-11-30
ms.custom: 
  - bap-template
---
# Deployment guidelines for Advance Invoice report printing for Czech Republic, Hungary, and Poland

[!include [banner](../../../finance/includes/banner.md)]

> [!WARNING]
> Implement the steps described in this article only if you're using Commerce version 10.0.34 or earlier. As of version 10.0.35, all required Commerce channel components for Advance Invoice report printing are enabled by default. If you're using Commerce version 10.0.34 or earlier, and are migrating to Commerce version 10.0.35 or later, follow the steps in the [Migrate to Commerce version 10.0.35 or later](#migrate-to-commerce-version-10035-or-later) section.

This article shows how to enable the Microsoft Dynamics 365 Commerce localization for Czech Republic, Hungary, and Poland. The localization consists of several extensions of Commerce components. These extensions let you print the **Advance Invoice** report from Point of Sale (POS). For more information about localization for Czech Republic, Hungary, and Poland, see [Advance invoices for Commerce for Eastern Europe](emea-eeu-advance-invoices-for-retail.md).

The localization is part of the Retail software development kit (SDK). For information, see the [Retail software development kit (SDK) architecture](../../dev-itpro/retail-sdk/retail-sdk-overview.md).

The localization consists of extensions for the Commerce runtime (CRT) and POS. To enable this localization, you must modify the CRT configuration file and modify and build POS projects. Use an unmodified Retail SDK to make the changes described in this article. Use a source control system, such as Microsoft Visual Studio Team Services, where no files are changed yet.

## Development environment

Complete these procedures to set up a development environment so that you can test the functionality.

### CRT extension components

1. Find the extensions configuration file for CRT.

    The file is named **commerceruntime.ext.config**, and is located in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.

1. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.UseAdvanceInvoice" />
    ```

    > [!WARNING]
    > Don't edit the commerceruntime.config file. This file isn't intended for any customizations.

### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it compiles without errors. Also, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Don't customize Modern POS. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

1. Enable the extensions to load in **extensions.json** by adding the following lines in the appropriate location.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AdvanceInvoice"
            }
        ]
    }
    ```

1. Rebuild the solution.
1. Run Modern POS in the debugger and test the functionality.

### Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it compiles without errors.
1. Enable the extensions to load in **extensions.json** by adding the following lines in the appropriate location.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AdvanceInvoice"
            }
        ]
    }
    ```

1. Rebuild the solution.
1. Run Cloud POS in the debugger and test the functionality.

### Set up required parameters in Headquarters

For more information, see [Advance invoices for Commerce for Eastern Europe](emea-eeu-advance-invoices-for-retail.md).

## Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Complete the steps in the **Cloud POS extension components** or **Modern POS extension components** sections earlier in this article.
1. Make the following change in the package configuration files under the **RetailSdk\\Assets** folder.

    In the **commerceruntime.ext.config** configuration files, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.UseAdvanceInvoice" />
    ```

1. Run **msbuild** for the Retail SDK to create deployable packages.
1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Migrate to Commerce version 10.0.35 or later

Follow the steps in this section if you're using Commerce version 10.0.34 or earlier and want to migrate to version 10.0.35 or later. To correctly update your Commerce environment, complete these steps.

1. Update Commerce headquarters.
1. Enable the [Advance invoice report printing feature](emea-eeu-advance-invoices-for-retail.md#enable-the-functionality-to-create-advance-invoices) in the **Feature management** workspace, and distribute the changes to channels.
1. Update the Commerce runtime, Cloud POS, and Modern POS, and exclude the following legacy extensions:

    - Commerce runtime extensions in the `commerceruntime.ext.config` and `CommerceRuntime.MPOSOffline.Ext.config` files:

        - `Microsoft.Dynamics.Commerce.Runtime.UseAdvanceInvoice`

    - POS extensions in the `extensions.json` file:

        - `Microsoft/AdvanceInvoice`

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
