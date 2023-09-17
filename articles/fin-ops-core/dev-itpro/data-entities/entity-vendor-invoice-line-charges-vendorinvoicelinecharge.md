---
title: Vendor invoice line charges entity
description: Definition of the Vendor invoice line charges data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Vendor invoice line charges entity

The **Vendor invoice line charges** entity supports creating and updating vendor invoice line level charges applied at invoice line document; and includes all the fields related to the vendor invoices line charges.

## When to use this entity

The **Vendor invoice line charges** entity can be used to apply charges to a vendor invoice line.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Vendor invoice line charges |
| **OData public entity** | VendorInvoiceLineCharge |
| **OData public collection** | VendorInvoiceLineCharges |
| **Related menu item** | Accounts payable / Invoices / Pending vendor invoices</br>Accounts payable / Invoices / Open vendor invoices</br>Accounts payable / Vendors / Invoice |
| **Related entities** | Vendor invoice line |
| **Performance pattern** | Multiple threads supported |
| **Application Object Tree (AOT) name** | VendorInvoiceLineChargeEntity |

## Fields

| Field | Description |
|--|--|
| Headerreference | Specifies the first segment of the primary key. Specifies  a foreign key to a **Vendor invoice header**. |
| ChargeLineNumber | Specifies  the second segment of the primary key. This field is required. |
| InvoiceLineNumber | Specifies the third segment of the primary key. This field is required. |
| ChargeCategory | Specifies a foreign key to a **Charge category**. |
| FixedChargeAmount | Fixed charge amount. |
| IsIntercompanyCharge | Specifies if the line is an intercompany charge. |
| PurchaseChargeCode | Specifies a foreign key to a **Charge code**. |
| ChargeAccountingCurrencyCode | Specifies a foreign key to a **Currency**. |
| SalesTaxGroupCode | Specifies a foreign key to a **Sales tax group**. |
| SalesTaxItemGroupCode | Specifies a foreign key to a **Sales tax item group**. |

## Issues and considerations

The **Vendor invoice line charges** entity supports creating and updating charges applied to a vendor invoice line. Line charges can be created only after vendor invoice line is created and before posting vendor invoice.

## Related resources

[Import vendor invoices in Dynamics 365 projects](/dynamics365/guidance/resources/import-vendor-invoices)  
