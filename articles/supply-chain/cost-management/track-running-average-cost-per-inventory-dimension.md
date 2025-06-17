---
title: Track running average cost per inventory dimension
description: The running average cost price of an item is calculated based on the selected inventory dimensions that are being tracked financially.
author: prasungoel
ms.author: prasungoel
ms.reviewer: kamaybac
ms.search.form: InventOnhandItem
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Track running average cost per inventory dimension

[!include [banner](../includes/banner.md)]

An inventory dimension group is attached to every inventory item. Therefore, the running average cost price of an item is calculated based on the selected inventory dimensions that are being tracked financially.

There are three types of inventory dimensions: product, storage, and tracking. Product dimensions include configuration, size, and color. Product dimensions are always tracked financially. Storage and tracking dimensions include site, warehouse, location, inventory status, license plate, batch number, and serial number. You can decide which storage and tracking dimensions are tracked financially.

## Example 1

If the storage dimension group that is attached to the item is financially tracked by warehouse, the running average cost price is calculated per warehouse. The following purchase orders have been invoiced:

- A purchase order for a quantity of 2 at a cost price of USD 10.00 has been invoiced for warehouse GW.
- A purchase order for a quantity of 3 at a cost price of USD 12.00 has been invoiced for warehouse GW.
- A purchase order for a quantity of 5 at a cost price of USD 15.00 has been invoiced for warehouse MW.

The running average cost price for warehouse GW is USD 11.20, and the running average cost price for warehouse MW is USD 15.00. A sales order invoice is posted for warehouse GW. The value of the inventory and the cost of goods sold (before inventory close is run and without marking) is USD 11.20. Another sales order is posted for warehouse MW. The value of the inventory and the cost of goods sold (before inventory close is run and without marking) is USD 15.00.

## Example 2

If the storage dimension group that is attached to the item is financially tracked by warehouse, and the tracking dimension group is financially tracked by batch number, the running average cost price is calculated for each batch. The following purchase orders have been invoiced:

- A purchase order for a quantity of 2 at a cost price of USD 10.00 has been invoiced for warehouse GW and batch AAA.
- A purchase order for a quantity of 3 at a cost price of USD 12.00 has been invoiced for warehouse GW and batch AAA.
- A purchase order for a quantity of 2 at a cost price of USD 15.00 has been invoiced for warehouse GW and batch BBB.

The running average cost price for warehouse GW and batch AAA is USD 11.20, and the running average cost price for warehouse GW and batch BBB is USD 15.00.

> [!NOTE]
> We recommend that you always view the cost price for all financial dimensions that are being tracked.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
