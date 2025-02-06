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

This article provides information about Invoice capture solution that automatically creates vendor invoices from digital invoice images. Learn more in [Invoice capture overview](../accounts-payable/invoice-capture-overview.md).

## February 2025

### Invoice capture

The February release of the invoice capture solution version 1.9.1.X contains the following features and bug fixes.
| Feature | Description | 
| ---|---|
| Feature | Addition of currency code as an attribute for OCR recognition. AI builder starts recognising currency code as an attribute from invoice as a part of OCR recognition process. |
| Bug fix | Formatting issues while identifying purchase order. |
| Bug fix | Continuous learning fails to identify item when description contains special characters. |
| Bug fix |Configuration group page keeps loading when the Dynamics 365 finanace and operations environment is disabled. |

### December 2024

The December release of the invoice capture solution version 1.9.0.X contains the following features and bug fixes.

| Feature | Description | 
| ---|---|
| Feature | Automatically remove invalid field value - If you enable this feature, a value is automatically removed if it doesn't exist in the lookup list. This eliminates the need to manually remove values during the review, streamlining the process. |
| Feature |Synchronize vendors based on filter conditions - You can set filter conditions to only synchronize vendors that are suitable for inclusion in Invoice capture.|
| Feature |Synchronize deleted legal entities and vendor accounts - When legal entities or vendor accounts are deleted in Dynamics 365 Finance, they have an **Inactive** status. The inactive legal entities or vendor vendors aren't going to be derived during Invoice capture processing. Invoices with inactive legal entities or vendor accounts can't be transferred to Dynamics 365 finance and operations.|
| Feature |Continuous learning for decimal format - The system learns from the historical record and automatically applies the correct decimal format on the **Amount** fields. Users should manually correct the first incoming invoice and do the successful transfer.|


### September 2024 

The September release of the invoice capture solution version 1.8.0.X contains the following features and bug fixes.

| Feature | Description | 
| ---|---|
| Bug fix | Date format: This release addresses a date formatting issue caused by ambiguity in date recognition. With the updated version, when a user corrects the date on the first invoice, the corresponding date format is automatically applied to the future invoice if it is coming from the same vendor. This functionality is enabled when the **Using continuous learning** parameter is active.
|Bug fix |Resizing side-by-side viewer column - Users can now adjust column widths within the side-by-side viewer.|
| Bug fix |Item number validation - Validation errors occur when an item number in the linked purchase line contains different variants, despite showing the same item number as the one in the purchase order, this blocked the invoice processing. |
| Bug fix |**Charges code** field - The **Charges code** field was not available when customer defines an own custom field and its technical field group is set to **Charge**.|
 


### August 2024
The August release of the invoice capture solution version 1.7.0.X contains the following features and bug fixes.

| Feature | Description | 
| ---|---|
| Feature | Improved **Link invoice line to purchase line** page to display purchase line options even when the item number or expense type isn't specified.|
| Feature | Added a group access level above the legal entity in Channel definition, enabling support for cases where a single AP clerk manages multiple legal entities. |
| Feature | When long documents are stuck in processing, users can reset the status of received files. |
| Bug Fix | Resolved the real-time vendor sync issue.|
| Bug Fix |Fixed an issue with the SBS viewer that sometimes resulted in a blank page.|
| Bug Fix |Corrected the display of the legal entity when syncing using the **Sync by selection** option.|
| Bug Fix |Addressed the issue where **Void** wasn't available in the **Captured invoice list** page when multiple invoices were selected.|


 

