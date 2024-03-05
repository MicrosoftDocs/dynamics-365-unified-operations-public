---
title: Electronic invoicing for Australia and New Zealand
description: This article provides information to help you get started with Electronic invoicing for Australia and New Zealand in Microsoft Dynamics 365 Finance.
author: ilikond
ms.date: 09/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Australia, New Zealand
ms.author: ikondratenko
ms.search.validFrom: 2023-09-01
ms.dyn365.ops.version: AX 10.0.37
ms.assetid: 
ms.search.form: 
---

# Electronic invoicing for Australia and New Zealand

[!include [banner](../../includes/banner.md)]

This article provides information that will help you get started with Electronic invoicing for Australia and New Zealand. It guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Service (RCS) and in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Set up Electronic invoicing](../global/e-invoicing-set-up-overview.md).

After you've configured electronic invoicing, you can generate XML files of electronic invoices by using the [Pan-European Public Procurement Online (PEPPOL)](https://docs.peppol.eu/poacc/billing/3.0/) format specification with the Australian and New Zealand extension.

> [!NOTE]
> The electronic invoicing approach that this article describes is implemented by using an Invoicing service that's applicable only to cloud deployments of Finance or Supply Chain Management. For on-premises deployments, see [Customer electronic invoices in Australia and New Zealand](apac-aus-nzl-e-invoices.md).

## Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

- Become familiar with Electronic invoicing as it's described in [Electronic invoicing overview](../global/e-invoicing-service-overview.md).
- Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:

    - [Sign up for and install the Electronic Invoicing service](../global/e-invoicing-sign-up-install.md)
    - [Set up Azure resources for Electronic invoicing](../global/e-invoicing-set-up-azure-resources.md)
    - [Install the add-in for microservices in Lifecycle Services](../global/e-invoicing-install-add-in-microservices-lcs.md)

- Activate the integration between your Finance or Supply Chain Management app and the Electronic Invoicing service as described in [Activate and setup integration with Electronic invoicing](../global/e-invoicing-activate-setup-integration.md).
- Make sure that the following Electronic reporting (ER) format configurations are imported. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

    - Peppol Sales Invoice AU-NZ
    - Peppol Sales Credit Note AU-NZ
    - Peppol Project Invoice AU-NZ
    - Peppol Project Credit Note AU-NZ

    > [!NOTE]
    > These formats are based on the corresponding **Peppol** format configurations. Those configurations, in turn, are based on the **UBL** format configurations that use the **Invoice model** and **Invoice model mapping** configurations. All required additional configurations are automatically imported.

## Country/region-specific configuration for the Electronic invoicing for Australia and New Zealand feature

Some of the parameters from the **Electronic invoicing for Australia and New Zealand** electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review the default values, and update them as required so that they better reflect your business operations.

1. Import the latest version of the **Electronic invoicing for Australia and New Zealand** Globalization feature as described in [Import features from the Global repository](../global/e-invoicing-import-feature-global-repository.md).
2. Create a copy of the imported Globalization feature, and select your configuration provider for it. For more information, see [Create a Globalization feature](../global/e-invoicing-create-new-globalization-feature.md).

    > [!NOTE]
    > The **Electronic invoicing for Australia and New Zealand** feature is provided by Microsoft. It's ready to use and requires no additional configuration. For information about how to configure invoicing features if you must apply changes, see [Work with feature setups](../global/e-invoicing-feature-setup.md). For example, you can filter specific legal entities so that they're processed in applicability rules. By default, the feature is applicable to all legal entities that have a primary address in Australia or New Zealand.

3. The copy of the feature is always created as a **Draft** version. Regardless of whether you made changes, complete, publish, and deploy the feature as described in [Complete, publish, and deploy a Globalization feature](../global/e-invoicing-complete-publish-deploy-globalization-feature.md).

## Finance configuration

Some additional parameters must be configured directly in Finance.

1. Make sure that the country/region-specific ER configurations for the document context and electronic document model mapping that are required for Australia and New Zealand are imported. For more information, see [Set up Electronic invoicing parameters](../global/e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).

    > [!NOTE]
    > After you import the **Electronic invoicing for Australia and New Zealand** electronic invoicing feature, electronic documents are configured by default. If you must make changes, complete the following steps.

2. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
3. In the **Electronic document** section, add records for the **Customer Invoice journal** and **Project invoice** table names.
4. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.

    ![Electronic document parameters page.](../media/apac_aus_nzl_einvoice_parameters.jpg)

5. Save your changes, and close the page.

## Finance business data configuration

### Prerequisites

The primary address of the legal entity must be in Australia or New Zealand.

### Configure legal entity data

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select a legal entity.
2. On the **Addresses** FastTab, add a valid primary address for the legal entity.
3. On the **Tax registration** FastTab, in the **Tax registration number** field, enter a valid tax registration number for the legal entity.

### Configure customer data

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select a customer.
2. On the **Addresses** FastTab, add a valid address for the customer.
3. On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the customer.
4. On the **Sales demographics** FastTab, in the **Primary contact** field, select a person who will be considered the buyer's contact.

    > [!NOTE]
    > All available contact persons must already be defined for this customer.

### Configure units of measure

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
2. Select a unit ID in the list, and then select **External codes**.
3. On the **External codes** page, in the **Overview** section, in the **Code** field, enter a code that corresponds to the selected unit ID.
4. In **Value** section, in **Value** field, enter the external code to use as the [units of measure](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/) code for international trade.

    > [!NOTE]
    > When no specific units of measure are assumed, the default value **EA** (each) is used.

### Configure sales tax codes

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
2. Select a sales tax code, and then, on the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
3. In the **Overview** section, create a line for the selected unit. In the **External code** field, enter the sales tax code that you selected in step 2.
4. In the **Value** section, in the **Value** field, enter an external code to use for the selected sales tax code, according to the [required codification](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNCL5305/).

### Customer requisition

When you register free text invoices, invoices that are based on sales orders, or project invoices, you must enter a customer requisition. You can also add an optional customer reference.

#### Free text invoices

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Create a new invoice, or select an existing invoice.
3. In the **Header** view, on the **Customer** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Sales orders

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
2. Create a new sales order, or select an existing sales order.
3. In the **Header** view, on the **General** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Project invoices

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
2. Create a new project contract, or select an existing project contract.
3. On the **Funding sources** FastTab, select or create a funding source of the **Customer** type, and then select **Details**.
4. On the **Funding source details** page, on the **Other** FastTab, in **References** section, in the **Customer requisition** and **Customer reference** fields, enter default values for the contract.

## Issue electronic invoices

When you've completed all the required configuration steps, you can generate electronic invoices for posted invoices. For more information about how to generate electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](../e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

You can inquire about the results of the submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log** and selecting the required document type.

To download the XML files of electronic invoices for successfully processed invoices, select **Electronic document** \> **Download file**.

![Download file command on the Electronic document submission log page.](../media/apac_aus_nzl_einvoice_log.jpg)

## Additional resources

- [Electronic invoicing overview](../global/e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](../e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](../e-invoicing-get-started.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
