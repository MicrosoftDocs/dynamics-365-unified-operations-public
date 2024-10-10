---
title: Assign price groups (preview)
description: Lear now to assign price groups for trade agreements, adjustments, and discounts 
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: XXXX
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---


# Assign price groups (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

## Assign price groups to trade agreements

To assign a price group to a trade agreement, follow these steps.

1. Go to **Pricing management** \> **During-sales pricing** \> **Sales trade agreement price** \> **Trade agreements journals**.
1. ou can only assign price groups to journals that haven't been posted yet, so set the **Show** filter to *Not posted*.
1. Find and select the trade agreement journal you want to assign a price group to.
1. In the **Price group** column, specify the price group that should be inherited bt all lines added to the journal.

    :::image type="content" source="media/trade-journal-price-group.png" alt-text="Assign a price group to a trade journal" lightbox="media/trade-journal-price-group.png":::

1. On the Action Pane, select **Lines**.
1. The **Journal lines, trade agreement** page shows the lines that belong to the selected journal.
    - To add a new line, select **New** from the Action Pane. Each new line inherits the **Price group** you assigned for the journal on the previous page.
    - You can edit the **Price group** for each line as needed.

## Assign price groups to price adjustments

To assign a price group to a price adjustments, follow these steps.

1. Go to **Pricing management** \> **During-sales pricing** \> **Price adjustments** \> **Margin component price adjustments**.
1. On the list pane, select the price adjustment you want to assign a price group to. It must have a **Status** of *Disabled* (as seen on the **General** FastTab).
1. On the Action Pane, select **Price groups**.
1. The **Price groups** page opens. To add a new price group, select **New** on the Action Pane.
1. In the header of the new record, set **Price group** to the name of the price group you want to add.

    - The value of **pricing priority** will default in the field **Pricing priority** on the current price adjustment record. <!-- KFM: Continue here. There are some repeated steps here that need to get cleaned up... -->

    It is non-editable when override priority field is set to be **No**.

1. Select **New** button on top to select price group for the current adjustment record.
1. Select the drop-down list of Price group to specify a price group.
1. Select **Save** button.

    - **Pricing priority** of the selected pricing group displays accordingly.
    - **Price attribute group** value is visible.

1. Predefined fields names and values for the **Price attribute group** are visible.
1. Multiple price groups can be created for the current adjustment record by selecting **New** button.

## Assign price groups to discounts

1. Go to **Pricing management** \> **During-sales pricing** \> **Discounts** \> **All discounts**.
1. Select a specific discount record with status **Disabled**.
1. Select **Price group** button on top and there displays a price group form.

    ![A screenshot of a computer Description automatically generated](media/image7.png)

1. Select **New** button on top to add new records
1. Select drop-down list of price group and choose the name.

    The inherited information displays as follows.

    The value of **pricing priority** will default in the field **Pricing priority** on the current discount record.

    It is non-editable when override priority field is set to be **No**.

    ![A screenshot of a computer Description automatically generated](media/image8.png)

1. Select **New** button on top to select price group for the current adjustment record.
1. Select the drop-down list of Price group to specify a price group.
1. Select **Save** button.

    - **Pricing priority** of the selected pricing group displays accordingly.
    - **Price attribute group** value is visible.

1. Predefined fields names and values for the **Price attribute group** are visible.
1. Multiple price groups can be created for the current adjustment record by selecting **New** button.
