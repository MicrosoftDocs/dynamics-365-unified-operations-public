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
1. You can only assign price groups to journals that haven't been posted yet, so set the **Show** filter to *Not posted*.
1. Find and select the trade agreement journal you want to assign a price group to.
1. In the **Price group** column, specify the price group that should be inherited by all lines added to the journal.

    :::image type="content" source="media/trade-journal-price-group.png" alt-text="Assign a price group to a trade journal" lightbox="media/trade-journal-price-group.png":::

1. On the Action Pane, select **Lines**.
1. The **Journal lines, trade agreement** page shows the lines that belong to the selected journal.
    - To add a new line, select **New** from the Action Pane. Each new line inherits the **Price group** you assigned for the journal on the previous page.
    - Edit the **Price group** for each line as needed.

## Assign price groups to price adjustments or discounts

<!-- KFM: Note: I combined these two sections, since they were nearly identical. -->

To assign price groups to a price adjustment or discount, follow these steps.

1. Go to one of the following pages, depending on whether you want to work with a price adjustment or a discount:
    - **Pricing management** \> **During-sales pricing** \> **Price adjustments** \> **Margin component price adjustments**.
    - **Pricing management** \> **During-sales pricing** \> **Discounts** \> **All discounts**

1. On the list pane, select the price adjustment or discount you want to assign a price group to. It must have a **Status** of *Disabled* (as seen on the **General** FastTab).
1. On the Action Pane, select **Price groups**.
1. The **Price groups** page opens. To add a new price group, select **New** on the Action Pane.
1. In the header of the new record, set **Price group** to the name of the price group you want to add.

    The value of **Pricing priority** will default in the field **Pricing priority** on the current price adjustment or discount record. It's read-only when the **Override priority** option is set to *No*. <!-- KFM: This appears to be false or misleading. Delete this? -->

1. On the Action Pane, select **Save**. The page updates the following values:

    - **Pricing priority** – Updates to show the **Rank** of the selected **Price group**. <!-- KFM: I think this is correct, but it's strange that the field names don't match. -->
    - **Price attribute group** – Updates to show the **Price attribute group** of the selected **Price group**. The grid below this field updates to show the **Conditions** for the selected **Price group**. <!-- KFM: This FastTab should have a name. -->

1. Repeat this procedure to add more price groups as needed.
