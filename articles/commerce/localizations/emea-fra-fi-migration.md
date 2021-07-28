---
# required metadata

title: Migrating from legacy Commerce functionality for France
description: This topic provides guidelines on how to migrate from the legacy digital signing sample for France to the functionality that is based on the Fiscal integration framework
author: EvgenyPopovMBS
manager: annbe
ms.date: 07/28/2021
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

If you're using the earlier [Deployment guidelines for cash registers for France](emea-fra-deployment.md), you might have to migrate from it to the current integration sample. To uptake the change and receive timely updates for the features for France in the future, you might have to upgrade. No major changes are required in the extension logic that you created. As this is a major update, some of your customizations will not continue to work if no changes are made from your side. Therefore, you should plan, prepare for, and do the uptake for your environment.

### Migration process

The migration from the earlier integration sample to the current control unit integration sample should be based on the concept of a gradual update. In other words, all Headquarters and Commerce Scale Unit components should already be updated before you start to update the POS.

To help prevent a situation where an event or transaction is signed twice (that is, it's signed by both the earlier extension and the current extension), or where it can't be signed because of the missing configuration, we recommend that you turn off all POS devices that use the earlier sample, and then update them simultaneously. This simultaneous update can be done, for example, on a store-by-store basis by updating the store's functionality profile.

The migration process should consist of the following steps.

1. Update the Headquarters components.
2. Update the Commerce Scale Unit components, and enable the extensions of the current sample.
3. Update the POS components, and enable the extensions of the current sample.
4. Make sure that all offline transactions are synced from offline-enabled MPOS devices.
5. Close shifts and logoff from all POS.
6. Enable Fiscal integration and configure functional profile.
7. Adjust receipt formats.
8. Restart POS.

    > [!NOTE]
    > Depending on the type of environment, you can find more technical details about the migration process in either the [Migration in a development environment](#migration-in-a-development-environment) section or the [Migration in a production environment](#migration-in-a-production-environment) section.

#### Adjust receipt formats

You need to adjust your receipt formats to use updated custom fields. Review the [Configure custom fields so that they can be used in receipt formats for sales receipts](./emea-fra-cash-registers.md#configure-custom-fields-so-that-they-can-be-used-in-receipt-formats-for-sales-receipts) section for up-to-date custom fields for France.

#### Set up the registration process

To enable the registration process, follow these steps to set up Headquarters. For more details, see [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The file location is **???\\MicrosoftSequentialSignatureConnector.xml**.
2. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configuration. The file location is **???\\MicrosoftSequentialSignatureFRA.xml**.
3. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile, and select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
4. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Set the connector type as **Internal**. Update the other connection settings as required.
5. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, create a fiscal registration process step, and select the fiscal connector group that you created earlier.

### Configure the digital signature parameters for Headquarters

Starting new version you should use the [User-defined certificate profiles for retail stores](./certificate-profiles-for-retail-stores.md) feature that supports failover to offline when Key Vault or Headquarters are not available. The feature extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature.

To configure a digital certificate stored in Microsoft Azure Key Vault storage then the following steps must be completed before you can use a certificate that is stored in Key Vault storage:

- The Key Vault storage must be created. We recommend that you deploy the storage in the same geographical region as the Commerce Scale Unit.
- The certificate must be uploaded to the Key Vault storage.
- The Application Object Server (AOS) application must be authorized to read secrets from the Key Vault storage.

For more information about how to work with Key Vault, see [Get started with Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-get-started).

Then, on the **Key Vault parameters** page, you must specify the parameters for accessing the Key Vault storage:

- **Name** and **Description** – The name and description of the Key Vault storage.
- **Key Vault URL** – The URL of the Key Vault storage.
- **Key Vault client** – An interactive client ID of the Azure Active Directory (Azure AD) application that is associated with the Key Vault storage for authentication purposes. This client should have access to read secrets from the storage.
- **Key Vault secret key** – A secret key that is associated with the Azure AD application that is used for authentication in the Key Vault storage.
- **Name**, **Description**, and **Secret reference** – The name, description, and secret reference of the certificate.

Then, to must configure the certificate profile with your Key Vault or local sertificates:
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Certificate profiles**. 
2. Create a new certificate profile.
3. On the **Legal entities** FastTab, add requred legal entities.
4. On the same FastTab, go to settings.
5. Add a new certificate. It supports Key Vault and Local certificate. You can add as many certificates as you need. If one of is not avalible, then system will try to use the other according to the priority.
   - For Key Vault you must select certificate from dropdown list.
   - For Local you must specify certificate thumbprint prom your certificale local storage.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**.
7. On the **Settings** FastTab, you must specify the parameters for digital signatures:
   - Certificate profile – Select the certificate profile that you configured in the previous step.
   - Hash algorithm – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET, such as SHA256.
   - Activate health check – For more information about Health Check feature, see [Fiscal registration health check](https://docs.microsoft.com/dynamics365/commerce/localizations/fiscal-integration-for-retail-channel#fiscal-registration-health-check).

### Migration in a development environment

#### Update CRT

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

#### Update Modern POS

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

#### Update Cloud POS

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

#### Enable Fiscal Integration

When you will be ready to upgrate, follow next steps to enable Fiscal integration and start using new version of localization. 

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier. 
3. Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

> [!WARNING]
    > After this steps previous customization will not work.

### Future update

In a next update you can remove obsolete customization from your Retail Servers and POS. The following describes extensions that can be safely removed.

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

### Migration in a production environment

#### Update CRT

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

#### Update Modern POS

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

#### Update Cloud POS

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

#### Create deployable packages

Run **msbuild** for the whole Retail SDK to create deployable packages. Apply the packages via LCS or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).

### Future update

In a next update you can remove obsolete customization from your Retail Servers and POS. The following describes extensions that can be safely removed.

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
