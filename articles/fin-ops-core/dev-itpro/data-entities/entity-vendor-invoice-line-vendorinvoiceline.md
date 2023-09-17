---
title: Vendor invoice line entity
description: Definition of the Vendor invoice line data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Vendor invoice line entity

The **Vendor invoice line** entity supports creating and updating vendor invoices lines. It includes all the fields related to vendor invoice lines.

## When to use this entity

Use the **Vendor invoice line** entity to create vendor invoices before importing the related vendor invoice lines.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Vendor invoice line |
| **OData public entity** | VendorInvoiceLine |
| **OData public collection** | VendorInvoiceLines |
| **Related menu items** | Accounts payable / Invoices / Pending vendor invoices / Edit / Lines</br>Accounts payable / Invoices / Open vendor invoices / New / Vendor tax invoice / Lines</br>Accounts payable / Invoices / Open vendor invoices / New / One-time vendor and invoice / Lines</br>Accounts payable / Vendors / Invoice / New / Vendor invoice / Lines |
| **Related entities** | Vendor invoice line charges |
| **Performance pattern** | Multiple threads supported |
| **Application Object Tree (AOT) name** | VendorInvoiceLineEntity |

## Fields

| Field | Description |
|--|--|
| HeaderReference | Specifies the first segment of the primary key. Specifies a foreign key to a **Vendor invoice header**. |
| InvoiceLineNumber | Specifies the second segment of the primary key. |
| Currency | Specifies a foreign key to a **Currency**. This field is required. |
| DimensionDISPLAYVALUE | Specifies the string value for the default dimensions. Updating this field requires configuring the **Default dimension format** using the **Financial dimension configuration for integrating applications** menu item. |
| InvoiceAccount | Specifies a foreign key to a **Vendor**. |
| ItemNumber | Specifies a foreign key to a **Product**. This field is required for stocked items. |
| NetAmount | The invoice net amount for each invoice line not including charges and tax. |
| ProcurementCategoryName | Specifies a foreign key to a **Procurement category**. |
| PurchaseOrder | Specifies a foreign key to a **Purchase order**. This field is required if the vendor invoice is linked to a purchase order. |
| PurchLineNumber | Specifies a foreign key to a **Purchase order**. This field is required if the vendor invoice line is linked to a purchase order line. |
| VendorAccount | Specifies a foreign key to a **Vendor.** |

## Issues and considerations

The **Vendor invoice line** entity supports creating and updating vendor invoice lines after vendor invoice headers are created. An update is applicable only before posting vendor invoices.

## Related resources

[Import vendor invoices in Dynamics 365 projects](/dynamics365/guidance/resources/import-vendor-invoices)  
