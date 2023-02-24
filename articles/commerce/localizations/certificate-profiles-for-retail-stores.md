---
title: User-defined certificate profiles for retail stores
description: This article provides an overview of the certificate profiles that are available in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: v-chgriffin
ms.search.validFrom: 2020-10-09
ms.dyn365.ops.version: 10.0.15
ms.search.industry: Retail
ms.search.form: RetailFormLayout, RetailParameters
---
# User-defined certificate profiles for retail stores

[!include [banner](../includes/banner.md)]

This article provides an overview of the certificate profiles that are available in Microsoft Dynamics 365 Commerce. This functionality extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature by adding support for local certificates.

While the point of sale (POS) is running in offline mode, it can't access the certificates that are stored in Microsoft Azure Key Vault. The local certificate should be used instead. The following capabilities are supported:

- Using local certificates in Key Vault fallback scenarios
- Using local certificates without Key Vault (for example in an on-premises installation)
- Gradual update of certificates, where some stores and terminals use a new version of the certificate, but other stores and terminals continue to use the previous version

The certificate profiles functionality lets you specify a default certificate and set the order that certificates in the same certificate profile are searched in. This functionality also provides a similar setup approach for local certificates and Key Vault certificates. You can add company-specific settings for certificates, but the unique cross-company identifier for each certificate can be used in the Commerce channels.

### Scenarios

The certificate profiles functionality supports the following scenarios in the Commerce channels:

- Use a local certificate in Key Vault fallback scenarios. Here are some examples of these fallback scenarios:

    - The key vault storage isn't accessible.
    - A certificate isn't found in the key vault storage.
    - The POS is running in offline mode.

- Use local certificates, but without storing them in Key Vault (for example, in an on-premises installation).
- Do a gradual update of certificates, where a new version of the certificate is used only in stores or on terminals where the new version is already available.
- Use the same certificate in several companies.

## Set up certificate profiles

The following procedure explains how to set up certificate profiles.

### Set up Key Vault

The following steps must be completed before you can use a digital certificate that is stored in Key Vault.

1. Create a Key Vault storage account. We recommend that you deploy the storage account in the same geographical region as the Commerce Scale Unit.
1. Upload the digital certificate to the Key Vault storage account.
1. Authorize the Application Object Server (AOS) application to read secrets from the Key Vault storage account.

For more information about how to work with Key Vault, see [Get started with Azure Key Vault](/azure/key-vault/key-vault-get-started).

### Set up system parameters

Before you configure certificate profiles in the Commerce channels, you must enable Commerce to use both certificates that are stored in Key Vault and certificate profiles.

To set up system parameters in Commerce headquarters, follow these steps.

1. On the **System parameters** page, set the **Use advanced certificate store** option to **Yes**.
1. In the **Feature management** workspace, turn on the **User-defined certificate profiles for retail stores** feature.

### Set up Key Vault parameters

On the **Key Vault parameters** page, you must specify the following parameters for accessing the Key Vault storage:

- **Name** and **Description** – The name and description of the Key Vault storage account.
- **Key Vault URL** – The URL of the Key Vault storage account.
- **Key Vault client** – An interactive client ID of the Azure Active Directory (Azure AD) application that is associated with the Key Vault storage account for authentication purposes. This client should have access to read secrets from the storage account.
- **Key Vault secret key** – A secret key that is associated with the Azure AD application that is used for authentication in the Key Vault storage account.
- **Name**, **Description**, and **Secret reference** – The name, description, and secret reference of the certificate.

For more information, see [Set up the Azure Key Vault client](../../finance/localizations/setting-up-azure-key-vault-client.md).

### Configure a certificate profile

To configure a certificate profile in Commerce headquarters, follow these steps.

1. Go to **System administration \> Setup \> Certificate profiles**.
1. On the Action Pane, select **New** to create a record.
1. Enter values in the **Certificate profile**, **Name**, and **Description** fields.

    > [!NOTE]
    > The certificate profile is a unique identifier of a certificate across all companies and Commerce components.

1. On the **Legal entities** FastTab, select **Add** to add a line.
1. Under **Legal entity**, select the legal entity (company) that the current certificate profile should be used for.

    If the certificate profile should be used for multiple legal entities, repeat steps 4 and 5 to add a line for each additional legal entity.

1. Select **Settings** to open the **Certificate profile settings** page, where you can enter company-specific settings for the certificate profile. Specify which certificates can be used when the current certificate profile is called in the Commerce channels. Add as many certificates as you require, and set priorities for them. If a certificate that has a higher priority isn't available, the next certificate will be used, based on priority. For more information, see the [Workflow: Searching certificates in the Commerce runtime](#workflow-searching-certificates-in-the-commerce-runtime) section.

    > [!NOTE]
    > The **Priority** field is automatically set. A value of **1** represents the highest priority. When a new line is added on the **Certificate profile settings** page, its priority is set to a number that is one more than the priority of the previous line. To change the priority of a specific line, select the line, and then select either **Move up** to increase the priority or **Move down** to decrease the priority.

1. When you add a new line on the **Certificate profile settings** page, set the following fields:

    - **Location type** – Select the location where the certificate is stored. This field has two possible values: **Local certificate** and **Key Vault**.
    - **Key Vault certificate** – This field is required if you set the **Location type** field to **Key Vault**. Use it to specify a Key Vault certificate secret.
    - **Store name** – This field is optional and is available only if you set the **Location type** field to **Local certificate**. Use it to specify a default store name that should be used to search local certificates.
    - **Store location** – This field is optional and is available only if you set the **Location type** field to **Local certificate**. Use it to specify a default store location that should be used to search local certificates.

        > [!NOTE]
        > The default store name and store location are added to simplify the process of searching local certificates in the Commerce runtime. X509StoreProvider has a list of folders where certificates are stored. If the default store name and the default store location aren't specified, X509StoreProvider tries to find a certificate in the other folders in its list. For more information about available values for the store name and store location, see [StoreName Enum](/dotnet/api/system.security.cryptography.x509certificates.storename) and [StoreLocation Enum](//dotnet/api/system.security.cryptography.x509certificates.storelocation).

    - **Thumbprint** – This field is required and is available only if you set the **Location type** field to **Local certificate**. Use it to specify the certificate thumbprint.

        > [!IMPORTANT]
        > You must ensure that the user who runs the application that has to use the local certificate (for example, Store Commerce app in the offline mode) has at least read-only access to the private key of the certificate.

    - **Comments** – This field is optional and lets users enter notes.

## Workflow: Searching certificates in the Commerce runtime

Here is the basic workflow that is used to search for a certificate when a certificate profile is called in the Commerce runtime.

1. The system identifies whether the certificate profile has company-specific settings for the current legal entity.
1. The system tries to find the certificate by using the values on the **Certificate profile settings** page for the line where the **Priority** field is set to **1**.

    - If the **Location type** field is set to **Key Vault**, the value of the **Key Vault certificate secret** field is used to search for the certificate on the **Key vault parameters** page. The certificate is then searched for in the key vault storage.
    - If the **Location type** field is set to **Local certificate**, X509StoreProvider first searches for the certificate by using the default store name and store location, if these parameters are specified. It then searches in all other folders on its list of folders.

1. If the certificate isn't found, the process is repeated for the line where the **Priority** field is set to **2**, and so on.

> [!NOTE]
> If the certificate profile has no settings for the current legal entity, or if the certificate search is unsuccessful for all lines on the **Certificate profile settings** page, the certificate isn't found.

### Caching the results of certificate searches

The results of certificate searches are cached. The default expiration time for a cache is one hour. However, this time can be customized and can be set to a maximum value of 24 hours.

## Gradual update

If a new version of the certificate is introduced, but it can't be updated in all stores at the same time, the certificate profiles functionality enables the certificate to be updated gradually.

1. Find a certificate profile and the line that should be updated, and then select **Settings**.
1. Add a line, and specify settings that are related to the latest version of the certificate.
1. Increase the **Priority** value of the new line. Use the **Move up** button to move the line so that it's above the line for the previous version of the same certificate.
> [!NOTE]
> In the Commerce runtime, the new version of the certificate will be called first. If the certificate hasn't yet been updated in a specific store or on a specific terminal, the previous version will be called.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
