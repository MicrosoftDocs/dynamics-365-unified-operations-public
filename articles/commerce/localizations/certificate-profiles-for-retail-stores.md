---
# required metadata

title: User-defined certificate profiles for retail stores
description: This topic provides an overview about how certificates are used in retail stores.
author: josaw
ms.date: 10/09/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2020-10-09
ms.dyn365.ops.version: 10.0.15

---
# User-defined certificate profiles for retail stores

[!include [banner](../includes/banner.md)]


## Overview

This topic provides an overview of the certificate profiles that are available in Microsoft Dynamics 365 Commerce. This functionality extends the [Manage secrets for retail channels](../dev-itpro/manage-secrets.md) feature by adding support for local certificates.

While the point of sale (POS) is running in offline mode, it can't access the certificates that are stored in the key vault. The local certificate should be used instead. The following capabilities are supported:

- Using local certificates in key vault fallback scenarios
- Using local certificates without a key vault (for example in an on-premises installation)
- Gradual update of certificates, where some stores and terminals use a new version of the certificate, but other stores and terminals continue to use the previous version

The certificate profiles functionality lets you specify a default certificate and set the order that certificates in the same certificate profile are searched in. This functionality also provides a similar setup approach for local certificates and Key Vault certificates. You can add company-specific settings for certificates, but the unique cross-company identifier for each certificate can be used in the Commerce channels.

### Scenarios

The certificate profiles functionality supports the following scenarios in the Commerce channels:

- Use a local certificate in key vault fallback scenarios. Here are some examples of these fallback scenarios:

    - The key vault storage isn't accessible.
    - A certificate isn't found in the key vault storage.
    - The POS is running in offline mode.

- Use local certificates, but without storing them in the key vault (for example, in an on-premises installation).
- Do a gradual update of certificates, where a new version of the certificate is used only in stores or on terminals where the new version is already available.
- Use the same certificate in several companies.

## Set up certificate profiles

The following procedure explains how to set up certificate profiles. Before you use certificate profiles in the Commerce channels, follow these steps to configure the settings.

1. In the **Feature management** workspace, turn on the **User-defined certificate profiles for retail stores** feature.
2. Go to **System administration \> Setup \> Certificate profiles**.
3. Create a record, and set the **Certificate profile**, **Name**, and **Description** fields for it.

    > [!NOTE]
    > The certificate profile is a unique identifier of a certificate across all companies and Commerce components.

3. On the **Legal entities** tab, add a line, and select the legal entity (company) that the current certificate profile should be used for. If the certificate profile should be used for multiple legal entities, repeat this step to add a line for each additional legal entity.
4. Select **Settings** to open the **Certificate profile settings** page, where you can enter company-specific settings for the certificate profile.

### Certificate profile settings

When you select **Settings** for certificate profile lines, the **Certificate profile settings** page appears. This page lets you specify which certificates can be used when the current certificate profile is called in the Commerce channels. You can also specify the order that certificates should be searched in.

> [!NOTE]
> The **Priority** field is automatically set. A value of **1** represents the highest priority. When a new line is added on the **Certificate profile settings** page, its priority is set to a number that is one more than the priority of the previous line. To change the priority of a specific line, select the line, and then select either **Move up** to increase the priority or **Move down** to decrease the priority.

When you add a new line to the **Certificate profile settings** page, set the following fields:

- **Location type** – Select the location where the certificate is stored. This field has two possible values: **Local certificate** and **Key Vault**.
- **Key Vault certificate** – This field is required if you set the **Location type** field to **Key Vault**. Use it to specify a Key Vault certificate secret.

    > [!NOTE]
    > Before you use a Key Vault certificate in certificate profiles, be sure to upload a certificate to the key vault storage, and follow the instructions in [Set up the Azure Key Vault client](../../finance/localizations/setting-up-azure-key-vault-client.md).

- **Store name** – This field is optional and is available only if you set the **Location type** field to **Local certificate**. Use it to specify a default store name that should be used to search local certificates.
- **Store location** – This field is optional and is available only if you set the **Location type** field to **Local certificate**. Use it to specify a default store location that should be used to search local certificates.

    > [!NOTE]
    > The default store name and store location are added to simplify the process of searching local certificates in the Commerce runtime. X509StoreProvider has a list of folders where certificates are stored. If the default store name and the default store location aren't specified, X509StoreProvider tries to find a certificate in the other folders on its list.

- **Thumbprint** – This field is required and available only if you set the **Location type** field to **Local certificate**. Use it to specify the certificate thumbprint.
- **Comments** – This field is optional and lets users enter notes.

### Workflow: Searching certificates in the Commerce runtime

Here is the basic workflow that is used to search for a certificate when a certificate profile is called in the Commerce runtime.

1. The system identifies whether the certificate profile has company-specific settings for the current legal entity.
1. The system tries to find the certificate by using the values on the **Certificate profile settings** page for the line where the **Priority** field is set to **1**.

    - If the **Location type** field is set to **Key Vault**, the value of the **Key Vault certificate secret** field is used to search for the certificate on the **Key vault parameters** page. The certificate is then searched for in the key vault storage.
    - If the **Location type** field is set to **Local certificate**, X509StoreProvider first searches for the certificate by using the default store name and store location, if these parameters are specified. It then searches in all other folders on its list of folders.

1. If the certificate isn't found, the process is repeated for the line where the **Priority** field is set to **2**, and so on.

> [!NOTE]
> If the certificate profile has no settings for the current legal entity, or if the certificate search is unsuccessful for all lines on the **Certificate profile settings** page, the certificate isn't found.

#### Caching the results of certificate searches

The results of certificate searches are cached. The default expiration time for a cache is one hour. However, this time can be customized and can be set to a maximum value of 24 hours.

### Gradual update

If a new version of the certificate is introduced, but it can't be updated in all stores at the same time, the certificate profiles functionality enables the certificate to be updated gradually.

1. Find a certificate profile and the line that should be updated, and then select **Settings**.
1. Add a line, and specify settings that are related to the latest version of the certificate.
1. Increase the **Priority** value of the new line. Use the **Move up** button to move the line so that it's above the line for the previous version of the same certificate.

> [!NOTE]
> In the Commerce runtime, the new version of the certificate will be called first. If the certificate hasn't yet been updated in a specific store or on a specific terminal, the previous version will be called.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]