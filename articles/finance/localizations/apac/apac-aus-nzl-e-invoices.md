---
title: Customer electronic invoices in Australia and New Zealand
description: This article explains how to get started with Electronic invoicing for Australia and New Zealand in Microsoft Dynamics 365 Finance.
author: ilikond
ms.date: 08/14/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Australia, New Zealand
ms.author: ikondratenko
ms.search.validFrom: 2022-11-03
ms.dyn365.ops.version: AX 10.0.36
ms.custom: 574542
ms.assetid: 
ms.search.form: 
---

# Customer electronic invoices in Australia and New Zealand

[!include [banner](../../includes/banner.md)]

This article explains how to configure and issue customer electronic invoices by using the Australian and New Zealand extension of the [Pan-European Public Procurement Online (PEPPOL)](https://docs.peppol.eu/poacc/billing/3.0/) format specification.

## Prerequisites

Before you complete the tasks in this article, the following prerequisites must be met:

- The primary address of the legal entity must be in Australia or in New Zealand.
- The latest versions of the following Electronic reporting (ER) format configurations must be imported. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

    - Peppol Sales Invoice AU-NZ
    - Peppol Sales Credit Note AU-NZ
    - Peppol Project Invoice AU-NZ
    - Peppol Project Credit Note AU-NZ

> [!NOTE]
> The ER formats are based on the corresponding **Peppol** format configurations. Those format configurations, in turn, are based on the **UBL** format configurations that use the **Invoice model** configuration and the **Invoice model mapping** configuration. All required additional configurations are automatically imported.

## Configure parameters

### Reference the imported ER format configurations

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the imported formats for electronic documents:

    - **Sales and Free text invoice:** Peppol Sales Invoice AU-NZ
    - **Sales and Free text credit note:** Peppol Sales Credit Note AU-NZ
    - **Project invoice:** Peppol Project Invoice AU-NZ
    - **Project credit note:** Peppol Project Credit Note AU-NZ

    ![Formats for electronic documents.](../media/apac_aus_nzl_einvoice_configs.jpg)

### Configure legal entity data

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select a legal entity.
2. On the **Addresses** FastTab, add a valid primary address for the legal entity.
3. On the **Tax registration** FastTab, in the **Tax registration number** field, enter a valid tax registration number for the legal entity.

### Configure customer data

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select a customer.
2. On the **Addresses** FastTab, add a valid address for the customer.
3. On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the customer.
4. Set the **eInvoice** option to **Yes** to enable electronic invoices to be generated.
5. Set the **eInvoice attachment** option to **Yes** to attach a PDF copy of the printable invoice to the electronic invoice, if an attachment is necessary.
6. On the **Sales demographics** FastTab, in the **Primary contact** field, select a person who will be considered the buyer's contact.

    > [!NOTE]
    > All available contact persons must already be defined for the selected customer.

### Configure units of measure

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
2. Select a unit ID, and then select **External codes**.
3. On the **External codes** page, in the **Overview** section, in the **Code** field, enter a code that corresponds to the selected unit ID.
4. In **Value** section, in **Value** field, enter the external code to use as the [units](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/) of measure code for international trade.

    > [!NOTE]
    > For scenarios where no specific units of measure are assumed, the default value **EA** (each) is used.

### Configure sales tax codes

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
2. Select a sales tax code, and then, on the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
3. In the **Overview** section, create a line for the selected unit. In the **External code** field, enter the sales tax code that you selected in step 2.
4. In the **Value** section, in the **Value** field, enter an external code to use for the selected sales tax code, according to the [required codification](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNCL5305/).

### Enter customer requisitions

When you register free text invoices, invoices that are based on sales orders, or project invoices, you must enter a customer requisition. You can also add an optional customer reference.

#### Enter a customer requisition for a free text invoice

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Create a new invoice, or select an existing invoice.
3. In the **Header** view, on the **Customer** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Enter a customer requisition for a sales order

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
2. Create a new sales order, or select an existing sales order.
3. In the **Header** view, on the **General** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Enter a customer requisition for a project invoice

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
2. Create a new project contract, or select an existing project contract.
3. On **Funding sources** FastTab, create or select a funding source of the **Customer** type, and then select **Details**.
4. On the **Funding source details** page, on the **Other** FastTab, in **References** section, in the **Customer requisition** and **Customer reference** fields, enter default values for the contract.

## Export customer electronic invoices

### Generate e-invoices

When an invoice is posted, you can generate an electronic invoice from any invoice journal. Select the invoice, and then, on the Action Pane, on the **Invoice** tab, in the **Document** group, select **Send** \> **Original**.

![Sending an e-invoice.](../media/emea-nor-ger-einvoice.jpg)

### View e-invoices

To inquire about the XML files of electronic invoices that have been generated, follow these steps.

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
2. Select a job, and then select **Show files**.

    ![Show files button.](../media/emea-nor-ger-einvoice-open.jpg)

3. Select **Open** to download the file that contains the electronic invoice.

If generation of the electronic invoices fails because of errors, select **Show log** \> **Message details** to view more details about the error.

![Viewing message details.](../media/emea-nor-ger-einvoice-log.jpg)

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, output XML files that contain electronic invoices are automatically sent to the defined destinations immediately after the invoices are posted. When you post the invoices, you must turn on the **Print invoice** parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

## Additional resources

- [Forced electronic invoices generation](../europe/emea-eur-forced-einvoices.md)
- [Supported standards for electronic invoicing](../europe/emea-oioubl-standards-electronic-invoicing.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
