---
title: Invoice capture FAQ
description: Access answers to frequently asked questions about the Invoice capture solution, including questions about error messages.
author: NishantNalawade
ms.author: NNalawade
ms.topic: faq
ms.date: 09/30/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Invoice capture FAQ

[!INCLUDE [banner](../includes/banner.md)]

This article answers frequently asked questions about the Invoice capture solution. The Invoice capture solution automatically creates vendor invoices from digital invoice images.

## Why do I receive the following error message in Received files: "There's insufficient capacity for your current invoice capture license plan"?

You've consumed the entitled credits and must subscribe to Electronic Invoicing. Contact the Microsoft account team or your partner cloud solution provider (CSP) to purchase licenses.

### What if invoices that are received are in an unsupported format (for example, Word documents)?

Word documents aren't yet supported. However, Power Automate can convert a Word document into a PDF file before it calls the invoice capture API.

### When do the invoice review process and approval require manual intervention in Invoice capture?

It depends on the **Manual review required** setting in the configuration group. The following values are available:

- **Errors or warnings** – Manual intervention is required only if there are warnings or errors.
- **Errors only** – Manual intervention is required only if there are errors.
- **Always needs manual review** – Manual review is always required.

### How many invoices can Invoice capture process?

Microsoft Power Platform performance throttling limits the number of invoices. Currently, you can process more than 50 invoices at the same time, and the average invoice processing time is about 15 to 30 seconds.

### How can I extend the default AI Builder model so it recognizes invoices that have a more complex format?

To help increase the confidence score and the touchless rate, use the **custom prebuilt model**, which is built on top of a prebuilt model in Invoice capture. Add enhancements to the model by training it with additional invoice samples. The custom prebuilt model is in preview, and additional functions will be available in a future release.

### Does Invoice capture support PO invoices and non-PO invoices? Does it support an invoice journal for non-PO invoices?

Invoice capture supports three invoice types:

- Purchase order (PO) invoice
- Header-only invoice
- Cost invoice

If an invoice is associated with one or more POs, or if it's a header-only PO, treat it as a PO invoice. Map these documents to a **vendor invoice** in Dynamics 365 Finance.

If an invoice isn't associated with any PO, treat it as a non-PO invoice. You can map a non-PO invoice to a vendor invoice or an invoice journal. When you map it to a vendor invoice, only service items or procurement categories are allowed on the invoice lines. When you map it to an invoice journal, only the header invoice is considered during the invoice transfer.

### Does Invoice capture learn from changes that are made to an invoice if the invoice wasn't correctly processed or if the AP clerk changed it?

Yes, continuous learning capabilities are available. Invoice capture learns from corrections that the accounts payable (AP) clerk makes to a previous invoice. The next time that a similar invoice is captured, Invoice capture applies what it learned to derive the entities. After the invoice is reviewed and transferred, the mapping between entities and invoice context is recorded. The entities, such as legal entities, vendor accounts, items, and procurement category are automatically derived for the next time a similar invoice is captured. These capabilities can increase the touchless rate of invoice processing.

### Can I extend the item mapping rule to map between an external item number and an internal item number?

Yes. Invoice capture uses the external item number in Dynamics 365 Finance to derive the item number.

### Does Invoice capture support uploading multiple invoices at the same time?

Yes. You can upload up to 20 invoice files at the same time.

### What languages of invoices are supported?

For a complete list of supported languages, see the [Document intelligence page](/azure/ai-services/document-intelligence/concept-invoice).

### If I use a custom model for invoice capture, do I need to purchase AI Builder credits in addition to the electronic invoicing credits?

When you train the custom model, you need to purchase AI Builder credits for that activity. However, after the custom model is trained and is used in Invoice capture, only the electronic invoice credits are used.

### When should I enable asynchronous processing?

If your environment processes large invoices (many pages) or handles high invoice volumes, enable the **Enable asynchronous processing** option in **System preference**. In asynchronous mode, the OCR recognition request is submitted and the system polls for the result. The system retries up to 12 times. If all attempts fail, the received file is set to **Canceled** and you can resubmit it by selecting **Retry**.

### An invoice is stuck in the In-process status. What should I do?

If you enable asynchronous processing and the OCR service is temporarily unavailable or slow, a file can remain in **In-process** status for an extended time. On the **Received files** page, select **Reset processing status** to unblock the file and resubmit it for processing. If you don't enable asynchronous processing, a stuck file usually indicates a transient service error, and resetting the processing status resolves the issue.

### What does the "Only accept confirmed purchase orders" setting do?

When you enable the **Only accept confirmed purchase orders** option in **System preferences**, Invoice capture matches invoices only against purchase orders that have a **Confirmed** status in Dynamics 365 Finance. Purchase orders with other statuses, such as **Open order** or **Received**, are excluded from the matching lookup. This restriction helps prevent premature invoice processing against orders that aren't officially approved.

### What happens when the "Autoclear invalid lookup values" setting is enabled?

When you enable **Auto-clear invalid lookup values** in **System preferences**, any captured field value that doesn't match a valid entry in its corresponding lookup list in Dynamics 365 Finance is automatically removed during derivation. This removal prevents invalid values from causing validation errors and allows invoice processing to continue. Users can then manually enter correct values during review.

### What does the "Exclude cost invoice lines" setting do?

When you enable **Exclude cost invoice lines** in **System preferences**, and you transfer cost invoices to Dynamics 365 Finance as an invoice journal, the invoice line details aren't shown in the side-by-side viewer and aren't validated. Only the invoice header fields are required for review and transfer. This setting applies only when the target invoice type for cost invoices is configured as **Invoice journal** in Finance.

### Why did my PO invoice automatically change to a header-only invoice?

If an invoice has a purchase order reference but OCR doesn't capture any line items, and the assigned configuration group supports both **PO invoice** and **Header-only** invoice types, the system automatically reclassifies the invoice as header-only during derivation. This automatic reclassification removes the need for manual reclassification for invoices where line details aren't expected. To prevent this behavior, remove **Header-only** from the supported invoice types in the configuration group.

### What file formats can I upload to Invoice capture?

You can restrict accepted formats by using the **File filter** settings in **System preference** or on a per-channel basis.

Invoice capture supports the following file formats: 
PDF 
PNG 
JPG 
JPEG
TIF 
TIFF
