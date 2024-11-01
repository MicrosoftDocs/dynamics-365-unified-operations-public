---
title: Preload a streamlined on-hand query
description: Learn how to preload a streamlined on-hand query, so that you can view preloaded on-hand query results according to their group-by configuration.
author: Weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 12/08/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Preload a streamlined on-hand query

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management stores lots of information about your current on-hand inventory and makes it available for a wide range of purposes. However, many everyday operations and third-party integrations require just a small subset of the stored details. If the system is queried for all of them, the result can be large data sets that take time to assemble and transfer. Therefore, the Inventory Visibility service can periodically fetch and store a streamlined set of on-hand inventory data to make that optimized information continuously available. The stored on-hand inventory details are filtered based on configurable business criteria, to ensure that only the most relevant information is included. Because the filtered on-hand inventory lists are stored locally in the Inventory Visibility service and regularly updated, they support quick access, on-demand data exports, and streamlined integration with external systems.

Preloaded on-hand queries provide the following benefits:

- A cleaner view that stores an inventory summary that includes only the dimensions that are relevant to your daily business
- An inventory summary that's compatible with items that are enabled for warehouse management processes (WMS)

> [!IMPORTANT]
> We recommend that you use either the *Preloaded onhand* feature or the *Inventory summary* feature, but not both. If you enable both features, performance will be affected.

The **Onhand index query preload results** page provides a view for the *On-hand Index Query Preload Results* entity. Unlike the *Inventory summary* entity, the *On-hand Index Query Preload Results* entity provides an on-hand inventory list for products together with selected dimensions. Inventory Visibility syncs the preloaded summary data every 15 minutes.

> [!NOTE]
> Like the *Inventory summary* feature, the *Preloaded onhand* feature tracks only on-hand inventory changes that occur after you turn on the feature. Data for products that haven't changed since you turned on the feature isn't synced from the inventory service cache to the Dataverse environment.
>
> If you change the settings for a calculated measure, data on the **Onhand index query preload results** page isn't automatically updated until the related product data is modified.
>
> If the **Onhand index query preload results** page doesn't show all the on-hand information that you expect, go to **Inventory management** \> **Periodic tasks** \> **Inventory Visibility integration**, disable the batch job, and then reenable it to do the initial push. All data will be synced to the *On-hand Index Query Preload Results* entity within 15 minutes. If you want to use this feature, we recommend that you turn it on before you create any on-hand changes and enable the **Inventory Visibility integration** batch job.

<!--KFM: It ins't clear what the "set number", "group by", or "order" settings mean or do. We should add a section that explains this. -->

## <a name="query-preload-configuration"></a>Turn on and configure preloaded on-hand queries in UI version 2

This section applies when you're using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

To turn on and configure preloaded on-hand queries in UI version 2, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Preloaded onhand** tile, select **Manage**.
1. Set the **Enable feature** option to *True*.
1. In the **Preload group by dimensions** section, add a row for each dimension that you want to use for preloaded on-hand queries. The dimensions that you add here are used to group the preloaded on-hand data.

    - To add a row, select **New onhand index query preload configuration** on the toolbar. Set the **Group by value** field to the dimension that you want to group by, and then assign an order. Preloaded on-hand queries use only dimensions from set number *0* as group-by values. Other sets are ignored. <!--KFM: Where do these set numbers come from? -->When you've finished, select **Save & Close** on the toolbar.
    - To modify a row, select the **Preload set number** link to open the row settings, edit the fields as you require, and then select **Save & Close** on the toolbar.
    - To remove a row, select the **Preload set number** link to open the row settings, and then select **Delete** on the toolbar.

1. If you changed the group-by configuration, select **Admin settings** on the navigation pane, and then, on the **Delete preloaded onhand data** tile, select **Manage**. This step cleans up the database and makes it ready to accept your new group-by settings.
1. On the navigation pane, select **Admin settings**. Then, on the **Update configuration** tile, select **Manage** to update the configuration and activate your changes.

## Turn on and configure preloaded on-hand queries in UI version 1

This section applies when you're using [Inventory Visibility UI version 1](inventory-visibility-ui-version-2.md).

To turn on and configure preloaded on-hand queries in UI version 1, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. On the navigation pane, select **Configuration**.
1. On the **Feature Management & Settings** tab, if the *Preloaded onhand query results* feature is already enabled, we recommend that you use the option to turn it off for now, because the cleanup process might take a long time. You'll turn the feature on again later in this procedure.
1. On the **Preload Setting** tab, in the **Step 1: Clean up preload storage** section, select **Clean** to clean up the database and make it ready to accept your new group-by settings.
1. In the **Step 2: Set up group by values** section, in the **Group result by** field, enter a comma-separated list of field names to group your query results by. After you have data in the preload storage database, you won't be able to change this setting until you clean the database as described in the previous step.
1. On the **Feature Management & Settings** tab, use the option to turn on the *Preload on-hand query results* feature.
1. Select **Update configuration** in the upper-right corner of the page to commit your changes.

## <a name="additional-tip-for-viewing-data"></a>Filter and browse the preloaded query

To filter and browser the preloaded query, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Inventory visibility**. <!--KFM: Seems like you can only see this page from the new UI. Is that right? -->
1. On the navigation pane, select **Preloaded onhand**.
1. On the **Onhand index query preload results** page, you can filter and browse your preloaded summary.

    - Use the **Edit filters** button to create a personal view that shows the rows that are important to you. These filter options let you create a wide range of views, from simple to complex. They also let you add grouped and nested conditions to the filters. For more information about how to use the advanced filter, see [Edit or create personal views using advanced grid filters](/powerapps/user/grid-filters-advanced).
    - Because you've predefined the dimensions that are used to load summary data, the **Onhand index query preload results** page shows dimension-related columns. *The dimensions aren't customizable. The system supports only site and location dimensions for preloaded on-hand lists.* The page provides filters that are similar to the filters on the **Inventory summary** page. However, the dimensions are already selected.
    - The bottom of the page shows information such as *50 records (29 selected)* or *50 records*. This information refers to the records that are currently loaded from the **Edit filters** result. The text *29 selected* refers to the number of records that have been selected by using the column header filters for the loaded records. There's a **Load More** button that you can use to load more records from Dataverse. By default, 50 records are loaded. When you select **Load More**, the next 1,000 available records are loaded into the view. The numbers on the **Load More** button indicate the number of currently loaded records and the total number of records that the **Edit filters** result found.

The following illustration highlights the filtering fields that are available on the **Onhand index query preload results** page.

:::image type="content" source="media/inventory-visibility-preload-onhand-list.png" alt-text="Screenshot of the Onhand index query preload results page." lightbox="media/inventory-visibility-preload-onhand-list.png":::
