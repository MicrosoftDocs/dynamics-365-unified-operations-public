---
title: Deployment guidelines for cash registers for Norway
description: This article provides guidance about how to enable the cash register functionality for the Microsoft Dynamics 365 Commerce localization for Norway.
author: EvgenyPopovMBS
ms.date: 08/09/2024
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2019-03-01
ms.custom: 
  - bap-template
---
# Deployment guidelines for cash registers for Norway

[!include[banner](../../../finance/includes/banner.md)]

> [!IMPORTANT]
> You should implement the steps that are described in this article only if you're using Microsoft Dynamics 365 Commerce version 10.0.29 or later. In Commerce version 10.0.28 or earlier, you must use the previous version of the Retail software development kit (SDK) on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Deployment guidelines for cash registers for Norway (legacy)](emea-nor-loc-deployment-guidelines.md). If you're using Commerce version 10.0.28 or earlier and are migrating to Commerce version 10.0.29 or later, you must follow the steps in [Migrate from legacy Commerce functionality for Norway](emea-nor-fi-migration.md).

This article provides guidance about how to enable the cash register functionality for the Commerce localization for Norway. The localization consists of several component extensions that let you perform actions such as printing custom fields on receipts, registering additional audit events, sales transactions, and payment transactions in point of sale (POS), digitally signing sales transactions, and printing reports in local formats. For more information about the localization for Norway, see [Cash register functionality for Norway](../norway/emea-nor-cash-registers.md). For more information about how to configure Commerce for Norway, see [Set up Commerce for Norway](../norway/emea-nor-cash-registers.md#setting-up-commerce-for-norway).

## Set up fiscal registration for Norway

The fiscal registration sample for Norway is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Commerce SDK. The sample is located in the **src\\FiscalIntegration\\SequentialSignatureNorway** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository. The [sample](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) consists of a fiscal document provider and a fiscal connector, which are extensions of the Commerce runtime (CRT). For more information about how to use the Commerce SDK, see [Download Commerce SDK samples and reference packages from GitHub and NuGet](../../dev-itpro/retail-sdk/sdk-github.md) and [Set up a build pipeline for the independent-packaging SDK](../../dev-itpro/build-pipeline.md).

Complete the fiscal registration setup steps that are described in [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Be sure to make a note of the settings of the fiscal registration process that are [specific to Norway](#configure-the-fiscal-registration-process).
1. [Set error handling settings](setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Enable manual execution of deferred fiscal registration](setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-deferred-fiscal-registration).
1. [Configure channel components](#configure-channel-components).

### Configure the fiscal registration process

Follow these steps to enable the fiscal registration process for Norway in Commerce headquarters.

1. Download configuration files for the fiscal document provider and the fiscal connector from the Commerce SDK:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Open the last available release branch.
    1. Open **src \> FiscalIntegration \> SequentialSignatureNorway \> CommerceRuntime**.
    1. Download the fiscal document provider configuration file at **DocumentProvider.SequentialSignNorway \> Configuration \> DocumentProviderSequentialSignatureNorwaySample.xml**.
    1. Download the fiscal connector configuration file at **Connector.SequentialSignNorway \> Configuration \> ConnectorSequentialSignatureNorwaySample.xml**.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Shared parameters**. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connectors**, and load the fiscal connector configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal document providers**, and load the fiscal document provider configuration file that you downloaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector functional profiles**. Create a new connector functional profile, and select the document provider and the connector that you loaded earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**. Create a new connector technical profile, and select the connector that you loaded earlier. Set the connector type to **Internal**.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal connector groups**, and create a new fiscal connector group for the connector functional profile that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Fiscal registration processes**. Create a new fiscal registration process and a fiscal registration process step, and select the fiscal connector group that you created earlier.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. Select a functionality profile that is linked to the store where the registration process should be activated. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier. 
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**. Open the distribution schedule, and select jobs **1070** and **1090** to transfer data to the channel database.

### Configure the digital signature parameters

You must configure certificates that will be used for digital signing of sales transactions in a store. A digital certificate that is stored in Azure Key Vault is used to do the signing. For the offline mode of Modern POS, the signing can also be done by using a digital certificate that is stored in the local storage of the machine that Modern POS is installed on.

Before you can use a digital certificate that is stored in Key Vault storage, the following steps must be completed.

1. The Key Vault storage must be created. We recommend that you deploy the storage in the same geographical region as the Commerce Scale Unit.
1. The certificate must be uploaded to the Key Vault storage as a base64 string secret.
1. The Application Object Server (AOS) application must be authorized to read secrets from the Key Vault storage.

For more information about how to work with Key Vault, see [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started).

Next, on the **Key Vault parameters** page, you must specify the parameters for accessing the Key Vault storage:

- **Name** and **Description** – The name and description of the Key Vault storage.
- **Key Vault URL** – The URL of the Key Vault storage.
- **Key Vault client** – An interactive client ID of the Microsoft Entra application that is associated with the Key Vault storage for authentication purposes. This client should have access to read secrets from the storage.
- **Key Vault secret key** – A secret key that is associated with the Microsoft Entra application that is used for authentication in the Key Vault storage.
- **Name**, **Description**, and **Secret reference** – The name, description, and secret reference of the certificate.

Next, you must configure a connector for your certificates that are stored in Key Vault or local certificate storage. This connector is used for signing on the channel side.

1. Go to **Retail and Commerce \> Channel setup \> Fiscal integration \> Connector technical profiles**.
1. On the **Settings** FastTab, specify the following parameters for digital signatures:

    - **Secret name** – Select the secret name that you configured earlier on the **Key Vault parameters** page.
    - **Local certificate thumbprint** – Provide a thumbprint for a certificate that is stored locally.
    - **Hash algorithm** – Specify one of the cryptographic hash algorithms that are supported by Microsoft .NET, such as **SHA1**.
    - **Certificate store name** – This field is optional. Use it to specify a default store name that should be used to search local certificates.
    - **Certificate store location** – This field is optional. Use it to specify a default store location that should be used to search local certificates.
    - **Try local certificate first** – Select this option to use the certificate from the local store by default for signing data, instead of the certificate from Key Vault.
    - **Activate health check** – For more information about the health check feature, see [Fiscal registration health check](fiscal-integration-for-retail-channel.md#fiscal-registration-health-check).

> [!NOTE]
> - Only the **SHA1** cryptographic hash algorithm is currently acceptable for Norway.
> - The default store name and store location are added to simplify the process of searching local certificates in CRT. X509StoreProvider has a list of folders where certificates are stored. If the default store name and the default store location aren't specified, X509StoreProvider tries to find a certificate in all the folders on its list.

### Configure channel components

#### Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

1. Clone or download the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository. Select a correct release branch version according to your SDK/application version. For more information, see [Download Commerce SDK samples and reference packages from GitHub and NuGet](../../dev-itpro/retail-sdk/sdk-github.md).
1. Open the **SequentialSignatureNorway.sln** solution under **Dynamics365Commerce.Solutions\\FiscalIntegration\\SequentialSignatureNorway**, and build it.
1. Install CRT extensions:

    1. Find the CRT extension installer:

        - **Commerce Scale Unit:** In the **SequentialSignatureNorway\\ScaleUnit\\ScaleUnit.SequentialSignNorway.Installer\\bin\\Debug\\net461** folder, find the **ScaleUnit.SequentialSignNorway.Installer** installer.
        - **Local CRT on Modern POS:** In the **SequentialSignatureNorway\\ModernPOS\\ModernPos.SequentialSignNorway.Installer\\bin\\Debug\\net461** folder, find the **ModernPos.SequentialSignNorway.Installer** installer.

    1. Start the CRT extension installer from the command line:

        - **Commerce Scale Unit:**

            ```Console
            ScaleUnit.SequentialSignNorway.Installer.exe install --verbosity 0
            ```

        - **Local CRT on Modern POS:**

            ```Console
            ModernPOS.SequentialSignNorway.Installer.exe install --verbosity 0
            ```

#### Production environment

Follow the steps in [Set up a build pipeline for a fiscal integration sample](../global/fiscal-integration-sample-build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the fiscal integration sample. The **SequentialSignatureNorway build-pipeline.yaml** template YAML file can be found in the **Pipeline\\YAML_Files** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository.

### Enable the digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, you must follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
1. On the **Database connection status** page, make sure that the offline database is fully synced. When the value of the **Pending downloads** field is **0** (zero), the database is fully synced.
1. Sign out of POS.
1. Wait for the offline database to be fully synced.
1. Sign in to POS.
1. On the **Database connection status** page, make sure that the offline database is fully synced. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synced.
1. Reopen Modern POS.
