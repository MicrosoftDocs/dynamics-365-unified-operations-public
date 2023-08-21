---
# required metadata

title: Invoice capture FAQ
description: This article answers frequently asked questions about the Invoice capture solution.
author: sunfzam
ms.date: 08/21/2023
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

### Why do I get the error “The required minimal Dynamics 365 Finance version isn’t met” while upgrading or installing Invoice capture? 
The following versions of Dynamics 365 Finance versions are supported:  
- Dynamics 365 Finance version 10.0.35 10.0.1627.86 or later 
- Dynamics 365 Finance version 10.0.34 10.0.1591.124 or later


### Why do I receive an error message "There's insufficient capacity for your current invoice capture license plan" in Received files? 
You have consumed the entitled credits and need to subscribe to **Electronic Invoicing**. Contact the Microsoft account team or your partner CSP to purchase licenses.  

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

We recommend that customers use the **Custom prebuilt model** which is built on top of a prebuilt model within Invoice capture. Customers can add enhancements to the model by training the model with additional invoice samples. The custom prebuilt model is in preview and additional functions will be available in a future release.  

### Does Invoice capture support PO invoices and Non-PO invoices? Does it support an invoice journal for Non-PO invoices?

Invoice capture supports three invoice types:
 - Purchase order (PO) invoice
 - header-only invoice
 - cost invoice

If an invoice is associated with one or more POs or is a header-only PO, it's treated as a PO invoice. These documents are mapped to a **Vendor invoice** in Dynamics 365 Finance.  

If an invoice isn't associated with any PO, it's treated as a Non-PO invoice. A non-PO invoice can be mapped to a vendor invoice or invoice journal. When it's mapped to a vendor invoice, only service items or procurement categories are allowed on the invoice lines. When it's mapped to an invoice journal, only the header invoice is considered during the invoice transfer.  

### Does Invoice capture learn from changes that are made to an invoice if the invoice wasn't correctly processed or it was changed by the AP clerk?

Yes, continuous learning capabilities are available. Invoice capture learns from corrections made by the Accounts payable (AP) clerk of a previous invoice. The next time a similar invoice is captured, Invoice will apply what it as learned to derive the entities. After the invoice is reviewed and transferred, the mapping between entities and invoice context will be recorded. The entities such as legal entities, vendor accounts, invoice type, items, procurement category, currency code will be automatically derived for the next time a similar invoice is captured. This can increase the touchless rate of invoice processing. 

### Can I extend the item mapping rule to map between an external item number and an internal item number?

Yes, Invoice capture uses the external item number in Dynamics 365 Finance to derive the item number.  

### Does Invoice capture support uploading multiple invoices at the same time?

Yes, users can upload multiple invoices (Maximum of 20 files) simultaneously.  

### What languages of invoices are supported?

For a complete list of supported languages, see [Document intelligence page](/azure/ai-services/document-intelligence/concept-invoice?view=doc-intel-3.1.0.md#supported-languages-and-locales).
