---
title: Vendor electronic invoices
description: Learn how to configure and submit vendor electronic invoices in Italy, including prerequisites and an outline on configuring accounts payable parameters.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2021-12-01
ms.search.form: 
ms.dyn365.ops.version: 10.0.21
---

# Vendor electronic invoices

[!include [banner](../../includes/banner.md)]

According to Italian legislation, you must submit to the Exchange system (SDI) invoices that you receive from foreign vendors who aren't Italian tax residents. This article explains how to configure and submit vendor electronic invoices in the **FatturaPA** electronic format.

## Prerequisites

- The primary address of the legal entity is in Italy.
- You implement the export of vendor electronic invoices symmetrically to the export of Italian customer electronic invoices. You use the common parameters that you define on the **Electronic invoice parameters** page in Accounts receivable. You configure those parameters in advance. For more information, see [Customer electronic invoices](emea-ita-e-invoices.md).

## <a id="apparameters"></a>Configure Accounts payable parameters

Follow these steps to set up the electronic invoice configuration in Accounts payable parameters.

1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
1. On the **Electronic documents** tab, in the **Vendor invoice (export)** field, select the **Vendor invoice (IT)** configuration. Use this configuration to generate the XML files for the export of vendor electronic invoices.

   :::image type="content" source="../media/emea-ita-AP-parameter-e-invoices.jpg" alt-text="Screenshot of the Vendor invoice (export) field set on the Electronic documents tab of the Accounts payable parameters page.":::

   > [!NOTE]
   > Import configurations before you select them. For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
   >
   > The parent model configuration, **Invoice model**, and the related model mapping configuration, **Vendor invoice model mapping (IT)**, are automatically imported or updated.
   >
   > 1. After importing the configurations, set up application-specific parameters in the **Electronic reporting** workspace, for the Vendor invoice (IT) format. On the Action Pane, select **Configuration** > **Application specific parameters** > **Setup**. You must set up at least two lines for **Blank** and **Not blank** values.
   >  
   >     :::image type="content" source="../media/emea-ita-vendor-einvoice-asp.png" alt-text="Screenshot of the Application-specific parameters page.":::
   >
   >     These default settings are required for all scenarios, even if **Reverse charge** isn't applicable.
   >
   > 2. In the **Conditions** section, in the **Name** column, add the other required Reverse charge item groups and associate them with the related values in the **Lookup result** column. For more details about how to set up Reverse charge item groups, see [Customer electronic invoices](emea-ita-e-invoices.md).

## Enable electronic invoice generation

Follow these steps to enable the eInvoice register and the generation of electronic invoice for a vendor.

1. Go to **Accounts payable** \> **All vendors**.
1. Select and open the record of the vendor to enable the eInvoice register for.
1. On the **Invoice and delivery** FastTab, in the **E-invoice** section, turn on the **eInvoice register** option to enable electronic invoice generation for the selected vendor.

## Configure invoice types

The invoice type is a mandatory attribute of electronic invoices. You must assign it to an electronic invoice before you submit that invoice to the Exchange system.

### Define invoice types

Follow these steps to define one or more invoice types.

1. Go to **Accounts receivable** \> **Setup** \> **Electronic invoice parameters**.
1. On the **Invoice types** tab, define codes for one or more required invoice types, and enter a description for each.

   :::image type="content" source="../media/emea-ita-invoice-types.jpg" alt-text="Screenshot of the Invoice types defined on the Invoice types tab of the Electronic invoice parameters page.":::

### Assign invoice types to sales tax codes

You can associate invoice types with specific sales tax codes.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. On the **General** FastTab, in the **Invoice type** field, enter the reference to a specific invoice type.

   :::image type="content" source="../media/emea-ita-invoice-types-tax-codes.jpg" alt-text="Screenshot of the Invoice type assigned to a sales tax code on the Sales tax codes page.":::

## Invoice types processing

The system automatically enters invoice types that are associated with the sales tax code on an invoice in the **TipoDocumento** tag of the XML file generated for the electronic invoice.

If you don't associate an invoice type with the sales tax code, the system automatically enters the following types of vendor invoice documents:

- **TD16** – For vendors located in Italy, if an invoice contains a sales tax code where either **Use tax** or **Reverse charge** is activated.
- **TD17** – For vendors located in the European Union (EU), if an invoice is issued for the provision of **services**.
- **TD18** – For vendors located in the EU, if an invoice is issued for the sale of **products**.
- **TD28** – For vendors located in San-Marino and the sales tax amount is greater than zero (available from version 273.47 of the **Vendor Invoice (IT)** format).

If the system doesn't enter a required invoice type, you can manually adjust the invoice type in the vendor invoice journal.

### Configure electronic document properties

1. Go to **Accounts receivable** > **Setup** > **Electronic document property types**.
1. Select **New** to add a property type.
1. In the **Type** field, enter **DocumentType**.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Vendor invoice journal**.
1. Save and return to the **Electronic document property types** page.

   :::image type="content" source="../media/emea-ita-invoice-type-parameter.jpg" alt-text="Screenshot of the Property type added on the Electronic document property types page.":::

### Register invoice types

Follow these steps to register invoice types.

1. Go to **Accounts payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**.
1. Select an invoice in the list, and then select **Electronic document properties**.

    :::image type="content" source="../media/emea-ita-invoice-type-in-invoice.jpg" alt-text="Screenshot of the Electronic document properties button.":::

1. Enter a required invoice type. The value of the **Value** field for the invoice type overrides any automatically created codes when XML files are generated for electronic invoices.

    :::image type="content" source="../media/emea-ita-invoice-type-value.jpg" alt-text="Screenshot of the Invoice type value entered on the Electronic document properties page.":::

## Process vendor electronic invoices

To view all electronic invoices for vendors and perform various actions, go to **Accounts payable** > **Invoices** > **E-Invoices** > **Electronic invoices**. The functionality resembles the functionality for processing customers electronic invoices. For more information, see [Electronic invoice register](emea-ita-e-invoices.md#einvoiceregister).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
