---
# required metadata

title: Get started with the Electronic invoicing add-on for France
description: This article provides information that will help you get started with the Electronic invoicing add-on for France.
author: dkalyuzh
ms.date: 07/07/2022
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2022-00-02
ms.dyn365.ops.version: AX 10.0.29

---

# Get started with the Electronic invoicing add-on for France

[!include [banner](../includes/banner.md)]

This article provides information that will help you get started with Electronic invoicing for France. It guides you through the configuration steps that are country-dependent in Regulatory Configuration Service (RCS). These steps complement the steps that are described in [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md).

## Country-specific configuration for French Chorus Pro submission (FR) Electronic invoicing feature

Some steps are required to configure the **French Chorus Pro submission (FR)** Electronic invoicing feature. Some of the parameters from the configuration are published with default values. These values must be reviewed and updated so that they better reflect your business operations.

### Prerequisites

Before you begin the procedures in this article, complete the following prerequisites:

- Become familiar with Electronic invoicing. For more information, see [Electronic invoicing overview](e-invoicing-service-overview.md).
- Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:

    - [Sign up for and install the Electronic Invoicing service](e-invoicing-sign-up-install.md)
    - [Set up Azure resources for Electronic invoicing](e-invoicing-set-up-azure-resources.md)
    - [Install the add-in for microservices in Lifecycle Services](e-invoicing-install-add-in-microservices-lcs.md)
    - [Activate and setup integration with Electronic invoicing](e-invoicing-activate-setup-integration.md) – Use the information in this article to activate the integration between your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management app and the Electronic Invoicing service.
    - [NAF codes and siret numbers](emea-fra-naf-codes-siret-numbers.md) and [Set up NAF codes and Siret numbers](tasks/fr-00003-naf-codes-siret-numbers.md) – Use the information in these articles to set up NAF codes and Siret numbers in your legal entities. 

- Your organization must be registered to operate with Chorus Pro. Microsoft provides integration with Chorus pro in OAuth2 Mode via an application programming interface (API). For detailed information about Chorus Pro registration and application activation, see the [official documentation](https://communaute.chorus-pro.gouv.fr/documentation/help-for-api-developers-in-oauth2-mode/).

    Follow these steps to register with Chorus Pro.

    1. Go to the [PISTE portal](https://piste.gouv.fr/en/component/apiportal/registration) to start your registration. 
    2. Register an application, and activate Open Authorization (OAuth) credentials.
    3. Copy and save the client ID of the OAuth credentials and the secret key. You will use this information in later steps.
    4. Go to the [Chorus Pro portal](https://portail.chorus-pro.gouv.fr/aife_csm/?id=aife_enrollment) to register. 
    5. Create a technical account for API access. For more information, see [Creation of a technical account for API access in production](https://communaute.chorus-pro.gouv.fr/documentation/creation-of-a-technical-account-for-an-api-access-in-production/).
    6. Copy the user ID of the technical account and the password. You will use this information in later steps.

## Country-specific configuration of the application setup for the French Chorus Pro submission (FR) Electronic invoicing feature

Some of the parameters from the **French Chorus Pro submission (FR)** electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review and update the default values as required, so that they better reflect your business operations.

1. In the Azure key vault, create secrets and the corresponding reference to them. For more information, see [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md).
2. Import the latest version of the **French Chorus Pro submission (FR)** globalization feature as described in [Import features from the Global repository](e-invoicing-import-feature-global-repository.md).
3. Create a copy of the imported globalization feature, and select your configuration provider. For more information, see [Create a Globalization feature](e-invoicing-create-new-globalization-feature.md).
4. On the **Versions** tab, verify that the **Draft** version is selected.
5. On the **Setups** tab, in the grid, select the **UBL Sales invoice derived** feature setup.
6. Select **Edit**, and then, on the **Processing pipeline** tab, in the **Processing pipeline** section, select **(Preview) Integrate with French Chorus Pro** with the action name **French Chorus Pro submit**.
7. In the **Parameters** section, in the **Client ID secret name** field, select the secret name that you created for the client ID in the key vault.
8. In the **Client Secret secret name** field, select the secret name you created for the client secret in the key vault.
9. In the **Technical login secret name** field, select the secret name that you created for technical account sign-in in the key vault.
10. In the **Technical password secret name** field, select the secret name that you created for the technical account password in the key vault.
11. On the **Processing pipeline** tab, in the **Processing pipeline** section, select **Integrate with French Chorus Pro** with the action name **French Chorus Pro request status**.
12. In the **Parameters** section, in the **Client ID secret name** field, select the secret name that you created for the client ID in the key vault.
13. In the **Client Secret secret name** field, select the secret name you created for the client secret in the key vault.
14. In the **Technical login secret name** field, select the secret name that you created for technical account sign-in in the key vault.
15. In the **Technical password secret name** field, select the secret name that you created for the technical account password in the key vault.
16. Select **Save**, and then close the page.
17. Repeat steps 6 through 16 for the **UBL Project invoice derived** feature setup, **UBL Sales Credit Note derived** feature setup, and **UBL Project Credit Note derived** feature setup.

## Finance business data configuration

### Prerequisites

The primary address of the legal entity must be in France.

### Configure legal entity data

#### Enter a legal entity's address

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity, and then, on the **Addresses** FastTab, add a valid primary address for the legal entity.

> [!NOTE]
> Make sure that the following mandatory address elements are defined: country/region code, ZIP/postal code, city, and building number.

#### Enter a legal entity's SIRET 

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity, and then, on the **Tax registration** FastTab, in the **Tax registration number** field, enter a valid tax registration number for the legal entity. This number will be used as the seller's tax identification number (SIRET).

## Additional resources

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md)
- [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md)
