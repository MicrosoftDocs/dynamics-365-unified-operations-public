---
# required metadata

title: Inventory availability in dual-write
description: This topic provides information about how to check inventory availability in dual-write.
author: yijialuan
manager: AnnBe
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: riluan
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-05-26

---

# Inventory availability in dual-write

[!include [banner](../../includes/banner.md)]

By using inventory availability, you can check your inventory before you add a product to the **Quotations**, **Orders**, or **Invoices** page in Microsoft Dynamics 365 Sales. For example, you check inventory and determine a fulfillment date as one key task in the [prospect-to-cash](dual-write-prospect-to-cash.md) process.

If you don't have enough inventory, you can estimate a delivery date, based on projected inventory receipts and issues. You can also check the product's available-to-promise (ATP) information, where you can find the ATP quantity in the predefined time fence.

## On-hand inventory

In Dynamics 365 Sales, a new **On-hand Inventory** button has been added to the header of the **Quotes**, **Orders**, and **Invoices** pages. When you select this button, a dialog box appears, where you can specify the company and the product that you want to check the on-hand inventory for. This dialog box shows the same information as [On-hand inventory](../../../../supply-chain/inventory/tasks/check-availability-stock.md).

The dialog box returns the inventory information from Dynamics 365 Supply Chain Management. This information includes the following quantities:

- On-hand quantity
- Reserved on-hand quantity
- Available on-hand quantity
- Ordered quantity
- On-order quantity
- Reserved ordered quantity
- Total available quantity

## ATP information

In Sales, a new **ATP Information** button has been added to line items on the **Quotes**, **Orders**, and **Invoices** pages. When you select this button, a dialog box appears, where you can specify the company, product, inventory site, inventory warehouse, and order quantity. This dialog box has the same settings that are described in [Order promising](../../../../supply-chain/sales-marketing/delivery-dates-available-promise-calculations.md#atp-calculations).

The dialog box returns the ATP information from Supply Chain Management. This information includes the following quantities:

- ATP quantity
- Receipt quantity
- Issue quantity
- On-hand quantity
