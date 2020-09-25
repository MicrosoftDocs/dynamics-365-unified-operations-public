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

## Overview

This topic is an overview of the certificate profiles that are available in Dynamics 365 Commerce. This functionality extends the [Manage secrets for retail channels](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/manage-secrets) feature with support of the local certificates. 

While operating in the offline mode, Retail POS cannot access the certificates stored in the Azure Key vault, and the local certificate should be used instead. The feature supports the following capabilities:
  - Using local certificates in key vault fallback scenarios.
  - Using local certificates without key vault (e.g. in on-premises installation).
  - Gradual update of certificates, where some stores terminals use a new version of the certificate, while other stores and terminals continue using the previous version.

  The certificates profiles functionality allows specifying a default certificate an order of searching certificates within the same certificate profile. It also provides a similar set up approach for local and key vault certificates - add company-specific settings for certificates but have the unique cross-company identifier for each certificate used in the Commerce channels.

### Scenarios 

The certificate profiles functionality supports the following scenarios in the Commerce channels:
  - Use a local certificate in in key vault fallback scenarios, for example:
    - When the key vault storage is not accessible
    - If a certificate is not found in the key vault storage
    - When POS is operating in the offline mode
  - Using local certificates only without storing them in the key vault (e.g. in on-premises installation)
  - Gradual update of certificates with using new version of a certificate only in stores or terminals, where this new version is already available
  - Using the same certificate in several companies

## How to set up certificate profiles

This section describes how to set up certificate profiles. Before you use certificate profiles in the Commerce channels, you should configure the following settings. 

1. Enable the **User-defined certificate profiles for retail stores** feature on the **Feature management** page.

2. Open the **Certificate profiles** page (**System administration \> Setup \> Certificate profiles**). Create a new record and specify fields: **Certificate profile**, **Name**, **Description**.

    > [!NOTE]
    > The **Certificate profile** is a unique identifier of a certificate across all companies and Commerce components.

3. Add line on the **Legal entities** tab and select a company where the current certificate profile is planned to be used. Add other legal entities in certificate profile lines if necessary.

4. Click the **Settings** button to enter company-specific settings of the certificate profile.

### Certificate profile settings

The **Certificate profile settings** form is opened when you click the **Settings** button in certificate profile lines. This form allows specifying what certificates can be used when the current certificate profile is called in the Commerce channels, and the order of searching certificates.

> [!NOTE]
> The **Priority** field is assigned automatically, value **1** is the highest priority. 
When new line is added on the **Certificate profile settings** form, it gets the priority next after the last existing line. 
To change the priority of a specific line you should set a cursor on this line and then click the **Move up** button (to increase priority) or **Move down** button (to decrease priority).

The following parameters need to be specified when new line is added on the **Certificate profile settings** form.

  - **Location type** - this parameter identifies where the certificate is stored and it has two values: **Local certificate** and **Key Vault**.
  - **Key Vault certificate** - this parameter is mandatory if the **Location type** is set to **Key Vault**. You should specify a **Key Vault certificate secret** in this field.

    > [!NOTE]
    > Before using a Key Vault certificate in certificate profiles you should upload a certificate to the key vault storage and follow the instructions provided in the [Set up the Azure Key Vault client](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/setting-up-azure-key-vault-client). 

  - **Store name** - this parameter is optional and available for local certificates only. It allows specifying a default store name for searching local certificates. 

  - **Store location** - this parameter is optional and available for local certificates only. It allows specifying a default store location for searching local certificates. 

    > [!NOTE]
    > The default store name and store location are added to simplify searching local certificates in the Commerce runtime. The X509StoreProvider has a list of folders, where certificates are stored, and it attempts to find a certificate in all other folders from the list if the default store name and the default store location are not specified.

  - **Thumbprint** - this field is mandatory and available only for local certificates. The certificate thumbprint must be specified here.

  - **Comments** - this field is option and it allows users to make notes.

### Workflow of searching certificates in the Commerce runtime

When a certificate profile is called in the Commerce runtime, the basic workflow of searching the certificate will be as described below.

  - The system identifies if the certificate profile has company-specific settings for the current legal entity. 

  - The system attempts to find the certificate using the **Certificate profile settings** from the line with the **Priority** equal to 1. 

    - If the **Location type** is set to **Key Vault**, the certificate is searched in the **Key vault parameters** first by the **Key Vault certificate secret** field, and then it is searched in the key vault storage.

    - If the **Location type** is set to **Local certificate**, the X509StoreProvider searches the certificate by default store name and store location if these parameters are specified, and then in all other folders from its list of folders.

  - If the certificate is not found, it repeats the same for the line with the **Priority** equal to 2, and so on.

> [!NOTE]
> If the certificate profile has no settings for the current legal entity or searching the certificate was unsuccessful for all lines of the **Certificate profile settings** form, this means that the certificate is not found.

#### Caching results of searching certificates

The results of searching certificates are cached. The default expiration time for cache is 1 hour. It can be exceeded in a customization up to 24 hours.


### Gradual update

When a new version of the certificate is introduced, but updating it cannot be updated in all stores at the same time, the certificate profiles functionality allows updating it gradually.

The recommended approach is the following:

  - Find a certificate profile and its line that should be updated, and click **Settings** button.

  - Add a new line and specify settings related to the latest version of the certificate.

  - Increase the **Priority** of the new line by using the **Move up** button, and set it above the line with the previous version of the same certificate.

    > [!NOTE]
    > As a result in the Commerce runtime the new version of the certificate will be called first, and if the certificate is not updated yet in a specific store a terminal, the previous version will be called.


