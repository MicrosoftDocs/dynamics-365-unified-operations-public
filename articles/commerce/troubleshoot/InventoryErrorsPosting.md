---
title: Statement posting error either due to unavailable inventory or due to update conflict
description: This article provides the possible workarounds for inventory related issues during statement posting.
author: Shajain
ms.date: 12/06/2022
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-01-31

---

# Statement posting error either due to unavailable inventory or due to update conflict 

[!include [banner](../../includes/banner.md)]

## Symptoms
During posting of the Commerce transactions, you might receive an error message that resembles "xx cannot be picked because only yy is/are available from the inventory".

The second type of error you might encounter is about an update conflict. This issue can occur when the inventory valuation method is either *Standard cost* or *Moving average*. Both these methods are perpetual costing methods. In other words, the final cost is determined at the time of posting.

If you're using the *Moving average* method, the error message resembles this example:
> Inventory value xx.xx is not expected after the proportional expense calculation

If you're using the *Standard cost* method, the error message resembles this example:
> The standard cost does not match with the financial inventory value after the update. Value = xx.xx, Qty = yy.yy, Standard cost = zz.zz

## Workaround
### Workaround for not enough inventory error
This issue can be mitigated by either manually updating the inventory for the item or by turning on the negative physical inventory on the item model group associated with the item (refer the image below to enable physical negative inventory). We recommend turning on the negative physical inventory on the item model group, for a seamless posting experience. In some scenarios, statements might not be able to be posted unless there is negative physical inventory enabled. For example, if there was no inventory available for an item, but to mimic a price match, the cashier returns the item and adds it back to the same transaction at a reduced price, then both return and sale transactions will be pulled in the same statement in a single customer order. There is no guarantee that the return will be posted first (to increase the inventory), followed by the sales line (to reduce the inventory) and thus errors can occur. If negative inventory is turned on in this scenario, the transaction posting isn't negatively affected, and the system will correctly reflect the inventory.

![Enable physical negative inventory](./media/Physical_Negative_Inventory.png "Enable negative physical inventory")
 
### Workaround for update conflict error
For the error message related to the update conflict please refer the link [Update conflict mitigation](https://learn.microsoft.com/en-us/troubleshoot/dynamics-365/supply-chain/costing/update-conflict-standard-cost-moving-average-inventory-valuation) for possible workarounds.

> [!NOTE]
> For this error, you do not need to delete the customer orders generated with the aggregation step of posting. After implementing the suggested workarounds, reattempting the statement posting should post the statement.


