---
# required metadata

title: User-defined certificate profiles for retail stores
description: This topic provides an overview of the usage of certificates in retail stores. 
author: josaw
manager: annbe
ms.date: 10/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailFormLayout, RetailParameters
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.validFrom: 2020-10-09
ms.dyn365.ops.version: 10.0.15

---
# User-defined certificate profiles for retail stores

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

## Overview

This topic provides an overview of the certificate profiles that are available in Dynamics 365 Commerce. This functionality extends the [Manage secrets for retail channels](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/manage-secrets) feature with support of the local certificates. 

While operating in the offline mode, the point of sale (POS) can't access the certificates stored in the Azure Key vault, and the local certificate should be used instead. The following capabilities are supported.
  - Using local certificates in key vault fallback scenarios.
  - Using local certificates without key vault (e.g. in on-premises installation).
  - Gradual update of certificates, where some stores terminals use a new version of the certificate and other stores and terminals continue using the previous version.

The certificates profiles functionality enables you to specify a default certificate and set the order that certificates are searched within the same certificate profile. It also provides a similar setup approach for local and key vault certificates - add company-specific settings for certificates but have the unique cross-company identifier for each certificate used in the Commerce channels.

### Scenarios 

The certificate profiles functionality supports the following scenarios in the Commerce channels.
  - Using a local certificate in key vault fallback scenarios, for example:
    - When the key vault storage is not accessible,
    - If a certificate is not found in the key vault storage,
    - When POS is operating in the offline mode.
  - Using local certificates only without storing them in the key vault (e.g. in on-premises installation).
  - Gradual update of certificates with use of new version of a certificate only in stores or terminals where the new version is already available.
  - Using the same certificate in several companies.

## Set up certificate profiles

This section describes how to set up certificate profiles. Before you use certificate profiles in Commerce channels, configure the following settings. 

1. Enable the **User-defined certificate profiles for retail stores** feature on the **Feature management** page.

2. Go to **System administration \> Setup \> Certificate profiles**. Create a new record and enter a value for these fields: **Certificate profile**, **Name**, **Description**.

    > [!NOTE]
    > The **Certificate profile** is a unique identifier of a certificate across all companies and Commerce components.

3. Add a line on the **Legal entities** tab and select a company that the current certificate profile will be used for. Add other legal entities in certificate profile lines if necessary.

4. Select **Settings** to enter company-specific settings for the certificate profile.

### Certificate profile settings

The **Certificate profile settings** page opens when you select **Settings** in certificate profile lines. This page allows you to specify which certificates can be used when the current certificate profile is called in the Commerce channels, and the order that certificates will be searched.

> [!NOTE]
> The **Priority** field is assigned automatically. The value **1** is the highest priority. When a new line is added on the **Certificate profile settings** page, it gets the priority that follows the last existing line. To change the priority of a specific line, put your cursor on the line and select the **Move up** button to increase priority, or **Move down** to decrease priority.

The following parameters need to be specified when a new line is added to the **Certificate profile settings** page.

  - **Location type**: This parameter identifies where the certificate is stored. It has two values: **Local certificate** and **Key Vault**.
  - **Key Vault certificate**: This parameter is required if **Location type** is set to **Key Vault**. Specify a **Key Vault certificate secret** in this field.

    > [!NOTE]
    > Before using a Key Vault certificate in certificate profiles, upload a certificate to the key vault storage and follow the instructions provided in the [Set up the Azure Key Vault client](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/setting-up-azure-key-vault-client) topic. 

  - **Store name**: This parameter is optional and available for local certificates only. It enables you to specify a default store name for searching local certificates. 

  - **Store location**: This parameter is optional and available for local certificates only. It enables you to specify a default store location for searching local certificates. 

    > [!NOTE]
    > The default store name and store location are added to simplify searching local certificates in the Commerce runtime. The X509StoreProvider has a list of folders where certificates are stored. It attempts to find a certificate in the other folders on the list if the default store name and the default store location aren't specified.

  - **Thumbprint**: This field is mandatory and available only for local certificates. The certificate thumbprint must be specified here.

  - **Comments**: This field is optional and enables users to make notes.

### Workflow: searching certificates in the Commerce runtime

When a certificate profile is called in the Commerce runtime, the basic workflow for searching the certificate is as follows.

1. The system identifies if the certificate profile has company-specific settings for the current legal entity. 
1. The system attempts to find the certificate using the **Certificate profile settings** from the line with the **Priority** equal to 1. 
    - If the **Location type** is set to **Key Vault**, the certificate is searched in the **Key vault parameters** first by the **Key Vault certificate secret** field, and then it's searched in the key vault storage.
    - If the **Location type** is set to **Local certificate**, the X509StoreProvider searches the certificate by default store name and store location if these parameters are specified, and then in all other folders from its list of folders.
1. If the certificate isn't found, the same process is followed for the line with the **Priority** equal to 2, etc.

> [!NOTE]
> If the certificate profile has no settings for the current legal entity or if searching the certificate was unsuccessful for all lines of the **Certificate profile settings** page, it means that the certificate is not found.

#### Caching results of searching certificates

The results of searching certificates are cached. The default expiration time for a cache is 1 hour. This time can be customized for up to 24 hours.


### Gradual update

When a new version of the certificate is introduced, but it can't be updated in all stores at the same time, the certificate profiles functionality allows the certificate to be updated gradually.

1. Find a certificate profile and the line that should be updated, and select **Settings**.
1. Add a new line and specify settings related to the latest version of the certificate.
1. Increase the **Priority** of the new line by using the **Move up** button, and set it above the line with the previous version of the same certificate.

    > [!NOTE]
    > In the Commerce runtime, the new version of the certificate will be called first, and if the certificate isn't updated yet in a specific store or terminal, the previous version will be called.


