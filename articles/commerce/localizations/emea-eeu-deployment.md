---
# required metadata
title: Deployment guidelines for Advance Invoice report printing for Czech Republic, Hungary, and Poland
description: This topic describes how to build extensions of the Commerce components to enable printing advance invoices from POS in Czech Republic, Hungary, and Poland.
author: anmukh
ms.date: 11/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Eastern Europe
ms.search.industry: Retail
ms.author: anmukh
ms.search.validFrom: 2018-11-30
ms.dyn365.ops.version: 8.1.1

---
# Deployment guidelines for Advance Invoice report printing for Czech Republic, Hungary, and Poland

[!include [banner](../includes/banner.md)]


This topic shows how to enable the Dynamics 365 Commerce localization for Czech Republic, Hungary, and Poland. The localization consists of several extensions of Commerce components. These extensions let you print the **Advance Invoice** report from Point of Sale (POS). For more information about localization for Czech Republic, Hungary, and Poland, see [Advance invoices for Commerce for Eastern Europe](./emea-eeu-advance-invoices-for-retail.md).

The localization is part of the Retail software development kit (SDK). For information, see the [Retail software development kit (SDK) architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md).

The localization consists of extensions for the Commerce runtime (CRT) and POS. To enable this localization, you must modify the CRT configuration file and modify and build POS projects. We recommend that you use an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Team Services, where no files have been changed yet.

## Development environment

Complete these procedures to set up a development environment, so that you can test the functionality.

### CRT extension components

1. Find the extensions configuration file for CRT.

    The file is named **commerceruntime.ext.config**, and is located in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.

2. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.UseAdvanceInvoice" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config file. This file isn't intended for any customizations.

### Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Enable the extensions to be loaded in **extensions.json** by adding the following lines in the appropriate location.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AdvanceInvoice"
            }
        ]
    }
    ```

3. Rebuild the solution.
4. Run Modern POS in the debugger and test the functionality.

### Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Enable the extensions to be loaded in **extensions.json** by adding the following lines in the appropriate location.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/AdvanceInvoice"
            }
        ]
    }
    ```

3. Rebuild the solution.
4. Run Cloud POS in the debugger and test the functionality.

### Set up required parameters in Headquarters

For more information, see [Advance invoices for Commerce for Eastern Europe](./emea-eeu-advance-invoices-for-retail.md).

## Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment.

1. Complete the steps in the **Cloud POS extension components** or **Modern POS extension components** sections earlier in this topic.
2. Make the following change in the package configuration files under the **RetailSdk\\Assets** folder.

    In the **commerceruntime.ext.config** configuration files, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.UseAdvanceInvoice" />
    ```

3. Run **msbuild** for the Retail SDK to create deployable packages.
4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]