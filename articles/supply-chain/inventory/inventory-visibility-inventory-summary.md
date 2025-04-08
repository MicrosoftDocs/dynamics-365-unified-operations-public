---
title: Inventory Visibility inventory summary
description: Learn how to use inventory summary feature, which provides an inventory summary for products together with all dimensions.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 12/01/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Inventory Visibility inventory summary

[!include [banner](../includes/banner.md)]

The **Inventory summary** page is a customized view for the *Inventory OnHand Sum* entity. It provides an inventory summary for products together with all dimensions. Inventory summary data is periodically synced from Inventory Visibility.

> [!NOTE]
> The inventory summary feature tracks only on-hand inventory changes that occur after you turn on the feature. Data for products that haven't changed since you turned on the feature isn't synced from the Inventory Visibility cache to the Microsoft Dataverse environment.
>
> If you change the settings for a calculated measure, data on the **Inventory summary** page isn't automatically updated until the related product data is modified.
>
> If the **Inventory summary** page doesn't show all the on-hand information that you expect, open Dynamics 365 Supply Chain Management, go to **Inventory Management** \> **Periodic tasks** \> **Inventory Visibility integration**, disable the batch job, and then reenable it to do the initial push. All data will be synced to the *Inventory OnHand Sum* entity immediately after the initial push. If you want to use the inventory summary feature, we recommend that you turn it on before you create any on-hand changes and enable the **Inventory Visibility integration** batch job.

## Turn on the inventory summary feature in UI version 2

This section applies when you're using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

To enable the **Inventory summary** page and set the synchronization frequency in UI version 2, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Inventory summary** tile, select **Manage**.
1. Set the following fields:

    - **Enable feature** – Set this option to *True*.
    - **Synchronize frequency** – Set the frequency (in minutes) that inventory summary data should be synced at. The minimum frequency is five minutes.

1. On the toolbar, select **Save & close**.
1. On the navigation pane, select **Admin Settings**.
1. On the **Update configuration** tile, select **Manage**.
1. Review your modifications in the dialog box.

    > [!IMPORTANT]
    > Be sure to verify all the important modifications that are about to be made to your data sources, physical measures, and dimension mappings.

1. Select **Confirm Update** to apply your configuration changes.

## Turn on the inventory summary feature in UI version 1

To enable the **Inventory summary** page and set the synchronization frequency in UI version 1, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. On the navigation pane, select **Configuration**.
1. On the **Feature management & settings** tab, turn on the option for the *Inventory summary* feature.
1. After the feature is enabled, the **Service Configuration** section becomes available. It includes a row that you can use to configure the *OnHandMostSpecificBackgroundService* feature. To set the frequency that inventory summary data is synced at, use the **Up** and **Down** buttons in the **Value** field to change the interval between synchronizations. The minimum interval is five minutes. When you've finished, select **Save**.
1. Select **Update configuration** to save and apply your new settings.

## <a name="additional-tip-for-viewing-data"></a>Filter and browse the inventory summaries

Follow these steps to open the **Inventory summary** page, where you can filter and browse your inventory summaries. <!--KFM: Is this the same for both UI versions? If so, we should probably mention that. -->

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Inventory Visibility**.
1. On the navigation pane, select **Inventory summary**.

    - On the **Inventory summary** page, there are three fields above the grid: **Default dimension**, **Custom dimension**, and **Measure**. Use these fields to control which columns are visible. You can also select any column header in the grid to filter or sort the current result by that column. 
    - Use the **Edit filters** button in the upper right of the page to create a personal view that shows the rows that are important to you. The filter options let you create a wide range of views, from simple to complex. They also let you add grouped and nested conditions to the filters. For more information about how to use the advanced filter, see [Edit or create personal views using advanced grid filters](/powerapps/user/grid-filters-advanced).
    - The lower left of the page shows information such as *2 records (2 selected)* or *50 records*. This information refers to the records that are currently loaded from the **Edit filters** result. The text *2 selected* refers to the number of records that have been selected by using the column header filters for the loaded records. There's a **Load More** button that you can use to load more records from Dataverse. By default, 50 records are loaded. When you select **Load More**, the next 1,000 available records are loaded into the view. The numbers on the **Load More** button indicate the number of currently loaded records and the total number of records that the **Edit filters** result found. For example, the text *(5/5)* indicates that all five of the records from the **Edit filters** result are currently loaded into the view.

The following illustration highlights the dimension, filtering, result count, and "load more" fields on the **Inventory summary** page.

:::image type="content" source="media/inventory-visibility-onhand-list.png" alt-text="Screenshot of the Inventory summary page." lightbox="media/inventory-visibility-onhand-list.png":::
