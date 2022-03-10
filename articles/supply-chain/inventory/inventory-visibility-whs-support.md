---
title: Inventory Visibility support for WHS items
description: This topic describes Inventory Visibility support for items that are enabled for advanced warehouse processes (WHS items).
author: yufeihuang
ms.date: 03/10/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2022-03-10
ms.dyn365.ops.version: 10.0.26
---

# Inventory Visibility support for WHS items

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This topic describes Inventory Visibility support for items that are enabled for advanced warehouse processes (WHS items).

## Prerequisites

A WHS item is an item that has warehouse management process enabled, and the processing of this item takes place in a warehouse that also has warehouse management process (WHS) enabled.

To enable support for WHS items in Inventory Visibility (AdvancedWHS):
<!--KFM: This seems to be list of what makes an item enabled for WHS. But what does this have to do with Inventory Visibility? -->

- The item must have advanced warehouse management enabled
- The operation of this item must take place in a warehouse where WHS is enabled as well.

For more information about the Warehouse management module in Supply Chain Management, see [Warehouse management overview](../warehousing/warehouse-management-overview.md)

## Conceptual Description from Dynamics 365 Supply Chain Management Point of View

Inventory Visibility support for WHS items focuses on on-hand quantity calculations based on on-hand queries. It isn't intended to allow you to use Inventory Visibility to manage warehouse processing activities in general. Specifically, the following WHS features aren't supported by Inventory Visibility:

- Warehouse work
- Loads
- Waves
- Transportation management <!--KFM: Are you referring to the Transportation management module? That isn't part of WHS anyway, is it? -->

<!--KFM: Can we combine the previous list with the following list? They seem similar and repetitive. -->

Inventory Visibility does not expose warehouse-specific concepts to its users. Such concepts include:

- Reservation hierarchy
- Whether an item or warehouse is WHS-enabled
- Unit sequence group ID
- Warehouse specific processes, such as shipments, loads, waves, and work.

Inventory visibility infers such information based on the data sent from Supply Chain Management. The Warehouse specific data (i.e., data from `WHSInventReserve` table) is not visible to users.

With this enhancement all the query results will be identical to the queries made on Finance and Operations environments, but not the same as warehouse mobile apps.

## Use Scenarios for This Feature

We suggest users use this feature if all the following requisites are matched:

- Dynamics 365 Supply Chain Management data is synced to Inventory Visibility
- Advanced warehouse management module is used in Dynamics 365 Supply Chain Management, and
- Users make reservations for WHS items at levels other than warehouses. (E.g., users use warehouse works).

Otherwise, the on-hand query result should make no difference with or without AdvancedWHS feature enabled in Inventory Visibility, and we suggest not to enable this feature to reduce the extra calculation overhead to get better performance.

## Enable the WHS feature in Inventory Visibility

You need 3 steps to enable the WHS feature in Inventory Visibility

1. From Dynamics 365 Supply Chain Management, this is a private preview feature on 10.0.25 and will be public preview on 10.0.26. To use this feature on 10.0.25, please contact inventory visibility support team for further information. On 10.0.26 and later versions, go to feature management workspace and enable the feature with name *Enable warehouse items in Inventory Visibility*.
1. On Dynamics 365 Supply Chain Management go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**. Enable WHS item sync on tab page **Enable WHS Items**
1. For inventory visibility side, go to the **Feature Management** page in Power Apps, enable **Advanced** feature.

Now disable and enable the inventory visibility add-in inside Finance and Operations (**Inventory Management \> Periodic Tasks \> Inventory Visibility Integration**, select **Disable** and then **Enable**). The warehouse related data starts to sync to Inventory Visibility.

## Reading the On-hand Quantities of WHS items

There is no specific API call for querying WHS item. The user does not need to specify whether the item is WHS, or non-WHS. Inventory Visibility distinguishes them based on the data stored.

The result for querying a WHS item is the same as querying a non-WHS item. The difference is that the following physical measures under data source `FNO` from the result are calculated based on advanced warehouse management logics in Dynamics 365 Supply Chain Management:

- `AvailOrdered`
- `AvailPhysical`
- `ReservOrdered`
- `ReservPhysical`

The rest of the physical measures are the same as the query result with AdvancedWHS feature disabled in Inventory Visibility.

You may refer to this white paper for a detailed explanation of the on-hand calculation for WHS items. <http://www.microsoft.com/en-gb/download/details.aspx?id=43284>

The On-hand most specific background service is not yet supporting updating the quantities for WHS items. The on-hand most specific results are correct for non-WHS items, as well as those quantities not affected by WHS logics for WHS items (that is, measures excluding AvailPhysical, AvailOrdered, ReservPhysical and ReservOrdered in data source `FNO`)

Changing WHS-item quantities related to Supply Chain Management is prohibited. Is with other features of Inventory Visibility, changing data related to Supply Chain Management isn't allowed to avoid conflicts.

## Soft Reservations on WHS Items in Inventory Visibility

Soft reservation on WHS item is generally supported. You can set WHS-related physical measures into soft reservation calculations. There is a known limitation that the*available for reservation* of WHS item is not supported for now. When there's reservation above the current dimensions where soft reservation is taking place, the available for reservation calculation is incorrect. Soft reservation with the option **check available for reservation** disabled will not be affected.

This is also applicable to features / customizations based on soft reservations, e.g., allocation.

## Calculation of Available to Promise (ATP) quantities

ATP for WHS items is fully supported. You can define ATP calculations without worrying about WHS specific details. <!--KFM: Add link to new ATP topic. -->
