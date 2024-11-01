---
title: Reserve the same batch for a sales order
description: Learn how to set up a product to allow reservation of inventory against a single batch of inventory, including definitions of various groups.
author: adpattanaik
ms.author: adpattanaik
ms.topic: article
ms.date: 03/17/2020
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetailsExtended, EcoResStorageDimensionGroup, EcoResTrackingDimensionGroup, InventBatch, InventModelGroup, PdsAskSameLotForm, PdsCustSellableDays, WHSReservationHierarchy, WHSInventTableReservationHierarchy
ms.assetid: 5823d75e-f839-46dd-beb3-e09b79fc8aa4
---

# Reserve the same batch for a sales order

[!include [banner](../includes/banner.md)]

This article explains how to set up a product to allow reservation of inventory against a single batch of inventory.

Same batch reservation lets you reserve inventory for a sales order line against a single batch of inventory. For example, a customer who orders wallpaper can request that the whole order be filled from the same batch or lot, to avoid inconsistencies among the rolls. To set up a product to use same batch reservation, the following settings must be active in the item model group, tracking dimension group, and storage dimension group that you assign to the product:

- **Item model groups** – The item model group must have the **Same batch selection** and **Consolidate requirement** fields selected in the **Reservation** field group for inventory policies.
- **Tracking dimensions groups** – The tracking dimension group must have the **Coverage plan by dimension** field selected for the batch number.
- **Storage dimensions groups** – The storage dimension group must have the **Coverage plan by dimension** field selected for **Site** and **Warehouse**.

When you reserve inventory for a product on a sales order line that is set up for same batch selection, the system tries to reserve the ordered quantity from a single inventory batch. Any specific batch attribute requirements are also considered. If the quantity can't be filled from a single batch, the **Same batch reservation conflict** page appears. This page describes the issues and also the actions that you can take to continue with the reservation. The following conditions might prevent the batch from being reserved:

- The batch disposition code has **Block reservation** for sales flagged as **Blocked**.
- The batch has expired, based on the expiration date and any applicable customer sellable days. The item can still be considered for reservation if the item model group for the item is First Expiry First Out (FEFO) date–controlled, and if the best-before date is selected as the pick criterion.
- The batch doesn't have enough shelf-life days remaining, based on the expiration date and best-before date, plus any customer sellable days.

For items associated with a storage dimension group that has **Use warehouse management processes** enabled, you can reserve specific batch numbers by using a reservation hierarchy where the batch number inventory dimension is defined above the location dimension. This type of reservation hierarchy is also known as a *Batch-above \[location\]* reservation hierarchy. The **Batch reservation** page for sales and transfer order lines also lets you select and reserve multiple lines based on the available batch numbers. For more information about what to do if you are using a reservation hierarchy that has the batch number dimension below the location (*Batch-below \[location\]*), see [Flexible warehouse-level dimension reservation policy](../warehousing/flexible-warehouse-level-dimension-reservation.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
