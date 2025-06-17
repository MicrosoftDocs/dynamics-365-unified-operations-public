---
title: Calculate capacity load
description: Learn how to calculate capacity load in Asset Management, including a step-by-step process detailing the process of calculating capacity loads.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: EntAssetCapacityLoad, EntAssetWorkOrderCapacityLoadCalculate, EntAssetWorkOrderCapacityLoad 
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Calculate capacity load

[!include [banner](../../includes/banner.md)]

In Asset Management, you can calculate capacity load on:

- Maintenance schedule lines  
- Work orders that haven't yet been scheduled  
- Scheduled work orders

This is useful if you want to get an overview of expected capacity load for a specific period. Calculation of capacity load can be done on all assets or selected assets. You can also make a calculation on maintenance downtime activities or work order pools.

1. Go to one of the following pages, depending on what you want to calculate capacity load for:
    - **Asset management** \> **Inquiries** \> **Capacity load**
    - **Asset management** \> **Work order pools** \> **All work order pools**
    - **Asset management** \> **Work order pools** \> **Active work order pools**
    - **Asset management** \> **Maintenance downtime activities** \> **All maintenance downtime activities**
    - **Asset management** \> **Maintenance downtime activities** \> **Active maintenance downtime activities**

1. Select the record you want to work with and then, on the Action Pane, select **Capacity load**.
1. In the **Calculate capacity load** dialog, select a period for the calculation in the **Start date/time** and **End date/time** fields.
1. Select *Yes* on the **Include maintenance schedule** toggle button if you want to include maintenance schedule lines in the calculation.
1. Select *Yes* on the **Include work order** toggle button if you want to include work order jobs in the calculation.
1. You can use the **Level** field to indicate how detailed you want the capacity load lines to be regarding functional locations.

    For example, if you insert the number *1* in the field, and you have a multi-level functional location structure, all maintenance schedule lines and work orders for a functional location will be shown on the top level, and therefore the hours on a line might be added up from functional locations located at a lower level.

    If you insert the number *0* in the **Level** field, you'll see a detailed result showing all maintenance schedule lines and all work orders on all the functional location levels to which they're related.

1. Select **OK** to start the calculation.

1. In the **Group by...** groups, select the relevant buttons to show the required detail level of the calculation. In the following screenshot, the selected **Group by** buttons are highlighted in blue color. Select on a button to activate or deactivate it.

    ![Figure 1.](media/01-capacity-planning.png)

> [!NOTE]
> If you want to focus only on capacity planning regarding scheduled work orders, see [Calculate capacity load on scheduled work orders](../work-order-scheduling/calculate-capacity-load-on-scheduled-work-orders.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
