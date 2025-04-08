---
title: Use the Inventory Visibility app UI version 1
description: Learn how to use the Inventory Visibility app when UI version 1 is active with a step-by-step process for authenticating with the Inventory Visibility service.
author: yufei-huang
ms.author: yufeihuang
ms.topic: article
ms.date: 09/15/2022
ms.reviewer: kamaybac
ms.search.form:
---

# Use the Inventory Visibility app UI version 1

[!include [banner](../includes/banner.md)]

This article describes how to use the Inventory Visibility app, which runs in Microsoft Power Apps.

The Inventory Visibility app offers two versions of a model-driven user experience for visualization. Users can now choose between the new user interface (referred to as *UI version 2* in this article) and the old (legacy) user interface (referred to as *UI version 1* in this article).

This article describes how to work with UI version 1. For information about how to work with UI version 2, see [Use the Inventory Visibility app UI version 2](inventory-visibility-power-platform.md).

## Prerequisites

Before you can use UI version 1 to work with the Inventory Visibility app, the following prerequisites must be in place:

- [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- [Turn on Inventory Visibility UI version 1](inventory-visibility-ui-version-2.md).

## Authenticate with the Inventory Visibility service

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. On the navigation pane, select **Operational Visibility**.
1. Select **Settings** at the top of the page.
1. In the dialog box, enter the **Client ID**, **Tenant ID**, and **Client secret** values. You should have found these values when you [installed the Inventory Visibility Add-in](inventory-visibility-setup.md#install-add-in).
1. Select the **Refresh** button on the right side of the **Bearer Token** field. The system generates a new bearer token for your sessions. This token expires after one hour.

## <a name="ui-version"></a>Switch between user interface versions

Regardless of which version of the user interface is active, you can switch to the other version at any time. However, only the settings that you apply in the active version of the UI have any effect. To switch between the two versions, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select one of the following options:

    - **Inventory Visibility** – The navigation pane shows the pages for UI version 2.
    - **Legacy UI** – The navigation pane shows the pages for UI version 1.

## Find your service endpoint and read the configuration

The Inventory Visibility service is deployed on Azure Service Fabric in multiple geographies and multiple regions. Currently, there's no central endpoint to automatically redirect your requests to the appropriate geography and region. Therefore, the service endpoint uses the following pattern, which includes the required information:

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

To obtain your service endpoint and runtime configuration, follow these steps.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Select **Show Service Details** in the upper-right corner.
1. In the dialog box, you can find your service endpoint and configuration details.

## <a name="update-configuration"></a>Update the configuration

Any time that you modify the configuration and save your changes, the system saves the new configuration settings only temporarily. The changes don't take effect until you commit the new settings to the service. Follow these steps to commit new configuration settings to the service.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. On the navigation pane, select **Configuration**.
1. Select **Update Configuration** in the upper-right corner.
1. In the dialog box, set the **Client ID**, **Tenant ID**, and **Client secret** fields. You should have found the values for these fields when you [installed the Inventory Visibility Add-in](inventory-visibility-setup.md#install-add-in).
1. Select **Login**.
1. Review your modifications in the dialog box.

    > [!IMPORTANT]
    > Be sure to verify all the important modifications that are about to be made to your data sources, physical measures, and dimension mappings.

1. Select **Confirm Update** to apply your configuration changes.

## Partition configuration

<!--KFM: Why is this section here? What does this have to do with the app? -->

Partition configuration controls how data is distributed. Operations that are performed inside the same partition provide better performance, at lower cost, than operations that cross partitions. The following partition configuration is included in the solution by default. Therefore, *you don't have to set it up yourself*.

| Base dimension | Hierarchy |
|---|---|
| *SiteId* | 1 |
| *LocationId* | 2 |

> [!IMPORTANT]
> Don't customize the partition configuration. If you delete or change the configuration without official guidance, you're likely to encounter an unexpected error.

## Set up the on-hand index configuration

The on-hand index configuration has the same purpose and functionality, regardless of which version of the user interface is active. For an overview of the on-hand index configuration and examples that show how it works, see [On-hand index configuration](inventory-visibility-power-platform.md#index). This section describes only how to find the on-hand index configuration settings in UI version 1.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. On the **Product Index Hierarchy** tab, add sets and dimensions as you require. Add dimensions in order, according to the hierarchy that you want to create. For information about what the settings mean and how they work, including some examples, see [On-hand index configuration](inventory-visibility-power-platform.md#index). Set and dimensions numbers are automatically generated as you make modifications.
1. [Update the configuration](#update-configuration) to apply your changes.

## <a name="feature-management"></a>Feature management

The following table shows the features that Inventory Visibility offers. Each of these features can be turned on or off for your environment.

| Feature name | Description |
|---|---|
| [Available to promise](inventory-visibility-available-to-promise.md) | Track your available to promise (ATP) across all data sources and channels. |
| [Inventory allocation](inventory-visibility-allocation.md) | Allocate your valuable on-hand stock to your most important channels, customers, or predefined groups, and track the consumption of each allocated pool. |
| [Advanced warehouse inventory](inventory-visibility-whs-support.md) | Sync and view advanced warehouse item inventory by using warehouse hierarchies. |
| [Soft reservation](inventory-visibility-reservations.md) | Post your omnichannel reservations to Inventory Visibility soft reservations for real-time inventory availability checks and updates. |
| [Inventory log history](inventory-visibility-track-inventory-log-history.md) | Enable Inventory Visibility to store your successful transaction logs. You can query the log history for details about the organization, product, date range, site, and warehouse. |
| [Inventory summary](inventory-visibility-inventory-summary.md) | Periodically sync your raw inventory summary from the cache to Dataverse. This feature isn't compatible with advanced warehouse items. Enable either this feature or the *Preloaded on-hand* feature. Don't enable both features. |
| [Preload on-hand](inventory-visibility-preload-on-hand.md) | Periodically preload the inventory summary to Dataverse from a query result. The query result can be configured with the dimensions that are most relevant to your business. This feature is compatible with advanced warehouse items. Enable either this feature or the *Inventory summary* feature. Don't enable both features. |

By default, all these features are disabled. To turn a feature on or off, and to make related configuration settings, follow these steps.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Find the tile for the feature that you want to turn on or off, and then select **Manage**.
1. On the **Feature management & settings** tab, use the option for each feature that's listed to turn it on or off. More fields might be added to the page when some features are turned on. For more information, see the documentation for the feature that you're setting up.
1. [Update the configuration](#update-configuration) to commit your changes so that they take effect.

## Delete all configurations

If necessary, you can delete all configurations except those in the *fno* and *@iv* Inventory Visibility data sources. Deleted configurations can't be restored.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Select the **More** menu (three dots) in the upper-right corner, and then select **Delete all configurations**.

## Delete all inventory data

If necessary, you can delete all Inventory Visibility data, except configurations, in both the cache and Dataverse. Deleted data can't be restored, and users are blocked until deletion is completed.

1. On the [UI version 1](#ui-version) navigation pane, select **Configuration**.
1. Select the **More** menu (three dots) in the upper-right corner, and then select **Delete all inventory data**.

## Inventory queries and updates

The **Operational visibility** page provides tabs where you can perform real-time on-hand inventory queries and updates. When the [soft reservation](inventory-visibility-reservations.md) or [inventory allocation](inventory-visibility-allocation.md) feature is [turned on](#feature-management), you can also post reservation or allocation requests. For more information about API requests, see [Inventory Visibility public APIs](inventory-visibility-api.md).

The following subsections provide details about how to set up and use each tab.

### On-hand query

Use the **Onhand query** tab of the **Operational visibility** page to query real-time on-hand inventory. Follow these steps to set up and run a query.

1. On the [UI version 1](#ui-version) navigation pane, select **Operational visibility**.
1. On the **Onhand query** tab, enter the **Organization ID**, **Site ID**, and **Location ID** values of the products that you want to find.
1. In the **Product ID** field, enter one or more product IDs to get an exact match for your query. Alternatively, leave the field blank to include all products in the specified organization, site, and location.
1. To get a more granular result (for example, a view that's grouped by dimensions such as color and size), select the dimensions to group by in the **Group result by** field.
1. To filter items that have a specific dimension value (for example, color = red), select the dimension in the **Filter dimensions** field, and then enter the value.
1. To include ATP information, select the **Query ATP** checkbox.
1. Select **Query** to send the request.

### Reservation posting

Use the **Reservation posting** tab of the **Operational visibility** page to make soft reservations of inventory.

> [!IMPORTANT]
> The capability to make soft reservations through the user interface should be used only to test the feature. Every soft reservation request should be associated with a transaction order line change (create, modify, delete, and so on). Therefore, we recommend that you make only soft reservations that are linked to back-end orders. Learn more in [Inventory Visibility soft reservations](inventory-visibility-reservations.md).

Follow these steps to set up and submit a soft reservation.

1. On the [UI version 1](#ui-version) navigation pane, select **Operational visibility**.
1. On the **Reservation posting** tab, in the **Quantity** field, enter the quantity that you want to soft reserve.
1. Select the **Enable negative inventory to support oversell** checkbox to skip the available-for-reservation check, or clear it to enforce the check.
1. In the **Operator** field, select the data source and physical measure to make the soft reservation on.
1. Enter the **Organization ID**, **Site ID**, **Location ID**, and **Product ID** values that you want to soft reserve.
1. In the **Dimension** field, select a data source. Then add dimensions from that data source, and enter values for each of the selected dimensions.
1. Select **Post** to send the request.
1. Select **Show details** to view a detailed response, including the `reservationId` value.

### Inventory allocation

The inventory allocation feature lets sales planners or key account managers manage and preallocate important stock across allocation groups (such as channels, regions, and customer groups). It also supports real-time tracking, adjustment, and analytics of consumption against allocated quantities, to ensure that replenishment or reallocation can be done on time. The ability to have real-time visibility into allocation, consumption, and allocation balance is especially important at fast-sale or promotion events.

For more information about inventory allocation, including information about how to work with it in the Inventory Visibility app, see [Inventory Visibility inventory allocation](inventory-visibility-allocation.md)

## Search for products in the Inventory Visibility app

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes, such as size and color. For information about how to set up this feature, see [Set up product search for Inventory Visibility](inventory-visibility-product-search.md). For information about how to use it in the Inventory Visibility app, see [Search for products using the Inventory Visibility app](inventory-visibility-product-search-app.md). <!--KFM: Does this work when UIv1 is active? -->
