---
title: Inventory Visibility Inventory summary
description: This article describes how to use Inventory summary feature, which provides inventory summary for products together with all dimensions.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 12/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Inventory summary

The **Inventory summary** page provides an inventory summary for products together with all dimensions. It's a customized view for the *Inventory OnHand Sum* entity. Inventory summary data is synced periodically from Inventory Visibility.

> [!NOTE]
> The inventory summary feature only tracks on-hand inventory changes that occurred after you turned on the feature. Data for products that haven't changed since you turned on the feature won't be synced from the Inventory Visibility cache to the Dataverse environment.
>
> When you change the settings for a calculated measure, data on the **Inventory summary** page won't update automatically until the related product data is modified.
>
> If your **Inventory summary** page doesn't show all of the on-hand information you are expecting, open Supply Chain Management, go to **Inventory Management \> Periodic tasks \> Inventory Visibility integration**, disable the batch job and reenable it. This will do the initial push, and all data will sync to the *Inventory OnHand Sum* entity right after the initial push. If you want to use the inventory summary feature, we recommend that you turn it on before you create any on-hand changes and enable the **Inventory Visibility integration** batch job.

## Turn on the inventory summary feature in UI version 2 (preview)

[!INCLUDE [preview-banner-section](../includes/preview-banner-section.md)]

<!--KFM: preview until further notice -->

This section applies when you are using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

[!INCLUDE [preview-note](../includes/preview-note.md)]

To enable the **Inventory summary** page and set the synchronization frequency in UI version 2, follow these steps:

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Data source settings** tile, select **Manage**.
1. Make the following settings:
    - **Enable feature** – Set to *True*.
    - **Synchronize frequency** – Set the frequency (in minutes) at which inventory summary data should be synced. The minimum is 5 minutes.
1. On the toolbar, select **Save & close**.
1. On the navigation pane, select **Admin Settings**.
1. On the **Update configuration** tile, select **Manage**.
1. Check your modifications in the dialog box.

    > [!IMPORTANT]
    > Be sure to verify all of the important modifications that are about to be made to your data sources, physical measures, and dimension mappings.

1. Select **Confirm Update** to apply your configuration change.

## Turn on the inventory summary feature in UI version 1

To enable the **Inventory summary** page and set the synchronization frequency in UI version 1, follow these steps:

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. From the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. From the navigation pane, select **Configuration**.
1. Open the **Feature management & settings** tab.
1. Turn on the **Toggle switch** for the *Inventory summary* feature.
1. When the feature is enabled, the **Service Configuration** section becomes available and includes a row for configuring the *OnHandMostSpecificBackgroundService* feature. This setting lets you choose the frequency at which inventory summary data is synced. Use the **Up** and **Down** buttons in the **Value** field to change the time between syncs (which can be as low as 5 minutes). Then select **Save**.
1. Select **Update configuration** to save and apply your new settings.

## <a name="additional-tip-for-viewing-data"></a>Filter and browse the inventory summaries

Follow these steps to open the **Inventory summary** page where you can filter and browse your inventory summaries: <!--KFM: Is this the same for both UI versions? If so, we should probably mention that. -->

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. From the **Change area** menu at the bottom of the navigation pane, select **Inventory Visibility**.
1. From the navigation pane, select **Inventory summary**.

    - The **Inventory summary** page provides three fields above the grid (**Default dimension**, **Custom dimension**, and **Measure**). Use these fields to control which columns are visible. You can also select any column header to filter or sort the current result by that column. 
    
    - Use the **Edit filters** button to create a personal view that shows the rows that are important to you. These filter options let you create a wide range of views, from simple to complex. They also let you add grouped and nested conditions to the filters. To learn more about how to use the advanced filter, see [Edit or create personal views using advanced grid filters](/powerapps/user/grid-filters-advanced).
    
    - At the bottom-left of the **Inventory summary** page, you'll find information such as *2 records (2 selected)* or *50 records*. This information refers to the currently loaded records from the **Edit filters** result. The text *2 selected* refers to the number of records that have been selected using the column header filters for the loaded records. There's also a **Load more** button that you can use to load more records from Dataverse. The default number of loaded records is 50. When you select **Load more**, the next 1,000 available records will be loaded into the view. The numbers on the **Load more** button indicates the currently loaded records and the total number of records found by the **Edit filters** result.

The following screenshot highlights the dimension, filtering, result count, and "load more" fields available on the **Inventory summary** page.

:::image type="content" source="media/inventory-visibility-onhand-list.png" alt-text="The Inventory summary page" lightbox="media/inventory-visibility-onhand-list.png":::