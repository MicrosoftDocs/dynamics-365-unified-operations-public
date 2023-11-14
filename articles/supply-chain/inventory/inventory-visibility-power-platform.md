---
title: Inventory Visibility app
description: This article describes how to use the Inventory Visibility app.
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

# Use the Inventory Visibility app

[!include [banner](../includes/banner.md)]

This article describes some basic usage of the Inventory Visibility power app.

Inventory Visibility power app offers two versions of model-driven user experiences for visualization. Users now have the option to choose between the new version UI (referred to as UI Version 2 in this article) and the legacy UI (also refferred to as UI Version 1 in this article).

## Introduction

For UI Version 2 users, refer to the following sections.
- [Authenticate the Inventory Visibility app](#authenticate-the-inventory-visibility-app)
- [Find service endpoint and read cofiguration](#find-service-endpoint-and-read-configuration)
- [Update configuration](#update-configuration)
- [Partition configuration](#partition-configuration)
- [Onhand index configuration](#onhand-index-configuration)
- [Feature Management](#feature-management)
- [Delete all configuration](#delete-all-configurations)
- [Delete all inventory data](#delete-all-inventory-data)
- [Inventory query and update](#inventory-query-and-update)

For UI Version 1 users, refer to the following sections.

- [Authenticate the Inventory Visibility app (Legacy UI)](#authenticate-the-inventory-visibility-app-legacy-ui)
- [Find service endpoint and read cofiguration (Legacy UI)](#find-service-endpoint-and-read-configuration-legacy-ui)
- [Update configuration (Legacy UI)](#update-configuration-legacy-ui)
- [Partition configuration](#partition-configuration)
- [Onhand index configuration](#onhand-index-configuration)
- [Feature Management](#feature-management)
- [Delete all configuration (Legacy UI)](#delete-all-configurations-legacy-ui)
- [Delete all inventory data (Legacy UI)](#delete-all-inventory-data-legacy-ui)
- [Inventory query and update (Legacy UI)](#inventory-query-and-update-legacy-ui)

## Prerequisites

Before you start, [install and set up Inventory Visibility](inventory-visibility-setup.md).

## Authenticate the Inventory Visibility app

1. Sign in to your Power Apps environment.

1. Open the **Inventory Visibility** app.

1. Go to **Settings (Preview)** - **Admin Settings** - **Set Tokens** and click **Manage** button.

1. Enter `Client Id`, `Tenant Id`, and `Client Secret` in the dialog box with the same values when you [installed the Inventory Visibility Add-in](inventory-visibility-setup.md#install-the-inventory-visibility-add-in).

1. Click **Login** button. A new bearer token will be generated and will expire after an hour.

## Find service endpoint and read configuration

The microservice of Inventory Visibility is deployed on Microsoft Azure Service Fabric, in multiple geographies and multiple regions. Currently there is no central endpoint to automatically redirect your request to the corresponding geography and region. Therefore, service endpoint is composed in the following pattern to include necessary information.

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

To obtain your service endpoint and runtime configuration, apply the following steps.

1. Open the **Inventory Visibility** power app.

1. Go to **Settings (Preview)** - **Admin Settings** - **Show Service Details** and click **Manage** button.

## Update configuration

Each time configuration is modified, new configuration will not take effect until commited through update configuration.

1. Open the **Inventory Visibility** power app.

1. Go to **Settings (Preview)** - **Admin Settings** - **Update Configuration** and click **Manage** button.

1. Check your modification in the dialog box.
    > [!IMPORTANT]
    > Be sure to validate important modification on data sources, physical measures, and dimension mappings.
    
1. Click **Confirm Update** to commit. Runtime configuration will be replaced by your new configuration.

## Partition configuration

Partition configuration controls how data is distributed. Operations inside the same partition will deliver better performance at lower cost, comparing to those cross multiple partitions. Below is the default partition configuration included in solution, so *you don't need to set it up yourself*.

| Base dimension | Hierarchy |
|---|---|
| `SiteId` | 1 |
| `LocationId` | 2 |

> [!IMPORTANT]
> Don't customize your partition configuration. If you delete or change it without official guide, you are likely to encounter an unexpected error.

## Onhand index configuration

In many cases, on-hand inventory are queried not only at the most detailed level, but also at some aggregated levels based on the inventory dimensions.
For frequently used query patterns, Inventory Visibility allows users to improve query performance by setting up *indexes*.
As defined in the following table, an index is composed of *set number*, *dimension(s)* and *hierarchy*.

| Name | Description |
|---|---|
| *Set number* | Dimensions under the same set number belong to the same set (index), and will be grouped together. |
| *Dimension(s)* | Base dimension(s) that query results are aggregated on. |
| *Hierarchy* | Hierarchy determines the specific combinations of dimensions that can take advantage of index query. For example, if you set up an index with dimensions and hierarchy of `(ColorId, SizeId, StyleId)`, only queries that use the following four dimension combinations for their filter and group-by fields will be enhanced. (Filter field is not order-restricted.) The first combination is empty, the second is `(ColorId)`, the third is `(ColorId, SizeId)`, and the fourth is `(ColorId, SizeId, StyleId)`. Queries with other dimension combinations will not be sped up. |

A list of indexes are provided in the default onhand index configuration. To make modification, refer to [set up onhand index configuration](#set-up-onhand-index-configuration) or [set up onhand index configuration (Legacy UI)](#set-up-onhand-index-configuration-legacy-ui) according to your UI version. An [example](#onhand-index-configuration-example) is also provided to help with understanding.

> [!TIP]
> Be aware of the following tips when setting up your onhand index configuration:
> - Base dimensions that are reserved in partition configuration (set number 0) should not be included in other onhand index configurations.
> - If you are not interested in querying some specific dimension combinations, set up an index with only one base dimension `Empty`.

### Set up onhand index configuration

1. Open the **Inventory Visibility** power app.

1. Go to **Settings (Preview)** - **Index Configurations**. One line in the table represents one dimension in the corresponding index.

1. [Update Configuration](#update-configuration) after you modify onhand index configuration.

### Set up onhand index configuration (Legacy UI)

1. Open the **Inventory Visibility** power app.

1. Go to **Inventory Visibility (Legacy UI)** - **Configuration** - **Product Index Hierarchy**. Set number and hierarchy will be automatically generated when you make modification.

1. [Update Configuration](#update-configuration) after you modify onhand index configuration.

### Onhand index configuration example

This section provides an example to help illustrate how onhand index works.

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

The following table shows an onhand index configuration.

| Set Number | Dimension | Hierarchy |
|---|---|---|
| 1 | `ColorId` | 1 |
| 1 | `SizeId` | 2 |
| 1 | `StyleId` | 3 |

This index improves the performance of following on-hand inventory queries.

- `()` – Grouped by all

    - D0002, 28

- `(ColorId)` – Grouped by `ColorId`

    - D0002, Black, 10
    - D0002, Red, 18

- `(ColorId, SizeId)` – Grouped by the combination of `ColorId` and `SizeId`

    - D0002, Black, Small, 3
    - D0002, Black, Large, 7
    - D0002, Red, Small, 11
    - D0002, Red, Large, 7

- `(ColorId, SizeId, StyleId)` – Grouped by the combination of `ColorId`, `SizeId`, and `StyleId`

    - D0002, Black, Small, Wide, 1
    - D0002, Black, Small, Regular, 2
    - D0002, Black, Large, Wide, 3
    - D0002, Black, Large, Regular, 4
    - D0002, Red, Small, Wide, 5
    - D0002, Red, Small, Regular, 6
    - D0002, Red, Large, Regular, 7

## Feature management

Inventory Visibility Add-in offers multiple features as below.

| Feature Name | Description |
|--- |---|
| [Available to Promise](inventory-visibility-available-to-promise.md) | Track your ATP across all data sources and channels for up to 7 days into the future. |
| [Inventory Allocation](inventory-visibility-allocation.md) | Allocate your valuable onhand stock to most important channels, customers or pre-defined groups and track consumption of each allocated pool. |
| [Advanced Warehouse Inventory](inventory-visibility-whs-support.md) | Sync and view advanced warehouse item inventory with warehouse hierarchies. |
| [Soft Reservation](inventory-visibility-reservations.md) | Post your omnichannel reservation to Inventory Visibility soft reservation for real-time inventory availability check and updates. |
| Inventory Log History | Allow Inventory Visibility to store your successful transaction logs. You can query your log history with details on organization, product, date range, site and warehouse. |
| Inventory Summary | Periodically sync your raw Inventory summary from cache to dataverse. This feature is not compatiable with advanced warehouse items. Either enable this feature or Preloaded Onhand feature, do not enable both. |
| Preloaded Onhand | Periodically preload the Inventory summary to dataverse from a query result that is configurable with dimensions that are most relevant to your business. This feature is compatable to advanced warehouse items. Either enable this feature or Inventory Summary feature, do not enable both. |

By default, all features are disabled. This status can be managed on **Settings (Preview)** - **Feature Management** for UI Version 2 users, and on **Inventory Visibility (Legacy UI)** - **Configuration** - **Feature Management & Settings** for UI Version 1 users. [Update configuration](#update-configuration) is required to commit your modification.

## Delete all configurations

Delete all out-of-box configurations except for ones contained in Inventory Visibility datasources `fno` and `@iv`. Deleted configurations cannot be restored. 

1. Open the **Inventory Visibility** power app.

1. Go to **Settings (Preview)** - **Admin Settings** - **Delete all configurations** and click **Manage** button.

## Delete all inventory data

Delete all Inventory Visibility data in both cache and Dataverse except for configurations. Deleted data cannot be restored and users will be blocked until deletion completes.

1. Open the **Inventory Visibility** power app.

1. Go to **Settings (Preview)** - **Admin Settings** - **Delete all inventory data** and click **Manage** button.

## Inventory query and update

The **Operational Visibility** group provides pages to make real-time on-hand inventory query and update. When the [soft reservation](inventory-visibility-reservations.md) feature is [enabled](#feature-management), reservation requests can also be posted. For more details about API requests, refer to [Inventory Visibility public APIs](inventory-visibility-api.md).

Below are the common components for each of these pages.

- **Post/Query** button on the top navigation bar allows users to send API requests to Inventory Visibility Add-in. It is disabled until all necessary contents for an API call are filled in the page.

- A **Product** section to fill in `Product ID`, `Organization ID`, and dimensions for the API request. User can click **Edit Dimensions** and select dimensions needed for the request.

- A **Settings** section to fill in API-specific settings. E.g., whether to query available-to-promise contents for on-hand query.

- A **Request Body** section to show the raw contents of this request. This is a read-only field for developer references. 

Detailed setup for each type of operations is as below.

### Onhand query

The **On Hand Query** page in **Operational Visibility** group allows users to query real-time on-hand inventory. Follow these steps to set up and run a query.

1. In the **Product** section, enter the `Organization ID`, `Site ID`, and `Location ID` values that you want to query.

1. Click **Edit Dimensions** to select or unselect dimensions from query body.

1. Select `Use all values` if a dimension should be included in query without filtering any certain value.

1. In the **Query Settings** section, select `Query ATP` to include ATP related information; select `Include negative quantities` to include negative quantities for calculated measure results.

1. Click **Query** button on top navigation bar to send the request. 

### Inventory adjustment

The **Inventory Adjustment** page in **Operational Visibility** group allows users to make real-time updates to inventory. Follow these steps to set up and run an update.

1. In the **Product** section, enter the `Organization ID`, `Site ID`, and `Location ID` values that you want to update inventory.

1. Click **Edit Dimensions** to select or unselect dimensions from request body. Enter correpsonding values.

1. Click **Add** button in **Measures to update** section. Select data source, physical measure and quantity to update. At least one measure is required for an update. 

1. Click **Post** button on top navigation bar to send the request. 

### Soft reserve

The **Soft Reserve** page in **Operational Visibility** group allows users to make soft reservations to inventory.

> [!NOTE]
> The capability of making soft reservations through user interface is intended for feature test. Each soft reservation request should be associated with a transaction order line change (creation, modification, deletion, etc.). Therefore, it is recommended to only make soft reservations that are linked to back-end orders. For more information, see [Inventory Visibility soft reservations](inventory-visibility-reservations.md).

Follow these steps to set up and run a soft reservation.

1. In the **Product** section, enter the `Organization ID`, `Site ID`, and `Location ID` values that you want to make soft reservation.

1. Click **Edit Dimensions** to select or unselect dimensions from request body. Enter correpsonding values.

1. In **Reservation Settings** section, select `Enable negative inventory to support oversell` to skip available-for-reservation check, or unselect it to enforce the check.

1. In **Reservation Settings** section, select for `Reserve on measure` the data source and physical measure to execute soft reservation on, and then enter the quantity below. 

1. Click **Post** button on top navigation bar to send the request. 

### Inventory Allocation

Allocation operations are only supported in Legacy UI. 

## <a name="additional-tip-for-viewing-data"></a>Filter and browse the inventory summaries

By using the **Advanced filter** that Dataverse provides, you can create a personal view that shows the rows that are important to you. The advanced filter options let you create a wide range of views, from simple to complex. They also let you add grouped and nested conditions to the filters. To learn more about how to use the advanced filter, see [Edit or create personal views using advanced grid filters](/powerapps/user/grid-filters-advanced).

The **Inventory summary** page provides three fields above the grid (**Default dimension**, **Custom dimension**, and **Measure**) that you can use to control which columns are visible. You can also select any column header to filter or sort the current result by that column. The following screenshot highlights the dimension, filtering, result count, and "load more" fields available on the **Inventory summary** page.

![The Inventory summary page.](media/inventory-visibility-onhand-list.png "The Inventory summary page")

Because you'll have predefined the dimensions used for loading summary data, the **Preload the Inventory Visibility summary** page displays dimension-related columns. *The dimensions aren't customizable&mdash;the system only supports site and location dimensions for preloaded on-hand lists.* The **Preload the Inventory Visibility summary** page provides filters that are similar to those on the **Inventory summary** page, except the dimensions are already selected. The following screenshot highlights the filtering fields available on the **Preload the Inventory Visibility summary** page.

![The Preload the Inventory Visibility summary page.](media/inventory-visibility-preload-onhand-list.png "The Preload the Inventory Visibility summary page")

At the bottom of the **Preload the Inventory Visibility summary** and  **Inventory summary** pages, you'll find information such as "50 records (29 selected)" or "50 records". This information refers to the currently loaded records from the **Advanced filter** result. The text "29 selected" refers to the number of records that have been selected by using the column header filter for the loaded records. There's also a **Load more** button that you can use to load more records from Dataverse. The default number of loaded records is 50. When you select **Load more**, the next 1,000 available records will be loaded into the view. The number on the **Load more** button indicates the currently loaded records and the total number of records for the **Advanced Filter** result.
## <a name="preload-streamlined-onhand-query"></a>Preload a streamlined on-hand query

## Authenticate the Inventory Visibility app (Legacy UI)

1. Sign in to your Power Apps environment.

1. Open the **Inventory Visibility** app.

1. Go to **Inventory Visibility (Legacy UI)** - **Operational Visibility** - **Onhand Query**.

1. Click **Settings** button (gear symbol) at the top of the page.

1. Enter `Client Id`, `Tenant Id`, and `Client Secret` in the **Settings** dialog box with the same values when you [installed the Inventory Visibility Add-in](inventory-visibility-setup.md#install-the-inventory-visibility-add-in).

1. Click **Refresh** button next to the `Bearer Token` field. A new bearer token will be generated and will expire after an hour.

    ![On-hand query settings.](media/inventory-visibility-query-settings.png "On-hand query settings")

## Find service endpoint and read configuration (Legacy UI)

The microservice of Inventory Visibility is deployed on Microsoft Azure Service Fabric, in multiple geographies and multiple regions. Currently there is no central endpoint to automatically redirect your request to the corresponding geography and region. Therefore, service endpoint is composed in the following pattern to include necessary information:

`https://inventoryservice.<RegionShortName>-il<IsLandNumber>.gateway.prod.island.powerapps.com`

To obtain your service endpoint and runtime configuration, apply the following steps.

1. Open the **Inventory Visibility** power app.

1. Go to **Inventory Visibility (Legacy UI)** - **Configuration** and click **Show Service Details** on the upper-right corner.

## Update configuration (Legacy UI)

Each time configuration is modified, new configuration will not take effect until commited through update configuration.

1. Open the **Inventory Visibility** power app.

1. Go to **Inventory Visibility (Legacy UI)** - **Configuration** and click **Update Configuration** on the upper-right corner.

1. Enter `Client Id`, `Tenant Id`, `and Client Secret` in the dialog box with the same values when you [installed the Inventory Visibility Add-in](inventory-visibility-setup.md#install-the-inventory-visibility-add-in). Click **Login** button.

1. Check your configuration modification in the dialog box.
    > [!IMPORTANT]
    > Be sure to validate important modification on data sources, physical measures, and dimension mappings.
    
1. Click **Confirm Update** to commit. Runtime configuration will be replaced by your new configuration.

## Delete all inventory data (Legacy UI)

Delete all Inventory Visibility data except configurations in both cache and Dataverse. Deleted data cannot be restored and users will be blocked until deletion completes.

1. Open the **Inventory Visibility** power app.

1. Go to **Inventory Visibility (Legacy UI)** - **Configuration** and click **More** button (three dots symbol) on the upper-right corner.

1. Click **Delete all inventory data**.

## Delete all configurations (Legacy UI)

Delete all out-of-box configurations except for ones contained in Inventory Visibility datasources `fno` and `@iv`. Deleted configurations cannot be restored. 

1. Open the **Inventory Visibility** power app.

1. Go to **Inventory Visibility (Legacy UI)** - **Configuration** and click **More** button (three dots symbol) on the upper-right corner.

1. Click **Delete all configurations**.

## Inventory query and update (Legacy UI)

The **Operational Visibility** page provides pages to make real-time on-hand inventory query and update. When the [soft reservation](inventory-visibility-reservations.md)/[inventory allocation](inventory-visibility-allocation.md) feature is [turned on](#feature-management), reservation/allocation requests can also be posted. For more details about API requests, refer to [Inventory Visibility public APIs](inventory-visibility-api.md).

### Onhand query (Legacy UI)

The **Onhand Query** tab of the **Operational Visibility** page allows users to query real-time on-hand inventory. Follow these steps to set up and run a query.

1. Enter the `Organization ID`, `Site ID`, and `Location ID` values that you want to query.

1. In `Product ID` field, enter one or more product IDs to get an exact match for your query, or leave it blank to include all products at the specific site and location.

1. To get a more granular result (e.g., a view by dimensions color and size), select dimensions to group by in `Group Result By` field.

1. To filter items with a specific dimension value (e.g., color = red), select the dimension in `Filter Dimensions` field and enter the value.

1. Select `Query ATP` to include ATP related information.

1. Click **Query** button to send the request.

### Reservation posting (Legacy UI)

The **Reservation Posting** tab of the **Operational Visibility** page allows users to make soft reservations to inventory.

> [!NOTE]

> The capability of making soft reservations through user interface is intended for feature test. Each soft reservation request should be associated with a transaction order line change (creation, modification, deletion, and so on). Therefore, it is recommended to only make soft reservations that are linked to back-end orders. For more information, see [Inventory Visibility soft reservations](inventory-visibility-reservations.md).

Follow these steps to set up and run a soft reservation.

1. In `Quantity` field, enter the quantity that you want to soft reserve.

1. Select `Enable negative inventory to support oversell` to skip available-for-reservation check, or unselect it to enforce the check.

1. In `Operator` field, select the data source and physical measure to execute the soft reservation on.

1. Enter the `Organization ID`, `Site ID`, `Location ID`, and `Product ID` values that you want to make soft reservation.

1. In `Dimension` field, select dimensions and enter correpsonding values.

1. Click **Post** button to send the request. 

1. Click **Show details** button for detailed response, including `reservationId` value.

### Allocation (Legacy UI)

Refer to [use the allocation user interface](inventory-visibility-allocation.md#use-the-allocation-user-interface) for details.

> As with the *OnHandMostSpecificBackgroundService* feature, the *OnHandIndexQueryPreloadBackgroundService* feature only tracks on-hand inventory changes that occurred after you turned on the feature. Data for products that haven't changed since you turned on the feature won't be synced from the inventory service cache to the Dataverse environment.
>
> When you change the settings for a calculated measure, data on the **Preload the Inventory Visibility Summary** page won't update automatically until the related product data is modified.
>
> If your **Preload the Inventory Visibility Summary** page doesn't show all of the on-hand information you are expecting, go to **Inventory Management > Periodic tasks > Inventory Visibility integration**, disable the batch job, and reenable it. This will do the initial push, and all data will sync to the *On-hand Index Query Preload Results* entity in next 15 minutes. If you want to use this feature, we recommend that you turn it on before you create any on-hand changes and enable the **Inventory Visibility integration** batch job.
