---
# required metadata

title: Include physical value
description: You use the Include physical value check box on the Inventory model FastTab of the Item model groups page to specify whether physically updated transactions are considered when the running average cost price is calculated for an item.
author: JennySong-SH
ms.date: 10/31/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventModelGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 1928c145-bf82-436d-87ca-e7a173e31923
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Include physical value

[!include [banner](../includes/banner.md)]

You use the Include physical value check box on the Inventory model FastTab of the Item model groups page to specify whether physically updated transactions are considered when the running average cost price is calculated for an item.

The **Include physical value** check box has the following values.

| Value    | Result                                                                                                                          |
|----------|---------------------------------------------------------------------------------------------------------------------------------|
| Selected | Both physically updated transactions and financially updated transactions are used to calculate the running average cost price. |
| Cleared  | Only financially updated transactions are used to calculate the running average cost price.                                     |

The check box has slightly different effects, depending on the inventory model that you use.

-   If you select the **Include physical value** check box when you use the FIFO (First in, first out), LIFO (Last in, first out), or LIFO date inventory model, inventory close also makes adjustments to physically updated transactions.
-   If you don't select the **Include physical value** check box when you use these inventory models, inventory close makes settlements only to financially updated transactions.
-   When you use the weighted average or weighted average date inventory model, inventory close settles only financially updated transactions, regardless of whether you select the **Include physical value** check box.

**Example 1** You've selected the **Include physical value** check box and receive the following purchase orders:

-   A purchase order for a quantity of 2 and a cost price of USD 10.00 that has been packing slip–updated.
-   A purchase order for a quantity of 3 and a cost price of USD 12.00 that has been invoice-updated.

In this case, the running average cost price will be USD 11.20 = (2x10+3x12)/(2+3), because both physically updated transactions and financially updated transactions are used to calculate the cost price. 

**Example 2** You haven't selected the **Include physical value** check box, and the cost price on the item setup is USD 10.00. 

-   You receive a purchase order for a quantity of 20 and a cost price of USD 12.00 that has been packing slip–updated.

When a sales order is posted, the posted cost amount is USD 10.00, because the running average cost price won't include physically posted transactions. 

> [!NOTE]
> For comparison, if you select the **Include physical value** check box for this item, when a sales order is posted, the posted cost amount will be USD 12.00.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]