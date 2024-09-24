---
title: Supply schedule
description: Learn about the Supply schedule page and its capabilities, including outlines on opening the supply schedule page and using the supply schedule page.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 9/3/2021
ms.reviewer: kamaybac
ms.search.form: ReqSupplyDemandSchedule, ReqSupplyDemandScheduleFilters, ReqSupplyDemandItemDetails, ReqTransFuturesActionsPart, ReqSupplyDemandOverviewLegendPart
---

# Supply schedule

[!include [banner](../includes/banner.md)]

The **Supply schedule** page shows a comprehensive overview of supply and demand for a product or product family. The information is filtered by location, master plan, and periods. You can also use the page to create new orders, modify existing planned orders, and run master planning.

## Open the Supply schedule page

You can open the **Supply schedule** page in any of the following ways:

- Go to **Master planning \> Master planning \> Supply schedule**. In the **Modify filter** dialog box, specify the plan and product that you're looking for by entering filter values in the fields that are provided. (In the rest of this article, the collection of filter values that you enter is referred to as "the filter" or "the current filter.") When you've finished, select **OK**.
- Go to **Product information management \> Products \> Released products**. Select or open a product. Then, on the Action Pane, on the **Plan** tab, in the **View** group, select **Supply schedule**.
- Go to **Master planning \> Setup \> Demand forecasting \> Item allocation keys**. Select an item allocation key that is used as a product family. Then, on the Action Pane, select **Supply schedule**.
- Go to **Master planning \> Master planning \> Planned orders**. Select or open a planned order. Then, on the Action Pane, on the **View** tab, in the **View** group, select **Supply schedule**.

> [!NOTE]
> When you open the **Supply schedule** page from a product, product family, or planned order, you don't have to enter filter values. The system will use the default period template.

## Use the Supply schedule page

The **Supply schedule** page consists of an upper section, the **Period end inventory** FastTab, an additional FastTab that becomes visible, based on the line that is selected in the upper section, and the FactBox pane. (To open the FactBox pane and view a FactBox, select **Related information** on the right edge of the page.)

### Upper section

The upper section of the **Supply schedule** page contains a grid that shows the following data for a product or product family. This data is broken down by periods that are defined by the **Period template** value from the filter.

- **Period start inventory** – This line shows the expected inventory balance at the start of the period if all orders in the system occur.
- **Period end inventory** – This line shows the expected inventory balance at the end of the period if all orders in the system occur.
- **Period end pegged inventory** – This line shows the amount of inventory at the end of the period that is pegged against future demand.
- **Period net supply** – This line shows the difference between supply and demand in the period.
- **Minimum inventory** – This node shows safety stock for a product or product family. To expand or collapse this node, select it, and then select **Expand** or **Collapse** on the toolbar. This node is shown only when there is safety stock for the product or product family.
- **Demand** – This node shows demand for a product or product family. The demand is grouped by transaction type. To expand or collapse this node, select it, and then select **Expand** or **Collapse** on the toolbar. Demand transaction types include sales, transfers, and inventory journals. This node is shown only when there is demand for the product or product family.
- **Supply** – This node shows supply for a product or product family. The supply is grouped by transaction type. To expand or collapse this node, select it, and then select **Expand** or **Collapse** on the toolbar. Supply transaction types include production, purchase, and transfers. This node is shown only when there is supply for the product or product family.

Many of the available toolbar buttons, FactBox displays, and FastTab displays depend on your selections in the upper section. Typically, you will choose a transaction type by selecting one of the rows under the **Supply** or **Demand** node. You will then choose a period by selecting a specific column for the selected row.

The toolbar above the grid in the upper section of the **Supply schedule** page provides the following buttons:

- **Expand/Collapse** – Expand or collapse a selected node, such as the **Demand** node, the **Supply** node, and their subnodes. (Nodes show a **\[+\]** or **\[-\]** prefix to indicate whether they are currently collapsed or expanded.)
- **New** – Open a menu where each command, in turn, opens a dialog box or page that lets you add a specific type of item for the selection. Available commands include **Forecast supply**, **Planned order**, **Scheduled kanban**, **New production order**, **Purchase order**, and **Transfer order**.
- **Master planning** – Run master planning. A dialog box appears, where you can specify the plan to run. By default, the **Master plan** field is set to match the current filter.
- **Max. report as finished** – Open the **Max. report as finished** page for the product that is defined in the current filter.
- **Update planned orders** – Open the **Planned orders** page, which shows planned orders for the product or product family that is defined in the current filter.
- **Level** – Spread planned orders according to the settings from the dialog box that appears.
- **Material plan policy by location** – Open the **Item coverage** page for the product defined in the current filter.
- **Kanban rule** – Open the **Kanban rules** page for the product that is defined in the current filter.

### FastTabs

The **Supply schedule** page can contain following FastTabs:

- **Period end inventory** – This FastTab shows the period end inventory data in a graphical format.
- **Supply profile** – This FastTab shows the supply data in a graphical format. It becomes visible when you select a **Supply** node or a line below it in the upper section.
- **Summary** – This FastTab shows summary details that are related to the transaction type that you selected in the upper section. For example, if you select **Sales** under the **Demand** node, this FastTab shows fields that are related to sales orders, such as **Requested sales order lines** or **Total amount**. If you select **Production orders** under the **Production** subnode of the **Supply** node, this FastTab shows fields that are related to production orders, such as **Production orders scheduled** or **Total scheduled**. Field values depend on the period that you selected in the upper section. 
- **\[Transaction type\] - \[Period\]** – This FastTab shows orders for the transaction type and period that you selected in the upper section. The name of the FastTab reflects those selections. For example, it might be named **Sales orders - Backlog** or **Production orders - Week 37**.

### Action Pane

The following buttons are available on the Action Pane:

- **Modify filter** – Open the **Modify filter** dialog box, where you can update filter values and then reopen the **Supply schedule** page, which reflects the updated filter settings.
- **Show delays** – Highlight the relevant lines in the upper section if there is a delayed order of that transaction type.

### FactBox pane

To open the FactBox pane and view a FactBox, select **Related information** on the right edge of the page. The following FactBoxes are available on the **Supply schedule** page:

- **Item details** – This FactBox shows basic information about the product that is defined in the current filter. It's blank if you defined a product family in the filter.
- **Actions** – This FactBox shows actions for the orders of the transaction type that you selected in the upper section.
- **Delays** – This FactBox shows delays for the orders of the transaction type that you selected in the upper section.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
