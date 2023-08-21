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

### Why do I get the error “The required minimal D365 Finance version doesn’t meet.” during invoice upgrade or installation? 
Please make sure both the released version and quality build version match the following: 
- 10.0.35 10.0.1627.86 + 
- 10.0.34 10.0.1591.124 +
  
If it doesn’t match the required version and quality build, the installation or upgrade will be blocked.  

### Why do I receive an error message "There's insufficient capacity for your current invoice capture license plan." in Received files? 
You have consumed up the entitled credit and need to subscribe the **Electronic Invoicing** to gain additional batches of the transactions. You could contact the MS account team or partner CSP to purchase the license.  

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

We recommend that customers use the **custom prebuilt model** which is built on top of prebuilt model within Invoice capture. Customers can make some additional enhancements by training the model with additional invoice samples. The custom prebuilt model is owned by the AI Builder team, which is still in preview phase. The complete function will be ready when the integration part is done after the custom prebuilt model is in GA.  

### Does Invoice capture support PO invoices and Non-PO invoices? Does it support an invoice journal for Non-PO invoices?

It contains three invoice types within Invoice capture, PO invoice, header-only invoice and cost invoice.  

PO invoice and header-only are the invoices which are associated with purchase order. It can be only mapped to “vendor invoice” in D365 Finance.  

Cost invoice is the invoice which has no association with purchase order, which is treated as Non-PO invoice. It can be mapped to the vendor invoice or invoice journal. When it is mapped to the vendor invoice, only service items or procurement categories are allowed on the invoice lines. When it is mapped to the invoice journal, only the header invoice will be considered during the invoice transfer.  

### Does Invoice capture learn from changes that are made to an invoice if the invoice wasn't correctly processed or it was changed by the AP clerk?

Yes, continuous learning capabilities are available, which can learn from the decision made by AP clerk in the previous invoice to automatically derive the entities for the next coming invoice. Once the invoice is reviewed and transferred, the mapping between entities and invoice context will be recorded. The entities such as legal entities, vendor accounts, invoice type, items, procurement category, currency code will be automatically derived for the next coming invoice with the same context. This can increase the touchless rate of invoice processing. 

### Can I extend the item mapping rule to map between an external item number and an internal item number?

Yes, invoice capture will use the external item number maintained in the D365 Finance to derive the item number.  

### Does Invoice capture support uploading multiple invoices at the same time?

Yes, users can upload multiple invoices (maximal 20 files) simultaneously in Manage received files.  

### What languages of invoices are supported?

The complete list of supported languages is shown in the [Document Intelligence page](https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/concept-invoice?view=doc-intel-3.1.0#supported-languages-and-locales)
