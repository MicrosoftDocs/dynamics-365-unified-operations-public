---
title: Copilot grid cursor
description: Learn how to work with the smart for Demand planning.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/30/2025
ms.custom: 
  - bap-template
---

# Copilot grid cursor

[!include [banner](../includes/banner.md)]

The *Copilot grid cursor* offers detailed insights into a selected time-series cell's value, including its original value, manual adjustments, and full adjustment history. User comments are also shown, to help make the changes easier to understand.

To use the Copilot grid cursor, follow these steps:

1. Open the time series that you want to analyze. For example, on the navigation pane, select **Planning data** \> **Forecasts**, and then select the time series.
1. In the **Time series values section**, find and select the cell that you want to analyze. After you select the cell, the Copilot grid cursor icon appears to the right of the cell and points to it.

    :::image type="content" source="media/copilot-grid-cursor-icon.png" alt-text="The Copilot grid cursor icon.":::

1. Select the Copilot grid cursor icon to open the **Cell analysis** dialog for your selected cell.

    :::image type="content" source="media/copilot-grid-cursor-info.png" alt-text="The Copilot grid cursor dialog.":::

1. Use the following features of the **Cell analysis** dialog to analyze the selected cell:

    - **Summary** – At the top of the dialog, you can see a summary of the cell's value and its history.
    - **Breakdown** – Select this button to see a graph that shows how the cell's value has been adjusted over time.
    - **Adjustment history** – Select this button to see a timeline that lists each time the cell was edited. To read the comments associated with a listed event, select the **Show details** button for the relevant row.

1. When you're done exploring the cell history, select the **Close** button in the upper-right corner of the dialog.
