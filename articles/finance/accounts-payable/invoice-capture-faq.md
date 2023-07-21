---
# required metadata

title: Invoice capture FAQ
description: This article answers frequently asked questions about the Invoice capture solution.
author: sunfzam
ms.date: 07/11/2023
ms.topic: faq
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture FAQ

[!include [banner](../includes/banner.md)]

This article answers frequently asked questions about the Invoice capture solution. The Invoice capture solution automatically creates vendor invoices from digital invoice images.

### Why do I receive an "OCR Process failed" error message in Received files?

The most common reason for this error is that you don't have an AI Builder license. You can fix the issue by requesting a trial version. To request a trial AI Builder license, go to the [Microsoft Power Apps maker portal](https://make.powerapps.com/), and select **AI Builder/Explorer**.

### What if invoices that are received are in an unsupported format (for example, they're Word documents)?

Word documents aren't yet supported. However, Power Automate can convert a Word document into a PDF file before it calls the invoice capture API.

### When do the invoice review process and approval require manual intervention in Invoice capture?

It depends on the **Manual review required** setting in the configuration group. The following values are available:

- **Errors or warnings** – Manual intervention is required only if there are warnings or errors.
- **Errors only** – Manual intervention is required only if there are errors.
- **Always needs manual review** – Manual review is always required.

### How many invoices can be processed by using Invoice capture?

The number is limited by the performance throttling of Microsoft Power Platform. Currently, 50+ invoices can be processed at the same time, and the average invoice processing time is about 15 to 30 seconds.

### How can I extend the default AI Builder model so that it recognizes invoices that have a more complex format, to help increase the confidence score and the touchless rate?

A custom model can be built on the top of the prebuilt model. This custom model will contain most of the capability of the prebuilt model. The customer will have to provide additional training about the invoices that have exceptional layouts.

### Does Invoice capture support PO invoices and Non-PO invoices? Does it support an invoice journal for Non-PO invoices?

If an invoice isn't associated with a purchase order (PO), it's treated as a Non-PO invoice. Only service items or procurement categories are allowed on the invoice lines.

If an invoice is associated with one or more POs, it's treated as a PO invoice. Both stock items and non-stock items are allowed on the invoice lines.

If the item on the invoice line is a stock item, the PO must be linked with the invoice line by the PO and line numbers. Otherwise, the following error message will be shown during the transfer of the invoice:

> Write validation failed for table row of type 'VendorInvoiceLineEntity'. Infolog: Warning: The item's inventory model policy must be not stocked.; Warning: The item's inventory model policy must be not stocked...

Support for using an invoice journal for Non-PO invoices will be available in a future release.  

### Does Invoice capture learn from changes that are made to an invoice if the invoice wasn't correctly processed or it was changed by the AP clerk?

Yes, continuous learning capabilities are available in the latest public preview version. Invoice capture will learn from the correction of a previous invoice. Then, the next time that a similar invoice is captured, Invoice capture will apply what it has learned to derive the entities. Some work is still in progress to increase continuous learning capabilities so that the Accounts payable (AP) clerk's review effort is reduced and the touchless rate is increased.

### What happens to the tax on an invoice in Invoice capture?

The **Total tax** field sums all the tax amounts on the invoices and transfers the total amount to Dynamics 365 Finance. When invoice validation is enabled, the amount will be compared to the sales tax on the associated PO to ensure the correctness of the invoice.

### Can I extend the item mapping rule to map between an external item number and an internal item number?

This capability is available in a version 1.0.1.x.

### Does Invoice capture support uploading multiple invoices at the same time?

In Invoice capture version 1.0.1.0 and later, users can upload multiple invoices simultaneously.

### What languages of invoices are supported?

The following languages are currently supported:
Current:
-	English(en)
-	Spanish (es)
-	German (de)
-	French (fr)
-	Italian (it)
-	Portuguese (pt)
-	Dutch (de)

More languages will be supported in a future release. If you want to share data with Microsoft to help make the model for your language ready more quickly, contact us.
