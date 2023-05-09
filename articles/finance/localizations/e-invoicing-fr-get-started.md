---
# required metadata

title: Get started with the Electronic invoicing for France
description: This article provides information that will help you get started with Electronic invoicing for France in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
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

This article provides information that will help you get started with Electronic invoicing for France. It guides you through the configuration steps that are country-dependent in Regulatory Configuration Service (RCS) and in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md).

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

## Finance configuration

### Prerequisites

The primary address of the legal entity must be in France.
Feature management key **(France) Electronic invoicing integration with Chorus Pro** must be enabled.

> [!NOTE]
> If apart from having infomration about sucessful or failed document submittion you want want to have possibility to track status of submitted document at Chorus pro you need to enable two more feature management keys: **Extended document identification in submission log** and **Execute update actions for submitted documents**.

### Configure legal entity data

#### Enter a legal entity's address

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity, and then, on the **Addresses** FastTab, add a valid French primary address for the legal entity.

> [!NOTE]
> Make sure that the following mandatory address elements are defined: country/region code, ZIP/postal code, city, and building number.

#### Enter a legal entity and a customer SIRET 

Use the information in [NAF codes and siret numbers](emea-fra-naf-codes-siret-numbers.md) and [Set up NAF codes and Siret numbers](tasks/fr-00003-naf-codes-siret-numbers.md) articles to set up NAF codes and Siret numbers. Alternatively you can use [Registration IDs](emea-registration-ids.md) to setup SIRET number.

### Setup project manager account

When you sumbit work invoices you may use apart from contrating authority (invoice account) also a newly intoduced party **Project manager**. The new party needs to be setup as a customer account and then can be used when posting invoices. Use below procedure to enable project manager for a project invoice.
1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**
2. Expand **Funding sources** and in **Project manager** select a customer account **Project contracts** \> **Project contracts** \> **Project contracts**

> [!NOTE]
> **Project manager** is only available for Funding type = Customer..

### Define electronic invoice frameworks

1. Go to **Accounts receivable** \> **Setup** \> **Electronic invoice frameworks**.
2. In **Type** enter elctronic invoicing framework. 

> [!NOTE]
> When no electronic invoice framework is confugyured and used, all invoices are sent as A1 - simple invoice. You can use following codes for invoice framework to attribute work invoices: A4 , A7, A8, A9, A10, A12, A13, A14 and A22. Refer official documentation for more details [Invoicing framework and transmission modes](https://communaute.chorus-pro.gouv.fr/documentation/submit-works-invoices-for-suppliers-contracting-party-subcontracting-co-contracting/?lang=en#1530527446538-8a6bf25f-3ff8).

### Set up Chorus Pro lectronic document parmaters
You can enable SIRET numbers and service code validation prior posting and invoice.

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
2. Expand **Chorus Pro** tab to set up:
	- Web service URL
	- Login service URL
	- Client Id
	- Client secret
	- Technical user name
	- Technical user password

> [!NOTE]
> It is highly recomended to use Azure Key Vault storage for storing those secrets. Refer to [Set up the Azure Key Vault client](setting-up-azure-key-vault-client.md) for details.	
	
3. Enable **SIRET and service code validation** parameter
4. In **Report format** select a cofigurable business document that will be used to print a submission report.

> [!NOTE]
> If you want to creatae a new submission report instead of customizing default one, you should use **DocumentSubmitted** model name and **SubmittedInvoice** mapping name for integration point.


## Issue electronic invoices

When you've completed all the required configuration steps, you can generate and submit electronic invoices for posted invoices. For more information about how to generate electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

In France, you may add addtional information prior executing the standard invoice posting procedure. To provide extra information for invoices, follow these steps in your applibale business process.

For Sales orders or Free text invoices:
1. Go to **Accounts receivable** \> **Orders** \> **All sales orders** or **Accounts receivable** \> **Invoices** \> **All free text invoices** 
2. When you swith to **Header** view you can select:
	- Electronic invoice framweork type
	- Invoice aacount service code (if you enabled **SIRET and service code validation** parameter, the list of available service codes will be obtained from Chorus Pro)
	- Project manager
For project invoice:
1. Create a new or open created **Project management and accounting** \> **Proejct invoices** \> **Project invoic proposals** 
2. In invoice proposal header you can select:
	- Electronic invoice framework type
	- Funding source service code
	- Project manager
	- Project manager service code

You can inquire about the results of the submission at **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log** and use **Electronic document** \> **Generate report** fucntion in the form to generate a sumission report.

## Receive electronic invoices

You can use **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents** to import documents from Chorus Pro. Once process executed sucessfuly, imported documents will be present in **Pending vendor invoice** workspace, where when needed addtional attributes for received docuemnt might be added:
- Electronic invoice framework type
- Invoice account service code
- Project manager
- Project manager service code.
For more details refer to [Use the electronic invoicing service to import vendor invoices](e-invoicing-get-started-import-vendor-invoices.md)

## Additional resources

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md)
- [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md)
