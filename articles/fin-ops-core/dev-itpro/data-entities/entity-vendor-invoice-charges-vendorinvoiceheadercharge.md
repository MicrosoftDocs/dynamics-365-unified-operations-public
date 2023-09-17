---
title: Vendor invoice charges entity
description: Definition of the Vendor invoice charges data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Vendor invoice charges entity

The **Vendor invoice charges** entity supports creating and updating vendor invoice charges applied to the invoice header. It includes all the fields related to the vendor invoices charges.

## When to use this entity

The **Vendor invoice charges** entity is used to add charges to a vendor invoice header.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Vendor invoice charges |
| **OData public entity** | VendorInvoiceHeaderCharge |
| **OData public collection** | VendorInvoiceHeaderCharges |
| **Related menu items** | Accounts payable / Invoices / Pending vendor invoices</br>Accounts payable / Invoices / Open vendor invoices</br>Accounts payable / Vendors / Invoice |
| **Related entities** | Vendor invoice header |
| **Performance pattern** | Multiple threads supported |
| **Application Object Tree (AOT) name** | VendorInvoiceHeaderChargeEntity |

## Fields

| Field | Description |
|--|--|
| Headerreference | Specifies the first segment of the primary key. Specifies a foreign key to a **Vendor invoice header**. |
| ChargeLineNumber | Specifies the second segment of the primary key. This field is required. |
| VendInvoiceInfoTableDataAreaId | Specifies the third segment of the primary key. This field is required. |
| ChargeCategory | Specifies a foreign key to a charge category. |
| PurchaseChargeCode | Specifies a foreign key to a charge code. |
| ChargeAccountingCurrencyCode | Specifies a foreign key to a currency. |
| SalesTaxGroupCode | Specifies a foreign key to the **Sales tax groups** entity. |
| SalesTaxItemGroupCode | Specifies a foreign key to a **Sales tax item group**. |

## Issues and considerations

The **Vendor invoice charges** entity supports creating and updating charges applied to a vendor invoice header. Charges can be created or updated before the vendor invoice is posted.

## Related resources

[Import vendor invoices in Dynamics 365 projects](/dynamics365/guidance/resources/import-vendor-invoices)  
