---
title: What's new or changed in Invoice capture
description: Learn about features that are either new or changed in Invoice capture.
author: shielas  
ms.author: shielas
ms.topic: whats-new
ms.date: 10/01/2025
ms.update-cycle: 1095-days
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

## September 2025 
The September release of the Invoice capture solution version 1.9.9.x contains the following feature enhancements and bug fixes.

| Feature  | Description |
| --- |--- |
|	Enhanced invoice derivation plugin for better performance. (Preview) | The derivation logic is updated for better performance when deriving. |
| Improvements when transferring invoices to Dynamics 365 Finance to prevent invoices getting stuck in **Awaiting** status. (Preview) | This improvement updates the transfer of invoices from Invoice capture to Dynamics 365 Finance to be asynchronous to avoid plugin timeouts. | 
|Improved accessibility for side-by-side viewer| Implemented tab sequence and the ability to move between lines and cells utilizing the keyboard. For more information, see [Power Apps keyboard shortcuts for editable grid views](../../../power-apps/user/keyboard-shortcuts.md#editable-grids-views). |
|Bug fix - Procurement category derivation is optimized for performance when using invoice line descriptions. |The resolves an issue where customers may see invoices stuck in **In processing** due to a large number of defined procurement categories. |
| Bug fix - Improved derivation accuracy for invoice types. (Known issue 5505068)  |This fixes an issue when deriving the invoice type, if the invoice header doesn't have both the vendor account and legal entity, the derivation doesn't consider if the derived value is one of the allowed types. This results in invoices being marked as PO Invoices when Invoice capture has been configured to classify invoices only as Cost invoices.|
|Bug fix - Improved performance of **Remove all lines**. | This fixes an issue where the system is unresponsive when customers click **Remove all** to delete multiple line items in Invoice capture.|
|Bug fix - Fixed consistency issues during invoice validation and transfer.| This fixes an issue where custom attributes are missing when transferring to Finance. For example, if a custom dimension is added to a line level, the custom attribute isn't transferred to Dynamics 365 Finance. This results in invoices failing at posting or posting with a blank dimension attribute.  
|Bug fix - Fixed derivation issues while populating details from purchase orders.  (Known issue:  5641845) | Improved derivation accuracy when populating item numbers where product variants are used on the purchase order. For example, a purchase order has lines with items that contain product variants. The invoice doesn’t contain an item number, but it contains a line description. The purchase order number and line are populated, but the item number isn't populated.|


## August 2025
The August release of the Invoice capture solution version 1.9.8.x contains the following feature enhancements and bug fixes. 

| Feature | Description |
| --- |--- |
|Bug Fix |The **Link purchase order line to invoice line** page was only displaying 50 lines. Updated to remove the 50 line restriction. |
|Bug Fix |Inconsistent derivation results were being encountered during cache lookup errors. Users may have encountered issues where vendor wasn't derived.  |
|Feature |Copy and paste support from PDF image to Invoice capture page. Users can now select text and numbers from the PDF page, and copy the selection to the invoice fields for easier data updates. Keyboard shortcuts of ctrl+c and ctrl+v are supported.| 


## July 2025 

The July release of the Invoice capture solution version 1.9.7.x contains the following feature enhancements and bug fixes.

### Bug fixes
The following bugs were fixed in the July release:
 - Credit memo amounts might incorrectly appear as positive during the derivation phase when continuous learning is enabled.
 - Derivation process behaves inconsistently when a custom header field of type Date is added and then removed.
 - Invoices stuck in a **Processing** or **Time out** states when the AI model couldn't be identified.
 - Vendors with the same tax registration number across multiple legal entities aren't derived correctly. The derivation logic has been updated to include the legal entity when resolving vendor accounts.
 - The item number isn't derived when the invoice line contained a product with variants.


## June 2025

The June release of the Invoice capture solution version 1.9.6.x contains the following feature enhancements and bug fixes.

### Bug fixes

- **Currency code derivation fix** — Fixed an issue where the system was assigning incorrect currency codes for some currencies.

    As a result of this fix:

    - For purchase order (PO)–based and header-only invoices, the currency code is now correctly derived from the associated PO.
    - For cost invoices, the currency code is derived from the vendor master if the **Derive currency code for cost invoices** configuration is enabled.

    > [!NOTE]
    > This fix is a preview fix and is being rolled out to specific customers. Contact Microsoft if you want to have it enabled for your cloud environment.

- **Product variant matching fix** – Fixed an issue where invoices that included product variants were triggering an "Item number isn't the same as the one on the purchase order line" validation error, even if a matching PO line existed.

    As a result of this fix, item numbers are accurately matched with variants during the derive and check process.

### Feature enhancements

| Feature | Description |
| --- |--- |
| Multi-line selection and removal for invoice lines | The select all and multi-line removal feature simplifies the review process for invoices that have multiple lines. Users can now use a single checkbox to select or clear the selection of all invoice lines on the current page. Therefore, they can more quickly remove unwanted lines. This feature is useful for invoices that have hundreds of entries. A confirmation dialog ensures safe deletion, and a notification confirms success. |
| Quantity decimal precision configuration | The **Quantity decimal precision** feature lets users control the number of decimal places that are shown for quantity fields. Quantity fields were previously limited to two decimal places. This limitation caused issues in precision-sensitive industries like steel manufacturing. A new dropdown list lets users select between two decimal places (the default setting) and three decimal places for greater accuracy. |

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
