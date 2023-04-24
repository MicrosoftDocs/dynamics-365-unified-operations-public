---
title: Migrate from legacy Commerce functionality for France
description: This article explains how to migrate from the legacy digital signing solution in the Microsoft Dynamics 365 Commerce localization for France to the solution that is based on the Commerce fiscal integration framework.
author: EvgenyPopovMBS
ms.date: 08/23/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: France
ms.author: josaw
ms.search.validFrom: 2021-03-01
ms.dyn365.ops.version: 10.0.18
ms.search.industry: Retail
ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
---
# Migrate from legacy Commerce functionality for France

[!include [banner](../includes/banner.md)]

This article explains how to migrate from the [legacy digital signing solution](emea-fra-deployment.md) in the Microsoft Dynamics 365 Commerce localization for France to the solution that is based on the [Commerce fiscal integration framework](emea-fra-fi-deployment.md).

If you're using the [legacy digital signing solution for France](emea-fra-deployment.md), you must migrate to the [current Commerce fiscal integration solution](./emea-fra-fi-deployment.md) to uptake the changes and receive timely updates for France-specific features in the future. No major changes are required in the extension logic that you created. However, because this update is a major update, some of your customizations will stop working unless changes are made on your side. Therefore, you should plan, prepare for, and complete the uptake for your environment.

## Migration process

The migration process from the legacy digital signing solution to the current fiscal integration solution is based on the concept of a gradual update. In other words, all Commerce headquarters and Commerce Scale Unit components should already be updated before you start to update the point of sale (POS).

To help prevent scenarios where an event or transaction is signed twice (by both the legacy extension and the current extension), or where an event or transaction can't be signed because of incorrect or incomplete configuration, we recommend that you turn off all POS devices that use the legacy solution and then update all of them simultaneously. For example, you can do this simultaneous update on a store-by-store basis, by updating each store's functionality profile.

To complete the migration process, follow these steps.

1. Update the Commerce headquarters components.
1. In Commerce headquarters, [configure the fiscal integration functionality for France](#configure-fiscal-integration).
1. Make sure that all offline transactions are uploaded from offline-enabled Modern POS devices to the channel database.
1. Close shifts, and sign out of all POS devices.
1. Update the Commerce Scale Unit components, and then enable the extensions of the current solution.
1. Update the POS components, and then enable the extensions of the current solution.

    > [!NOTE]
    > - You must enable the Commerce runtime (CRT) and POS extensions only if you're using Commerce version 10.0.28 or earlier. As of Commerce version 10.0.29, all required Commerce channel components for France are enabled out of the box. However, you must [enable France-specific features](./emea-fra-cash-registers.md#enable-features-for-france) instead.
    > - Depending on the type of environment, you can find more technical details about the migration process in either [Migration in a development environment](#migration-in-a-development-environment) or [Migration in a production environment](#migration-in-a-production-environment).

1. [Adjust receipt formats](#adjust-receipt-formats) so that they use updated custom fields.
1. [Enable the fiscal integration functionality](#enable-fiscal-integration).
1. Restart the POS.

## Configure fiscal integration

To configure the fiscal integration functionality for France, follow the steps in [Set up fiscal registration](./emea-fra-cash-registers.md#set-up-fiscal-registration) and [Configure the digital signature parameters](./emea-fra-cash-registers.md#configure-the-digital-signature-parameters).

> [!IMPORTANT]
> Don't enable fiscal integration on the **Commerce shared parameters** page at this point.

## Adjust receipt formats

You must adjust your receipt formats so that they use updated custom fields. For up-to-date information about custom fields for France, see [Configure custom fields so that they can be used in receipt formats for sales receipts](./emea-fra-cash-registers.md#configure-custom-fields-so-that-they-can-be-used-in-receipt-formats-for-sales-receipts).

## Enable fiscal integration

When you're ready to enable the fiscal integration functionality in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile that is linked to the store where the registration process should be activated.
1. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
1. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Open the distribution schedule, and select jobs **1070** and **1090** to transfer data to the channel database.

> [!WARNING]
> After you complete the preceding steps, your previous customizations of the digital signing functionality will stop working.

## Migration in a development environment

> [!NOTE]
> You should implement the steps that are described in this section only if you're using Commerce version 10.0.28 or earlier. As of Commerce version 10.0.29, all required Commerce channel components for France are enabled out of the box. However, you must [enable France-specific features](./emea-fra-cash-registers.md#enable-features-for-france) instead.

### Update the Commerce runtime (development)

To update the Commerce runtime (CRT), follow these steps.

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **CommerceRuntime.ext.config** and can be found in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found in the **bin\\ext** folder under the local CRT client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

1. In the extension configuration file, find and remove the earlier CRT extension, as shown in the following example.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
    ```

1. In the extension configuration file, add the following lines to register the current sample CRT extensions.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
    ```

### Update Modern POS (development)

To update Modern POS, follow these steps.

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
1. In the **extensions.json** file, add the following lines to enable the current sample POS extension.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }, 
    {
        "baseUrl": "Microsoft/RestrictShiftDuration"
    }
    ```

### Update Cloud POS (development)

To update Cloud POS, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
1. In the **extensions.json** file, add the following lines to enable the current sample POS extension.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }, 
    {
        "baseUrl": "Microsoft/RestrictShiftDuration"
    }
    ```

### Remove obsolete customizations from the development environment after future updates

After a future update, you can remove the obsolete Retail Server and POS customizations from your development environment. The following procedures describe how to remove extensions that can safely be removed.

#### Remove the earlier CRT extensions (development)

To remove the earlier CRT extensions, follow these steps.

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **CommerceRuntime.ext.config** and can be found in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config** and can be found in the **bin\\ext** folder under the local CRT client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

1. In the extension configuration file, find and remove the earlier CRT extensions, as shown in the following example.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.CommonFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    <add source="assembly" value="Contoso.Commerce.Runtime.DataSignatureKeyVaultSample" />
    ```

#### Remove the earlier Retail Server extension (development)

To remove the earlier Retail Server extension, follow these steps.

1. Find the configuration file for Retail Server. The file is named **web.config** and can be found in the root folder under the IIS Retail Server site location.
1. In the configuration file, find the earlier Retail Server extension in the **extensionComposition** section, and remove it, as shown in the following example.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

#### Disable the earlier Modern POS extension (development)

To disable the earlier Modern POS extension, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
1. In the **extensions.json** file, remove the following lines to disable the earlier POS extension.

    ``` json
    {
        "baseUrl": "Microsoft/AuditEvent.FR"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SequentialSignature"
    },
    {
        "baseUrl": "AuditEventSignatureSample"
    },
    {
        "baseUrl": "SalesTransBuildNumberSample"
    }
    ```

#### Disable the earlier Cloud POS extension (development)

To disable the earlier Cloud POS extension, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. In the **extensions.json** file, remove the following lines to disable the earlier POS extension.

    ``` json
    {
        "baseUrl": "Microsoft/AuditEvent.FR"
    },
    {
        "baseUrl": "SalesTransactionSignatureSample"
    },
    {
        "baseUrl": "SequentialSignature"
    },
    {
        "baseUrl": "AuditEventSignatureSample"
    },
    {
        "baseUrl": "SalesTransBuildNumberSample"
    }
    ```

## Migration in a production environment

> [!NOTE]
> You should implement the steps that are described in this section only if you're using Commerce version 10.0.28 or earlier. As of Commerce version 10.0.29, all required Commerce channel components for France are enabled out of the box. However, you must [enable France-specific features](./emea-fra-cash-registers.md#enable-features-for-france) instead.

### Update CRT (production)

To update CRT, follow these steps.

1. In the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, remove the earlier CRT extension, as shown in the following example.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
    ```

1. In the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, make the following changes to enable the current sample CRT extensions.

    ``` xml	
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
    ```

### Update Modern POS (production)

To update Modern POS, follow these steps.

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
1. In the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder, add the following lines to enable the current sample POS extension.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }, 
    {
        "baseUrl": "Microsoft/RestrictShiftDuration"
    }
    ```

### Update Cloud POS (production)

To update Cloud POS, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
1. In the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder, add the following lines to enable the current sample POS extension.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }, 
    {
        "baseUrl": "Microsoft/RestrictShiftDuration"
    }
    ```

### Create deployable packages (production)

To create deployable packages, follow these steps.

1. Run **msbuild** for the whole Retail software development kit (SDK) to create deployable packages.
1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually.

For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

### Remove obsolete customizations from the production environment after future updates

After a future update, you can remove the obsolete Retail Server and POS customizations from your production environment. The following procedures describe how to remove extensions that can safely be removed.

#### Remove the earlier CRT extension (production)

1. In the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, remove the earlier CRT extension.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.CommonFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    <add source="assembly" value="Contoso.Commerce.Runtime.DataSignatureKeyVaultSample" />
    ```

2. In the **Customization.settings** package customization configuration file under the **BuildTools** folder, remove the following lines to exclude the earlier sample CRT extension from the deployable packages.

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.CommonFrance.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.ReceiptsFrance.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExt.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SalesPaymentTransExtFrance.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureFrance.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.dll.config" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.SequentialSignatureRegister.Contracts.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.XZReportsFrance.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DataSignatureKeyVaultSample.dll" />
    ```

3. In the **ItemGroup** section, remove the following lines to exclude the Retail Server extension from the deployable packages.

    ``` xml
    <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
    ```

4. Update the Retail Server configuration file. In the **web.config** file under the **RetailSDK\\Packages\\RetailServer\\Code** folder, remove the following lines from the **extensionComposition** section.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

#### Disable the earlier Modern POS extension (production)

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the following folders to the exclude list:

        - SalesTransactionSignatureSample
        - SequentialSignature
        - AuditEventSignatureSample
        - SalesTransBuildNumberSample

    - In the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder, remove the following lines.

        ``` json
        {
            "baseUrl": "Microsoft/AuditEvent.FR"
        },
        {
            "baseUrl": "SalesTransactionSignatureSample"
        },
        {
            "baseUrl": "SequentialSignature"
        },
        {
            "baseUrl": "AuditEventSignatureSample"
        },
        {
            "baseUrl": "SalesTransBuildNumberSample"
        }
        ```

#### Disable the earlier Cloud POS extension (production)

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the following folders to the exclude list:

        - SalesTransactionSignatureSample
        - SequentialSignature
        - AuditEventSignatureSample
        - SalesTransBuildNumberSample

    - In the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder, remove the following lines.

        ``` json
        {
            "baseUrl": "Microsoft/AuditEvent.FR"
        },
        {
            "baseUrl": "SalesTransactionSignatureSample"
        },
        {
            "baseUrl": "SequentialSignature"
        },
        {
            "baseUrl": "AuditEventSignatureSample"
        },
        {
            "baseUrl": "SalesTransBuildNumberSample"
        }
        ```

#### Create deployable packages (production)

1. Run **msbuild** for the whole Retail SDK to create deployable packages.
1. Apply the packages via LCS or manually.

For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
