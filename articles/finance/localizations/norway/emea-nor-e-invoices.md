---
title: Customer electronic invoices in Norway
description: Learn how to set up and process customers electronic invoices in Norway in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/04/2026
ms.reviewer: johnmichalak
ms.search.region: Norway
ms.search.validFrom: 2019-11-01
---

# Customer electronic invoices in Norway

[!include [banner](../../includes/banner.md)]

This article explains how to set up and process customer electronic invoices in Norway in Microsoft Dynamics 365 Finance.

To comply with European Union Directive 2014/55/EU, Microsoft implemented the Norway-specific **EHF Billing 3.0** format for electronic invoices based on the [PEPPOL Billing 3.0](https://docs.peppol.eu/poacc/billing/3.0/) specification.

## Prerequisites

The primary address of the legal entity must be in Norway.

## Import Electronic reporting configurations

In the **Electronic reporting** workspace, import the following Electronic reporting (ER) formats from the repository:

- OIOUBL Sales invoice
- OIOUBL Project invoice
- OIOUBL Sales credit note
- OIOUBL Project credit note

> [!NOTE]
> These formats are based on the **Invoice model** configuration and use the **Invoice model mapping** configuration. The import process automatically imports all required additional configurations.

For more information about how to import ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

### Reference the imported ER format configurations

To reference the imported ER format configurations, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
1. On the **Electronic documents** tab, in the **Electronic reporting** section, select the imported formats for electronic documents:

    - **Sales and Free text invoice:** OIOUBL Sales invoice
    - **Sales and Free text credit note:** OIOUBL Sales credit note
    - **Project invoice:** OIOUBL Project invoice
    - **Project credit note:** OIOUBL Project credit note

:::image type="content" source="../media/emea-nor-ger-configs.jpg" alt-text="Screenshot of formats for electronic documents.":::

## Configure parameters

### Configure legal entity parameters

To configure legal entity parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Organizations** > **Legal entities**.
1. In the **Tax registration** section, enter the company's value-added tax (VAT) number in the **Tax registration number** field.
1. In the **Registration numbers** section, set the **Print Foretaksregisteret on sales documents** option for Norway to **Yes**.
1. In the **Bank account information** section, enter the company's organization number in the **Routing number** field.
1. Enter the company's bank account number in the **Bank account** field.

    > [!NOTE]
    > You must already set up the company bank account at **Cash and bank management** > **Bank accounts** > **Bank accounts**.

### Configure customer parameters

To configure customer parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Customers** > **All customers**, and select a customer.
1. On the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable electronic invoices.
1. Set the **eInvoice attachment** option to **Yes** to attach a PDF copy of the printable invoice to the electronic invoice.
1. In the **Tax exempt number** field, enter the customer's VAT exempt number.

:::image type="content" source="../media/emea-nor-ger-customer.jpg" alt-text="Screenshot of customer parameters.":::

### Configure units of measure configuration

To configure units of measure configuration, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit ID in the list, and then select **External codes**.
1. On **External codes**, in the **Overview** section, enter a code in the **Code** field that corresponds to the selected unit ID.
1. In the **Value** section, enter the external code in the **Value** field that should be used as the units of measure code for international trade. This code is recommended by the [United Nations Economic Commission for Europe (UN/ECE)](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/).

:::image type="content" source="../media/emea-nor-ger-units.jpg" alt-text="Screenshot of units of measure configuration.":::

### Sales tax codes transformation

When you generate electronic invoices, the system analyzes the sales tax code rates and transforms them into [UNCL5305-compliant categories](https://docs.peppol.eu/pracc/catalogue/1.0/codelist/UNCL5305/). The system uses the following logic:

- For all non-zero tax rates, the system uses the **S** category as a default value. You can use **External codes** by going to **Tax** > **Sales tax code** to enter an explicit **Value** that represents the external code that should be used as the tax compliant category.
- For all zero tax rates, the system uses either the **E** category or the **Z** category, depending on the reporting code that you configure for tax-free sales.

### Customer requisition

When you register free text invoices, invoices that are based on sales orders, or project invoices, enter a customer requisition. You can also add an optional customer reference.

#### Free text invoices

To enter a customer requisition for a free text invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. Create a new invoice, or select an existing invoice.
1. In the **Header** view, on the **Customer** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Sales orders

To enter a customer requisition for a sales order, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Create a new sales order, or select an existing sales order. 
1. In the **Header** view, on the **General** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Project invoices

To enter a customer requisition for a project invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Project management and accounting** > **Projects** > **Project contracts**.
1. Create a new project contract, or select an existing project contract.
1. On **Funding sources** FastTab, select or create a funding source of the **Customer** type, and then select **Details**.

    :::image type="content" source="../media/emea-nor-ger-proj-contracts.jpg" alt-text="Screenshot of funding sources.":::

1. On the **Funding source details** page, on the **Other** FastTab, in **References** section, enter default values for the contract in the **Customer requisition** and **Customer reference** fields. Alternatively, enter project-specific values in the corresponding fields on the **E-invoice** FastTab.

    :::image type="content" source="../media/emea-nor-ger-proj-refs.jpg" alt-text="Screenshot of project references.":::

1. To enter customer requisition and reference values directly on the project invoice proposal, follow these steps:

    1. Go to **Project management and accounting** > **Projects invoices** > **Project invoice proposals**.
    1. Create a new invoice proposal, or select an existing invoice proposal.
    1. On the **Invoice proposal header** FastTab, in the **e-Invoice** section, enter values in **Customer requisition** and **Customer reference** fields.

    :::image type="content" source="../media/emea-nor-ger-proj-prop.jpg" alt-text="Screenshot of project proposal.":::

### Customer accounting code registration

Enter customer accounting codes when you work with free text invoices, invoices that are based on sales orders, or project invoices.

#### Free text invoices

To enter customer accounting codes for free text invoices, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. Create a new invoice, or select an existing invoice. 
1. In the **Header** view, on the **General** FastTab, in the **e-Invoice** section, in the **Dimension account** field, enter the accounting code for the invoice. 
1. To have a separate accounting code for each invoice line, follow these steps:

    1. Set the **Line-specific** option to **Yes**.
    1. Switch to the **Lines** view.
    1. On the **Line details** FastTab, on the **General** tab, in the **Dimension account** field, enter a line-specific accounting code for each invoice line.

    :::image type="content" source="../media/emea-nor-ger-fti-cost.jpg" alt-text="Screenshot of line-specific accounting code for a free text invoice.":::

#### Sales orders

To enter customer accounting codes for sales orders, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Orders** > **All sales orders**.
1. Create a new sales order, or select an existing sales order.
1. In the **Header** view, on the **General** FastTab, in the **e-Invoice** section, in the **Dimension account** field, enter the accounting code for the order.
1. To have a separate accounting code for each order line, follow these steps:

    1. Set the **Line-specific** option to **Yes**.
    1. Switch to the **Lines** view.
    1. On the **Line details** FastTab, on the **General** tab, in the **Dimension account** field, enter a line-specific accounting code for each order line.

#### Project invoices

To enter customer accounting codes for project invoices, follow these steps:

1. In Dynamics 365 Finance, go to **Project management and accounting** > **Projects** > **Project contracts**.
1. Create a new project contract, or select an existing project contract.
1. On **Funding sources** FastTab, create or select a funding source of the **Customer** type, and then select **Details**.
1. On **Funding source details**, on the **E-invoice** FastTab, in the **Dimension account** field, enter the project-specific default accounting code.

    :::image type="content" source="../media/emea-nor-ger-proj-cost.jpg" alt-text="Screenshot of project-specific accounting code.":::

1. To enter customer accounting codes directly in project invoice proposals, follow these steps:

    1. Go to **Project management and accounting** > **Projects invoices** > **Project invoice proposals**.
    1. Create a new invoice proposal, or select an existing invoice proposal.
    1. On the **Invoice proposal header** FastTab, in the **e-Invoice** section, in the **Dimension account** field, enter the accounting code.

1. To have a separate accounting code for each transaction line, follow these steps:

    1. Set the **Line-specific** option to **Yes**.
    1. On the **Invoice proposal transactions** FastTab, in the **Dimension account** field, enter a line-specific accounting code for each transaction line.

    :::image type="content" source="../media/emea-nor-ger-proj-prop-cost.jpg" alt-text="Screenshot of transaction line-specific accounting code.":::

## Export customer electronic invoices

### Send e-invoices

When you post an invoice, you can generate an electronic invoice by selecting **Send** > **Original** for the selected invoice.

:::image type="content" source="../media/emea-nor-ger-einvoice.jpg" alt-text="Screenshot of sending an e-invoice.":::

### View e-invoices

To view e-invoices, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.
1. Select a job, and then select **Show files**.

    :::image type="content" source="../media/emea-nor-ger-einvoice-open.jpg" alt-text="Screenshot of the Show files button.":::

1. Select **Open** to download the file that contains the electronic invoice.

If generation of the electronic invoices fails because of errors, select **Show log** > **Message details** to view more details about the error message.

:::image type="content" source="../media/emea-nor-ger-einvoice-log.jpg" alt-text="Screenshot of message details.":::

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, the system automatically sends output XML files that contain electronic invoices to the defined destinations immediately after you post the invoices. When you post the invoices, turn on the **Print invoice** parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
