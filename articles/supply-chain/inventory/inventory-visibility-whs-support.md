---
title: Inventory Visibility support for WMS items
description: Learn about Inventory Visibility support for items that are enabled for warehouse management processes (WMS items) with an outline on the scope of the feature.
author: Weijiesa
ms.author: weijiesa
ms.topic: article
ms.date: 11/04/2022
ms.reviewer: kamaybac
ms.search.form:
---

# Inventory Visibility support for WMS items

[!include [banner](../includes/banner.md)]

This article describes Inventory Visibility support for items that are enabled for warehouse management processes (WMS). The feature that adds this capability to Inventory Visibility is named *Advanced WMS*.

## WMS items

A WMS item is an item that's enabled for WMS and processed at a warehouse that's also WMS enabled.

For more information about WMS and the **Warehouse management** module in Microsoft Dynamics 365 Supply Chain Management, see [Warehouse management overview](../warehousing/warehouse-management-overview.md).

## Scope of the feature

The Advanced WMS feature for Inventory Visibility focuses on on-hand quantity calculations that are based on on-hand queries. The feature isn't intended to let you use Inventory Visibility to manage warehouse processing activities in general. Inventory Visibility doesn't expose warehouse-specific concepts to its users. Here are some examples of these concepts:

- Reservation hierarchy
- Whether an item or warehouse is WMS enabled
- Unit sequence group ID
- Warehouse-specific processes, such as shipments, loads, waves, and work

Inventory Visibility infers this information, based on the data that's sent from Supply Chain Management. The WMS-specific data (in other words, data from the `WHSInventReserve` table) isn't visible to users.

When you use the Advanced WMS feature for Inventory Visibility, all query results will be identical to the results from queries that are made directly in Supply Chain Management. However, they won't be identical to the results from queries that are made by using the Warehouse Management mobile app, because the mobile app uses slightly different calculation logic.

## When to use the feature

We recommend that you use the WMS feature for Inventory Visibility in scenarios where all the following conditions are met:

- You're syncing Supply Chain Management data with Inventory Visibility.
- You're using WMS in Supply Chain Management.
- Users make reservations for WMS items at levels below the warehouse level (for example, at the license plate level because you're processing warehouse work).

In other scenarios, on-hand query results will be the same, regardless of whether the Advanced WMS feature for Inventory Visibility is enabled. Additionally, performance will be better if you don't enable the feature in these scenarios, because there are fewer calculations and less overhead.

## <a name="enable-the-WMS-feature"></a>Enable the WMS feature for Inventory Visibility

To enable the WMS feature for Inventory Visibility, follow these steps.

1. Sign in to Supply Chain Management as an admin.
1. Open the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, and enable the following features in this order:

    1. *Inventory Visibility integration*
    1. *Enable warehouse items in Inventory Visibility*

1. Go to **Inventory Management** \> **Setup** \> **Inventory Visibility integration parameters**.
1. On the **Enable WMS items** tab, set the **Enable WMS items sync** option to *Yes*. Then save the setup.
1. Select **Sync WMS data** to sync the WMS data to Inventory Visibility. This step is required because, when you first enable the synchronization of WMS items, only subsequent changes to on-hand quantities of WMS items will be synced to Inventory Visibility. When you select **Sync WMS data**, the system syncs all available WMS data to Inventory Visibility. This synchronization might take a long time, depending on your data volume. Therefore, we recommend that you complete this step during off-peak hours.

If you're using the new user interface for the Inventory Visibility app ([UI version 2](inventory-visibility-ui-version-2.md)), the WMS feature is turned on by default. Therefore, you're ready to [query on-hand quantities of WMS items](#query-wms-items). If you're using the old user interface ([UI version 1](inventory-visibility-ui-version-2.md)), you must turn on the *Advanced warehouse inventory* feature in the Inventory Visibility app in Power Apps before you can query for WMS items. Follow these steps to turn on the feature.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. On the navigation pane, select **Configuration**.
1. On the **Feature management & settings** tab, turn on the *Advanced warehouse inventory* feature.

## <a name="truncate"></a>Choose whether to truncate unused dimensions

This section applies when you're using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md). If you want to use the feature that's described here, but you're still using UI version 1, consider updating to UI version 2.

When you use the WMS feature, you can choose to truncate dimensions that you aren't using. The system can then accept queries that exclude specific dimensions. This functionality helps increase query performance and reduce the amount of storage that's required for the feature. Unused dimensions are truncated by default when you sync WMS data from Supply Chain Management, unless one or more of the following dimensions are included in your [index hierarchy](inventory-visibility-power-platform.md#index):

- Batch ID
- Serial ID
- License plate ID
- WMS Location ID

If you're using any of the preceding dimensions, but you haven't added them to your [index hierarchy](inventory-visibility-power-platform.md#index), you should disable the **Truncate unused dimensions** option by following these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Advanced warehouse inventory** tile, select **Manage**.
1. Set the **Truncate unused dimensions** option to *No*.
1. On the toolbar, select **Save & close**.
1. On the navigation pane, select **Admin settings**.
1. On the **Update configuration** tile, select **Manage**.
1. Review your modifications in the dialog box.

    > [!IMPORTANT]
    > Be sure to verify all the important modifications that are about to be made to your data sources, physical measures, and dimension mappings.

1. Select **Confirm Update** to apply your configuration changes.

> [!IMPORTANT]
> If you turn off the **Truncate unused dimensions** option after you've already synced some WMS item data from Supply Chain Management, you must [sync WMS data](#enable-the-WMS-feature) to ensure that all the previously truncated dimension data is re-synced to Inventory Visibility.

## <a name="query-wms-items"></a>Query on-hand quantities of WMS items

To query for WMS items, you use the same [application programming interface (API) and message syntax](inventory-visibility-api.md) that you use for non-WMS items. You don't have to specify whether an item is a WMS item or a non-WMS item. Inventory Visibility automatically distinguishes items, based on the data that's stored.

The results from queries for WMS items are essentially the same as the results for non-WMS items. The only difference is that the following physical measures from the `fno` data source are calculated based on WMS logic in Supply Chain Management:

- `AvailOrdered`
- `AvailPhysical`
- `ReservOrdered`
- `ReservPhysical`

All other physical measures are calculated just as they are when the WMS feature for Inventory Visibility is disabled.

For detailed information about how on-hand calculations for WMS items work, see the [Reservations in Warehouse management](https://www.microsoft.com/download/details.aspx?id=43284) white paper.

## On-hand list view and data entity for WMS items

The **Preload the Inventory Visibility Summary** page provides a view for the *On-hand Index Query Preload Results* entity. Unlike the *Inventory summary* entity, the *On-hand Index Query Preload Results* entity provides an on-hand inventory list for products together with selected dimensions. Inventory Visibility syncs the preloaded summary data every 15 minutes.

If you use Inventory Visibility with WMS items and want to view the on-hand list for WMS items, we recommend that you enable the *Preload the Inventory Visibility Summary* feature. (Learn more in [Preload a streamlined on-hand query](inventory-visibility-preload-on-hand.md).) A corresponding data entity in Dataverse stores your preloaded query result, which is updated every 15 minutes. The name of the data entity is *Onhand Index Query Preload Result*.

> [!IMPORTANT]
> The Dataverse entity is read-only. You can view and export the data in the Inventory Visibility entities, but **don't modify it**.

Changes to WMS item quantities that are stored in the Supply Chain Management data source (`fno`) are prohibited. This behavior matches the behavior of other features of Inventory Visibility. This restriction is enforced to help prevent conflicts.

## WMS item compatibility for other functions in Inventory Visibility

[Soft reservations](inventory-visibility-reservations.md) and [inventory allocation](inventory-visibility-allocation.md) of WMS items are supported. You can include WMS-related physical measures in soft reservation and allocation calculations.

## Calculate available-to-promise quantities

The solution fully supports [available to promise (ATP)](inventory-visibility-available-to-promise.md) for WMS items. You can define ATP calculations without worrying about WMS-specific details.
