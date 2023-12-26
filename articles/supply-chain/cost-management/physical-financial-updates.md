---
# required metadata

title: Physical and financial updates
description: This article provides an overview of which types of transactions increase or decrease inventory quantities. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventTrans, InventTransVoucher
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 128340e1-c573-48e6-b835-6c350d8dd0fb
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Physical and financial updates

[!include [banner](../includes/banner.md)]

This article provides an overview of which types of transactions increase or decrease inventory quantities. 

Inventory transactions can be physically updated and financially updated in Dynamics 365 Supply Chain Management. Some types of physical and financial transactions increase inventory quantities, whereas others decrease the quantity.

## Physical increases
When a physical transaction is posted, the status of the transaction record is **Received**. The following transactions are considered physical increases:

-   Purchase order receipt
-   Sales order packing slip return
-   Reporting a production order as finished
-   By-product on a production order picking list

## Financial increases
When a financial receipt transaction is posted, the status of the transaction record that increases the quantity is **Purchased**. The following transactions are considered financial increases:

-   Vendor invoice
-   Sales order invoice for a return
-   Production order costing
-   Positive quantity inventory journals, such as movement, profit and loss, counting, bill of materials, and transfer

## Transactions that increase quantity
Transactions that increase quantity are posted at the running average cost price. The calculated running average cost price is based on the cost of each of these transactions for each inventory dimension that is being tracked financially. For information about running average cost prices, see [Running average cost price](running-average-cost-price.md).

## Transactions that decrease quantity
The calculated running average cost price is used  when a transaction that decreases quantity is posted, regardless of the inventory model that is associated with that inventory. The transaction that decreases quantity must not have been marked to another transaction before it was posted. If the physical on-hand inventory becomes negative, the inventory cost that is defined for the item on the **Item** page is used. 

> [!NOTE]
> If multisite functionality is enabled, this cost will instead be the inventory cost that is defined for a site on the **Default order settings** page.

## Physical issues vs. financial issues
When a physical issue transaction is posted, the status of the transaction record is **Deducted**. The following transactions are considered physical issues:

-   Production order picking list journal
-   Sales order packing slip
-   Purchase order packing slip return

When a financial transaction is posted, the status of the transaction record is **Sold**. The following transactions are considered financial issues:

-   Ending a production order
-   Sales order invoice
-   Vendor invoice return
-   Negative quantity inventory journals, such as movement, profit and loss, counting, bill of materials, and transfer

Transactions that decrease quantity are posted at the running average cost price. Therefore, the inventory close procedure is required in order to settle issue transactions to receipt transactions, based on the inventory model that is assigned to each item.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]