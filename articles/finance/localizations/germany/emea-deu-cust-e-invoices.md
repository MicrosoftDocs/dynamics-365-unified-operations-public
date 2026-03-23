---
title: Customer electronic invoices in Germany
description: Learn how to get started with Electronic invoicing for Germany in Microsoft Dynamics 365 Finance, including prerequisites and an outline on configure parameters.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: Germany
ms.search.validFrom: 2022-11-03
ms.custom: 
  - bap-template
---

# Customer electronic invoices in Germany

[!include [banner](../../includes/banner.md)]

To comply with European Union (EU) Directive 2014/55/EU, the Germany-specific **xRechnung** format was implemented. This article explains how to set up and process customer electronic invoices in **xRechnung** format.

## Prerequisites

Before you complete the procedures in this article, make sure the following prerequisites are met:

- The primary address of the legal entity must be in Germany.
- To enable the generation of electronic invoices in **xRechnung** format version **3** and later, import the specified or later versions of the following Electronic reporting (ER) format configurations. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

  - **Sales Invoice DE** (version 288.9.16.11)
  - **Project Invoice DE** (version 288.8.22.12)
  - **Invoice model mapping** (version 288.293)

> [!NOTE]
> The **Sales Invoice DE** and **Project Invoice DE** format configurations are based on the corresponding **Peppol** format configurations. Those format configurations are based on the **UBL** format configurations that use the **Invoice model** configuration and the **Invoice model mapping** configuration. All remaining additional configurations are automatically imported.

## Configure parameters

### Reference the imported ER format configurations

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
1. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the imported formats for electronic documents:

    - **Sales and Free text invoice:** Sales Invoice DE
    - **Sales and Free text credit note:** Sales Invoice DE
    - **Project invoice:** Project Invoice DE
    - **Project credit note:** Project Invoice DE

### Configure legal entity data

1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add a valid primary address for the legal entity.
1. On the **Foreign trade and logistics** FastTab, in the **VAT exempt number export** field, enter a valid tax registration number for the legal entity.
1. On the **Bank account information** FastTab, in the **Routing number** field, enter a valid number for the legal entity.
1. In the **Bank account** field, enter the reference to the legal entity bank account.

    > [!NOTE]
    > Make sure that a valid International Bank Account Number (IBAN) is defined for the selected bank account.

### Configure customer data

1. Go to **Accounts receivable** > **Customers** > **All customers**, and select a customer.
1. On the **Addresses** FastTab, add a valid address for the customer.
1. On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the customer.
1. Set the **eInvoice** option to **Yes** to enable electronic invoices to be generated.
1. Set the **eInvoice attachment** option to **Yes** to attach a PDF copy of the printable invoice to the electronic invoice, if an attachment is necessary.
1. On the **Sales demographics** FastTab, in the **Primary contact** field, select the person who is considered the buyer's contact.

    > [!NOTE]
    > All available contact persons must already be defined for the selected customer.

1. On the **Sales demographics** FastTab, in the **Employee responsible** field, select the person who is considered the seller's contact.

### Configure units of measure

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit ID, and then select **External codes**.
1. On the **External codes** page, in the **Overview** section, in the **Code** column, enter a code that corresponds to the selected unit ID.
1. Select the **Standard code** checkbox.
1. In the **Value** section, enter the external code to use as the [units](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/) of measure code for international trade.

    > [!NOTE]
    > For scenarios where no specific units of measure are assumed, use the default value **EA** (each).

### Configure sales tax codes

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
1. Select a sales tax code. On the Action Pane, select the **Sales tax code** tab. In the **Sales tax code** group, select **External codes**.
1. In the **Overview** section, create a line for the selected unit. In the **External code** field, enter the sales tax code that you selected in step 2.
1. In the **Value** section, enter an external code in the **Value** field to use for the selected sales tax code, according to the [required codification](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNCL5305/).

### Enter customer requisitions

When you register free text invoices, invoices that are based on sales orders, or project invoices, you must enter a customer requisition. You can also add an optional customer reference.

#### Enter a customer requisition for a free text invoice

1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. Create a new invoice, or select an existing invoice.
1. In the **Header** view, on the **Customer** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Enter a customer requisition for a sales order

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Create a new sales order, or select an existing sales order.
1. In the **Header** view, on the **General** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Enter a customer requisition for a project invoice

1. Go to **Project management and accounting** > **Projects** > **Project contracts**.
1. Create a new project contract, or select an existing project contract.
1. On the **Funding sources** FastTab, create or select a funding source of the **Customer** type, and then select **Details**.
1. On the **Funding source details** page, on the **Other** FastTab, in the **References** section, enter default values for the contract in the **Customer requisition** and **Customer reference** fields.

## Export customer electronic invoices

### Generate e-invoices

When you post an invoice, you can generate an electronic invoice from any invoice journal. Select the invoice, and then, on the Action Pane, on the **Invoice** tab, in the **Document** group, select **Send** > **Original**.

:::image type="content" source="../media/emea-nor-ger-einvoice.jpg" alt-text="Screenshot of sending an e-invoice.":::

### View e-invoices

To view the XML files of electronic invoices that you generated, follow these steps:

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.
1. Select a job, and then select **Show files**.

    :::image type="content" source="../media/emea-nor-ger-einvoice-open.jpg" alt-text="Screenshot of the Show files button.":::

1. Select **Open** to download the file that contains the electronic invoice.

    If the system can't generate the electronic invoices because of errors, select **Show log** > **Message details** to view more details about the error.

    :::image type="content" source="../media/emea-nor-ger-einvoice-log.jpg" alt-text="Screenshot of viewing message details.":::

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, the system automatically sends output XML files that contain electronic invoices to the defined destinations immediately after you post the invoices. When you post the invoices, you must turn on the **Print invoice** parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

## Additional resources

[Forced electronic invoices generation](../europe/emea-eur-forced-einvoices.md)

[Supported standards for electronic invoicing](../europe/emea-oioubl-standards-electronic-invoicing.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
