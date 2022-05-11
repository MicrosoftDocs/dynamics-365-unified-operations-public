---
# required metadata

title: Deployment guidelines for cash registers for France
description: This topic provides guidance about how to enable the cash register functionality for the Microsoft Dynamics 365 Commerce localization for France.
author: EvgenyPopovMBS
manager: annbe
ms.date: 08/10/2021
ms.topic: article
ms.prod: 

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

This topic provides guidance about how to enable the cash register functionality for the Microsoft Dynamics 365 Commerce localization for France. The localization consists of several extensions of components. These extensions let you perform actions such as printing custom fields on receipts, registering additional audit events, sales transactions, and payment transactions in Point of Sale (POS), digitally signing sales transactions, and printing X and Z reports in local formats. For more information about the localization for France, see [Cash register functionality for France](./emea-fra-cash-registers.md). For more information about how to configure Commerce for France, see [Set up Commerce for France](./emea-fra-cash-registers.md#set-up-commerce-for-france).

> [!NOTE]
> This version of the Commerce cash register functionality for France is based on the [fiscal integration framework](./fiscal-integration-for-retail-channel.md). For information about the legacy digital signing sample for France, see [Deployment guidelines for cash registers for France (legacy)](./emea-fra-deployment.md). For guidelines about how to enable the fiscal integration functionality for France in existing environments that use the legacy digital signing sample, see [Migrate from legacy Commerce functionality for France](./emea-fra-fi-migration.md).

## Development environment

Follow these steps to set up a development environment so that you can test and extend the localization functionality.

### Enable Commerce runtime extension components

#### RegisterAuditEventFrance component

To enable the RegisterAuditEventFrance component, follow these steps.

1. Find the extension configuration file for the Commerce runtime (CRT):

    - **Retail Server:** The file is named **commerceruntime.ext.config** and can be found in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found under the local CRT client broker location.

1. Register the CRT change in the extension configuration file, as shown in the following example.

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

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and ensure that it can be compiled without errors. Additionally, confirm that you can run Modern POS from Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC) and uninstall previously installed instances of Modern POS as required.

1. In the **extensions.json** file, add the following lines to enable the extensions that must be loaded.

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
    > For more information, and for examples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run Modern POS in the debugger, and test the functionality.

### Enable Cloud POS extension components

To enable Cloud POS extension components, follow these steps.

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and ensure that it can be compiled without errors.
1. In the **extensions.json** file, add the following lines to enable the extensions that must be loaded.

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
    > For more information, and for examples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run the solution by using the **Run** command, and then follow the steps in the Retail software development kit (SDK) handbook.

## Production environment

To create deployable packages that contain Commerce components, and to apply those packages in a production environment, follow these steps.

1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** package configuration files under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.

    ``` xml	
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    ```

1. In the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder, add the following lines to enable the POS extension.

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

1. Open the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
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
