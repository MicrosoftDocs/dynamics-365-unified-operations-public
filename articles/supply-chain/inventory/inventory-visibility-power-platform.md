---
title: Use the Inventory Visibility app UI version 2
description: Learn how to use the Inventory Visibility app UI version 2, including an process for authenticating with the Inventory Visibility service.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 12/04/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Use the Inventory Visibility app UI version 2

[!include [banner](../includes/banner.md)]

This article describes how to use the Inventory Visibility app, which runs in Microsoft Power Apps.

The Inventory Visibility app offers two versions of a model-driven user experience for visualization. Users can now choose between the new user interface (referred to as *UI version 2* in this article) and the old (legacy) user interface (referred to as *UI version 1* in this article).

## Prerequisites

Before you can use UI version 2 to work with the Inventory Visibility app, the following prerequisites must be in place:

- [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- [Turn on Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md). 

## Authenticate with the Inventory Visibility service

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Admin settings**.
1. On the **Set tokens** tile, select **Manage**.
1. In the dialog box, enter the **Client ID**, **Tenant ID**, and **Client secret** values. These values were defined when [the Inventory Visibility Add-in was installed](inventory-visibility-setup.md#install-add-in).
1. Select **Login**. The system generates a new bearer token for your sessions. This token expires after one hour.

## <a name="ui-version"></a>Switch between user interface versions

Regardless of which version of the user interface is active, you can switch to the other version at any time. However, only the settings that you apply in the active version of the UI have any effect. To switch between the two versions, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select one of the following options:

    - **Inventory Visibility** – The navigation pane shows the pages for UI version 2.
    - **Legacy UI** – The navigation pane shows the pages for UI version 1.

## <a name="endpoint"></a>Find your service endpoint and read the configuration

The Inventory Visibility service is deployed on Azure Service Fabric in multiple geographies and multiple regions. Currently, there's no central endpoint to automatically redirect your requests to the appropriate geography and region. Therefore, the service endpoint uses the following pattern, which includes the required information:

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

To obtain your service endpoint and runtime configuration, follow these steps.

1. On the [UI version 2](#ui-version) navigation pane, select **Admin settings**.
1. On the **Show service details** tile, select **Manage**.
1. In the dialog box, you can find your service endpoint and configuration details.

## <a name="update-configuration"></a>Update the configuration

Any time that you modify the configuration and save your changes, the system saves the new configuration settings only temporarily. The changes don't take effect until you commit the new settings to the service. Follow these steps to commit new configuration settings to the service.

1. On the [UI version 2](#ui-version) navigation pane, select **Admin settings**.
1. On the **Update Configuration** tile, select **Manage**.
1. Review your modifications in the dialog box.

    > [!IMPORTANT]
    > Be sure to verify all the important modifications that are about to be made to your data sources, physical measures, and dimension mappings.

1. Select **Confirm Update** to apply your configuration change.

## <a name="data-partition"></a>Data partition rule

Inventory Visibility can distribute and store inventory data in either of the following ways:

- *By location* – Choose this option if you always know site and warehouse information when you make on-hand queries, inventory adjustments, inventory reservations or inventory allocations through Inventory Visibility.
- *By product ID* – Choose this option if you often don't know site or warehouse information when calling Inventory Visibility. For example, when making e-commerce in-basket reservations, the fulfillment warehouse might be unknown when online orders are initially placed. In this case, it's important to be able to call Inventory Visibility to query on-hand inventory and make reservations without providing warehouse information.

To change the data partition rule, follow these steps:

1. Open the Inventory Visibility app
1. Select **Data partition rule** and choose the rule you want to use.
1. [Clear all inventory data](#delete-data).
1. [Update the configuration](#update-configuration) to apply your changes. (The update-configuration operation will fail if you don't clear the data first.)

The data partition rule controls how data is distributed. Operations that are performed inside the same partition provide better performance, at lower cost, than operations that cross partitions. Therefore, we recommend using the *By product ID* option if you often query across different locations. However, we recommend using the *By location* option if you more often query for multiple products at the same location.

When using the *By location* partition rule, the rule in the following table is included in the solution by default and can't be changed (this becomes set 0 of the index hierarchy). When using *By product ID*, the rule has no effect on Inventory Visibility APIs.

| Base dimension | Hierarchy |
|---|---|
| *SiteId* | 1 |
| *LocationId* | 2 |

> [!IMPORTANT]
> Don't customize the partition configuration. If you delete or change the configuration without official guidance, you're likely to encounter an unexpected error.

## <a name="index"></a>On-hand index configuration

In many cases, on-hand inventory is queried not only at the most detailed level but also at some aggregated levels, based on the inventory dimensions.

For frequently used query patterns, you can help improve query performance by setting up *indexes*.

An index is composed of a *set number*, *dimensions*, and a *hierarchy*.

| Name | Description |
|---|---|
| Set number | Dimensions under the same set number belong to the same set (index) and are grouped together. |
| Dimensions | The dimensions are base dimensions that query results are aggregated on. |
| Hierarchy | <p>The hierarchy determines the specific combinations of dimensions that can take advantage of an index query. For example, you set up an index that has the following dimensions and hierarchy: *(ColorId, SizeId, StyleId)*. In this case, only queries that use the following four dimension combinations for their filter and group-by fields are enhanced:</p><ul><li><b>First combination:</b> Empty</li><li><b>Second combination:</b> <i>(ColorId)</i></li><li><b>Third combination:</b> <i>(ColorId, SizeId)</i></li><li><b>Fourth combination:</b> <i>(ColorId, SizeId, StyleId)</i></li></ul><p>(The filter field isn't order-restricted.)</p><p>The index doesn't speed up queries that use other dimension combinations.</p> |

The default on-hand index configuration includes a standard set of indexes.

> [!TIP]
> These tips can help when you set up your on-hand index configuration:
>
> - Base dimensions that are reserved in the partition configuration (set number *0*) should not be included in other on-hand index configurations.
> - If you aren't interested in querying specific dimension combinations, set up an index that has only one base dimension, *Empty*.

### Set up the on-hand index configuration

1. On the [UI version 2](#ui-version) navigation pane, select **Index Configuration**.
1. Add and remove lines in the grid as you require to define your index. For more information, see the introduction to this section and the [example](#index-configuration-example) in the next subsection.
1. [Update the configuration](#update-configuration) to apply your changes.

### <a name="index-configuration-example"></a>On-hand index configuration example

This section provides an example that shows how an on-hand index works.

The following table shows a list of available inventory.

| Item | ColorId | SizeId | StyleId | Quantity |
|---|---|---|---|---|
| D0002 | Black | Small | Wide | 1 |
| D0002 | Black | Small | Regular | 2 |
| D0002 | Black | Large | Wide | 3 |
| D0002 | Black | Large | Regular | 4 |
| D0002 | Red | Small | Wide | 5 |
| D0002 | Red | Small | Regular | 6 |
| D0002 | Red | Large | Regular | 7 |

The following table shows an on-hand index configuration.

| Set Number | Dimension | Hierarchy |
|---|---|---|
| 1 | *ColorId* | 1 |
| 1 | *SizeId* | 2 |
| 1 | *StyleId* | 3 |

This index helps improve the performance of the following on-hand inventory queries:

- *()* – Grouped by all

    - D0002, 28

- *(ColorId)* – Grouped by *ColorId*

    - D0002, Black, 10
    - D0002, Red, 18

- *(ColorId, SizeId)* – Grouped by the combination of *ColorId* and *SizeId*

    - D0002, Black, Small, 3
    - D0002, Black, Large, 7
    - D0002, Red, Small, 11
    - D0002, Red, Large, 7

- *(ColorId, SizeId, StyleId)* – Grouped by the combination of *ColorId*, *SizeId*, and *StyleId*

    - D0002, Black, Small, Wide, 1
    - D0002, Black, Small, Regular, 2
    - D0002, Black, Large, Wide, 3
    - D0002, Black, Large, Regular, 4
    - D0002, Red, Small, Wide, 5
    - D0002, Red, Small, Regular, 6
    - D0002, Red, Large, Regular, 7

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

1. On the [UI version 2](#ui-version) navigation pane, select **Feature management**.
1. Find the tile for the feature that you want to turn on or off, and then select **Manage**.
1. Turn on and set up the feature as you require. Each feature provides different settings. For more information, see the documentation for the feature that you're setting up.
1. [Update the configuration](#update-configuration) to commit your changes so that they take effect.

## Delete all configurations

If necessary, you can delete all configurations except those in the *fno* and *@iv* Inventory Visibility data sources. Deleted configurations can't be restored.

1. On the [UI version 2](#ui-version) navigation pane, select **Admin Settings**.
1. On the **Delete all configurations** tile, select **Manage**.
1. You're prompted to confirm the deletion. Select **OK** to continue.

## <a name="delete-data"></a> Delete all inventory data

If necessary, you can delete all Inventory Visibility data, except configurations, in both the cache and Dataverse. Deleted data can't be restored, and users are blocked until deletion is completed.

1. On the [UI version 2](#ui-version) navigation pane, select **Admin Settings**.
1. On the **Delete all inventory data** tile, select **Manage**.
1. You're prompted to confirm the deletion. Select **OK** to continue.

## Inventory queries and updates

On the navigation pane, the **Operational visibility** group provides access to pages where you can perform real-time on-hand inventory queries and updates. When the [soft reservation](inventory-visibility-reservations.md) feature is [enabled](#feature-management), you can also post reservation requests to the API. For more details about API requests, see [Inventory Visibility public APIs](inventory-visibility-api.md).

The following elements are common to all the pages:

- A **Post** or **Query** button on the toolbar lets you send API requests to the Inventory Visibility service. This button becomes available only after you enter all the content that's required for the API call on the page.
- A **Product** section lets you enter a product ID, an organization ID, and dimension values for the API request. Select the **Edit Dimensions** button in this section to choose which of the available dimensions to include in the request.
- A **Settings** section (the exact name varies) lets you enter API-specific settings, such as whether to query ATP contents for an on-hand query.
- A **Developer reference** button on the toolbar lets you view the raw contents of your API request (read-only).
- A **Settings** button on the toolbar lets you view and edit the authentication details that are used to access the Inventory Visibility service.

The following subsections provide details about how to set up and use each type of operation.

### On-hand query

Use the **On hand query** page in the **Operational visibility** group to query real-time on-hand inventory. Follow these steps to set up and run a query.

1. On the [UI version 2](#ui-version) navigation pane, select **On hand query**.
1. In the **Product** section, enter the **Organization ID**, **Site ID**, and **Location ID** values of the products that you want to find.
1. In the **Product ID** field, enter one or more product IDs to get an exact match for your query. Alternatively, leave the field blank to include all products at the specified site and location.
1. Select **Edit Dimensions** to choose which dimensions to include in the query body. Then enter values for the selected dimensions in the **Product** section.

    > [!NOTE]
    > If you plan to make an ATP query, ensure that every dimension that is included in the ATP index is also listed in the **Product** section. For example, if your ATP index includes `ColorId` and `SizeId`, both those dimensions must be listed in the **Product** section. If any dimensions are missing, select **Edit Dimensions** to add them. In the search form, you can leave some of the dimension values blank. However, the dimensions must be included in the query body if they are included in the ATP index.

1. For each field that you want to include in the query, but without filtering on any specific value, select **Use all values**.
1. In the **Query Settings** section, set the following options:

    - **Query ATP** – Select this checkbox to include ATP information.
    - **Include negative quantities** – Select this checkbox to include negative quantities for calculated measure results.

1. Select **Query** on the toolbar to send the request.

### Inventory adjustment

Use the **Inventory Adjustment** page in the **Operational visibility** group to make real-time updates to inventory. Follow these steps to set up and submit an update.

1. On the [UI version 2](#ui-version) navigation pane, select **Inventory Adjustment**.
1. In the **Product** section, enter the **Product ID**, **Organization ID**, **Site ID**, and **Location ID** values of the products that you want to update. <!--KFM: I added product ID here. But should we list this separately as optional (as with on-hand query)? -->
1. Select **Edit Dimensions** to choose which dimensions to include in the request body. Then enter values for the selected dimensions in the **Product** section.
1. In the **Measures to update** section, select **Add** to add a row for the measure that you want to update. For the new row, select a data source, physical measure, and quantity to update. You must specify at least one measure. You can add multiple measures.
1. Select **Post** on the toolbar to send the request.

### Soft reserve

Use the **Soft reserve** page in the **Operational visibility** group to make soft reservations of inventory.

> [!IMPORTANT]
> The capability to make soft reservations through the user interface should be used only to test the feature. Every soft reservation request should be associated with a transaction order line change (create, modify, delete, and so on). Therefore, we recommend that you make only soft reservations that are linked to back-end orders. Learn more in [Inventory Visibility soft reservations](inventory-visibility-reservations.md).

Follow these steps to set up and submit a soft reservation.

1. On the [UI version 2](#ui-version) navigation pane, select **Soft reserve**.
1. In the **Product** section, enter the **Product ID**, **Organization ID**, **Site ID**, and **Location ID** values of the products that you want to update. <!--KFM: I added product ID here. But should we list this separately as optional (as with on-hand query)? -->
1. Select **Edit Dimensions** to choose which dimensions to include in the request body. Then enter values for the selected dimensions in the **Product** section.
1. In the **Reservation settings** section, set the following fields:

    - **Enable negative inventory to support oversell** – Select this checkbox to skip the available-for-reservation check. Clear it to enforce the check.
    - **Reserve on measure** – Select the data source and physical measure to perform the soft reservation on.
    - **Quantity** – Specify the quantity to reserve.

1. Select **Post** on the toolbar to send the request.

### Change a schedule

Use the **Post on hand change schedule** page in the **Operational visibility** group to post inventory changes with dates to the Inventory Visibility service. Follow these steps to set up and submit a schedule change.

1. On the [UI version 2](#ui-version) navigation pane, select **Change schedule**.
1. In the **Product** section, enter the dimension values of the products that you want to update.
1. In the **Change schedule measure, quantity and date** section, sect **Add** to specify the date, data source, physical measure, and quantity for the change.
1. Select **Post** on the toolbar to send the request.

## Search for products in the Inventory Visibility app

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes, such as size and color. For details about how to set up this feature, see [Set up product search for Inventory Visibility](inventory-visibility-product-search.md). For details about how to use it in the Inventory Visibility app, see [Search for products using the Inventory Visibility app](inventory-visibility-product-search-app.md).
