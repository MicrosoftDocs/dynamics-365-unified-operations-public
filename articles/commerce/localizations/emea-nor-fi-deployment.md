---
# required metadata

title: Deployment guidelines for cash registers for Norway
description: This topic provides guidance about how to enable the cash register functionality for the Microsoft Dynamics 365 Commerce localization for Norway.
author: EvgenyPopovMBS
ms.date: 12/20/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: epopov
ms.search.validFrom: 2019-3-1

---
# Deployment guidelines for cash registers for Norway

[!include[banner](../includes/banner.md)]

This topic provides guidance about how to enable the cash register functionality for the Microsoft Dynamics 365 Commerce localization for Norway. The localization consists of several extensions of components. These extensions let you perform actions such as printing custom fields on receipts, registering additional audit events, sales transactions, and payment transactions in point of sale (POS), digitally signing sales transactions, and printing reports in local formats. For more information about the localization for Norway, see [Cash register functionality for Norway](./emea-nor-cash-registers.md). For more information about how to configure Commerce for Norway, see [Set up Commerce for Norway](./emea-nor-cash-registers.md#setting-up-commerce-for-norway).

> [!WARNING]
> Because of limitations of the [new independent packaging and extension model](../dev-itpro/build-pipeline.md), it can't currently be used for this localization functionality. You must use the version of the digital signing sample for Norway in the previous version of the Retail software development kit (SDK) on a developer virtual machine (VM) in Microsoft Dynamics Lifecycle Services (LCS). For more information, see [Deployment guidelines for cash registers for Norway (legacy)](./emea-nor-loc-deployment-guidelines.md).
>
> Support for the new independent packaging and extension model for fiscal integration samples is planned for later versions.

## Set up fiscal registration for Norway

The fiscal registration sample for Norway is based on the [fiscal integration functionality](fiscal-integration-for-retail-channel.md) and is part of the Retail SDK. The sample is located in the **src\\FiscalIntegration\\SequentialSignatureNorway** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository (for example, [the sample in release/9.34](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.34/src/FiscalIntegration/SequentialSignatureNorway)). The sample [consists](fiscal-integration-for-retail-channel.md#fiscal-registration-process-and-fiscal-integration-samples-for-fiscal-devices-and-services) of a fiscal document provider and a fiscal connector, which are extensions of the Commerce runtime (CRT). For more information about how to use the Retail SDK, see [Retail SDK architecture](../dev-itpro/retail-sdk/retail-sdk-overview.md) and [Set up a build pipeline for the independent-packaging SDK](../dev-itpro/build-pipeline.md).

Complete the fiscal registration setup steps that are described in [Set up the fiscal integration for Commerce channels](./setting-up-fiscal-integration-for-retail-channel.md):

1. [Set up a fiscal registration process](./setting-up-fiscal-integration-for-retail-channel.md#set-up-a-fiscal-registration-process). Be sure to make a note of the settings of the fiscal registration process that are [specific to Norway](#configure-the-fiscal-registration-process).
1. [Set error handling settings](./setting-up-fiscal-integration-for-retail-channel.md#set-error-handling-settings).
1. [Enable manual execution of postponed fiscal registration](./setting-up-fiscal-integration-for-retail-channel.md#enable-manual-execution-of-postponed-fiscal-registration).
1. [Configure channel components](#configure-channel-components).

### Configure the fiscal registration process

Follow these steps to enable the fiscal registration process for Norway in Commerce headquarters.

1. Download configuration files for the fiscal document provider and the fiscal connector from the Commerce SDK:

    1. Open the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/) repository.
    1. Open the last available release branch (for example, **[release/9.34](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.34)**).
    1. Open **src \> FiscalIntegration \> SequentialSignatureNorway \> CommerceRuntime**.
    1. Download the fiscal document provider configuration file at **DocumentProvider.SequentialSignNorway \> Configuration \> DocumentProviderSequentialSignatureNorwaySample.xml** (for example, [the file for release/9.34](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.34/src/FiscalIntegration/SequentialSignatureNorway/CommerceRuntime/DocumentProvider.SequentialSignNorway/Configuration/DocumentProviderSequentialSignatureNorwaySample.xml)).
    1. Download the fiscal connector configuration file at **Connector.SequentialSignNorway \> Configuration \> ConnectorSequentialSignatureNorwaySample.xml** (for example, [the file for release/9.34](https://github.com/microsoft/Dynamics365Commerce.Solutions/blob/release/9.34/src/FiscalIntegration/SequentialSignatureNorway/CommerceRuntime/Connector.SequentialSignNorway/Configuration/ConnectorSequentialSignatureNorwaySample.xml)).

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
- **Key Vault client** – An interactive client ID of the Azure Active Directory (Azure AD) application that is associated with the Key Vault storage for authentication purposes. This client should have access to read secrets from the storage.
- **Key Vault secret key** – A secret key that is associated with the Azure AD application that is used for authentication in the Key Vault storage.
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
    - **Activate health check** – For more information about the health check feature, see [Fiscal registration health check](./fiscal-integration-for-retail-channel.md#fiscal-registration-health-check).

> [!NOTE]
> - Only the **SHA1** cryptographic hash algorithm is currently acceptable for Norway.
> - The default store name and store location are added to simplify the process of searching local certificates in CRT. X509StoreProvider has a list of folders where certificates are stored. If the default store name and the default store location aren't specified, X509StoreProvider tries to find a certificate in all the folders on its list.

### Configure channel components

### Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

1. Clone or download the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository. Select a correct release branch version according to your SDK/application version. For more information, see [Download Retail SDK samples and reference packages from GitHub and NuGet](../dev-itpro/retail-sdk/sdk-github.md).
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

### Production environment

Follow the steps in [Set up a build pipeline for a fiscal integration sample](fiscal-integration-sample-build-pipeline.md) to generate and release the Cloud Scale Unit and self-service deployable packages for the fiscal integration sample. The **SequentialSignatureNorway build-pipeline.yaml** template YAML file can be found in the **Pipeline\\YAML_Files** folder of the [Dynamics 365 Commerce Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repository.

### Enable the digital signature in offline mode for Modern POS

To enable the digital signature in offline mode for Modern POS, you must follow these steps after you activate Modern POS on a new device.

1. Sign in to POS.
1. On the **Database connection status** page, make sure that the offline database is fully synced. When the value of the **Pending downloads** field is **0** (zero), the database is fully synced.
1. Sign out of POS.
1. Wait for the offline database to be fully synced.
1. Sign in to POS.
1. On the **Database connection status** page, make sure that the offline database is fully synced. When the value of the **Pending transactions in offline database** field is **0** (zero), the database is fully synced.
1. Reopen Modern POS.
