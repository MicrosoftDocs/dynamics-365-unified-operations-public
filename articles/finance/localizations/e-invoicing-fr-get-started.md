---
# required metadata

title: Get started with Electronic invoicing for France
description: Learn how to get started with Electronic invoicing for France in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: dkalyuzh
ms.date: 05/17/2023
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

# Get started with Electronic invoicing for France

[!include [banner](../includes/banner.md)]

Learn more about how to get started with Electronic invoicing for France. This article guides you through the configuration steps that are country/region-dependent in the Regulatory Configuration Service (RCS) and in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Get started with the Electronic invoicing](e-invoicing-get-started.md).

## Country/region-specific configuration for the French Chorus Pro submission (FR) Electronic invoicing feature

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

## Country/region-specific configuration of the application setup for the French Chorus Pro submission (FR) Electronic invoicing feature

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

- The primary address of the legal entity must be in France.
- The following Feature management key must be enabled: **(France) Electronic invoicing integration with Chorus Pro**.

> [!NOTE]
> If you want to be able to track the status of submitted documents in Chorus Pro, you must enable two features in the **Feature management** workspace: **Extended document identification in submission log** and **Execute update actions for submitted documents**.

### Configure legal entity data

#### Enter a legal entity's address

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity, and then, on the **Addresses** FastTab, add a valid French primary address for the legal entity. Make sure that the following mandatory address elements are defined:

    - Country/region code
    - ZIP/postal code
    - City
    - Building number

#### Enter a legal entity and a customer Siret number

Use the information in [NAF codes and siret numbers](emea-fra-naf-codes-siret-numbers.md) and [Set up NAF codes and Siret numbers](tasks/fr-00003-naf-codes-siret-numbers.md) to set up NAF codes and Siret numbers. Alternatively, you can use [registration IDs](emea-registration-ids.md) to set up Siret numbers.

### Set up the project manager account

When you submit work invoices, you can use the **Project manager** party. Before you use it, the new party type must be set up as a customer account. It can then be used when invoices are posted.

Follow these steps to enable the project manager for a project invoice.

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
2. On the **Funding sources** tab, in the **Project manager** field, select a customer account. Then select **Project contracts** \> **Project contracts** \> **Project contracts**.

    > [!NOTE]
    > The **Project manager** field is available only when the funding type is **Customer**.

### Define electronic invoice frameworks

1. Go to **Accounts receivable** \> **Setup** \> **Electronic invoice frameworks**.
2. In the **Type** field, enter the electronic invoicing framework.

If no electronic invoice framework is configured, all invoices are sent as **A1 - simple invoice**. Use the following codes for the invoice framework to attribute work invoices: A4 , A7, A8, A9, A10, A12, A13, A14, and A22. For more information, see [Invoicing framework and transmission modes](https://communaute.chorus-pro.gouv.fr/documentation/submit-works-invoices-for-suppliers-contracting-party-subcontracting-co-contracting/?lang=en#1530527446538-8a6bf25f-3ff8).

### Set up Chorus Pro electronic document parameters

You can enable Siret numbers and service code validation before you post and invoice documents.

1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
2. On the **Chorus Pro** tab, add the following information:

    - Web service URL
    - Login service URL
    - Client ID
    - Client secret
    - Technical user name
    - Technical user password

    > [!NOTE]
    > We recommend that you use Azure Key Vault storage to store the secrets. For more information, see [Set up the Azure Key Vault client](setting-up-azure-key-vault-client.md).

3. Enable the **SIRET and service code validation** parameter.
4. In the **Report format** field, select the configurable business document to use when a submission report is printed.

> [!NOTE]
> To create a new submission report instead of customizing a default report, use the **DocumentSubmitted** model name and the **SubmittedInvoice** mapping name for the integration point.

To obtain the latest processing details of invoice from Chorus pro into submission log, you must configure the response types in Finance.

Follow these steps to complete the configuration.
1. Go to Organization administration > Setup > Electronic document parameters.
2. In the Electronic document section, add records for the Customer Invoice journal, Project invoice tables.
3. For each table name, set the Document context and Electronic document model mapping fields in accordance with Set up [Electronic invoicing parameters](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-set-up-parameters#set-up-electronic-document-parameters)
4. For the Customer Invoice journal table name, select Response types.
5. Create a new response type that has the same name that was defined for the related variable in the corresponding feature setups in RCS.
    1. In the Submission status field, select Pending.
    2. In the Data entity name field, select Sales invoice Chorus Pro entity.
    3. In the Model mapping field, select Chorus Pro invoice response data.
7. Create another response type that has the same name that was defined for the related variable in the corresponding feature setups in RCS.
    1. In the Submission status field, select Pending update actions execution.
    2. In the Data entity name field, select Sales invoice Chorus Pro entity.
    3. In the Model mapping field, select Chorus Pro invoice response data.

## Issue electronic invoices

After you've completed all the required configuration steps, you can generate and submit electronic invoices for posted invoices. For more information about how to generate electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

In France, you can add extra information before you run the standard invoice posting procedure. To add extra information for invoices, follow these steps in the applicable business process.

**For sales orders or free text invoices**

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders** or **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Switch to the **Header** view, and select the following information:

    - Electronic invoice framework type
    - Invoice account service code

        > [!NOTE]
        > If you enabled the **SIRET and service code validation** parameter in the previous section, the list of available service codes is obtained from Chorus Pro.

    - Project manager

**For project invoices**

1. Go to **Project management and accounting** > **Project invoices** \> **Project invoice proposals**.
2. Open an existing invoice proposal, or create a new one.
3. Switch to the **Header** view, and select the following information:

    - Electronic invoice framework type
    - Funding source service code
    - Project manager
    - Project manager service code

To view the submission results, go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**, and then select **Electronic document** \> **Generate report** to generate a submission report.

## Receive electronic invoices

To import documents from Chorus Pro, go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Receive electronic documents**. After the import process is completed, the received documents are available in the **Pending vendor invoice** workspace, where you can add more attributes to them as required. Here are some of the attributes that you can add:

- Electronic invoice framework type
- Invoice account service code
- Project manager
- Project manager service code

For more information, see [Use the electronic invoicing service to import vendor invoices](e-invoicing-get-started-import-vendor-invoices.md)

## Additional resources

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md)
- [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md)
