---
title: Preload a streamlined on-hand query
description: This article describes how to preload a streamlined on-hand query, which lets you see preloaded on-hand query result according to their group-by configuration.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/08/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Preload a streamlined on-hand query

[!include [banner](../includes/banner.md)]

Supply Chain Management stores a great deal of information about your current on-hand inventory and makes it available for a wide variety of purposes. However, many everyday operations and third-party integrations require just a small subset of these details, and querying the system for all of them can result in large data sets that take time to assemble and transfer. Therefore, the Inventory Visibility service can periodically fetch and store a streamlined set of on-hand inventory data to make that optimized information continuously available. The stored on-hand inventory details are filtered based on configurable business criteria to ensure that only the most relevant information is included. Because the filtered on-hand inventory lists are stored locally in the Inventory Visibility service and are regularly updated, they support quick access, on-demand data exports, and streamlined integration with external systems.

Preloaded on-hand queries provide the following benefits:

- A cleaner view that stores an inventory summary that only includes the dimensions that are relevant to your daily business.
- An inventory summary that is compatible with items enabled for warehouse management processes (WMS).

> [!IMPORTANT]
> We recommend that you use either the *Preloaded onhand* feature or the *Inventory summary* feature, not both. Enabling both features will impact performance.

The **Onhand index query preload results** page provides a view for the *On-hand Index Query Preload Results* entity. Unlike the *Inventory summary* entity, the *On-hand Index Query Preload Results* entity provides an on-hand inventory list for products together with selected dimensions. Inventory Visibility syncs the preloaded summary data every 15 minutes.

> [!NOTE]
> As with the *Inventory summary* feature, the *Preloaded onhand* feature only tracks on-hand inventory changes that occurred after you turned on the feature. Data for products that haven't changed since you turned on the feature won't be synced from the inventory service cache to the Dataverse environment.
>
> When you change the settings for a calculated measure, data on the **Onhand index query preload results** page won't update automatically until the related product data is modified.
>
> If your **Onhand index query preload results** page doesn't show all of the on-hand information you are expecting, go to **Inventory management > Periodic tasks > Inventory Visibility integration**, disable the batch job, and reenable it. This will do the initial push, and all data will sync to the *On-hand Index Query Preload Results* entity in next 15 minutes. If you want to use this feature, we recommend that you turn it on before you create any on-hand changes and enable the **Inventory Visibility integration** batch job.

<!--KFM: It ins't clear what the "set number", "group by", or "order" settings mean or do. We should add a section that explains this. -->

## <a name="query-preload-configuration"></a>Turn on and configure preloaded on-hand queries in UI version 2 (preview)

[!INCLUDE [preview-banner-section](../includes/preview-banner-section.md)]

<!--KFM: preview until further notice -->

This section applies when you are using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

[!INCLUDE [preview-note](../includes/preview-note.md)]

To turn on and configure preloaded on-hand queries in UI version 2, follow these steps:

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Preloaded onhand** tile, select **Manage**.
1. Set **Enable feature** to *True*.
1. In the **Preload group by dimensions** section, add a row for each dimension that you want to use for preloaded on-hand queries. The dimensions that you add here are used to group the preloaded on-hand data.
    - To add a new row, select **New onhand index query preload configuration** from the toolbar in the **Preload group by dimensions** section. Set **Group by value** to the dimension you want to group by and then assign an **Order**. Preloaded on-hand will only use set 0 as group by values, other sets will be ignored. <!--KFM: Where do these set numbers come from? -->Select **Save & Close** on the toolbar when you're done.
    - To modify a row, select the **Preload set number link** to open the row settings, edit the fields as needed and then select **Save & Close** from the toolbar.
    - To remove a row, select the **Preload set number link** to open the row settings and then select **Delete** from the toolbar.
1. If you changed the group-by configuration, go to **Admin settings** on the navigation page and, on the **Delete preloaded onhand data** tile, select **Manage**.This step cleans up the database and makes it ready to accept your new group-by settings.
1. On the navigation pane, select **Admin settings**. Then, on the **Update configuration** tile, select **Manage** to update configuration to activate your changes.

## Turn on and configure preloaded on-hand queries in UI version 1

This section applies when you are using [Inventory Visibility UI version 1](inventory-visibility-ui-version-2.md).

To turn on and configure preloaded on-hand queries in UI version 1, follow these steps:

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. From the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. From the navigation pane, select **Configuration**.
1. Open the **Feature Management & Settings** tab.
1. If the *Preloaded onhand query results* feature is already enabled, then we recommend you use the **Toggle switch** to turn it off for now because the cleanup process might take a very long time to complete. You'll turn it on again later in this procedure.
1. Open the **Preload Setting** tab.
1. In the **Step 1: Clean up preload storage** section, select **Clean** to clean up the database and make it ready to accept your new group-by settings.
1. In the **Step 2: Set up group by values** section, in the **Group result by** field, enter a comma-separated list of field names by which to group your query results. Once you have data in the preload storage database, you won't be able to change this setting until you clean the database, as described in the previous step.
1. Open the **Feature Management & Settings** tab.
1. Use the **Toggle switch** to turn on the *Preload on-hand query results* feature.
1. Select **Update configuration** in the upper-right corner of the **Configuration** page to commit your changes.

## <a name="additional-tip-for-viewing-data"></a>Filter and browse the preloaded query

To filter and browser the preloaded query, follow these steps:

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. From the **Change area** menu at the bottom of the navigation pane, select **Inventory visibility**. <!--KFM: Seems like you can only see this page from the new UI. Is that right? -->
1. From the navigation pane, select **Preloaded onhand**.
1. The **Onhand index query preload results** page opens, where you can filter and browse your preloaded summary.

    - Use the **Edit filters** button to create a personal view that shows the rows that are important to you. These filter options let you create a wide range of views, from simple to complex. They also let you add grouped and nested conditions to the filters. To learn more about how to use the advanced filter, see [Edit or create personal views using advanced grid filters](/powerapps/user/grid-filters-advanced).

    - Because you've predefined the dimensions used for loading summary data, the **Onhand index query preload results** page displays dimension-related columns. *The dimensions aren't customizable&mdash;the system only supports site and location dimensions for preloaded on-hand lists.* The **Onhand index query preload results** page provides filters that are similar to those on the **Inventory summary** page, except the dimensions are already selected. 

    - At the bottom of the **Onhand index query preload results** pages, you'll find information such as *50 records (29 selected)* or *50 records*. This information refers to the currently loaded records from the **Edit filters** result. The text *29 selected* refers to the number of records that have been selected using the column header filters for the loaded records. There's also a **Load more** button that you can use to load more records from Dataverse. The default number of loaded records is 50. When you select **Load more**, the next 1,000 available records will be loaded into the view. The numbers on the **Load more** button indicates the currently loaded records and the total number of records found by the **Edit filters** result.

The following screenshot highlights the filtering fields available on the **Onhand index query preload results** page.

:::image type="content" source="media/inventory-visibility-preload-onhand-list.png" alt-text="The Preload the Inventory Visibility summary page" lightbox="media/inventory-visibility-preload-onhand-list.png":::
