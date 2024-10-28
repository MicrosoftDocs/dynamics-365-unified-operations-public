---
title: Assign price groups (preview)
description: Learn now to assign price groups for trade agreements, adjustments, and discounts.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
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
1. You can assign price groups only to journals that haven't yet been posted. Therefore, set the **Show** filter to *Not posted*.
1. Find and select the trade agreement journal that you want to assign a price group to.
1. In the **Price group** column, specify the price group that should be inherited by all lines that are added to the journal.

    :::image type="content" source="media/trade-journal-price-group.png" alt-text="Screenshot that shows a price group being assigned to a trade journal on Trade agreement journals page." lightbox="media/trade-journal-price-group.png":::

1. On the Action Pane, select **Lines**.
1. The **Journal lines, trade agreement** page shows the lines that belong to the selected journal. You can perform the following actions as required:

    - To add a line, select **New** on the Action Pane. Each new line inherits the price group that you assigned to the journal in step 4.
    - Edit the price group for each line.

## Assign price groups to price adjustments or discounts

To assign price groups to a price adjustment or discount, follow these steps.

1. Follow one of these steps:

    - To work with a price adjustment, go to **Pricing management** \> **During-sales pricing** \> **Price adjustments** \> **Margin component price adjustments**.
    - To work with a discount, go to **Pricing management** \> **During-sales pricing** \> **Discounts** \> **All discounts**.

1. In the list pane, select the price adjustment or discount that you want to assign a price group to. The price adjustment or discount that you select must have a status of *Disabled*. (You can view the status on the **General** FastTab.)
1. On the Action Pane, select **Price groups**.
1. On the **Price groups** page, on the Action Pane, select **New** to add a price group.
1. On the header of the new record, in the **Price group** field, specify a name for the price group.
1. On the Action Pane, select **Save**. The following fields on the page are updated:

    - **Pricing priority** – The value is updated to the **Rank** value of the selected price group.
    - **Price attribute group** – The value is updated to the **Price attribute group** value of the selected price group. The grid under this field is updated to show the conditions for the selected price group. 

1. On the Action Pane, select the **Back** button to return to the price adjustment or discount. On the **General** FastTab, you can view the pricing priority that applies to that adjustment or discount. By default, the highest priority among the price groups that you assigned is shown. However, you can override the value by setting the **Override priority** option to *Yes*.
1. Repeat this procedure to add more price groups as required.
