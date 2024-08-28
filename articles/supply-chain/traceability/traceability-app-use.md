---
title: Work with the Traceability app (preview)
description: Learn how to work with the Traceability app in Power Apps.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Work with the Traceability app (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Traceability app lets you search for specific batch and serial numbers and analyze the genealogy of your products. This article describes the basics of how to work with it.

## In-app learning

The Traceability app provides in-app learning to help you get started. To access the in-app learning, follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Get started**.
1. A collection of links to videos and tutorials is shown. Select each link that you're interested in.

## Backward search

*Backward searches* let you retrieve the full history of a single product.

- In maintenance, repair, and operations (MRO) scenarios, backward search helps maintenance workers retrieve repair logs and component genealogy associated with a specific serial number for root cause analysis.
- Backward search retrieves component genealogy data that can help you decide whether all components included in a specific product were sourced sustainably (environmentally friendly).

To make a backward search, follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Trace** \> **Genealogy trace**.
1. In the search form, enter a unique identifier (such as a serial, batch, asset, or lot number) of a finished good to retrieve its genealogy, activity, and data collection.
1. Traceability shows a genealogy tree for the serial number you entered.

    :::image type="content" source="media/backward-search-example.png" alt-text="Example of backward search results in the graphic view" lightbox="media/backward-search-example.png":::

1. Now you can do an *activity verification* by following these steps:

    1. Select a node in the genealogy tree.
    1. Select the **View detail** button for your selected node to open a dialog.
    1. Open the **Activities** tab in the dialog. Activity events are displayed in reverse chronological order. For example, you might see five activities for *Consumption* and one activity for *Goods receipt*.

1. Until now, you've been working on the **Graphic view** tab. The table views provide another way to view and explore your data. Select **Table view - composition** to see a table view of your backward search.

    :::image type="content" source="media/backward-search-table-example.png" alt-text="Example of backward search results in the table view" lightbox="media/backward-search-table-example.png":::

## Forward (where-used) search

*Forward searches* help you locate the batch or serial number of finished products that contain semi-products or raw materials with a specific batch or serial number.

In recall scenarios, manufacturers can find the batch or serial number of specific impacted finished goods and then run a specific, accurate recall that minimizes the loss.

For example, in the electric vehicles industry, manufacturers can use the serial number of a battery that is going out of service to locate the cars that use it. They can then offer recycling and warranty services to the affected customers.

To make a forward search, follow these steps:

1. [Open the Traceability app](traceability-app-run.md) in Power Apps.
1. On the left navigation pane, select **Trace** \> **Genealogy trace**.
1. Enter a unique identifier of a raw material or semi-product to see the higher-level assembly related to a selected genealogy tree node.

    :::image type="content" source="media/forward-search-example.png" alt-text="Example of forward search results in the graphic view" lightbox="media/forward-search-example.png":::

1. Select the relevant node in the genealogy tree.
1. Select the **Trace** button for your selected node. The app now shows a high-level genealogy list.
1. Until now, you've been working on the **Graphic view** tab. The table views provide another way to view and explore your data. Select **Table view – where used** to see a table view of your forward search.
