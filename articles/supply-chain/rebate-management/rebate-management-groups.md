---
# required metadata

title: Rebate management groups
description: 
author: sherry-zheng
manager: tfehr
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TAMRebateGroup
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: Release 10.0.18
---

# Rebate management groups

[!include [banner](../includes/banner.md)]
<!-- KFM: continue here -->
The calculation for a group of customers is often created for a chain of companies, such as a supermarket chain or franchise company. This type of calculation normally relates to a rebate. With the group of customers requiring the same calculations and rebates, the rebates and deduction groups will process the details for these groups.

A deduction is often calculated irrespective of whom it was sold to. However, there are exceptions, for example, a licensee may construct a deductions scheme whereby customer group A will receive 4% and for customer group B they only receive 3%.

Rebate and deduction calculations can be driven by groups. A group can be attached to a master record. Rebate management groups can be created for Customers, Vendors and Items.

## Customer rebate Groups

The calculation for a group of customers is often created for a chain of companies, such as a supermarket chain or franchise company. This type of calculation normally relates to a rebate.

A deduction is often calculated irrespective of whom it was sold to. However, there are exceptions, for example a licensee may construct a deductions scheme whereby customer group A will receive 4% and for customer group B they only receive 3%.

### Set up a customer rebate group

To work with rebate and deduction customer groups, go to **Rebate management \> Rebates and Deduction groups setup \> Customer and vendor groups** , and then make settings as described in the following subsections.

| **Field** | **Description** |
| --- | --- |
| **Rebate and deductions Group** | Identification for the rebate and deduction groups |
| **Description** | Description of the rebate and deduction groups |

### Attach a rebate and deduction group to a customer

It is possible to add more than one Group to a customer. A customer rebate and deductions group can be attached in one of two ways:

- From the **Customers** button on the Rebate management customer group (above)
  - Select **New** and select the customer
- From **Accounts receivable \> Customers \> All customers \> Rebate deduction groups** in the Rebate and deduction group Action pane **Customers** button on the Rebate management customer group (above)
  - Select **New** to create a new record
  - Select the rebate and deductions group

## Vendor rebate groups

The calculation for a group of vendors is often created for a group of delivery points. This type of calculation normally relates to a rebate.

### Set up vendor rebate groups

To work with rebate and deduction customer groups, go to **Rebate management \> Rebates and Deduction groups setup \> Customer and vendor groups** , and then make settings as described in the following subsections.

| **Field** | **Description** |
| --- | --- |
| **Rebate and deductions group** | Identification for the rebate and deduction groups |
| **Description** | Description of the rebate and deduction groups |

### Attach a rebate and deduction group to a vendor

It is possible to add more than one Group to a vendor. A vendor rebate and deductions group can be attached in one of two ways:

- From the **Vendors** button on the Rebate management customer group (above)
  - Select **New** and select the vendor
- From **Accounts payable \> Vendors \> All vendors \> Rebate deduction groups** , in the **Rebate and deduction** group Action Pane **Vendors** button on the Rebate management vendor group (above)
  - Select **New** to create a new record
  - Select the rebate and deductions group

## Item rebate groups

The purpose of grouping items gives greater flexibility for calculating rebates / deductions by groups of items. It is often a more efficient method of setting up rebates / deductions for customers and vendors.

### Set up item rebate groups

To work with rebate and deduction item groups, go to **Rebate management \> Rebates and Deduction groups setup \> Item groups** , and then make settings as described in the following subsections.

| **Field** | **Description** |
| --- | --- |
| **Rebate and deductions group** | Identification for the rebate and deduction groups |
| **Description** | Description of the rebate and deduction groups |

### Attach a rebate and deduction group to an item

Items can be attached to a rebate and deductions group in one of three ways. From **Rebate management \> Rebates and deduction groups setup \> Item** (as above)

Via the **Add items button**

- Select **the Category hierarchy**.
- Optionally select the **category** from the left-hand pane.
- Select the **check box** next to the items.
- Select **OK** once completed.

Via the **Items button**

- Select **New** and enter / select items.
- Select **OK** once completed.

From **Product information management \> Products \> Released products** select **Rebate and deductions group** on the Action pane

- Select **New** to create a new record.
- Select the **rebate and deductions group**.
