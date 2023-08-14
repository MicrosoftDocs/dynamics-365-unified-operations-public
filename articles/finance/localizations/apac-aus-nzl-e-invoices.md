---
title: Customer electronic invoices in Australia and New Zealand
description: This article provides information that will help you get started with Electronic invoicing for Australia and New Zealand in Microsoft Dynamics 365 Finance.
author: ilikond
ms.date: 07/18/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Australia, New Zealand
ms.author: ilikond
ms.search.validFrom: 2022-11-03
ms.dyn365.ops.version: AX 10.0.37
ms.custom: 574542
ms.assetid: 
ms.search.form: 
---

# Customer electronic invoices in Australia and New Zealand

[!include [banner](../includes/banner.md)]

This article provides information about how to configure and issue customer electronic invoices using Australian and New Zealand extension of the [PEPPOL](https://docs.peppol.eu/poacc/billing/3.0/) format specification.

## Prerequisites

1. The primary address of the legal entity must be in Australia or in New Zealand.
2. Make sure that the latest versions of the following Electronic reporting (ER) format configurations are imported. For more information, see [Import Electronic reporting (ER) configurations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

    - Peppol Sales Invoice AU-NZ
    - Peppol Sales Credit Note AU-NZ
    - Peppol Project Invoice AU-NZ
    - Peppol Project Credit Note AU-NZ

> [!NOTE]
> These formats are based on the respective **Peppol** format configurations which are based on the **UBL** format configurations that use the **Invoice model** configuration and the **Invoice model mapping** configuration. All required additional configurations are automatically imported.

## Configure parameters

### Reference the imported ER format configurations

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the imported formats for electronic documents:

    - **Sales and Free text invoice:** Peppol Sales Invoice AU-NZ
    - **Sales and Free text credit note:** Peppol Sales Credit Note AU-NZ
    - **Project invoice:** Peppol Project Invoice AU-NZ
    - **Project credit note:** Peppol Project Credit Note AU-NZ

    ![Formats for electronic documents.](media/apac_aus_nzl_einvoice_configs.jpg)

### Configure legal entity data

Go to **Organization administration** \> **Organizations** \> **Legal entities**, select a legal entity, and configure the following parameters.

1. On the **Addresses** FastTab, add a valid primary address for the legal entity.
2. On the **Tax registration** FastTab, in the **Tax registration number** field, enter a valid tax registration number for the legal entity. 

### Configure customer data

Go to **Accounts receivable** \> **Customers** \> **All customers**, select a customer, and configure the following parameters.

1. On the **Addresses** FastTab, add a valid address for the customer.
2. On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the customer.
3. Set the **eInvoice** option to **Yes** to enable electronic invoices to be generated.
4. Set the **eInvoice attachment** option to **Yes** to attach a PDF copy of the printable invoice to the electronic invoice, if necessary.
5. On the **Sales demographics** FastTab, in the **Primary contact** field, select a person who will be considered the buyer's contact.
    > [!NOTE]
    > All available contact persons must already be defined for this customer.

### Units of measure configuration

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
2. Select a unit ID in the list, and then select **External codes**.
3. On the **External codes** page, in the **Overview** section, in the **Code** field, enter a code that corresponds to the selected unit ID.
4. In **Value** section, in **Value** field, enter the external code that should be used as the [units](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/) of measure code for international trade.
    > [!NOTE]
    > For the scenarios where no specific units of measure are assumed the default value **EA** (each) will be used.

### Sales tax codes configuration

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
2. Select a sales tax code, and then, on the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
3. In the **Overview** section, create a line for the selected unit. In the **External code** field, enter the sales tax code you selected in step 2.
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
3. On **Funding sources** FastTab, select or create a funding source of the **Customer** type, and then select **Details**.
4. On the **Funding source details** page, on the **Other** FastTab, in **References** section, in the **Customer requisition** and **Customer reference** fields, enter default values for the contract. 

## Export customer electronic invoices

### Generate e-invoices

When an invoice is posted, you can generate an electronic invoice from any invoice journal by running **Send** \> **Original** for the selected invoice.

![Sending an e-invoice.](media/emea-nor-ger-einvoice.jpg)

### View e-invoices

To inquire about the XML files of electronic invoices that have been generated, follow these steps.

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
2. Select a job, and then select **Show files**.

    ![Show files button.](media/emea-nor-ger-einvoice-open.jpg)

3. Select **Open** to download the file that contains the electronic invoice.

If generation of the electronic invoices fails because of errors, select **Show log** \> **Message details** to view more details about the error message.

![Message details.](media/emea-nor-ger-einvoice-log.jpg)

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, output XML files that contain electronic invoices will automatically be sent to the defined destinations immediately after the invoices are posted. When you post the invoices, you must turn on the **Print invoice** parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).


## Additional resources

- [Forced electronic invoices generation](emea-eur-forced-einvoices.md)
- [Supported standards for electronic invoicing](emea-oioubl-standards-electronic-invoicing.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
