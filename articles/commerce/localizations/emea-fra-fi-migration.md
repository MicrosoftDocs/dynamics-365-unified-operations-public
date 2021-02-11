---
# required metadata

title: Migrating from SDK to sealed extensions
description: This topic provides guidelines on how to migrate from the legacy digital signing sample for France to the functionality that is based on the Fiscal integration framework
author: josaw
manager: annbe
ms.date: 03/01/2021
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
# Migrating from SDK to sealed extensions

## Migrating from the earlier integration sample

If you're using the earlier [Deployment guidelines for cash registers for France](emea-fra-deployment.md), you might have to migrate from it to the current integration sample. To uptake the change and receive timely updates for the features for France in the future, you might have to upgrade, make minor code and configuration adjustments in the extensions that you built, and rebuild your solutions. No major changes are required in the extension logic that you created. The earlier integration sample and your customizations will continue to work if no changes are made from your side. Therefore, you can plan, prepare for, and do the uptake for your environment.

### Migration process

The migration from the earlier integration sample to the current control unit integration sample should be based on the concept of a gradual update. In other words, all Headquarters and Commerce Scale Unit components should already be updated before you start to update the POS.

To help prevent a situation where an event or transaction is signed twice (that is, it's signed by both the earlier extension and the current extension), or where it can't be signed because of the missing configuration, we recommend that you turn off all POS devices that use the earlier sample, and then update them simultaneously. This simultaneous update can be done, for example, on a store-by-store basis by updating the store's functionality profile.

The migration process should consist of the following steps.

1. Update the Headquarters components.
2. Update the Commerce Scale Unit components, and enable the extensions of the current sample.
3. Make sure that all offline transactions are synced from offline-enabled MPOS devices.
4. Turn off all devices that use the components of the earlier sample.
5. Update the POS components, disable the extensions that are parts of the earlier sample, and enable the extensions of the current sample.

    > [!NOTE]
    > Depending on the type of environment, you can find more technical details about the migration process in either the [Migration in a development environment](#migration-in-a-development-environment) section or the [Migration in a production environment](#migration-in-a-production-environment) section.

### Migration in a development environment

##### Set up the registration process

To enable the registration process, follow these steps to set up Headquarters. For more details, see [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The file location is **???\\MicrosoftSequentialSignatureConnector.xml**.
3. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configuration. The file location is **???\\MicrosoftSequentialSignatureFRA.xml**.
4. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile, and select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
5. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Set the connector type as **Internal**. Update the other connection settings as required.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, create a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier. 
9.  Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

#### Configure the digital signature parameters for Headquarters

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

#### Update CRT

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
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
    ```

    > [!WARNING]
    > Don't complete this step until you update all POS devices that work with this CRT instance.

3. Register the current sample CRT extensions in the extension configuration file by adding the following lines.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    ```

#### Update Modern POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
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

3. Enable the current sample POS extension by adding the following lines in the **extensions.json** file.

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

3. Enable the current sample POS extension by adding the following lines in the **extensions.json** file.

    ``` json
    {
        "baseUrl": "Microsoft/Receipts.FR"
    }, 
    {
        "baseUrl": "Microsoft/FifAuditEvent.FR"
    }
    ```

### Migration in a production environment

#### Update CRT

1. Remove the earlier CRT extension from the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.CommonFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExt" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SalesPaymentTransExtFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureFrance" />
    <add source="assembly" value="Contoso.Commerce.Runtime.SequentialSignatureRegister" />
    <add source="assembly" value="Contoso.Commerce.Runtime.XZReportsFrance" />
    ```

    > [!WARNING]
    > Don't complete this step until you update all POS devices that work with this CRT instance.

2. Enable the current sample CRT extensions by making the following changes in the **CommerceRuntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder.

    ``` xml	
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    ```

3. In the **Customization.settings** package customization configuration file under the **BuildTools** folder, add the following lines to include the current sample CRT extension in deployable packages.

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.DocumentProvider.CleanCashSample.dll" />
    ```

#### Update Modern POS

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the **FiscalRegisterSample** folder to the exclude list.
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

3. Enable the current sample POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

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
2. Disable the earlier POS extension:

    - In the **tsconfig.json** file, add the **FiscalRegisterSample** folder to the exclude list.
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

4. Enable the current sample POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

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
