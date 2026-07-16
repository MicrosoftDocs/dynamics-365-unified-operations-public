---
title: Procurement and sourcing in the public sector
description: Learn about the public sector Procurement and sourcing functionality, including purchase order codes, vendor certification types, purchase order line amounts.
author: velofog
ms.author: twheeloc
ms.topic: article
ms.date: 06/22/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AgreementClassification, BudgetParameters, ProcCategoryHierarchyManagement, PurchTableListPage, smmActivities, VendCertificationType, VendTableListPage
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: c99b2aeb-4ac2-4abe-b8b9-786b664c103d
---

# Procurement and sourcing in the public sector

[!include [banner](../includes/banner.md)]

This article introduces you to the public sector procurement and sourcing functionality. This functionality includes purchase order codes, vendor certification types, purchase agreement classification functionality, and purchase order line amounts.

## What are the prerequisites for setting up procurement and sourcing in the public sector?

Before you begin to adjust the settings and input your data, complete the following tasks:

- Set up vendors.
- Set up the numbering system for vendors, purchase orders, and other entities.
- Specify vendor certification types.

You might need to set up the following procurement and sourcing features for public sector organizations:

- [Purchase order codes in the public sector](purchase-order-codes-public-sector.md):
Create codes and special messages for confirming purchase orders. A confirming purchase order circumvents the typical purchasing process.

> [!NOTE]
> This feature also applies to accounts payable.

- [Public sector accounting in France](../localizations/emea-fra-public-sector-accounting.md)

For French organizations, additional steps might be required for the public sector.

The following sections describe the procurement and sourcing features that are available for the public sector.

## What are vendor certification types?

You can create and assign to vendor organizations any types of certification that the vendors hold. This certification types include not only professional credentials, such as a professional engineer’s license or Microsoft SQL Server Certification, but also whether they have liability insurance, minority status, or are in compliance with various environmental or consumer safety standards.

Use the **Certification type** page in Accounts payable to enter the certification type and the description.

## What do I need to know about purchase or sales agreement classifications?

When users create a new purchase agreement or sales agreement, they must always select the type of purchase agreement or sales agreement. Additional public sector controls are available on the **Agreement classifications** pages.

To create and specify agreement classifications, use the **Purchase agreement classification** page in Procurement and sourcing or the **Sales agreement classification** page in Sales and marketing.

Take the following information into account when specifying details for purchase or sales agreement classifications.

### How do I enter information about subcontractors on purchase agreements?

Select the **Subcontractors** option.

### How do I enter information about insurance policies and bonds on purchase agreements?

Select the **Certifications** option. The information can be used to generate a report that you can use to monitor vendor compliance with certification requirements. (To generate the report, go to the **Purchase agreement certification compliance** page.)

### How do I enter information about milestones and tasks on purchase agreements?

Select the **Activities** option.

### How do I require direct invoicing and prevent the use of release orders with purchase agreements?

Select the **Require direct invoicing** option.

## Can I view purchase order line amounts?

Yes. Line amounts for a purchase order can be viewed, including the current ordered amount and any amounts that have been received or invoiced. They can also view any amounts that remain to be invoiced or amounts for pending invoices.

### Tip

Suppose you view a purchase order line with purchases posted to two ledger accounts. One ledger account is for office furniture ordered from a vendor. The second ledger account is for office supplies. The ordered amount equals the sum of the invoiced amounts, pending invoice amounts, and invoice remaining amounts. The received amount is the portion of the ordered amount that you receive from the vendor.

| **Ledger account** | **Ordered** | **Received** | **Invoiced** | **Pending invoice** | **Invoice remaining** |
|---|---|---|---|---|---|
| 60010 (office furniture) | 1,200.00 | 250.00 | 350.00 | 200.00 | 650.00 |
| 60020 (office supplies) | 750.00 | 150.00 | 400.00 |  | 350.00 |
| Totals | 1,950.00 | 400.00 | 750.00 | 200.00 | 1,000.00 |

For more information, see [Procurement and sourcing overview](../../supply-chain/procurement/procurement-sourcing-overview.md) and
[Accounts payable in the public sector overview](accounts-payable-public-sector.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
