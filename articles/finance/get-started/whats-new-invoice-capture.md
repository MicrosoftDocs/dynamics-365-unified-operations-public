---
title: What's new or changed in Invoice capture 
description: Learn about features that are either new or changed in Invoice capture.
author: shielas  
ms.author: shielas
ms.topic: whats-new
ms.date: 02/21/2025
ms.reviewer: twheeloc
ms.custom: 
  - bap-template
  - evergreen
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# What's new or changed in Invoice capture

[!include [banner](../includes/banner.md)]

This article provides information about Invoice capture solution that automatically creates vendor invoices from digital invoice images. Learn more in [Invoice capture overview](invoice-capture-overview.md).

## February 2025

### Invoice capture

The February release of the invoice capture solution version 1.9.1.X contains the following features and bug fixes.

 - Addition of currency code as an attribute for OCR recognition - With this feature, AI builder will start recognising currency code as an attribute from invoice as a part of OCR recognition process.
 - Formatting issues while identifying purchase order
 - Continuous learning fails to identify item when description contains special characters
 - Configuration group form is keeping loading when the FnO environment is disabled.

### December 2024

The December release of the invoice capture solution version 1.9.0.X contains the following features and bug fixes.
 - Automatically remove invalid field value - If you enable this feature, the system will automatically remove the value if it doesn't exist in the lookup list. This eliminates the need to manually remove value
   during the review, streamlining the process. If you are stuck with invalid payment terms errors, enabling the feature will be a good option here.
 - Synchronize vendors based on filter conditions - In the new version, you can set filter conditions to only synchronize vendors that are suitable for inclusion in Invoice capture.
 - Sync deleted legal entities & vendor accounts - When legal entities or vendor accounts are deleted in Dynamics 365 Finance, their status is set to 'Inactive'. The inactive legal entities or vendor vendors are
   not going to be derived during Invoice capture processing. Meanwhile, invoices with inactive legal entities or vendor accounts can't be transferred to Dynamics 365 finance and operations.
 - Continuous learning for decimal format - This feature allows the system to learn from the history record and automatically apply the correct decimal format on the amount fields. What you need to do is to
   manually correct the first incoming invoice and do the successful transfer.


### September 2024 

The September release of the invoice capture solution version 1.8.0.X contains the following features and bug fixes.





### August 2024
The August release of the invoice capture solution version 1.7.0.X contains the following features and bug fixes.
New Features:

Improved the “Link invoice line to purchase line” form, now displaying purchase line options even when the item number or expense type is not specified.
Added a group access level above the legal entity in Channel definition, enabling support for cases where a single AP clerk manages multiple legal entities.
 

Additionally, when you have long documents which are stuck in processing, it provides the option to reset the status of received files

 

Bug Fixes:

Resolved the previous real-time vendor sync issue.
Fixed an issue with the SBS viewer that sometimes resulted in a blank page.
Corrected the display of the legal entity when syncing by the "Sync by selection" option.
Addressed the issue where the "Void" option was unavailable in the captured invoice list form when multiple invoices were selected.
 

For the upcoming releases, we intend to tackle the following issues:

When transferring the cost invoice to the invoice journal, we'll introduce an option to bypass specific invoice lines within Invoice Capture, streamlining the review process.
Automatically remove zero-amount lines. Occasionally, invoice lines with a zero amount, unit price, and quantity are captured, and manually deleting them can be time-consuming.
Address the date formatting problem where dates are sometimes incorrectly parsed. Once corrected, the system will learn the pattern and accurately parse the date for future invoices.
 

