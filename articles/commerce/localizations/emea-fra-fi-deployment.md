---
# required metadata

title: Deployment guidelines for cash registers for France
description: This topic provides guidance on how to enable the Microsoft Dynamics 365 Commerce localization for France cash register functionality.
author: EvgenyPopovMBS
manager: annbe
ms.date: 08/05/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: France
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2021-4-30
ms.dyn365.ops.version: 10.0.18

---
# Deployment guidelines for cash registers for France

[!include [banner](../includes/banner.md)]

This topic provides guidance on how to enable the Microsoft Dynamics 365 Commerce localization for France cash register functionality. The localization consists of several extensions of components. These extensions enable you to perform actions such as printing custom fields on receipts, registering additional audit events, sales transactions, and payment transactions in Point of Sale (POS), digitally signing sales transactions, and printing X and Z reports in local formats. See [Cash register functionality for France](./emea-fra-cash-registers.md#overview) for more information about the localization for France, and [Setting up Commerce for France](./emea-fra-cash-registers.md#setting-up-commerce-for-france) for more information on how to configure Commerce for France.

> [!NOTE]
> This version of the Commerce cash register functionality for France is based on the [Fiscal integration framework](./fiscal-integration-for-retail-channel.md). See [Deployment guidelines for cash registers for France (legacy)](./emea-fra-deployment.md) for information on the legacy digital signing sample for France, and [Migrating from legacy Commerce functionality for France](./emea-fra-fi-migration.md) for guidelines on how to enable the fiscal integration functionality for France in your existing environments that use the legacy digital signing sample.

## Development environment

Follow these steps to set up a development environment so that you can test and extend the localization functionality.

### Enable CRT extension components

#### RegisterAuditEventFrance component

To enable the RegisterAuditEventFrance component, follow these steps.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config** and can be found in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found under the local CRT client broker location.

1. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    ```

#### ReceiptsFrance component

To enable the ReceiptsFrance component, follow these steps.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config** and can be found in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found under the local CRT client broker location.

1. Register the CRT change in the extension configuration file, as shown in the following example.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    ```

#### XZReportsFrance component

To enable the XZReportsFrance component, follow these steps.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config** and can be found in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found under the local CRT client broker location.

1. Register the CRT change in the extension configuration file, as shown in the following example.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    ```

#### RestrictingShiftDuration component

To enable the RestrictingShiftDuration component, follow these steps.

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config** and can be found in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found under the local CRT client broker location.

1. Register the CRT change in the extension configuration file, as shown in the following example.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
    ```

### Enable Modern POS extension components

To enable Modern POS extension components, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and ensure that it can be compiled without errors. Additionally, confirm that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC) and uninstall previously installed instances of Modern POS as required.

1. Enable the extensions that must be loaded by adding the following lines in the **extensions.json** file, as shown in the following example.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/Receipts.FR"
            }, 
            {
                "baseUrl": "Microsoft/FifAuditEvent.FR"
            }
        ]
    }
    ```

    > [!NOTE]
    > For more information and for examples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run Modern POS in the debugger, and test the functionality.

### Enable Cloud POS extension components

To enable Cloud POS extension components, follow these steps.

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and ensure that it can be compiled without errors.
1. Enable the extensions that must be loaded by adding the following lines in the **extensions.json** file.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/Receipts.FR"
            }, 
            {
                "baseUrl": "Microsoft/FifAuditEvent.FR"
            }
        ]
    }
    ```

    > [!NOTE]
    > For more information and for examples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run the solution using the **Run** command and then follow the steps in the Retail SDK handbook.

## Production environment

To create deployable packages that contain Commerce components and apply those packages in a production environment, follow these steps.

1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section.

        ``` xml	
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
        ```

1. Enable the POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/Receipts.FR"
            }, 
            {
                "baseUrl": "Microsoft/FifAuditEvent.FR"
            }
        ]
    }
    ```

1. Start the MSBuild Command Prompt for Visual Studio utility and run **msbuild** under the Retail SDK folder to create deployable packages.
1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Enable the digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, you must follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
1. On the **Database connection status** page, ensure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
1. Sign out of POS.
1. Wait for the offline database to be fully synchronized.
1. Sign in to POS.
1. On the **Database connection status** page, ensure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
1. Restart Modern POS.
