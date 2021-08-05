---
# required metadata

title: Migrating from legacy Commerce functionality for France
description: This topic provides guidelines on how to migrate from the legacy digital signing sample for France to the functionality that is based on the Fiscal integration framework
author: EvgenyPopovMBS
manager: annbe
ms.date: 08/05/2021
ms.topic: article
ms.prod:
ms.service: dynamics-365-retail
ms.technology:

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang:
ms.reviewer: josaw
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: France
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2021-03-01
ms.dyn365.ops.version: 10.0.18

---
# Migrating from legacy Commerce functionality for France

[!include [banner](../includes/banner.md)]

This topic provides guidelines on how to migrate your environment from the [legacy digital signing solution for France](./emea-fra-deployment.md) to the [solution that is based on the Fiscal integration framework](./emea-fra-fi-deployment.md).

If you're using the [legacy digital signing solution for France](emea-fra-deployment.md), you need to migrate from it to the [current fiscal integration solution](./emea-fra-fi-deployment.md) to uptake the changes and receive timely updates for the features for France in the future. No major changes are required in the extension logic that you created, however, as this is a major update, some of your customizations will not continue to work if no changes are made from your side. Therefore, you should plan, prepare for, and complete the uptake for your environment.

## Migration process

The process of migration from the legacy digital signing solution to the current fiscal integration solution is  based on the concept of a gradual update. This means that all Commerce Headquarters and Commerce Scale Unit components should already be updated before you start updating Point of sale (POS).

To help prevent the situation when an event or transaction is signed twice (that is, it is signed by both the legacy extension and the current extension), or when it can't be signed because of missing configuration, you are recommended to switch off all POS devices that use the legacy sample, and then update them simultaneously. This simultaneous update can be done, for example, on the store-by-store basis by updating the store's functionality profile.

The migration process should consist of the following steps.

1. Update the Commerce Headquarters components.
2. Update the Commerce Scale Unit components and enable the extensions of the current solution.
3. Update the POS components and enable the extensions of the current solution.
4. Configure the fiscal integration functionality for France in Commerce Headquarters.
5. Make sure that all offline transactions are uploaded from offline-enabled MPOS devices to the channel database.
6. Close shifts and logoff from all POS.
7. Adjust receipt formats to use updated custom fields.
8. Enable the fiscal integration functionality.
9. Restart POS.

> [!NOTE]
> Depending on the type of environment, you can find more technical details about the migration process in either the [Migration in a development environment](#migration-in-a-development-environment) section or the [Migration in a production environment](#migration-in-a-production-environment) section.

## Configure fiscal integration

To configure the fiscal integration functionality for France, follow the steps that are described in the [Set up fiscal registration](./emea-fra-cash-registers.md#set-up-fiscal-registration) and [Configure the digital signature parameters](./emea-fra-cash-registers.md#configure-the-digital-signature-parameters) sections. Do **not** enable fiscal integration in **Commerce shared parameters** at this moment.

## Adjust receipt formats

You need to adjust your receipt formats to use updated custom fields. Review the [Configure custom fields so that they can be used in receipt formats for sales receipts](./emea-fra-cash-registers.md#configure-custom-fields-so-that-they-can-be-used-in-receipt-formats-for-sales-receipts) section for up-to-date custom fields for France.

## Enable fiscal integration

When you are ready to enable the fiscal integration functionality, make the following steps to start using it: 

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier. 
3. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

> [!WARNING]
> After making these steps, your previous customizations of the digital signing functionality will stop working.

## Migration in a development environment

### Update CRT

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **CommerceRuntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's in the **bin\\ext** folder under the local CRT client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

2. Find and remove the earlier CRT extension from the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
    ```

3. Register the current sample CRT extensions in the extension configuration file by adding the following lines.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    ```

### Update Modern POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Enable the current sample POS extension by adding the following lines in the **extensions.json** file.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }
    ```

### Update Cloud POS

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Enable the current sample POS extension by adding the following lines in the **extensions.json** file.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }
    ```

### Future update

In a next update, you can remove the obsolete customizations from your Retail Servers and POS. The following sections describe extensions that can be safely removed.

#### CRT

1. Find the extension configuration file for CRT:

    - **Commerce Scale Unit:** The file is named **CommerceRuntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's in the **bin\\ext** folder under the local CRT client broker location.

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

2. Find and remove the earlier CRT extension from the extension configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.CommonFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    <add source="assembly" value="Contoso.Commerce.Runtime.DataSignatureKeyVaultSample" />
    ```

#### Retail Server

1. Find the configuration file for Retail Server. The file is named **web.config**, and it's in the root folder under the IIS Retail Server site location.
2. Find and remove the earlier Retail Server extension in the **extensionComposition** section of the configuration file.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

#### Modern POS

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Disable the earlier POS extension by removing the following lines from the **extensions.json** file.

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

#### Cloud POS

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Disable the earlier POS extension by removing the following lines from the **extensions.json** file.

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

### Update CRT

1. Remove the earlier CRT extension from the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
    ```

2. Enable the current sample CRT extensions by making the following changes in the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder.

    ``` xml	
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    ```

### Update Modern POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Enable the current sample POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }
    ```

### Update Cloud POS

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Enable the current sample POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }
    ```

### Create deployable packages

Run **msbuild** for the whole Retail SDK to create deployable packages. Apply the packages via LCS or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

### Future update

In a next update, you can remove the obsolete customizations from your Retail Servers and POS. The following sections describe extensions that can be safely removed.

#### CRT

1. Remove the earlier CRT extension from the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder.

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

3. Remove the following lines to the **ItemGroup** section to exclude the Retail Server extension from the deployable packages.

        ``` xml
        <ISV_RetailServer_CustomizableFile Include="$(SdkReferencesPath)\Contoso.RetailServer.SalesTransactionSignatureSample.dll" />
        ```

4. Update the Retail Server configuration file. In **RetailSDK\\Packages\\RetailServer\\Code\\web.config**, remove the following lines from the **extensionComposition** section.

    ``` xml
    <add source="assembly" value="Contoso.RetailServer.SalesTransactionSignatureSample" />
    ```

#### Modern POS

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the next folders to the exclude list.
        - SalesTransactionSignatureSample
        - SequentialSignature
        - AuditEventSignatureSample
        - SalesTransBuildNumberSample
    - Remove the following lines from the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

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

#### Cloud POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the next folders to the exclude list.
        - SalesTransactionSignatureSample
        - SequentialSignature
        - AuditEventSignatureSample
        - SalesTransBuildNumberSample
    - Remove the following lines from the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

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

#### Create deployable packages

Run **msbuild** for the whole Retail SDK to create deployable packages. Apply the packages via LCS or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
