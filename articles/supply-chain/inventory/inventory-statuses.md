---
# required metadata

title: Inventory statuses
description: This article describes how you can use inventory statuses to categorize and keep track of inventory.
author: MarkusFogelberg
manager: tfehr
ms.date: 06/20/2017
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: EcoResStorageDimensionGroup, WHSInventStatus, WHSWarehouseStatusChange
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 21331
ms.assetid: b35f495f-de4f-48a0-9d09-4d06781d7650
ms.search.region: Global
# ms.search.industry:
ms.author: mafoge
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Inventory statuses

[!include [banner](../includes/banner.md)]

This article describes how you can use inventory statuses to categorize and keep track of inventory.

## Set up and use inventory statuses

You can use inventory statuses to categorize inventory. You can then initiate appropriate actions, such as replenishment or put-away work.

Here are some examples of ways that you can use inventory statuses:

- Create inventory statuses for on-hand inventory, inbound transactions, and outbound transactions.
- Specify a default inventory status for warehouse transactions.
- Change an inventory status for items before arrival, during arrival, or when the items are put away during inventory movement.
- Use an inventory status to price items that are returned and to plan item coverage during master planning.

An inventory status is one of the dimensions in the storage dimension group. Inventory statuses can be categorized as available or unavailable, and you can use the **Inventory blocking** parameter to block items that have an unavailable inventory status. Items that have a blocked status are considered physical inventory, and they can't be used on a production order, sales order, transfer order, or outbound transaction.

You can use warehouse items that have either available or unavailable inventory statuses for inbound work. For example, you create an available status that is named *Ready*, an unavailable status that is named *Damaged*, and a blocked status that is named *Blocked*. When you create a purchase order for received or returned items, if any items are damaged or broken, you can change the inventory status of those items to *Damaged* on the purchase order line. After these items are received, the status is automatically set to *Blocked*. If you scan the damaged items by using a mobile device, Supply Chain Management can use location directives and work templates to show information about an appropriate location or range of locations where you can put away those items. For returned items, an issue type of *Reservation* is created on the **Inventory transactions** page.

For outbound work, use items that have an available inventory status. If you have items that have a status of *Broken*, and master planning is run on these items, the items are considered missing, and inventory is automatically replenished.

After you set up inventory statuses, you can set the default inventory status for a site, item, and warehouse. You can also set a default status for sales, transfer, and purchase orders. The default status for sales orders and outbound transfer order can't have the **Inventory blocking** option set to *Yes*. The inventory status that is inherited from the default settings on a site, warehouse, item, purchase order, transfer order or sales order can be changed by using the mobile device, or on the purchase order, sales order, or transfer order line.

To plan coverage for items that have an available inventory status, select the **Coverage plan by dimension** option for a storage dimension on the **Storage dimension groups** page. When you open the **Item Coverage** wizard, items that have an available status appear on the **Status** page. To create coverage settings for these items, select the inventory status ID for the available inventory statuses. Based on the coverage settings, you can calculate the item requirements and forecast the supply and demand of available items during master planning. You can't create an item coverage setup that has a blocked inventory status. Alternatively, use the **Item coverage** page to create or modify the item coverage parameters.

## Change inventory statuses

You can change inventory statuses either by using the **On-hand by location** page or by using the *Inventory status change* periodic task.

- When using the *Inventory status change* periodic task, you can select which records to include and set the task to run in the batch at the desired interval.
- To change inventory status as an ad-hoc process, go to **On-hand by location** page, select the relevant records, and then select the **Inventory status change** button.

> [!NOTE]
> The *Change the inventory status of items controlled by tracking dimensions* feature allows you to change the inventory status of items controlled by tracking dimensions, including the ability to update only selected records. Use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the feature as needed. When the feature is enabled, you'll be able to do the following:
>
> - On the **On-hand by location** page, you can group lines based on shown dimensions using the **Display dimensions** button and change the status for the selected lines.
> - On the **On-hand by location** page, you can select multiple records and then use the **Inventory status change** button to change all of them at once.
> - On the **Inventory status change** periodic task you will be able to filter by tracking dimensions.
