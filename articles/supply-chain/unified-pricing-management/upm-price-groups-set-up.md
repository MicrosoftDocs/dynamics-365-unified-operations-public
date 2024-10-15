---
title: Set up price groups for Unified pricing management (preview)
description: Learn how to set up price groups with attributes for Unified pricing management
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

To create and manage the [price groups](upm-price-groups-overview.md) that you can associate with attributes, follow these steps:

1. Go to **Pricing management** \> **During-sales pricing** \> **Price groups** \> **All price groups**.
1. Do one of the following actions:
    - To create a new price group, 0n the Action Pane, select **New**.
    - To view or edit an existing price group, select it on the list pane and, if you want to edit it, select **Edit** on the Action Pane.
    - To delete an existing price group, select it on the list pane and select **Delete** on the Action Pane.

    :::image type="content" source="media/all-price-groups.png" alt-text="The All price groups page" lightbox="media/all-price-groups.png":::

1. Make the following settings in the header of the new record:
    - **Price group** – Enter a unique identifier for the price group. You can only edit this value when creating a new record.
    - **Name** – Enter a descriptive name for the price group.
    - **Rank** – Select a rank for the price group. In situations where more that one price group apply, the system will use the one that has the highest priority. A higher value results in a higher priority. 

1. Use the **Conditions** FastTab to establish membership rules that control which market segments will be part of the price group. Make the following settings here:
    - Set **Price attribute group** to the [price attribute group](upm-price-attribute-groups.md) that you want to use with this price group. The FastTab grid updates to show the attributes that belong to your selected price attribute group.
    - For each of the attributes in the grid, select an appropriate **Value**.
    - Set the **Enable multiple selections** option to allow multiple (comma-separated) values to be defined for each row. If you define more than one value, then the system combines those values using an *OR* operator.

1. To see a list of trade agreement lines to  which the current price group was assigned, expand the **Trade agreement lines** FastTab.
1. To view and edit the price adjustments that apply to the current price group, expand the **Price adjustments** FastTab. Use the buttons in the FastTab toolbar to add or remove price adjustments as needed.
1. To view and edit the discounts that apply to the current price group, expand the **Discounts** FastTab. Use the buttons in the FastTab toolbar to add or remove discounts as needed.
1. The **Shipping discounts** and **Tender discounts** FastTabs have no effect in the current version.
