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

This article describes how to use the Inventory Visibility app.

Inventory Visibility provides a model-driven app for visualization. The app contains three pages: **Configuration**, **Operational visibility**, and **Inventory summary**. It has the following features:

- It provides a user interface (UI) for on-hand configuration and soft reservation configuration.
- It supports real-time on-hand inventory queries on various dimension combinations.
- It provides a UI for posting reservation requests.
- It provides a view of the inventory on-hand for products together with all dimensions.
- It provides a view of an on-hand inventory list for products together with pre-defined dimensions. The onhand list view can either be a full summary, or a preloaded result from onhand query.


## Prerequisites

Before you begin, install and set up the Inventory Visibility Add-in as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## Open and authenticate the Inventory Visibility app

To open the Inventory Visibility app, sign in to your Power Apps environment and open **Inventory Visibility** app.
- Click on **Operationaly Visibility** tab on the left panel.
- On the new page, click on the gear tool icon on the upper screen. A new **Settings** pop-up window appears
- Enter your **Client Id**,**Tenant Id** and **Client Secret** that you noted down from [Install and set up Inventory Visibility](inventory-visibility-setup.md#install-the-inventory-visibility-add-in).
- On the **Bearer Token** field, click refresh button, this will generate a new Bearer Token based on the information you entered in previous step.
- Once you have a valid Bearer Token, close the window. The Bearer Token will expire after a while. So make sure to refresh your Bearer Token once a while when you need to update configuration or post/query data later.
![On-hand query settings](media/inventory-visibility-query-settings.png "On-hand query settings")

## <a name="configuration"></a>Configuration

The **Configuration** page of the Inventory Visibility app helps you set up the general data management configuration and feature configuration. After the add-in is installed, the default configuration includes a default setup for Microsoft Dynamics 365 Supply Chain Management (the `fno` data source). You can review the default setting. Hereafter, based on your business requirements and the inventory posting requirements of your external system, you can modify the configuration to standardize the way that inventory changes can be posted, organized, and queried across the multiple systems.

For complete details on how to configure the solution, see [Configure Inventory Visibility](inventory-visibility-configuration.md).

## Operational visibility

The **Operational Visibility** page provides the results of a real-time on-hand inventory query, Reservation Posting and Allocation based on various dimension combinations. When the *OnHandReservation* feature is turned on, you can also post reservation requests from the  **Operational Visibility** page.

### On-hand query

The **Onhand Query** tab allows you to query ta real-time on-hand inventory via UI. 
1. It is mandate for you to enter correct value for **Organization ID**, **Site ID** and **Location ID**,if you enter one or multiple product IDs, you will get a response with exact match of your query. If you leave **Product ID** filed blank, you will get result of all the products under the site and location specified.

1. If you want your result to display with more granulairty, such as view by dimension values like different color and size, you can select group by dimensions from **Group Result By** dropdown list.

1. Once you set your group by value, if you want to obtain result only with specific dimension value, for example color Id = red, you can select the specific dimension from **Filter Dimensions** and enter dimension value.
1. Click **Query**, you will receive a success (green) or failed message (red) upon successful or failed query. If your query is failed, check if the query criteria in the previous steps are entered accurately, and ensure your Bearer Token is not expire.

Another way to do an onhand query is via making direct API request. You can find details on APIs available in [Query by using the post method](inventory-visibility-api.md#query-with-post-method). You can use either /api/environment/{environmentId}/onhand/indexquery or /api/environment/{environmentId}/onhand

### Reservation posting

Use the **Reservation Posting** tab of the **Operational Visibility** page to post a reservation request. Before you can post a reservation request, you must turn on the *OnHandReservation* feature. For more information about this feature and how to turn it on, see [Inventory Visibility reservations](inventory-visibility-reservations.md). 
> [!NOTE]
> Soft reservation via UI is suggested to be used to test the feature, as each soft reservation request should associate with a transaction order line change (creation, modify, delete, etc.), therefore for best practice we do not recommend you to make individual soft reservation without any backend orders to link with. For more details on use case of soft reservation, see [Inventory Visibility reservations](inventory-visibility-reservations.md).

Follow the following steps to post a soft reservation request via UI.
1. Specify how many you want to soft reserve on the **Quantity** field
1. Leave the **Enable nagative inventory to support oversell** uncheck if you do not allow oversell/over-reserve the stock
1. On the **Operator** field, select datasource and physical measure that the soft reserved quantity will be recorded to. For example, datasource = iv, physical measure = softreservephysical
1. Enter Organization ID, Site ID, Location IDs and product ID
1. On **Dimensions**, select data source, dimensions and dimension values to make soft reservation with more granularity.

Another way to post soft reservation is via direct API posting. You can use the pattern that is described in [Create one reservation event](inventory-visibility-api.md#create-one-reservation-event). Then select **Post**. To view the request response details, select **Show details**. You can also get the `reservationId` value from the response details.

### Allocation
See [Inventory Visibility inventory allocation](inventory-visibility-allocation.md) for Allocation management via UI and APIs.
## <a name="inventory-summary"></a>Inventory summary

The **Inventory summary** page provides an inventory summary for products together with all dimensions. It's a customized view for the *Inventory OnHand Sum* entity. Inventory summary data is synced periodically from Inventory Visibility.

To enable the **Inventory summary** page and set the synchronization frequency, follow these steps:

1. Open the **Configuration** page.
1. Open the **Feature Management & Settings** tab.
1. Set the toggle switch for the **OnHandMostSpecificBackgroundService** feature to *Yes*.
1. When the feature is enabled, the **Service Configuration** section becomes available and includes a row for configuring the **OnHandMostSpecificBackgroundService** feature. This setting lets you choose the frequency at which inventory summary data is synced. Use the **Up** and **Down** buttons in the **Value** column to change the time between syncs (which can be as low as 5 minutes). Then select **Save**.

    ![The OnHandMostSpecificBackgroundService Setting](media/inventory-visibility-ohms-freq.png "The OnHandMostSpecificBackgroundService Setting")

1. Select **Update configuration** to save all the changes.


> [!NOTE]
> The *OnHandMostSpecificBackgroundService* feature only tracks on-hand inventory changes that occurred after you turned on the feature. Data for products that haven't changed since you turned on the feature won't be synced from the inventory service cache to the Dataverse environment. If your **Inventory summary** page doesn't show all of the on-hand information you are expecting, open Supply Chain Management, go to **Inventory Management > Periodic tasks > Inventory Visibility integration**, disable the batch job and reenable it. This will do the initial push, and all data will sync to the *Inventory OnHand Sum* entity in the next 15 minutes. If you want to use the *OnHandMostSpecificBackgroundService* feature, we recommend that you turn it on before you create any on-hand changes and enable the **Inventory Visibility integration** batch job.

## <a name="preload-the-inventory-visibility-onhand-query"></a>Preload a streamlined on-hand query

[!INCLUDE [preview-banner-section](../../includes/preview-banner-section.md)]
<!-- KFM: Preview until further notice -->

Supply Chain Management stores a great deal of information about your current on-hand inventory and makes it available for a wide variety of purposes. However, many everyday operations and third-party integrations require just a small subset of these details, and querying the system for all of them can result in large data sets that take time to assemble and transfer. Therefore, the Inventory Visibility service can periodically fetch and store a streamlined set of on-hand inventory data to make that optimized information continuously available. The stored on-hand inventory details are filtered based on configurable business criteria to ensure that only the most relevant information is included. Because the filtered on-hand inventory lists are stored locally in the Inventory Visibility service and are regularly updated, they support quick access, on-demand data exports, and streamlined integration with external systems.

> [!NOTE]
> The current preview version of this feature can only provide preloaded results that include site and location. The final version of the feature is expected to let you select other dimensions to preload the results.

The **Preload the Inventory Visibility Summary** page provides a view for the *On-hand Index Query Preload Results* entity. Unlike the *Inventory summary* entity, the *On-hand Index Query Preload Results* entity provides an on-hand inventory list for products together with selected dimensions. Inventory Visibility syncs the preloaded summary data every 15 minutes.

To view data on the **Preload the Inventory Visibility Summary** tab, you must turn on the *OnHandIndexQueryPreloadBackgroundService* feature on the **Feature Management** tab of the **Configuration** page and then select **Update configuration** (see also [Configure Inventory Visibility](inventory-visibility-configuration.md)).

> [!NOTE]
> As with the *OnhandMostSpecificBackgroudService* feature, the *OnHandIndexQueryPreloadBackgroundService* feature only tracks on-hand inventory changes that occurred after you turned on the feature. Data for products that haven't changed since you turned on the feature won't be synced from the inventory service cache to the Dataverse environment. If your **Inventory summary** page doesn't show all of the on-hand information you are expecting, go to **Inventory Management > Periodic tasks > Inventory Visibility integration**, disable the batch job and reenable it. This will do the initial push, and all data will sync to the *On-hand Index Query Preload Results* entity in next 15 minutes. If you want to use this feature, we recommend that you turn it on before you create any on-hand changes and enable the **Inventory Visibility integration** batch job.

## <a name="additional-tip-for-viewing-data"></a>Filter and browse the inventory summaries

By using the **Advanced filter** that Dataverse provides, you can create a personal view that shows the rows that are important to you. The advanced filter options let you create a wide range of views, from simple to complex. They also let you add grouped and nested conditions to the filters. To learn more about how to use the advanced filter, see [Edit or create personal views using advanced grid filters](/powerapps/user/grid-filters-advanced).

The **Inventory summary** page provides three fields above the grid (**Default dimension**, **Custom dimension**, and **Measure**) that you can use to control which columns are visible. You can also select any column header to filter or sort the current result by that column. The following screenshot highlights the dimension, filtering, result count, and "load more" fields available on the **Inventory summary** page.

![The Inventory summary page.](media/inventory-visibility-onhand-list.png "The Inventory summary page")

Because you will have predefined the dimensions used for loading summary data, the **Preload the Inventory Visibility summary** page displays dimension-related columns. *The dimensions aren't customizable&mdash;the system only supports site and location dimensions for preloaded on-hand lists.* The **Preload the Inventory Visibility summary** page provides filters that are similar to those on the **Inventory summary** page, except the dimensions are already selected. The following screenshot highlights the filtering fields available on the **Preload the Inventory Visibility summary** page.

![The Preload the Inventory Visibility summary page.](media/inventory-visibility-preload-onhand-list.png "The Preload the Inventory Visibility summary page")

At the bottom of the **Preload the Inventory Visibility summary** and  **Inventory summary** pages, you'll find information such as "50 records (29 selected)" or "50 records". This information refers to the currently loaded records from the **Advanced filter** result. The text "29 selected" refers to the number of records that have been selected by using the column header filter for the loaded records. There is also a **Load more** button that you can use to load more records from Dataverse. The default number of loaded records is 50. When you select **Load more**, the next 1,000 available records will be loaded into the view. The number on the **Load more** button indicates the currently loaded records and the total number of records for the **Advanced Filter** result.
