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

This topic describes Inventory Visibility support for items that are enabled for advanced warehouse processes (WHS). The feature that adds this capability to Inventory Visibility is called *Advanced WHS*.

## WHS items

A WHS item is an item that is enabled for advanced warehouse processes (WHS), and which is processed at a warehouse that is also WHS enabled.

For more information about WHS and the Warehouse management module in Supply Chain Management, see [Warehouse management overview](../warehousing/warehouse-management-overview.md)

## Conceptual description from a Supply Chain Management point of view

<!--KFM: A better heading is needed. What is this section, more specially, about? -->

The Advanced WHS feature for Inventory Visibility focuses on on-hand quantity calculations based on on-hand queries. The feature isn't intended to allow you to use Inventory Visibility to manage warehouse processing activities in general. Specifically, the following WHS features aren't supported by Inventory Visibility:

- Warehouse work
- Loads
- Waves
- Transportation management <!--KFM: Are you referring to the Transportation management module? That isn't part of WHS anyway, is it? -->

<!--KFM: Can we combine the previous list with the following list? They seem similar and repetitive, especially the last point below. -->

Inventory Visibility does not expose warehouse-specific concepts to its users. Such concepts include:

- Reservation hierarchy
- Whether an item or warehouse is WHS-enabled
- Unit sequence group ID
- Warehouse specific processes, such as shipments, loads, waves, and work.

Inventory Visibility infers such information based on the data sent from Supply Chain Management. The WHS-specific data (in other words, data from the `WHSInventReserve` table) is not visible to users.

When you use the Advanced WHS feature for Inventory Visibility, all query results will be identical to those from queries made directly in Supply Chain Management, but not the same as warehouse mobile apps. <!--KFM: How are they different, and why? Which mobile app do you mean? (*Warehouse Management mobile app* or the *Finance and Operations (Dynamics 365) mobile app*, or some other app? Why do we mention this?) -->

## When to use this feature

We recommend the Advanced WHS feature for Inventory Visibility in scenarios where all of the following are true:

- You are syncing Supply Chain Management data with Inventory Visibility.
- You are using WHS in Supply Chain Management.
- Users make reservations for WHS items at levels other than warehouses (for example, because you are using warehouse work).

In other scenarios, on-hand query results will be the same regardless of whether or not the Advanced WHS feature enabled in Inventory Visibility, and you will get better performance (due to reduced calculations and overhead) if you don't enable it.

## Enable the Advanced WHS feature for Inventory Visibility

To enable the Advanced WHS feature for Inventory Visibility, follow these steps.

1. Sign in to Supply Chain Management as an admin.
1. Go to the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace and enable the following features in the following order:
    1. *Inventory Visibility integration*
    1. *Enable warehouse items in Inventory Visibility*
1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**.
1. Open the **Enable WHS Items** tab and set **Enable WHS Items** to *Yes*.
1. Sign in to Power Apps.
1. Open the **Configuration** page in Power Apps, and then, on the **Feature Management** tab, turn on the *Advanced* feature. <!--KFM: Is this really the name of the feature? Should it maybe be "AdvancedWHS"? -->
1. Go back to Supply Chain Management.
1. Go to **Inventory Management \> Periodic Tasks \> Inventory Visibility integration**.
1. On the Action Pane, select **Disable** to temporarily disable Inventory Visibility.
1. On the Action Pane, select **Enable** to reenable Inventory Visibility together, which now loads with the new feature enabled. Your WHS-related data now starts to sync to Inventory Visibility.

## Query on-hand quantities of WHS items

You query for WHS items using the same [API and message syntax](inventory-visibility-api.md) that you use for non-WHS items. You don't need to specify whether an item is WHS, or non-WHS. Inventory Visibility automatically distinguishes them based on the data stored.

The results of querying a WHS item are essentially the same as those from querying a non-WHS item. The only difference is that the following physical measures from the `fno` data source are calculated based on WHS logics in Supply Chain Management:

- `AvailOrdered`
- `AvailPhysical`
- `ReservOrdered`
- `ReservPhysical`

The rest of the physical measures are the same as when the Advanced WHS feature is disabled in Inventory Visibility.

For a detailed explanation of how on-hand calculations for WHS items work, see the [Reservations in Warehouse management](https://www.microsoft.com/download/details.aspx?id=43284) white paper

The on-hand most specific background service <!-- KFM: What service is this? Is that the right name? We don't mention this anywhere else. --> isn't yet able to update the quantities for WHS items. The on-hand most specific results <!-- KFM: What do we mean by "on-hand most specific"? It might be the right term, but we don't use it anywhere else. --> are correct both for non-WHS items and for those quantities not affected by WHS logic (that is, measures excluding `AvailPhysical`, `AvailOrdered`, `ReservPhysical` and `ReservOrdered` in the `fno` data source).

Changing WHS-item quantities related to <!--KFM: is "related to" really the right word here? Do we mean "stored in"? --> Supply Chain Management is prohibited. As with other features of Inventory Visibility, changing data related to <!--KFM: is "related to" really the right word here? Do we mean "stored in"? --> Supply Chain Management isn't allowed to avoid conflicts.

## Soft reservations on WHS items in Inventory Visibility

[Soft reservations](inventory-visibility-reservations.md) on WHS items are generally supported. You can include WHS-related physical measures in soft reservation calculations. 

There is a known limitation that the *available for reservation* calculation is not currently supported for WHS items. As a result, when there is reservation above the current dimensions where a soft reservation is taking place, the *available for reservation* calculation is incorrect. Soft reservations won't be affected when the  **Check available for reservation** option is disabled. <!--KFM: Where is this option? It appears to be undocumented. What does this option do? What do we mean by "won't be affected..."? -->

This also applies to features and customizations based on soft reservations (such as allocation). <!--KFM: What are we referring to by "this"? -->

## Calculate available to promise quantities

The solution fully supports [available to promise (ATP)](inventory-visibility-available-to-promise.md) for WHS items. You can define ATP calculations without worrying about WHS-specific details.
