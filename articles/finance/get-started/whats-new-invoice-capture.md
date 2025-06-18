---
title: What's new or changed in Invoice capture
description: Learn about features that are either new or changed in Invoice capture.
author: shielas  
ms.author: shielas
ms.topic: whats-new
ms.date: 06/18/2025
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

This article provides information about the Invoice capture solution that automatically creates vendor invoices from digital invoice images. Learn more in [Invoice capture overview](../accounts-payable/invoice-capture-overview.md).

## June 2025
The June release of the invoice capture solution version 1.9.6.x contains the following feature enhancements and bug fixes.  

### Bug fixes 

 - Currency code derivation fix - Resolved an issue where the system was assigning incorrect currency codes for certain currencies.
   With this fix: 
     - For PO-based and header-only invoices, the currency code is now be correctly derived from the associated purchase order.
     - For cost invoices, the currency code is derived from the vendor master if the **Derive currency code for cost invoices** configuration is enabled.

>[!Note]
> This is a preview fix and is being rolled out to specific customers. Reach out to us if you would like this enabled for your cloud environment.  

 - Product variant matching fix - Resolved an issue where invoices with product variants triggered a “Item number isn't the same as the one on the purchase order line” validation error, even when a matching PO line existed.
   With this fix: 
     - Item numbers are accurately matched with variants during the derive and check process. 

### Feature enhancements

| Feature | Description |
| --- |--- |
|Multi-line selection and removal for invoice lines | The select all and multi-line removal feature simplifies the review process for invoices with multiple lines. Users can now select or deselect all invoice lines on the current page using a single checkbox. This enables faster removal of unwanted lines, this is useful for invoices with hundreds of entries. A confirmation dialog ensures safe deletion, and a notification confirms success. | 
|Quantity decimal precision configuration | The **Quantity decimal precision** feature allows users to control the number of decimal places displayed for quantity fields. Previously limited to two decimals, this caused issues in precision-sensitive industries like steel manufacturing. A new dropdown parameter allows users to choose between two (default) and three decimal places for greater accuracy. |

## May 2025

The May release of the invoice capture solution version 1.9.5.3 contains the following features and bug fixes.

| Feature | Description |
| --- |--- |
|Item number doesn't appear in the side-by-side viewer in Invoice capture.| Resolved the issue where the invoice number isn't populated in the header when using the standard model.|
|Manually selecting a purchase order overrides the invoice information with the purchase order information. | When selecting the purchase order line for an invoice item, the invoice quantity is updated with the purchase order quantity. Updated the logic to retain the details from the invoice line when selecting the purchase order line, unless the unit price, quantity, and unit of measure are all zero or empty.|
|Improvements to invoice capture installation. | The virtual entity solution installation was timing out and causing the installation to fail. Addressed this item in the April release. In the May release, the following were added: additional retries for solution conflicts, virtual entity refresh and company data, and added exception handling for various operations.|


## April 2025

The April release of the Invoice capture solution version 1.9.3.10 contains the following features and bug fixes.

| Feature | Description |
| --- |--- |
| Bug fix | Fixed cache issues with custom field mapping. While processing invoices using a custom model with custom fields mapped to the invoice header, users received **Can't find field ‘xxx_xxxx’ with field level '{fieldLevel}'** error. This issue was caused by an outdated internal cache. |
| Bug fix | Performance issue - Staging invoice derivation uses ecoresreleaseddistinctproductcdsentity. Fixed an issue where captured invoices are stuck in an **In processing** state prior to being available for review. |

## February 2025

The February release of the Invoice capture solution version 1.9.1.X contains the following features and bug fixes.

| Feature | Description |
| --- |--- |
| Feature | Added *currency code* as an attribute for optical character recognition (OCR). AI builder now recognizes *currency code* as an attribute from invoices as part of the OCR process. |
| Bug fix | Fixed formatting issues that occur while a purchase order is being identified. |
| Bug fix | Fixed an issue where continuous learning fails to identify items if the description contains special characters. |
| Bug fix | Fixed an issue where the **Configuration group** page keeps loading when the Dynamics 365 finance and operations environment is disabled. |

## December 2024

The December release of the Invoice capture solution version 1.9.0.X contains the following features and bug fixes.

| Feature | Description |
| --- |--- |
| Feature | Automatically remove invalid field value – If you enable this feature, values are automatically removed if they don't exist in the lookup list. This feature eliminates the need to manually remove values during the review. Therefore, it streamlines the process. |
| Feature | Synchronize vendors based on filter conditions – You can set filter conditions to sync only vendors that are suitable for inclusion in Invoice capture. |
| Feature | Synchronize deleted legal entities and vendor accounts – When legal entities or vendor accounts are deleted in Dynamics 365 Finance, they have an **Inactive** status. Inactive legal entities or vendor accounts aren't derived during Invoice capture processing. Invoices that have inactive legal entities or vendor accounts can't be transferred to finance and operations apps. |
| Feature | Continuous learning for decimal format – The system learns from the historical record and automatically applies the correct decimal format to the **Amount** fields. Users should manually correct the first incoming invoice and do a successful transfer. |

## September 2024 

The September release of the Invoice capture solution version 1.8.0.X contains the following features and bug fixes.

| Feature | Description | 
| --- |--- |
| Bug fix | Date format – This release addresses a date formatting issue that is caused by ambiguity in date recognition. In the updated version, when a user corrects the date on the first invoice from a vendor, the corresponding date format is automatically applied to future invoices from the same vendor. This functionality is enabled when the **Using continuous learning** parameter is active. |
|Bug fix | Resizing side-by-side viewer column – Users can now adjust column widths in the side-by-side viewer. |
| Bug fix | Item number validation – Validation errors occur if an item number on the linked purchase line contains different variants. Even though the item number matches the one on the purchase order, invoice processing is blocked. |
| Bug fix | **Charges code** field – The **Charges code** field wasn't available if customers define a custom field, and its technical field group is set to **Charge**. |

### August 2024

The August release of the Invoice capture solution version 1.7.0.X contains the following features and bug fixes.

| Feature | Description | 
| --- |--- |
| Feature | Improved the **Link invoice line to purchase line** page so that it shows purchase line options even when the item number or expense type isn't specified. |
| Feature | Added a group access level above the legal entity in the channel definition. This feature supports cases where a single Accounts Payable (AP) clerk manages multiple legal entities. |
| Feature | Add the ability for users to reset the status of received files when long documents are stuck in processing. |
| Bug Fix | Fixed the real-time vendor synchronization issue. |
| Bug Fix | Fixed an issue with the side-by-side viewer that sometimes resulted in a blank page. |
| Bug Fix | Corrected the display of the legal entity when synchronization is done by using the **Sync by selection** option. |
| Bug Fix | Addressed the issue where **Void** wasn't available on the **Captured invoice list** page when multiple invoices were selected. |
