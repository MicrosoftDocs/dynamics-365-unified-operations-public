---
title: The Supply schedule page
description: This topic provides information about the Supply schedule page and its capabilities.
author: crytt
ms.date: 9/3/2021
ms.topic: article
ms.search.form: ReqSupplyDemandSchedule, ReqSupplyDemandScheduleFilters, ReqSupplyDemandItemDetails, ReqTransFuturesActionsPart, ReqSupplyDemandOverviewLegendPart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-06-09
ms.dyn365.ops.version: 10.0.22
---

# The Supply schedule page

[!include [banner](../includes/banner.md)]

The **Supply schedule** page displays a comprehensive overview of supply and demand for a product (or product family) filtered by location, master plan, and time periods. You can also use the **Supply schedule** page to create new orders, modify existing planned orders, and run master planning.

## Open the Supply schedule page

You can open the **Supply schedule** page in any of the following ways:

- Go to **Master planning \> Master planning \> Supply schedule** to open the **Modify filter** dialog. In the dialog, specify which plan and product you are looking for by entering filter values in the fields provided (this collection of values is referred to elsewhere in this topic as "the filter" or "the current filter"). Then select **OK**. <!-- KFM: I'm not sure what the "Period template" is; it might make sense to mention it's purpose explicitly here. -->
- Go to **Product information management \> Products \> Released products**. Select or open a product. Then, on the Action Pane, on the **Plan** tab, in the **View** group, select **Supply schedule**.
- Go to **Master planning \> Setup \> Demand forecasting \> Item allocation keys**. Select an item allocation key that is used as a product family. Then, on the Action Pane, select **Supply schedule**.
- Go to **Master planning \> Master planning \> Planned orders**. Select or open a planned order. Then, on the Action Pane, on the **View** tab, in the **View** group, select **Supply schedule**.

> [!NOTE]
> When you open the **Supply schedule** page from a product, product family, or planned order, you don't need to enter values into the filter; the system will use the default period template.

## Use the Supply schedule page

The **Supply schedule** page consists of the upper section and the **Period end inventory** FastTab, an additional FastTab that becomes visible depending on the line selected in the upper section, and the FactBox pane. <!-- KFM: Where is the "FactBox"? -->

### Upper section

The upper section of the **Supply schedule** page contains a grid with data for a product or product family broken down by time periods defined by **Period template** value from the filter. The following information is displayed:

- **Period start inventory** line – Shows the expected inventory balance as of the start of the period if all orders in the system are to take place.
- **Period end inventory** line – Shows the expected inventory balance as of the end of the period if all orders in the system are to take place.
- **Period end pegged inventory** line – Shows the amount of the inventory as of the end of the period that is pegged against future. <!-- KFM: Against future what? -->
- **Period net supply** line – Shows the difference between supply and demand in the period.
- **Minimum inventory** node – Shows safety stock for a product or product family. Select this node and then select the **Expand** or **Collapse** toolbar buttons to expand or collapse the node. The node is only displayed when there is a safety stock for the product or product family.
- **Demand** node – Shows demand for a product or product family grouped by transaction type. Select this node and then select the **Expand** or **Collapse** toolbar buttons to expand or collapse the node. Demand transaction types include sales, transfers, inventory journals, and so on. The node is only displayed when there is a demand for the product or product family.
- **Supply** node – Shows supply for a product or product family grouped by transaction type. Select this node and then select the **Expand** or **Collapse** toolbar buttons to expand or collapse the node. Supply transaction types include production, purchase, transfers, and so on. The node is only displayed when there is a supply for the product or product family.

Many of the toolbar commands, FactBox displays, and FastTab displays depend on what you have selected in the upper section. You'll typically select a transaction type by choosing one of the rows under the **Supply** or **Demand** node, and then choose a time period by selecting a specific column for your chosen row. <!-- KFM: I added this. Please confirm. -->

The toolbar provided in the upper section of the **Supply schedule** page (above the grid) provides the following commands:

- **Expand/Collapse** – Expands or collapses a selected node (such as the **Demand** node, **Supply** node, and their subnodes. (Nodes show a [+] or [-] prefix).
- **New** menu – Each of the entries in this menu opens a dialog or page that lets you add a specific type of item for the selection <!--KFM: It isn't clear how these commands relate-to/affect the "selection". What are we selecting (both transaction type and time period)? -->. Available entries include **Forecast supply**, **Planned order**, **Scheduled kanban**, **New production order**, **Purchase order**, and **Transfer order**.
- **Master planning** – Runs master planning. This opens a dialog where you can specify the plan to run. By default, the **Master plan** field is set to match the current filter.
- **Max. report as finished** – Opens the **Max. report as finished** page for the product defined in the current filter.
- **Update planned orders** – Opens the **Planned orders** page, which shows planned orders for the product or the product family defined in the current filter.
- **Level** – Spreads planned orders according to the settings from the opened dialog. <!--KFM: This isn't clear. Which dialog is this referring to? The command is always disabled for me. -->
- **Material plan policy by location** – Opens the **Item coverage** page for the product defined in the current filter.
- **Kanban rule** – Opens the **Kanban rules** page for the product defined in the current filter.

### FastTabs

The **Supply schedule** page can contain following FastTabs:

- **Period end inventory** – Shows the period end inventory data in a graphical format.
- **Supply profile** – Shows the supply data in a graphical format. This FastTab becomes visible when you select a **Supply** node or a line underneath it in the upper section.
- **Summary** – Shows summary details related to the transaction type that you select in the upper section. For example, if you select **Sales** under the **Demand** node, the **Summary** FastTab will display fields related to sales orders, such as **Requested sales order lines** or **Total amount**. If you select **Production orders** under the **Supply \> Production** node, the **Summary** FastTab will display fields related to production orders, such as **Production orders** scheduled or **Total scheduled**. Field values will depend on the time period that you select in the upper section. <!-- KFM: I don't understand this last sentence. How do I select a time period in the upper section? For me, Summary was often blank unless I selected something under a node, as described above. -->
- **[Transaction type] – [Time period]** (for example **Sales orders - Backlog** or **Production orders - Week 37**) – Shows orders in a period of time, depending on the transaction type and time period selected in the upper section. <!--KFM: I never saw this FastTab. Please clarify "Shows orders in a period of time" (placed orders, planned orders, other types of orders? How are they "in" a period of time?). Not sure how to select both a time period and transaction type at the same time in the upper section. -->

### The Action Pane

The following commands are available on the Action Pane:

- **Modify filter** – Opens the **Modify filter** dialog box, where you can update filter values and then reopen the **Supply schedule** page based on the updated filter settings.
- **Show delays** – Highlights the line in the upper section if there is a delayed order of that transaction type. <!--KFM: Do you mean the selected transaction type? This isn't clear. I couldn't get this to do anything. -->

### The FactBox pane

To view a FactBox, expand the **Related information** pane on the right edge of the page. The following FactBoxes are available on the **Supply schedule** page:

- **Item details** – Shows basic information about the product defined in the current filter. The FactBox will be empty if you have defined a product family in the filter.
- **Actions** – Shows actions for the orders of the transaction type selected in the upper section.
- **Delays** – Shows delays for the orders of the transaction type that you select in the upper section.
- **Supply overview legend** – <!--KFM: Description needed. -->

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
