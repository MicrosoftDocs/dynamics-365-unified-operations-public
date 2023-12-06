---
title: Use the Inventory Visibility app UI version 1
description: This article describes how to use the Inventory Visibility app when UI version 1 is active.
author: yufeihuang
ms.date: 09/15/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# Use the Inventory Visibility app UI version 1

[!include [banner](../includes/banner.md)]

This article describes how to use the Inventory Visibility app, which runs in Microsoft Power Apps.

The Inventory Visibility app offers two versions of model-driven user experiences for visualization. Users now have the option to choose between the new version UI (referred to as *UI version 2* in this article) and the legacy UI (also referred to as *UI version 1* in this article).

This article describes how to work with UI version 1. For information about how to work with UI version 2, see [Use the Inventory Visibility app UI version 2](inventory-visibility-power-platform-v2.md).

## Prerequisites

To work with the Inventory Visibility app using UI version 1, the following prerequisites must be in place:

- You must [install and set up Inventory Visibility](inventory-visibility-setup.md).
- You must [turn on Inventory Visibility UI version 1](inventory-visibility-ui-version-2).

## Authenticate with the Inventory Visibility service

1. Sign in to your Power Apps environment.
1. Open the **Inventory Visibility** app.
1. At the bottom of the navigation pane, open the **Change area** menu and select *Legacy UI*.
1. On the navigation pane, select **Operational Visibility**.
1. Select **Settings** at the top of the page. <!--KFM: Seems unnecessary. For me, the settings opened when I came to Operational Visibility. -->
1. Enter the **Client ID**, **Tenant ID**, and **Client secret** in the dialog box. You should have found these values when you [installed the Inventory Visibility Add-in](inventory-visibility-setup.md#install-the-inventory-visibility-add-in).
1. Select the **Refresh** button on the right side of the **Bearer Token** field. The system generates a new bearer token for your sessions, which expires after one hour.

## <a name="ui-version"></a>Navigate between user interface versions

Regardless of which user interface version is active, you can navigate between the two versions at any time. However, only the settings you make to the active version of the UI will have any affect. To switch between the two versions, follow these steps:

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. At the bottom of the navigation pane, open the **Change area** menu and select one of the following entries:
    - **Inventory Visibility** – The navigation pane displays the pages for UI version 2.
    - **Legacy UI** – The navigation pane displays the pages for UI version 1.

## Find your service endpoint and read the configuration

The Inventory Visibility service is deployed on Microsoft Azure Service Fabric in multiple geographies and multiple regions. Currently, there is no central endpoint to automatically redirect your requests to the appropriate geography and region. Therefore, the service endpoint uses the following pattern, which includes the necessary information:

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

To obtain your service endpoint and runtime configuration, follow these steps:

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Select **Show Service Details** in the upper-right corner.
1. A dialog opens where you can find your service endpoint and configuration details.

## <a name="update-configuration"></a>Update the configuration

Any time you modify the configuration and save your settings, the system only saves the settings temporarily until you are ready to commit them to the system so they can take effect. Follow these steps to commit new configuration settings to the service:

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. On the navigation pane, select **Configuration**.
1. Select **Update Configuration** in the upper-right corner.
1. Enter the **Client ID**, **Tenant ID**, and **Client secret** in the dialog box. These values were established when [the Inventory Visibility Add-in was installed](inventory-visibility-setup.md#install-the-inventory-visibility-add-in).
1. Select **Login**.
1. Check your modifications in the dialog box.

    > [!IMPORTANT]
    > Be sure to verify all of the important modifications that are about to be made to your data sources, physical measures, and dimension mappings.

1. Select **Confirm Update** to apply your configuration change.

## Partition configuration

<!--KFM: Why is this section here? What does this have to do with the app? -->

Partition configuration controls how data is distributed. Operations inside the same partition will deliver better performance at lower cost, comparing to those cross multiple partitions. Below is the default partition configuration included in solution, so *you don't need to set it up yourself*.

| Base dimension | Hierarchy |
|---|---|
| *SiteId* | 1 |
| *LocationId* | 2 |

> [!IMPORTANT]
> Don't customize your partition configuration. If you delete or change it without official guide, you are likely to encounter an unexpected error.

## Set up the on-hand index configuration

Regardless of which user interface version is active, the purpose and functionally of on-hand index configuration is the same. For an overview and examples about how on-hand index configuration works, see [On-hand index configuration](inventory-visibility-power-platform.md#index). This section just describes how to find the on-hand index configuration settings in UI version 1.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Open the **Product Index Hierarchy** tab.
1. Add sets and dimensions as needed. Add dimensions in order according to the hierarchy you want to create. For details about what these settings mean and how they work, including some examples, see [On-hand index configuration](inventory-visibility-power-platform.md#index). Set and dimensions numbers are generated automatically as you make modifications.
1. [Update the configuration](#update-configuration) to apply your changes.

## <a name="feature-management"></a>Feature management

Inventory Visibility offers the features listed in the following table, each of which can be turned on or off for your environment.

| Feature name | Description |
|---|---|
| [Available to promise](inventory-visibility-available-to-promise.md) | Track your available to promise (ATP) across all data sources and channels. |
| [Inventory allocation](inventory-visibility-allocation.md) | Allocate your valuable on-hand stock to your most important channels, customers, or pre-defined groups and track consumption of each allocated pool. |
| [Advanced warehouse inventory](inventory-visibility-whs-support.md) | Sync and view advanced warehouse item inventory with warehouse hierarchies. |
| [Soft reservation](inventory-visibility-reservations.md) | Post your omnichannel reservations to Inventory Visibility soft reservations for real-time inventory availability checks and updates. |
| [Inventory log history](inventory-visibility-track-inventory-log-history.md) | Allow Inventory Visibility to store your successful transaction logs. You can query your log history with details on organization, product, date range, site and warehouse. |
| [Inventory summary](inventory-visibility-inventory-summary.md) | Periodically sync your raw inventory summary from cache to dataverse. This feature is not compatible with advanced warehouse items. Either enable this feature or the *Preloaded on-hand* feature, do not enable both. |
| [Preload on-hand](inventory-visibility-preload-on-hand.md) | Periodically preload the inventory summary to Dataverse from a query result that is configurable with dimensions that are most relevant to your business. This feature is compatible with advanced warehouse items. Either enable this feature or *Inventory summary* feature, do not enable both. |

By default, all of these features are disabled. To turn a feature on or off, and make related configuration settings, follow these steps:

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Find the tile named after the feature you want to turn on or off, and then select **Manage**.
1. Open the **Feature management & settings** tab.
1. Use the **Toggle switch** for each each listed feature to turn it on or off. Additional settings may be added to the page when some features are turned on. For more information, see the documentation for the feature you are setting up.
1. [Update the configuration](#update-configuration) to commit your changes so they will take effect.

## Delete all configurations

If necessary, you can delete all configurations except for those contained in Inventory Visibility data sources *fno* and *@iv*. Deleted configurations can't be restored.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Open the **More** menu (three dots icon) in the upper-right corner and select **Delete all configurations**.

## Delete all inventory data

If necessary, you can delete all Inventory Visibility data in both the cache and in Dataverse except for configurations. Deleted data can't be restored and users will be blocked until deletion completes.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Open the **More** menu (three dots icon) in the upper-right corner and select **Delete all inventory data**.

## Inventory queries and updates

The **Operational Visibility** page provides tabs for making real-time on-hand inventory queries and updates. When the [soft reservation](inventory-visibility-reservations.md) or [inventory allocation](inventory-visibility-allocation.md) feature is [turned on](#feature-management), reservation or allocation requests can also be posted. For more details about API requests, see [Inventory Visibility public APIs](inventory-visibility-api.md).

Details about how to set up and use each tab are provided in the following subsections.

### On-hand query

Use the **Onhand query** tab of the **Operational visibility** page to query real-time on-hand inventory. Follow these steps to set up and run a query.

1. On the [UI version 1](#ui-version) navigation pane, select **Operational visibility** and open the **Onhand query** tab.
1. Enter the **Organization ID**, **Site ID**, and **Location ID** for the products you want to look for.
1. In the **Product ID** field, enter one or more product IDs to get an exact match for your query, or leave it blank to include all products at the specified organization, site, and location.
1. To get a more granular result (for example, a view grouped by dimensions like color and size), select dimensions to group by in the **Group result by** field.
1. To filter items with a specific dimension value (such as color = red), select the dimension in hte **Filter dimensions** field and then enter the value.
1. If you want to include available-to-promise (ATP) information, select the **Query ATP** check box.
1. Select **Query** to send the request.

### Reservation posting

Use the **Reservation posting** tab of the **Operational visibility** page to make soft reservations of inventory.

> [!IMPORTANT]
> The ability to make soft reservations through the user interface should only be used to test the feature. Each soft reservation request should be associated with a transaction order line change (create, modify, delete, and so on). Therefore, we recommend that you only make soft reservations that are linked to back-end orders. For more information, see [Inventory Visibility soft reservations](inventory-visibility-reservations.md).

Follow these steps to set up and submit a soft reservation.

1. On the [UI version 1](#ui-version) navigation pane, select **Operational visibility** and open the **Reservation posting** tab.
1. In the **Quantity** field, enter the quantity that you want to soft reserve.
1. Select the **Enable negative inventory to support oversell** check box to skip the available-for-reservation check, or unselect it to enforce the check.
1. In the **Operator** field, select the data source and physical measure to make the soft reservation on.
1. Enter the **Organization ID**, **Site ID**, **Location ID**, and **Product ID** values that you want to soft reserve.
1. In **Dimension** field, select a data source and then add dimensions from that data source and enter values for each dimension you select.
1. Select **Post** to send the request.
1. Select **Show details** to see a detailed response, including the `reservationId` value.

### Inventory allocation

The inventory allocation feature lets sales planners or key account managers manage and preallocate important stock across allocation groups (such as channels, regions, and customer groups). It also supports real-time tracking, adjustment, and analytics of consumption against allocated quantities, to ensure that replenishment or reallocation can be done on time. This ability to have real-time visibility into allocation, consumption, and allocation balance is especially important at fast-sale or promotion events.

For more information about inventory allocation, including how to work with it in the Inventory Visibility app, see [Inventory Visibility inventory allocation](inventory-visibility-allocation.md)

## Search for products in the Inventory Visibility app

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes, such as size and color. For details about how to set up this feature, see [Set up product search for Inventory Visibility](inventory-visibility-product-search.md). For details about how to use it in the Inventory Visibility app, see [Search for products using the Inventory Visibility app](inventory-visibility-product-search-app.md). <!--KFM: Does this work when UIv1 is active? -->
