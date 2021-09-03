---
title: Supply schedule page
description: This topic provides information about Supply schedule page and its capabilities.
author: crytt
ms.date: 9/3/2021
ms.topic: article
ms.search.form: ReqSupplyDemandSchedule, ReqSupplyDemandScheduleFilters, ReqSupplyDemandItemDetails, ReqTransFuturesActionsPart, ReqSupplyDemandOverviewLegendPart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-06-09
ms.dyn365.ops.version: 10.0.20
---

# Supply schedule page

[!include [banner](../includes/banner.md)]

The **Supply schedule** page displays comprehensive overview of supply and demand for a product, or a product family filtered by a location, a master plan, and time periods. You can also use the **Supply schedule** page to create new orders, modify existing planned orders or run master planning.

## Open the Supply schedule page

You can open the **Supply schedule** page in any of the following ways:
- Go to **Master planning > Master planning > Supply schedule**, on the **Modify filter** dialog box (we will call it the filter) enter filter values like a master plan, a period template, a product and its dimensions or a product family, a site and a warehouse, and select **OK**.
- Go to **Product information management > Products > Released products**. Select or open a product. Then, on the Action Pane, on the **Plan** tab, in the **View** group, select **Supply schedule**. 
- Go to **Master planning > Setup > Demand forecasting > Item allocation keys**. Select an item allocation key that is used as a product family. Then, on the Action Pane, select **Supply schedule**.
- Go to **Master planning > Master planning > Planned orders**. Select or open a planned order. Then, on the Action Pane, on the **View** tab, in the **View** group, select **Supply schedule**.
 
> [!NOTE]
> When you open the Supply schedule page from a product, a product family or a planned order, you don't need to enter values into the filter, the system will use the default period template.

## Use the Supply schedule page

The **Supply schedule** page consists of the upper section, the **Period end inventory** FastTab and additional FastTab that become visible depending on the line selection in the upper section, and the FactBox pane. 

### Upper section

The upper section of the **Supply schedule** page contains a grid with data for a product or product family broken down by time periods defined by **Period template** value from the filter. The following information is displayed:

- **Period start inventory** line - Shows expected inventory balance as of the start of the period if all orders in the system are to take place.
- **Period end inventory** line - Shows expected inventory balance as of the end of the period if all orders in the system are to take place.
- **Period end pegged inventory** line - Shows the amount of the inventory as of the end of the period that is pegged against future.
- **Period net supply** line - Shows the difference between supply and demand in the period.
- **Minimum inventory** node - Shows safety stock for a product or product family. The node is displayed when there is a safety stock for the product or product family.
- **Demand** node - Shows demand for a product or product family grouped by transaction type. Demand transaction types include sales, transfers, inventory journals, etc. The node is displayed when there is a demand for the product or product family.
- **Supply** node - Shows supply for a product or product family grouped by transaction type. Supply transaction types include production, purchase, transfers, etc. The node is displayed when there is a supply for the product or product family.
 
You can use buttons located in the upper section of the **Supply schedule** page above the grid to perform following:

- **Expand/Collapse** - Expand or collapse a node (the **Demand** node, the **Supply** node, and underneath nodes. Each with [+] or [-] prefix).
- **New** - Depending on the selection, enter a forecast supply or create a planned order, a scheduled kanban, a production order, a purchase order, or a transfer order.
- **Master planning** - Run master planning. **Master plan** field value is defaulted from the filter.
- **Max. report as finished** - Open **Max. report as finished** page for the product that you define in the filter. 
- Update planned orders - Open Planned orders page that shows planned orders for the product or the product family products that you define in the filter.
- **Level** - Spread planned order according to the settings from the opened dialog.
- **Kanban rule** - Open the **Kanban rules** page for the product that you define in the filter. 
- **Material plan policy by location** - Open **Item coverage** page for the product that you define in the filter.

### FastTabs

The **Supply schedule** page contains following FastTabs:

- **Period end inventory** - Shows the period end inventory data in a graphical format.
- **Supply profile** - Shows the supply data in a graphical format. This FastTab becomes visible when you select a **Supply** node or a line underneath it in the upper section.
- **Summary** - Shows summary details related to the transaction type that you select in the upper section. For example, if you select **Sales** under the **Demand** node, the **Summary** FastTab will display sales orders related fields like **Requested sales order lines** or **Total amount**. And if you select **Production orders** under the **Supply > Production** node, the **Summary** FastTab will display production orders related fields like **Production orders** scheduled or **Total scheduled**. Field values will depend on the time period that you select in the upper section.
- **[Transaction type] - [Time period]**, for example **Sales orders - Backlog** or **Production orders - Week 37** - Shows orders in a period of time, depending on transaction type and time period that you select in the upper section.

### The Action Pane

The following commands are available on the Action Pane:

- **Modify filter** - Open **Modify filter** dialog box to update filter values and reopen **Supply schedule** page based on updated filter data.
- **Show delays** - Highlight the line in the upper section if there is a delayed order of that transaction type.

### The FactBox pane

The following FactBoxes are available on the **Supply schedule** page:

- **Item details** - Shows basic information about the product that you define in the filter. The FactBox will be empty when you define product family in the filter.
- **Actions** - Shows actions for the orders of the transaction type that you select in the upper section.
- **Delays** - Shows delays for the orders of the transaction type that you select in the upper section.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

