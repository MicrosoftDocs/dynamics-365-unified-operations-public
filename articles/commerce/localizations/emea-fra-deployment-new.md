---
# required metadata

title: Deployment guidelines for cash registers for France
description: This topic is a deployment guide for the Commerce localization for France.
author: EvgenyPopovMBS
manager: annbe
ms.date: 07/02/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
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

This topic is a deployment guide that shows how to enable the Dynamics 365 Commerce localization for France. The localization consists of several extensions of components. For example, the extensions let you print custom fields on receipts, register additional audit events, sales transactions, and payment transactions in Point of Sale (POS), digitally sign sales transactions, and print X and Z reports in local formats. For more information about the localization for France, see [Cash register functionality for France](https://docs.microsoft.com/en-us/dynamics365/commerce/localizations/emea-fra-cash-registers).

## Setting up Commerce for France

See [Setting up Commerce for France](https://docs.microsoft.com/en-us/dynamics365/commerce/localizations/emea-fra-cash-registers#setting-up-commerce-for-france) for basic settings of Commerce for France.

Complete the fiscal integration setup steps that are described in [Set up the fiscal integration for Commerce channels](https://docs.microsoft.com/en-us/dynamics365/commerce/localizations/setting-up-fiscal-integration-for-retail-channel):

- [Set up a fiscal registration process](https://docs.microsoft.com/en-us/dynamics365/commerce/localizations/setting-up-fiscal-integration-for-retail-channel#set-up-a-fiscal-registration-process). Be sure to note the settings for the fiscal registration process that are [specific to France](#set-up-the-registration-process).
- [Set error handling settings](https://docs.microsoft.com/en-us/dynamics365/commerce/localizations/setting-up-fiscal-integration-for-retail-channel#set-error-handling-settings).
- [Enable manual execution of postponed fiscal registration](https://docs.microsoft.com/en-us/dynamics365/commerce/localizations/setting-up-fiscal-integration-for-retail-channel#enable-manual-execution-of-postponed-fiscal-registration).

### Set up the registration process

To enable the registration process, follow these steps to set up Headquarters. For more details, see [Set up a fiscal registration process](https://docs.microsoft.com/en-us/dynamics365/commerce/localizations/setting-up-fiscal-integration-for-retail-channel#set-up-a-fiscal-registration-process).

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
2. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the connector configuration. The configuration file can be [downloaded from GitHub](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.29/src/FiscalIntegration/SequentialSignatureFrance/Configurations/Connector/ConnectorMicrosoftSequentialSignatureFRA.xml).
3. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the document provider configuration. The configuration file can be [downloaded from GitHub](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.29/src/FiscalIntegration/SequentialSignatureFrance/Configurations/DocumentProvider/DocumentProviderMicrosoftSequentialSignatureFRA.xml).
4. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile, and select the document provider and the connector that you loaded earlier. Update the data mapping settings as required.
5. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Set the connector type as **Internal**. Update the other connection settings as required.
6. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**. Create a new fiscal connector group for the connector functional profile that you created earlier.
7. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process, create a fiscal registration process step, and select the fiscal connector group that you created earlier.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier. 
9.  Open the distribution schedule (**Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**), and select jobs **1070** and **1090** to transfer data to the channel database.

### Configure the digital signature parameters for Headquarters

You need to configure certificates to be used for digital signing of sales transactions and audit events. The [User-defined certificate profiles for retail stores](https://docs.microsoft.com/en-us/dynamics365/commerce/localizations/certificate-profiles-for-retail-stores) feature  enables configuring certificates that are stored in a Microsoft Azure Key Vault storage and supports failover to offline when Key Vault or Headquarters are not available. The feature extends the [Manage secrets for retail channels](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/manage-secrets) feature.

The following steps must be completed before you can use a digital certificate stored in an Azure Key Vault storage :

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

Finally, you need to configure a certificate profile for your certificates stored in Key Vault or local certificate storage:

1. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Certificate profiles**. 
2. Create a new certificate profile.
3. On the **Legal entities** FastTab, add requred legal entities.
4. Click **Settings**.
5. Add a new certificate. Certificate stored in Key Vault and local certificates are supported. You can add as many certificates as you need and set priorities of the certificates. If a certificate with a higher priority is not available, another certificate will be used according to priority.
   - For a certificate stored in Key Vault, you must select the certificate from the dropdown list.
   - For a certificate stored locally, you must specify the thumbprint of the certificate.
6. Open **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**.
7. On the **Settings** FastTab, you must specify the parameters for digital signatures:
   - Certificate profile – Select the certificate profile that you configured on the previous step.
   - Hash algorithm – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET, such as SHA256.
   - Activate health check – For more information about the Health Check feature, see [Fiscal registration health check](https://docs.microsoft.com/dynamics365/commerce/localizations/fiscal-integration-for-retail-channel#fiscal-registration-health-check).

## Development environment

Follow these steps to set up a development environment so that you can test and extend the localization functionality.

### Enable CRT extension components

#### RegisterAuditEventFrance component

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
    ```

#### ReceiptsFrance component

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
    ```

#### XZReportsFrance component

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
    ```

#### RestrictingShiftDuration component

1. Find the extension configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail Server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

2. Register the CRT change in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
    ```

### Enable Modern POS extension components

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, make sure that you can run Modern POS from Microsoft Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

2. Enable the extensions that must be loaded by adding the following lines in the **extensions.json** file.

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
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

3. Rebuild the solution.
4. Run Modern POS in the debugger, and test the functionality.

### Enable Cloud POS extension components

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**, and make sure that it can be compiled without errors.
2. Enable the extensions that must be loaded by adding the following lines in the **extensions.json** file.

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
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file in the **Pos.Extensions** project.

3. Rebuild the solution.
4. Run the solution by using the **Run** command and following the steps in the Retail SDK handbook.

## Production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply those packages in a production environment:

1. Make the following changes in the package configuration files under the **RetailSdk\\Assets** folder:

    - In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files, add the following lines to the **composition** section.

        ``` xml	
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.ReceiptsFrance" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RegisterAuditEventFrance" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.RestrictShiftDuration" />
        <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.XZReportsFrance" />
        ```

2. Enable the POS extension by adding the following lines in the **extensions.json** file under the **RetailSDK\\POS\\Extensions** folder.

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

3. Start the MSBuild Command Prompt for Visual Studio utility, and run **msbuild** under the Retail SDK folder to create deployable packages.
4. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Create deployable packages](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-packaging).

## Enable digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, you must follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
2. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending downloads** field is **0** (zero), the database is fully synchronized.
3. Sign out of POS.
4. Wait a while for the offline database to be fully synchronized.
5. Sign in to POS.
6. On the **Database connection status** page, make sure that the offline database is fully synchronized. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synchronized.
7. Restart Modern POS.
