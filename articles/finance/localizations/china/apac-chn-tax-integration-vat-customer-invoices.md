---
title: Chinese tax integration modification for VAT customer invoices FAQ
description: You can generate value-added tax (VAT) customer invoices, and then export them as text files, then import reference numbers for the VAT customer invoices.
author: mrolecki
ms.author: johnmichalak
ms.topic: faq
ms.date: 12/05/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: China (PRC)
ms.search.validFrom: 2016-11-30
ms.search.form: CustParameters, VATInvoiceDescTable_CN, TaxProfileTable_CN
ms.dyn365.ops.version: Version 1611
---

# Chinese tax integration modification for VAT customer invoices FAQ

[!include [banner](../../includes/banner.md)]

You can generate value-added tax (VAT) customer invoices, then export them as text files. You can import reference numbers for the VAT customer invoices that link to the original invoices.

Before you export a VAT customer invoice, you can split the VAT customer invoice to create multiple invoice documents. You can also combine multiple VAT customer invoices to create one invoice export document that contains the line details of the original invoices.

## What is a VAT customer invoice?

You generate a VAT customer invoice when you post a customer transaction that uses the sales tax group for VAT and the item sales tax group for VAT. You can generate a VAT customer invoice from a sales order, return sales order, credit note, free text invoice, or project sales invoice.

## Can I create one tax integration profile for multiple types of documents?

Yes. You can create one tax integration profile for multiple types of documents.

## Can I create an invoice that has different sales tax codes and sales tax rates in lines?

Yes. If you turn on the **Allow multiple tax codes in VAT customer invoices lines for Chinese Golden tax integration** feature (see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)), and if there's a tax integration profile where the **Sales tax code** field is blank on **Tax integration profile** page (**Accounts receivable \> Setup \> Tax integration**), you can create and post invoices that have different sales tax codes and sales tax rates. You can also export the invoices to the file.   

## When should I split a VAT customer invoice?

You should split a VAT customer invoice if you select the **Over amount limit** check box on the **VAT invoice integration** page. Select the **Over amount limit** option for the invoices that have a total invoice amount that exceeds the amount limit that you specify in the **Maximum invoice amount** field on the **Tax integration profiles** page.

## Which VAT customer invoices can I combine?

You can combine VAT customer invoices that use the same invoice account number and sales tax code.

## How many times can I export an invoice?

You can export an invoice only once.

## Can I export summarized invoice lines including miscellaneous charge amounts if charges are applied for the invoice line?

You can export an invoice and its lines with summarized invoice line amounts, including miscellaneous charges, if you select the **Add line charges into invoice line** check box on the **Tax integration profile** page.

## Can I customize or add new information on VAT customer invoices?

Yes. You can customize VAT customer invoices by adding other fields, and then you can export the VAT customer invoices as text files.

To customize VAT customer invoices to include other details, follow these steps:

1. On the **Electronic reporting** page, select **Reporting configurations** to open **Configurations**.
1. In the tree, select **Golden Tax(CN)**.
1. Select **Designer**. Add other fields on the tree under **Exported Invoices** &gt; **Invoices**, and save the GER model.
1. Select **Map model to data source** and select **Golden Tax** &gt; **Designer**.
1. Select **Save** and return to **Configurations**.
1. Map the added fields to a table. 
    1. Select **GoldenTax(CN)** in the tree.
    1. Select **Change status** &gt; **Complete** to get a new version of the model.
    1. Expand **GoldenTax(CN)** in the tree.
    1. Select the **GoldenTax(CN)** format in the tree.
    1. Select **Rebase**. Confirm that the target version is the new completed version.
    1. Select **OK** to finish the rebase process.
    1. Select **Designer** to open the format designer.
    1. In the format designer, add new fields in the tree that are present in text files.
    1. Select the newly added field, and select the **Mapping** tab.
    1. Expand the model in the tree.
    1. Select the newly added model field and then select **Bind**.
    1. Select **Save**.
    1. Select **Change status** &gt; **Complete** to get a new version.

## Additional resources

[Configure tax integration for China](apac-chn-tax-integration.md)

[Import the Chinese Golden Tax data entity](apac-chn-import-golden-tax-data-entity.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
