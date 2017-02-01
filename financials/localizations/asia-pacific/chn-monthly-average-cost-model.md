---
# required metadata

title: Monthly average cost model for China | Microsoft Docs
description: Inventory costing is used to determine the cost or monetary value of warehoused inventory items.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-21 16:22:40
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 265044
ms.assetid: 043992e8-0fd7-42f5-9cf3-0d7eb41f96d6
ms.region: China (PRC)
# ms.industry: 
ms.author: leguo

---

# Monthly average cost model for China

Inventory costing is used to determine the cost or monetary value of warehoused inventory items.

Inventory costing can be performed by using the following standard models:
-   First in, first out (FIFO)
-   Last in, first out (LIFO)
-   Weighted average
-   Weighted average date
-   Standard cost

In addition to the standard inventory costing methods, the monthly average cost inventory model is widely used in China to evaluate inventory cost. The monthly average cost inventory model is based on the weighted average principle. This is like the weighted average date model, except that the value is calculated by month instead of by date. The monthly average cost model is considered to be an alternative to the weighted average date and standard cost models. By using the monthly average cost model, the average costs are calculated and adjusted for each month; therefore, the cost figures are closer to the actual prices than they are using the standard cost model. The following table lists specific differences between the weighted average date model and the monthly average cost model.

| Weighted average date                                                                                                                                                                                                                                                                                                                 | Monthly average cost                                                                                                                                                                                                                                                                                                                                                                                                        |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The items issued from inventory are valued by using the average value of the items that are received into inventory for each day during the inventory closing period.                                                                                                                                                                 | The items issued from inventory are valued by using the average value of the items that are received into inventory over a month-long period.                                                                                                                                                                                                                                                                               |
| All inventory issued transactions for the day are adjusted so that all output transactions have the same unit cost. Therefore, there can be several unit costs for a single item during the inventory closing period.                                                                                                                 | All inventory issued transactions for the month are adjusted so that all output transactions during the month have the same unit cost.                                                                                                                                                                                                                                                                                      |
| Invoiced inventory transactions are calculated and settled before the closing date. For example, if you are closing inventory on October 31, 2016, and there are open transactions for September and October, all open issued transactions for September and October will be settled together, and adjusted to the same average cost. | Invoiced inventory transactions are calculated and settled monthly. For example, if you are closing inventory on October 31, 2016, and there are open transactions for September and October, the September transactions are calculated and settled first, and are adjusted to the average cost for September. Then, the October transactions are calculated and settled, and are adjusted to the average cost for October. |

When you run a monthly inventory closing by using the monthly average cost model, all receipts for the month are settled against an issued transaction, which represents the total received quantity and value for that month. This issued transaction has a corresponding receipt transaction, from which all inventory transaction issues will be settled. In this manner, all issue are allocated the same average cost. The issued transaction and receipt transaction can be seen as a transfer, which is named the weighted average inventory closing transfer.
| **Note**                                                                                                                                                                                                                                                                                                                     |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If only one receipt occurred in or before the month, you do not have to average the value. This is because all issue are settled from the receipt, and the transfer is not created. Likewise, if only one issue occurs in the month, there are no receipts from which to average the value, and the transfer is not created. |

The monthly average cost model is used to calculate the weighted average cost of an item at the end of the month. This average cost is used to adjust all issued transactions during the month, so that all output transactions for the month carry the same unit cost. For example, when an issued transaction is posted, its unit cost is calculated as the average cost at that time. Therefore, the unit costs for all issued transactions will be different. At the end of the month, when you run the monthly average cost adjustment, all unit costs that are generated during the month are adjusted to a uniform monthly average cost. The adjustment is based on the following formula:
Monthly average cost = (The beginning inventory value for the month + The increased inventory value) / (The beginning quantity + The increased quantity)

Many Chinese manufacturing and trading companies use a monthly average cost model because it is a simple means of manually calculating inventory value. The following table compares the processes that are used to handle issue and receipt transactions in the manual monthly average cost model and the monthly average cost model that is available in Microsoft Dynamics 365 for Operations.
| Manual monthly average cost model                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Monthly average cost model in Microsoft Dynamics 365 for Operations                                                                                                                                                        |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The monthly average cost is calculated, including all receipt and issue transactions. If the receipt transactions have not been invoiced, the estimated physical price is considered. The calculated monthly average cost is used to settle all issued transactions for the month, whether they are invoiced or not. When the receipts are invoiced, if there are differences between the estimated physical price and the invoiced price, the difference is added to the current on-hand inventory value. No adjustment is made to the previously issued transactions. If the current inventory quantity is 0 (zero), the differences are adjusted in the expense account. | Only the monthly average cost from invoiced receipts is calculated, and only invoiced issue transactions are settled. Non-invoiced receipts and issue transactions are calculated and settled only when they are invoiced. |

 



