---
title: Statement posting error either due to unavailable inventory or due to update conflict
description: This article provides possible workarounds for inventory related issues during statement posting in Microsoft Dynamics 365 Commerce.
author: Shajain
ms.date: 12/14/2022
ms.topic: Troubleshooting
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-01-31

---

# Statement posting error either due to unavailable inventory or due to update conflict 

[!include [banner](../../includes/banner.md)]

This article provides possible workarounds for inventory related issues during statement posting in Microsoft Dynamics 365 Commerce.

## Description

During the posting of Commerce transactions, you may receive an error message similar to `xx cannot be picked because only yy is/are available from the inventory`.

The second type of error you might encounter is about an update conflict. This issue can occur when the inventory valuation method is either *standard cost* or *moving average*. Both of these methods are perpetual costing methods, which means that the final cost is determined at the time of posting.

If you're using the moving average method, the error message will be similar to this example:
`Inventory value xx.xx is not expected after the proportional expense calculation`

If you're using the standard cost method, the error message will be similar to this example:
`The standard cost does not match with the financial inventory value after the update. Value = xx.xx, Qty = yy.yy, Standard cost = zz.zz`

## Resolution

### Workaround for the not enough inventory error

This issue can be mitigated by either manually updating the inventory for the item or by turning on the negative physical inventory on the item model group associated with the item (refer the image below to enable physical negative inventory). We recommend turning on the negative physical inventory on the item model group, for a seamless posting experience. In some scenarios, statements might not be able to be posted unless there's negative physical inventory enabled. For example, if there was no inventory available for an item, but to mimic a price match, the cashier returns the item and adds it back to the same transaction at a reduced price, then both return and sale transactions will be pulled in the same statement in a single customer order. There's no guarantee that the return will be posted first (to increase the inventory), followed by the sales line (to reduce the inventory) and thus errors can occur. If negative inventory is turned on in this scenario, the transaction posting isn't negatively affected, and the system will correctly reflect the inventory.

![Enable physical negative inventory](./media/Physical_Negative_Inventory.png)
 
### Workaround for the update conflict error

For the error message related to the update conflict, see [Update conflict mitigation](/troubleshoot/dynamics-365/supply-chain/costing/update-conflict-standard-cost-moving-average-inventory-valuation) for possible workarounds.

> [!NOTE]
> For this error, you don't need to delete the customer orders generated with the aggregation step of posting. After implementing the suggested workarounds, reattempting the statement posting should post the statement.


