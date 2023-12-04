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
1. Go to **Inventory Visibility (Legacy UI)** - **Operational Visibility** - **Onhand Query**.
1. Click **Settings** button (gear symbol) at the top of the page.
1. Enter `Client Id`, `Tenant Id`, and `Client Secret` in the **Settings** dialog box with the same values when you [installed the Inventory Visibility Add-in](inventory-visibility-setup.md#install-the-inventory-visibility-add-in).
1. Click **Refresh** button next to the `Bearer Token` field. A new bearer token will be generated and will expire after an hour.

    ![On-hand query settings.](media/inventory-visibility-query-settings.png "On-hand query settings")

## Navigate between user interface versions

Regardless of which user interface version is active, you can navigate between the two versions at any time. However, only the settings you make to the active version of the UI will have any affect. To switch between the two versions, follow these steps:

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. At the bottom of the navigation pane, open the **Change area** menu and select one of the following values:
    - *Inventory Visibility* – The navigation pane displays the pages for UI version 2.
    - *Legacy UI* – The navigation pane displays the pages for UI version 1.

## Set up on-hand index configuration

Regardless of which user interface version is active, the purpose and functionally of on-hand index configuration is the same. For an overview and examples about how on-hand index configuration works, see [On-hand index configuration](inventory-visibility-power-platform.md#index). This section just describes how to find the on-hand index configuration settings in UI version 1.

1. Open the **Inventory Visibility** power app.

1. Go to **Inventory Visibility (Legacy UI)** - **Configuration** - **Product Index Hierarchy**. Set number and hierarchy will be automatically generated when you make modification.

1. [Update Configuration](#update-configuration) after you modify onhand index configuration.

## Feature management

Inventory Visibility Add-in offers multiple features as below.

| Feature name | Description |
|---|---|
| [Available to promise](inventory-visibility-available-to-promise.md) | Track your available to promise (ATP) across all data sources and channels. |
| [Inventory allocation](inventory-visibility-allocation.md) | Allocate your valuable on-hand stock to your most important channels, customers, or pre-defined groups and track consumption of each allocated pool. |
| [Advanced warehouse inventory](inventory-visibility-whs-support.md) | Sync and view advanced warehouse item inventory with warehouse hierarchies. |
| [Soft reservation](inventory-visibility-reservations.md) | Post your omnichannel reservations to Inventory Visibility soft reservations for real-time inventory availability checks and updates. |
| [Inventory log history](inventory-visibility-track-inventory-log-history.md) | Allow Inventory Visibility to store your successful transaction logs. You can query your log history with details on organization, product, date range, site and warehouse. |
| [Inventory summary](inventory-visibility-inventory-summary.md) | Periodically sync your raw Inventory summary from cache to dataverse. This feature is not compatible with advanced warehouse items. Either enable this feature or the Preloaded On-hand feature, do not enable both. |
| [Preload on-hand](inventory-visibility-preload-on-hand.md) | Periodically preload the Inventory summary to Dataverse from a query result that is configurable with dimensions that are most relevant to your business. This feature is compatible with advanced warehouse items. Either enable this feature or Inventory Summary feature, do not enable both. |

By default, all features are disabled. This status can be managed on **Settings (Preview)** - **Feature Management** for UI Version 2 users, and on **Inventory Visibility (Legacy UI)** - **Configuration** - **Feature Management & Settings** for UI Version 1 users. [Update configuration](#update-configuration) is required to commit your modification.


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

## Search for products in the Inventory Visibility app

The *product search* feature lets users search for products and on-hand inventory information based on specific attributes, such as size and color. For details about how to set up this feature, see [Set up product search for Inventory Visibility](inventory-visibility-product-search.md). For details about how to use it in the Inventory Visibility app, see [Search for products using the Inventory Visibility app](inventory-visibility-product-search-app.md).
