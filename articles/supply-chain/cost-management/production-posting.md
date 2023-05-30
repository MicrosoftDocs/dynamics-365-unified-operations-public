---
# required metadata

title: Production posting
description: This article provides information about different types of postings in the production process.
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventItemGroup, ProjCategory, WrkCtrResourceGroup, WrkCtrTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 0917fe64-f643-46ae-98ff-5013b266a067
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Production posting

[!include [banner](../includes/banner.md)]

This article provides information about different types of postings in the production process.

Production posting activities follow production processes that are described in the sections below.

## Material consumption
Materials are registered as consumed during production when the production picking list journal is posted. This process generates issue transactions that deduct the on-hand inventory. In the production parameters, you can specify whether the value of raw materials that are in progress (work in process \[WIP\]) should be posted in the ledger. The value of raw materials that are in progress (WIP) is then posted to a dedicated Picking list account and a dedicated Picking list offset account.

## Time consumption
The time that workers spend on production jobs is recorded in the Route card journal or the Job card journal. When these journals are posted, ledger posting to a dedicated account for resources that are in progress (WIP) is processed. This posting represents the value of the time that is spent on the production order. After the production order is registered as ended, the WIP accounts are settled.

## Reporting finished goods and error quantities
When a production order is reported as finished, the quantity of the finished goods that have been completed is updated in Inventory management through the Report as finished journal. If you're using WIP accounting, which can be set up in the production parameters, a ledger journal is made to reduce the WIP accounts and increase the inventory of the finished goods. The journal uses the standard cost that is defined for the product.

## Ending the production order
Before a production order is ended, actual costs are calculated for the quantity that was produced. All estimated costs of material, labor, and overhead are reversed and replaced with actual costs. The overall cost of the finished item is debited from the inventory Receipt account and credited to the inventory Issues account. If you select the **End job** check box when you run the cost calculation, the status of the production order is changed to **Ended**. This status prevents any additional costs from being unintentionally posted to a completed production order. You can specify that the value of error quantities that are reported during reporting as finished should be allocated to the good quantities that are reported as finished. Alternatively, you can specify that the value of error quantities should be posted to a dedicated scrap account.

## Controlling the level of ledger posting
In the **Production control parameters**, you can use the **Ledger posting** field to set the level of ledger posting for production processes. The following values are available:

-   **Item and resource** – Use the ledger accounts that are set up on the item groups for raw materials and finished goods. WIP for time consumption is taken from resource or resource group from the route operations.
-   **Item and category** – Use the ledger accounts that are set up on the item groups for raw materials and finished goods. WIP for time consumption is taken from the cost categories that are associated with the route operations.
-   **Production groups** – Use the ledger accounts that are set up on the production groups for both material and time consumption. The production groups are associated with the released products and copied to the production orders when those orders are created. The posting on the production orders will then follow the production groups that are associated with the production order.

**Note:** If the standard method for calculating the cost of the finished item was used, the final transactions reflect this fact. If actual costs and the costs that are calculated by using the standard method differ, the difference is posted to the account that shows profit or loss.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]