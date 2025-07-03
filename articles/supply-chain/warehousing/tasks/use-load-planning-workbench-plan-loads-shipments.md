---
title: Plan loads and shipments using the outbound load planning workbench
description: Learn how to use the outbound load planning workbench to create a load for a sales order, including a step-by-step process for creating sales orders. 
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 06/07/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: WHSHistory, WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench, WHSLoadPlanningWorkbenchFilter
---

# Plan loads and shipments using the outbound load planning workbench

[!include [banner](../../includes/banner.md)]

This article shows how to use the outbound load planning workbench to create a load for a sales order. As a prerequisite we'll create the sales order first. This procedure is part of the daily work for the transportation coordinator. The demo data company used to create this procedure is USMF.

## Create a sales order

1. Go to the **Accounts receivable** \> **Orders** \> **All sales orders**.
2. Select **New**.
3. In the **Customer account** field, select the drop-down button to open the lookup.
4. Select account *US-004*.
5. Select **OK**.
6. In the **Item number** field, select the drop-down button to open the lookup.
7. Select item *A0001*. *A0001* is enabled for transportation management.  
8. In the **Site** field, select the drop-down button to open the lookup, then select an item.
9. In the **Quantity** field, enter a number.
10. In the **Warehouse** field, type *24* for this example. This warehouse is enabled for transportation management and warehouse management processes (WMS).  
11. Select **Save**.
12. Close the page.

## Create a new load

1. Go to the **Transportation management** \> **Planning** \> **Outbound load planning workbench**.
2. Select the **Sales lines** tab. Now you'll build the load for the sales order that you just created. Loads can be built based on supply and demand from purchase orders, transfer orders, and sales orders.  
3. On the Action Pane, select **Supply and demand**.
4. Select **To new load**.
5. In the **Load template ID** field, select the drop-down button to open the lookup. The Load template defines maximum measurements for weight and volume of the entire load. For example, the load template might represent the size of a container or truck. Select an item.
6. Select **OK**.

## Rate and route the load

1. Select **Rating and routing**.
2. Select **Rate route workbench**.
3. Select **Rate shop**.
4. In the list, find and select the desired record.
5. Select **Assign**.
6. Close the page.

## Load planning filters

You can set up custom filters to control which types of lines to show in the **Outbound load planning workbench**. For example, you can choose to only show fully reserved transfer order lines. Follow these steps to set up one or more load planning workbench filters.

1. Go to **Warehouse management** \> **Loads** \> **Outbound load planning workbench**. (You can also open the workbench from the **Sales orders**, **Transfer orders**, and **Outbound shipment orders** pages.)
1. On the Action Pane, open the **Filters** tab and select **Load planning filters**.
1. On the Action Pane, select **New** to add a new load planning filter to the grid. Then make the following settings for the new line:
    - **Load planning filter code** – Enter a unique name for the filter.
    - **Description** – Enter a short description of the filter.
    - **Load planning filter type** – Choose the type of lines the filter should apply to (*Load*, *Sales order*, *Transfer order*, *Shipment*, or *Outbound shipment orders*). For example, if you want to set up a filter that only shows fully reserved transfer order lines, select *Transfer order*.

1. On the Action Pane, select **Save**.
1. With the new filter selected in the grid, select **Edit query** on the Action Pane. A standard query editor opens, where you can define the filter criteria that you want to apply. Here's an example of how to set up a filter to show only fully reserved transfer order lines:
    1. Open the **Joins** tab. Select the *Transfer order lines* node and then select **Add table join** from the toolbar. Find and select the row with a **Relation** of *Relationship between the inventory transfer order line and the inventory transactions originator of the shipment transactions (Line number)* (with **Join mode** *1:n*). Then select **Select** on the toolbar.
    1. Select the new *Relationship between the inventory transfer order line and the inventory transactions originator of the shipment transactions* node and then select **Add table join** from the toolbar. Find and select the row with a **Relation** of *Inventory transactions originator (Inventory transactions originator)*. Then select **Select** on the toolbar.
    1. Select the new *Inventory transactions originator* node and then select **Add table join** from the toolbar. Make sure that **Show details** is set to *Yes*. Find and select the row with a **Relation** of *Inventory transactions (NotExist Record-ID)* and a **Relation source** of *InventTrans : InventTransOrigin*. Then select **Select** on the toolbar. Your **Joins** tab should now resemble the following screenshot.

        :::image type="content" source="../media/load-planning-workbench-query-joins.png" alt-text="Screenshot of the Joins tab with these settings applied":::

    1. Open the **Range** tab. Add a new row to the grid with the following settings:
        - **Table** – Select *Inventory transactions (NotExist)*.
        - **Field** – Select *Issue status*.
        - **Criteria** – Enter *!Reserved physical*, which means "not *Reserved physical*."

        These settings result in a filter that only includes transfer order lines with an inventory transactions status of *Reserved Physical*, which are the fully reserved lines. Your **Range** tab should now resemble the following screenshot.

          :::image type="content" source="../media/load-planning-workbench-query-range.png" alt-text="Screenshot of the Range tab with these settings applied":::

    1. Select **OK** to save the query.

1. Select the **Back** button to go back to the **Outbound load planning workbench** page.
1. Open the tab you created your filter for (for example, the **Transfer lines** tab). Then set **Supply and demand filter** to the filter you just created. The page is now filtered according to the criteria you defined for the selected filter.
1. If you'd like to apply the new filter by default when you open the workbench, then on the Action Pane, open the **Filters** tab and select **Set as default**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
