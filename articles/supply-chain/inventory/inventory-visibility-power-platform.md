---
title: Use the Inventory Visibility app UI version 2 (preview)
description: This article describes how to use the Inventory Visibility app UI version 2.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/04/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Use the Inventory Visibility app UI version 2 (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article describes how to use the Inventory Visibility app, which runs in Microsoft Power Apps.

The Inventory Visibility app offers two versions of model-driven user experiences for visualization. Users now have the option to choose between the new version UI (referred to as UI Version 2 in this article) and the legacy UI (also referred to as UI Version 1 in this article).

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To work with the Inventory Visibility app using UI version 2, the following prerequisites must be in place:

- You must [install and set up Inventory Visibility](inventory-visibility-setup.md).
- You must [turn on Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md). 

## Authenticate with the Inventory Visibility service

1. Sign in to your Power Apps environment.
1. Open the **Inventory Visibility** app.
1. On the navigation pane, select **Admin settings**.
1. On the **Set tokens** tile, select **Manage**.
1. Enter the **Client ID**, **Tenant ID**, and **Client secret** in the dialog box. These values were established when [the Inventory Visibility Add-in was installed](inventory-visibility-setup.md#install-add-in).

1. Select **Login**. The system generates a new bearer token for your sessions, which expires after one hour.

## <a name="ui-version"></a>Navigate between user interface versions

Regardless of which user interface version is active, you can navigate between the two versions at any time. However, only the settings you make using the active version of the UI will have any affect. To switch between the two versions, follow these steps:

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. At the bottom of the navigation pane, open the **Change area** menu and select one of the following entries:
    - **Inventory Visibility** – The navigation pane displays the pages for UI version 2.
    - **Legacy UI** – The navigation pane displays the pages for UI version 1.

## <a name="endpoint"></a>Find your service endpoint and read the configuration

The Inventory Visibility service is deployed on Microsoft Azure Service Fabric in multiple geographies and multiple regions. Currently, there is no central endpoint to automatically redirect your requests to the appropriate geography and region. Therefore, the service endpoint uses the following pattern, which includes the necessary information:

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

To obtain your service endpoint and runtime configuration, follow these steps:

1. On the [UI version 2](#ui-version) navigation pane, select **Admin settings**.
1. On the **Show service details** tile, select **Manage**.
1. A dialog opens where you can find your service endpoint and configuration details.

## <a name="update-configuration"></a>Update the configuration

Any time you modify the configuration and save your settings, the system only saves the settings temporarily until you are ready to commit them to the system so they can take effect. Follow these steps to commit new configuration settings to the service:

1. On the [UI version 2](#ui-version) navigation pane, select **Admin settings**.
1. On the **Update Configuration** tile, select **Manage**.
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

## <a name="index"></a>On-hand index configuration

In many cases, on-hand inventory are queried not only at the most detailed level, but also at some aggregated levels based on the inventory dimensions.

For frequently used query patterns, you can improve query performance by setting up *indexes*.

As defined in the following table, an index is composed of a *set number*, *dimension(s)* and *hierarchy*.

| Name | Description |
|---|---|
| *Set number* | Dimensions under the same set number belong to the same set (index), and are grouped together. |
| *Dimension(s)* | Base dimension(s) that query results are aggregated on. |
| *Hierarchy* | Determines the specific combinations of dimensions that can take advantage of an index query. For example, if you set up an index with dimensions and hierarchy of *(ColorId, SizeId, StyleId)*, only queries that use the following four dimension combinations for their filter and group-by fields will be enhanced. The first combination is empty, the second is *(ColorId)*, the third is *(ColorId, SizeId)*, and the fourth is *(ColorId, SizeId, StyleId)*. (The filter field is not order-restricted.) The index won't speed up queries with other dimension combinations. |

A standard set of indexes are provided in the default on-hand index configuration.

> [!TIP]
> Be aware of the following tips when setting up your on-hand index configuration:
>
> - Base dimensions reserved in the partition configuration (set number 0) should not be included in other on-hand index configurations.
> - If you are not interested in querying some specific dimension combinations, set up an index with only one base dimension, *Empty*.

### Set up the on-hand index configuration

1. On the [UI version 2](#ui-version) navigation pane, select **Index Configuration**.
1. Add and remove lines in the grid as needed to define your index. See also the introduction to this section and the [on-hand index configuration example](#index-configuration-example) given in the next subsection.
1. [Update the configuration](#update-configuration) to apply your changes.

### <a name="index-configuration-example"></a>On-hand index configuration example

This section provides an example to help illustrate how on-hand index works.

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

This index improves the performance of following on-hand inventory queries.

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

1. On the [UI version 2](#ui-version) navigation pane, select **Feature management**.
1. Find the tile named after the feature you want to turn on or off, and then select **Manage**.
1. Turn on and set up the feature as needed. Each feature provides different settings. For more information, see the documentation for the feature you are setting up.
1. [Update the configuration](#update-configuration) to commit your changes so they will take effect.

## Delete all configurations

If necessary, you can delete all configurations except for those contained in Inventory Visibility data sources *fno* and *@iv*. Deleted configurations can't be restored.

1. On the [UI version 2](#ui-version) navigation pane, select **Admin Settings**.
1. On the **Delete all configurations** tile, select **Manage**.
1. You are asked to confirm the deletion. Select **OK** to proceed.

## Delete all inventory data

If necessary, you can delete all Inventory Visibility data in both the cache and in Dataverse except for configurations. Deleted data can't be restored and users will be blocked until deletion completes.

1. On the [UI version 2](#ui-version) navigation pane, select **Admin Settings**.
1. On the **Delete all inventory data** tile, select **Manage**.
1. You are asked to confirm the deletion. Select **OK** to proceed.

## Inventory queries and updates

On the navigation pane, the **Operational visibility** group provides pages to make real-time on-hand inventory queries and updates. When the [soft reservation](inventory-visibility-reservations.md) feature is [enabled](#feature-management), you can also post reservation requests to the API. For more details about API requests, see [Inventory Visibility public APIs](inventory-visibility-api.md).

The following elements are common for each of these pages.

- A **Post** or **Query** button on the toolbar lets you send API requests to Inventory Visibility service. This button is disabled until you have entered all the content required for the API call on the page.
- A **Product** section, where you can enter a **Product ID**, a **Organization ID**, and dimension values for the API request. Select the **Edit Dimensions** button in this section to choose which of the available dimensions to include in the request.
- A *Settings* section (with varying names), where you can enter API-specific settings (such as whether to query available-to-promise contents for an on-hand query).
- A **Developer reference** button on the toolbar lets you see the raw contents of your API request (read-only).
- A **Settings** button on the toolbar lets you view and edit the authentication details used to access the Inventory Visibility service.

Details about how to set up and use each type of operation are provided in the following subsections.

### On-hand query

Use the **On hand query** page in the **Operational visibility** group to query real-time on-hand inventory. Follow these steps to set up and run a query:

1. On the [UI version 2](#ui-version) navigation pane, select **On hand query**.
1. In the **Product** section, enter the **Organization ID**, **Site ID**, and **Location ID** for the products you want to look for.
1. In **Product ID** field, enter one or more product IDs to get an exact match for your query, or leave it blank to include all products at the specific site and location. <!--KFM: I copied this step from the UIv1 instructions. Please confirm it also applies here. -->
1. Select the **Edit Dimensions** button in the **Product** section to choose which dimensions to include in the query body. Then enter values for your selected dimensions in the **Product** section.
1. Select **Use all values** for each field that should be included in query without filtering on any certain value.
1. In the **Query Settings** section, set the following options:
    - **Query ATP** – Select this check box to include available-to-promise (ATP) information.
    - **Include negative quantities** – Select this check box to include negative quantities for calculated measure results.
1. Select **Query** in the toolbar to send the request.

### Inventory adjustment

Use the **Inventory Adjustment** page in the **Operational visibility** group to make real-time updates to inventory. Follow these steps to set up and submit an update:

1. On the [UI version 2](#ui-version) navigation pane, select **Inventory Adjustment**.
1. In the **Product** section, enter the **Product ID**, **Organization ID**, **Site ID**, and **Location ID** for the products you want to update. <!--KFM: I added product ID here. But should we list this separately as optional (as with on-hand query)? -->
1. Select the **Edit Dimensions** button in the **Product** section to choose which dimensions to include in the request body. Then enter values for your selected dimensions in the **Product** section.
1. Select **Add** in the **Measures to update** section to add a new row that defines a measure that you want to update. For the new row, select a data source, physical measure, and quantity to update. You must specify at least one measure. You can add multiple measures to update.
1. Select **Post** in the toolbar to send the request.

### Soft reserve

Use the **Soft reserve** page in the **Operational visibility** to make soft reservations of inventory.

> [!IMPORTANT]
> The ability to make soft reservations through the user interface should only be used to test the feature. Each soft reservation request should be associated with a transaction order line change (create, modify, delete, and so on). Therefore, we recommend that you only make soft reservations that are linked to back-end orders. For more information, see [Inventory Visibility soft reservations](inventory-visibility-reservations.md).

Follow these steps to set up and submit a soft reservation.

1. On the [UI version 2](#ui-version) navigation pane, select **Soft reserve**.
1. In the **Product** section, enter the **Product ID**, **Organization ID**, **Site ID**, and **Location ID** for the products you want to update. <!--KFM: I added product ID here. But should we list this separately as optional (as with on-hand query)? -->
1. Select the **Edit Dimensions** button in the **Product** section to choose which dimensions to include in the request body. Then enter values for your selected dimensions in the **Product** section.
1. In **Reservation settings** section, make the following settings:
    - **Enable negative inventory to support oversell** – Select this check box to skip available-for-reservation check. Unselect it to enforce the check.
    - **Reserve on measure** – Select the data source and physical measure to execute the soft reservation on.
    - **Quantity** – specify the quantity you want to reserve.
1. Select **Post** in the toolbar to send the request.

## Search for products in the Inventory Visibility app

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes, such as size and color. For details about how to set up this feature, see [Set up product search for Inventory Visibility](inventory-visibility-product-search.md). For details about how to use it in the Inventory Visibility app, see [Search for products using the Inventory Visibility app](inventory-visibility-product-search-app.md).
