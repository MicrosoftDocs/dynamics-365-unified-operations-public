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

This topic describes Inventory Visibility support for items that are enabled for advanced warehouse processes (WHS items). The feature that adds this capability to Inventory Visibility is named *Advanced WHS*.

## WHS items

A WHS item is an item that is enabled for advanced warehouse processes (WHS) and processed at a warehouse that is also WHS enabled.

For more information about WHS and the **Warehouse management** module in Microsoft Dynamics 365 Supply Chain Management, see [Warehouse management overview](../warehousing/warehouse-management-overview.md).

## Scope of the feature

The Advanced WHS feature for Inventory Visibility focuses on on-hand quantity calculations that are based on on-hand queries. The feature isn't intended to let you use Inventory Visibility to manage warehouse processing activities in general. Inventory Visibility doesn't expose warehouse-specific concepts to its users. Here are some examples of these concepts:

- Reservation hierarchy
- Whether an item or warehouse is WHS enabled
- Unit sequence group ID
- Warehouse-specific processes, such as shipments, loads, waves, and work

Inventory Visibility infers this information, based on the data that is sent from Supply Chain Management. The WHS-specific data (in other words, data from the `WHSInventReserve` table) isn't visible to users.

When you use the Advanced WHS feature for Inventory Visibility, all query results will be identical to the results from queries that are made directly in Supply Chain Management. However, they won't be identical to the results from queries that are made by using the Warehouse Management mobile app, because the mobile app uses slightly different calculation logic.

## When to use the feature

We recommend that you use the Advanced WHS feature for Inventory Visibility in scenarios where all the following conditions are met:

- You're syncing Supply Chain Management data with Inventory Visibility.
- You're using WHS in Supply Chain Management.
- Users make reservations for WHS items at levels other than the warehouse level (for example, because you're using warehouse work).

In other scenarios, on-hand query results will be the same, regardless of whether the Advanced WHS feature for Inventory Visibility is enabled. Additionally, performance will be better if you don't enable the feature in these scenarios, because there are fewer calculations and less overhead.

## Enable the Advanced WHS feature for Inventory Visibility

To enable the Advanced WHS feature for Inventory Visibility, follow these steps.

1. Sign in to Supply Chain Management as an admin.
1. Open the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, and enable the following features in this order:

    1. *Inventory Visibility integration*
    1. *Enable warehouse items in Inventory Visibility*

1. Go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**.
1. On the **Enable WHS Items** tab, set the **Enable WHS Items** option to *Yes*.
1. Sign in to Power Apps.
1. Open the **Configuration** page, and then, on the **Feature Management** tab, turn on the *AdvancedWHS* feature.
1. In Supply Chain Management, go to **Inventory Management \> Periodic Tasks \> Inventory Visibility integration**.
1. On the Action Pane, select **Disable** to temporarily disable Inventory Visibility.
1. On the Action Pane, select **Enable** to reenable Inventory Visibility. The add-in is reloaded, and the new feature is now enabled. Your WHS-related data starts to be synced to Inventory Visibility.

## Query on-hand quantities of WHS items

To query for WHS items, you use the same [application programming interface (API) and message syntax](inventory-visibility-api.md) that you use for non-WHS items. You don't have to specify whether an item is a WHS item or a non-WHS item. Inventory Visibility automatically distinguishes items, based on the data that is stored.

The results from queries for WHS items are essentially the same as the results for non-WHS items. The only difference is that the following physical measures from the `fno` data source are calculated based on WHS logic in Supply Chain Management:

- `AvailOrdered`
- `AvailPhysical`
- `ReservOrdered`
- `ReservPhysical`

All other physical measures are calculated just as they are when the Advanced WHS feature for Inventory Visibility is disabled.

For detailed information about how on-hand calculations for WHS items work, see the [Reservations in Warehouse management](https://www.microsoft.com/download/details.aspx?id=43284) white paper.

The data entities that are exported to Dataverse can't yet update the quantities for WHS items. The quantities that are shown in the data entities are correct both for non-WHS items and for quantities that aren't affected by WHS logic (that is, measures except `AvailPhysical`, `AvailOrdered`, `ReservPhysical`, and `ReservOrdered` in the `fno` data source).

Changes to WHS item quantities that are stored in the Supply Chain Management data source are prohibited. As for other features of Inventory Visibility, this restriction is enforced to help prevent conflicts.

## Soft reservations on WHS items in Inventory Visibility

In general, [soft reservations](inventory-visibility-reservations.md) on WHS items are supported. You can include WHS-related physical measures in soft reservation calculations. 

In a known limitation, the *available for reservation* calculation isn't currently supported for WHS items. Therefore, if there is reservation above the current dimensions where a soft reservation is occurring, the *available for reservation* calculation is incorrect. Soft reservations won't be affected when the **ifCheckAvailForReserv** option is disabled in the [soft reservation API](inventory-visibility-api.md#create-one-reservation-event).

This constraint also applies to features and customizations that are based on soft reservations (such as allocation).

## Calculate available-to-promise quantities

The solution fully supports [available to promise (ATP)](inventory-visibility-available-to-promise.md) for WHS items. You can define ATP calculations without worrying about WHS-specific details.
