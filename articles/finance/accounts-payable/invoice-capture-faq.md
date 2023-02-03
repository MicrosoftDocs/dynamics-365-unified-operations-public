---
# required metadata

title: Invoice capture FAQ
description: This article answers frequently asked questions about Invoice capture.
author: sunfzam
ms.date: 02/05/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture FAQ


[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article answers frequently asked questions about the Invoice capture solution. The Invoice capture solution automatically creates vendor invoices from digital 
invoice images.

### Why do I get the message “OCR Process failed” in Received files? What will be the next action item? 
The most common reason for this error is that you don’t have an AI Builder license, which could be solved by requesting a trial version. 
Go to make.powerapps.com > AI Builder/Explorer to get a trial AI builder license. 

### What if the invoices received are in an unsupported format, for example, word doc or excel doc? 
Word documents aren't supported yet. Power automate can convert a Word document into PDF before calling invoice capture API. 
 

### When does the invoice review process and approve require manual intervention in Invoice capture? 
It depends on the **Manual review required** setting in the configuration group.  
The following settings are available:
 - **Errors or warnings** - If there aren't any warnings or errors, doesn’t require any manual intervention. 
 - **Errors only** - If there are no errors, doesn’t require any manual interventions.  
 - **Always needs manual review** - Always requires manual review. 


### How many invoices can be processed using Invoice capture? 
The number is limited by the performance throttling of Power Platform. Currently, 50+ invoices can be processed at the same time and the average invoice processing 
time would be 15~30 seconds. 

### How can the default AI builder model be extended to recognize invoices with more complex format to increase the confidence score and the touchless rate?	 
Yes, a custom model can be built on the top of the prebuild model. This will contain the most of the capability of the prebuilt model. The customer will need to
provide additional training on the invoice of the exceptional layouts. 

### Does Invoice capture support PO invoices and Non-PO invoices? Does it support an invoice journal for the Non-PO invoices? 
When the invoice isn't associated with a purchase order, it is treated as a Non-PO invoice. Only service items or procurement categories are allowed on the invoice 
lines. When the invoice is associated with a purchase order(s), it is treated as a PO invoice. Both stock items and non-stock items are allowed on the invoice lines.   

If the item is a stock item on the invoice line, the purchase order has to be linked with the invoice line by the purchase order and line numbers. If not linked, 
an error will show during the transfer of the invoice: 
**Write validation failed for table row of type 'VendorInvoiceLineEntity'. Infolog: Warning: The item's inventory model policy must be not stocked.; Warning: The item's inventory model policy must be not stocked...**. 

The use of an invoice journal for Non-PO invoices is common. It will be available in a future release.  

### Does Invoice capture learn from changes made to the invoice if the invoice wasn't processed correctly or changed by the AP Clerk? 
Yes, continuous learning capability is available in the latest public preview version. Invoice capture will learn from the correction of the previous invoice. Next time, when a similar invoice is captured, it will apply what it has learned to derive the entities. Some tasks are still on-going to increase continuous learning capabilities to reduce the AP clerk's review effort and increase the touchless rate. 

 

### What happens to the tax on the invoice in Invoice capture? 
The field **Total tax** sums all of the tax amounts on the invoices and transferred to Dynamics Finance 365. The amount will ensure the correctness of the invoice by comparing the sales tax on the associated purchase order when the invoice validation is enabled. 

 
### Is it possible to extend the item mapping rule to map between an external item number to an internal item number?  
Not in the current release. It is on our roadmap and will be released in a future release. 

### Is there a model localization to capture invoices structure for different countries?  
The application can be extended to meet country specific requirements. 
 

### Does Invoice capture support uploading multiple invoices at once? 
The current version supports uploading one document at a time. Uploading multiple invoices will be available in a future release.   

### What languages of the invoices are supported? 
The following languages are currently supported: 
 - Dutch (Netherlands) 
 - English (United States) 
 - French (France) 
 - German (Germany) 
 - Italian (Italy) 
 - Portuguese (Portugal) 
 - Spanish (Spain) 

More languages will be supported in a future release. Contact us if you want to share data with Microsoft to speed up the readiness of the model for your language.  



