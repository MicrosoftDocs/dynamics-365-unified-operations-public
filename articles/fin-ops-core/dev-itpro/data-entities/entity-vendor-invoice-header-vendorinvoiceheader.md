---
title: Vendor invoice header entity
description: Definition of the Vendor invoice header data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Vendor invoice header entity

The **Vendor invoice header** entity supports creating and updating vendor invoice headers; and includes all the necessary fields.

## When to use this entity

Use the **Vendor invoice header** entity to create a vendor invoice header before importing anything else related to a vendor invoice.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Vendor invoice header |
| **OData public entity** | VendorInvoiceHeader |
| **OData public collection** | VendorInvoiceHeaders |
| **Related menu items** | Accounts payable / Invoices / Pending vendor invoices</br>Accounts payable / Invoices / Open vendor invoices</br>Accounts payable / Vendors / Invoice |
| **Related entities** | Vendor invoice charges</br>Vendor invoice document attachment V2</br>Vendor invoice line |
| **Performance pattern** | Multiple threads supported |
| **Application Object Tree (AOT) name** | VendorInvoiceHeaderEntity |

## Fields

| Field | Description |
|--|--|
| CURRENCY | The currency for the vendor invoice. |
| CASHDISCOUNT | Deduction allowed by vendor from the invoice price. |
| CASHDISCOUNTCODE | The cash discount that is offered. |
| CASHDISCOUNTDATE | If "Use document date" option is marked, then it uses the posting date as the base date, else it uses the invoice date as the base date. |
| CHARGESGROUP | Charges group is available in header entity, but that depends on Invoice is related to PO/Non-PO one, if it is non-po it is working. |
| DIMENSIONDISPLAYVALUE | Specifies the string value for the default dimensions. Updating this field requires configuring the **Default dimension format** using the **Financial dimension configuration for integrating applications** menu item**.** |
| IMPORTEDAMOUNT | Specifies the snapshot of the source total amount. |
| INVOICEACCOUNT | Specifies a foreign key to a **Vendor**. |
| INVOICEDATE | Invoice date will be blank if not specified |
| INVOICENUMBER | Specifies the vendor invoice document reference number. If VENDINVOICEINUSERECOVERENABLE is marked, then duplicate invoice numbers are allowed. This field is required. |
| SALESTAXGROUP | Specifies a foreign key to a **Sales tax group**. |
| VENDORACCOUNT | Specifies a foreign key to a **Vendor**. |

## Issues and considerations

The **Vendor invoice header** entity supports creating and updating vendor invoice headers related to PO linked or non-PO linked. Update is applicable only before posting the vendor invoice. This entity only creates headers, you must use the **Vendor invoice line** entity to import vendor invoice lines after the header is imported.

## Related resources

[Import vendor invoices in Dynamics 365 projects](/dynamics365/guidance/resources/import-vendor-invoices)  
