---
title: Set up price groups for Unified pricing management (preview)
description: Learn how to set up price groups with attributes for Unified pricing management.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPPriceGroupApplicability
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Set up price groups for Unified pricing management (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

To create and manage the [price groups](upm-price-groups-overview.md) that you can associate with attributes, follow these steps.

1. Go to **Pricing management** \> **During-sales pricing** \> **Price groups** \> **All price groups**.
1. Follow one of these steps:

    - To create a new price group, select **New** on the Action Pane.
    - To view an existing price group, select it in the list pane. Then, if you want to edit the price group, select **Edit** on the Action Pane.
    - To delete an existing price group, select it in the list pane, and then select **Delete** on the Action Pane.

    :::image type="content" source="media/all-price-groups.png" alt-text="Screenshot of the All price groups page." lightbox="media/all-price-groups.png":::

1. On the header of the new record, set the following fields:

    - **Price group** – Enter a unique identifier for the price group. You can edit this field only when you create a new record.
    - **Name** – Enter a descriptive name for the price group.
    - **Rank** – Select a rank for the price group. In situations where multiple price groups apply, the system uses the price group that has the highest priority. The larger the value is, the higher the priority.

1. On the **Conditions** FastTab, set the following fields to define membership rules that control which market segments are part of the price group:

    - Set the **Price attribute group** field to the [price attribute group](upm-price-attribute-groups.md) that you want to use with the price group. The grid is then updated to show the attributes that belong to the selected price attribute group.
    - For each attribute in the grid, select an appropriate value in the **Value** field.
    - Set the **Enable multiple selections** option to *Yes* to allow multiple values to be defined for each row. If more than one value is defined for a row, the values must be separated by commas. The system combines the values by using an *OR* operator.

1. To view the list of trade agreement lines that the current price group was assigned to, select the **Trade agreement lines** FastTab.
1. To view and edit the price adjustments that apply to the current price group, select the **Price adjustments** FastTab. Then use the buttons on the toolbar to add or remove price adjustments as you require.
1. To view and edit the discounts that apply to the current price group, select the **Discounts** FastTab. Then use the buttons on the toolbar to add or remove discounts as you require.

> [!NOTE]
> In the current version, the **Shipping discounts** and **Tender discounts** FastTabs on the **All price groups** page have no effect.
