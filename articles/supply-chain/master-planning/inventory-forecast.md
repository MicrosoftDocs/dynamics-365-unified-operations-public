---
title: Inventory forecasts
description: Learn about the supply and demand forecast functionality that can be used to create inventory forecasts in Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/08/2021
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetailsExtended, ForecastSales, ForecastPurch, ForecastInvent
---

# Inventory forecasts

[!include [banner](../includes/banner.md)]

[!INCLUDE [demand-planning-banner](../includes/demand-planning-banner.md)]

This article describes how to view and create inventory forecasts. You can create and view supply and demand forecast lines for items, item groups, item allocation keys, customer accounts, customer groups, vendor accounts, and vendor groups.

For each forecast line, you can select the forecast model that is used. You can then specify the item or item group, plus the quantity or the transaction amount. You can also set up a time schedule for allocating the forecast quantity.

The supply and demand forecast lines produce an inventory forecast for the same combination of an item and a model. This inventory forecast represents a balance between the supply and demand that were entered for the same item. It can't be edited. The inventory forecast helps the inventory management team review expected changes to the on-hand inventory of an item during the upcoming period that has been forecasted.

After you enter your demand and/or supply, you can run forecast planning to calculate gross requirements for materials and capacity, and to generate planned orders.

## <a name="manual-entry"></a>View and manually enter forecast lines

Use this procedure to manually create forecast lines for products.

There are also other ways to create forecast lines:

- [Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md).
- [Import historical data for demand forecasts](import-historical-data.md).
- [Generate the forecast by using a Microsoft Azure Machine Learning web service](demand-forecasting-setup.md).
- [Import demand or supply forecast lines by using the data management framework (ForecastDemandForecastEntryStaging and ForecastSupplyForecastEntryStaging data entities)](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages).

As the table in step 1 shows, there are different ways to access the pages that are used.

1. Depending on the type of entity that you want to create a forecast for, and the type of forecast that you want to create, open a supply, demand, or inventory forecast page as described in the following table.

    | Entity | Instructions |
    |---|---|
    | Released products | <ol><li>Go to **Product information management \> Products \> Released products**.</li><li>Select the product to create a forecast for.</li><li>On the Action Pane, on the **Plan** tab, in the **Forecast** group, select **Demand forecast**, **Supply forecast**, or **Inventory forecast**, depending on the type of forecast that you want to work with.</li></ol> |
    | Released product variants | <ol><li>Go to **Product information management \> Products \> Released product variants**.</li><li>Select the variant to create a forecast for.</li><li>On the Action Pane, on the **Plan** tab, in the **Forecast** group, select **Demand forecast**, **Supply forecast**, or **Inventory forecast**, depending on the type of forecast that you want to work with.</li></ol> |
    | Item groups | <ol><li>Go to **Inventory management \> Setup \> Inventory \> Item groups**.</li><li>Select the item group to create a forecast for.</li><li>On the Action Pane, select **Forecasting \> Demand**, **Forecasting \> Supply**, or **Forecasting \> Inventory forecast**, depending on the type of forecast that you want to work with.</li></ol> |
    | Item allocation keys | <ol><li>Go to **Inventory management \> Setup \> Forecast**.</li><li>Select the item allocation key to create a forecast for.</li><li>On the Action Pane, select **Demand forecast**.</li></ol> |
    | Customers | <ol><li>Go to **Master planning \> Forecasting \> Manual forecast entry \> Customers**.</li><li>Select the customer to create a forecast for.</li><li>On the Action Pane, select **Define demand forecast**.</li></ol> |
    | Customer groups | <ol><li>Go to **Master planning \> Forecasting \> Manual forecast entry \> Customer groups**.</li><li>Select the customer group to create a forecast for.</li><li>On the Action Pane, select **Define demand forecast**.</li></ol> |
    | Vendors | <ol><li>Go to **Master planning \> Forecasting \> Manual forecast entry \> Vendors**.</li><li>Select the vendor to create a forecast for.</li><li>On the Action Pane, select **Entry** to open the **Supply forecast** page.</li></ol> |
    | Vendor groups | <ol><li>Go to **Master planning \> Forecasting \> Manual forecast entry \> Vendor groups**.</li><li>Select the vendor group to create a forecast for.</li><li>On the Action Pane, select **Entry** to open the **Supply forecast** page.</li></ol> | 
    | All lines | <ul><li>Go to **Master planning \> Forecasting \> Demand forecast lines** or **Master planning \> Forecasting \> Supply forecast lines**, depending on the type of forecast that you want to work with.</li></ul> |

    Depending on your selection, the **Supply forecast** or **Demand forecast** page appears. It shows any existing forecast lines for the record that you selected before you opened the page.

1. On the Action Pane, select **New** to add a forecast line to the grid in the upper part of the page.
1. On the new line, in the **Model** field, select the forecast model to use. Then enter other details as required, such as the item, item group, customer or vendor account or group, item quantity, or total transaction amount. For complete details about the fields that are available on the **Supply forecast** and **Demand forecast** pages, see the later sections in this article.
1. To distribute the forecast over the period, on the **Overview** tab, select **Allocate forecast** on the toolbar.
1. In the **Allocation** grid, review the time horizon and the time intervals that are used to distribute the forecast quantities.

## Supply forecast lines

The supply forecast lets you create a plan for items that must be purchased. It tells procurement and sourcing clerks what they are expected to order.

You can enter a supply forecast by item, item group, item allocation key, vendor, and vendor group. For information about all the ways to open the **Supply forecast** page for various entities and records, see the [View and manually enter forecast lines](#manual-entry) section earlier in this article.

The upper part of the **Supply forecast** page provides a grid of supply forecast lines and a set of tabs that you can use to view and set more information about a selected forecast line. The lower part of the page provides an **Allocation** grid.

The following subsections describe all the fields that are available on each tab, and all the commands that are available on the page's Action Pane and on the toolbar on the **Overview** tab.

### Action Pane commands on the Supply forecast page

The following table describes the commands that are available on the Action Pane of the **Supply forecast** page.

| Command | Description |
|---|---|
| Save | Save your current settings. |
| Edit | Enable settings on the page to be edited. |
| New | Add a forecast line to the upper grid. |
| Delete | Remove the selected forecast line from the upper grid. |
| Forecast balances | View forecast balances that have been calculated for the selected line's model ID for the current fiscal year. The balances are split by period (month). |
| Cash flow forecasts | View forecast transactions that have been allocated to the general ledger. Learn more in [Cash flow forecasting](../../finance/cash-bank-management/cash-flow-forecasting.md). |
| Inventory \> Display dimensions | Select the inventory dimensions that should be shown in the grid on the **Overview** tab. |

### Toolbar commands on the Overview tab of the Supply forecast page

The following table describes the commands that are available on the toolbar on the **Overview** tab of the **Supply forecast** page.

| Command | Description |
|---|---|
| Allocate forecast | If you're using an allocation method, generate the individual schedule lines for the forecast transaction. The line's quantity is then distributed by date (according to the selected time intervals), quantity, and amount for the whole time horizon. (See the [Allocate forecast](#allocate-forecast) section later in this article.) |
| Bulk update | Open the **Edit forecast transactions** page. (See the [Bulk update forecast transactions](#bulk-update) section later in this article.) |
| Inventory forecast | Open a view of the **Inventory forecast** page that is filtered for the selected item/model combination. (See the [Inventory forecast](#inventory-forecast) section later in this article.) |
| Create item requirement | Open a dialog box where you can create item requirements, and sales order or item journal lines for project-related forecast transactions. Although this command is available for both supply forecast lines and demand forecast lines, it can't be used on the **Supply forecast** page. |

### The Overview tab on the Supply forecast page

The following table describes the fields on the **Overview** tab of the **Supply forecast** page.

| Field | Description |
|---|---|
| **Model** | The forecast model that the transaction is associated with. |
| **Date** | The start date of the transaction. |
| **Vendor account** | The vendor account that the transaction is associated with. |
| **Vendor group** | The vendor group that the transaction is associated with. |
| **Item number** | The identifier of the item. |
| **Item group** | The item group that the transaction is associated with. |
| **Item allocation key** | The item allocation key that is associated with the forecast. |
| **CW quantity** | The forecast quantity in the specified catch-weight unit. |
| **CW unit** | The catch-weight unit that the item is purchased in. The value is automatically retrieved from the item setup. |
| **Quantity** | The forecast quantity in the specified purchase unit. |
| **Unit** | The unit that the item is purchased in. The value is automatically retrieved from the item setup. However, you can modify it if unit conversions are set up. |
| **Amount** | The gross amount, minus discounts, that the forecast transaction contributes to the forecast. |
| **Currency** | The currency that is used for the forecast transaction. The default currency is automatically entered, but you can select a different currency. |
| (Other dimensions) | Additional dimensions can be shown as columns in the grid. To select the additional dimensions that are shown, select **Display dimensions** on the Action Pane. |

### The General tab on the Supply forecast page

The **General** tab shows more information about the line that is currently selected on the **Overview** tab. Some of this information is repeated from the **Overview** tab. The following table describes the fields that are unique to the **General** tab.

| Field | Description |
|---|---|
| Report | Set this option to *Yes* to include the transaction in reporting. |
| Comments | Enter any comments that you have about the forecast transaction. |
| Active | Select this checkbox to include the transaction in budget reporting. |
| Include in cash flow forecasts | Select this checkbox to allocate the forecast transaction to the general ledger. The setting of this checkbox can't be modified for reporting transactions. |
| Sales tax group | The tax group that is used to specify tax for the forecast transaction. |
| Item sales tax group | The item tax group that is used to specify tax for the forecast transaction. |
| Method | <p>Select the method that is used to allocate the forecast transaction:</p><ul><li>**None** – No allocation occurs.</li><li>**Period** – Forecast the same quantity for each period. If you select this value, specify a quantity in the **Per** field and a unit of time in the **Unit** field.</li><li>**Key** – Allocate the forecast according to the period allocation key that you specify in the **Period key** field. You can use this method when you want seasonal variation to be considered.</li></ol>|
| Per | <p>Enter the number of time intervals into the future that the forecast extends. This field is available only if you select *Period* in the **Method** field.</p><p>For example, you select *Period* in the **Method** field, enter *1* in the **Per** field, and select *Months* in the **Unit** field. In the **End** field, you specify an end date that extends one year into the future. In this case, one forecast line will be created for each month of the upcoming year, based on the item and quantity that are specified on the header line.</p> |
| Unit | Select the unit of the time interval: *Days*, *Months*, or *Years*. Allocation then corresponds to the number of days, months, or years that you specify in the **Per** field.|
| Period key | Specify the period allocation key. |
| End | Specify the end date when you use the **Per** and **Unit** fields. |

### The Item tab on the Supply forecast page

The **Item** tab shows more item information about the line that is currently selected on the **Overview** tab.

The grid at the top of the **Item** tab repeats item information that is also shown on the **Overview** tab. In addition, it includes the **Unit price** field, which shows the purchase price for the number of units that is specified in the **Unit** field. The unit price is automatically retrieved from the item setup, but you can modify it.

The fields below the grid provide more item details. Some of this information is repeated from the **Overview** tab. The following table describes the fields that are unique to the **Item** tab.

| Field | Description |
|---|---|
| Price unit | The number of units that the purchase price applies to. The value is automatically retrieved from the Items table, but you can modify it. |
| Charges on purchases | Fixed charges on the purchase price. The charges are independent of the quantity. |
| Discount percentage | The discount as a percentage. |
| Discount amount | The discount as an amount per sales unit. |
| Gross amount | The amount when no discounts are applied. |
| Quantity | The transaction quantity in the item's inventory unit. |
| Sub-BOM | The bill of materials (BOM) number of a specific sub-BOM. |
| Subroute | The route number of a specific sub-route. |

### The Financial dimensions tab on the Supply forecast page

The **Financial dimensions** tab shows all the financial dimension values for the line that is currently selected on the **Overview** tab.

### The Inventory dimensions tab on the Supply forecast page

The **Inventory dimensions** tab shows all the inventory dimension values for the line that is currently selected on the **Overview** tab.

### The Allocation grid on the Supply forecast page

If you're using an item allocation key, or if you've entered an item forecast for one or more future periods, you can allocate the forecast by selecting **Allocate forecast** on the toolbar on the **Overview** tab. The quantity is then distributed in the manner that is indicated by the lines in the **Allocation** grid.

## Demand forecast lines

The demand forecast lets you enter or generate demand for a customer. It helps sales and marketing clerks inform master planning clerks about the expected demand during the upcoming forecast period.

You can enter a demand forecast by item, item group, item allocation key, customer, and customer group. For information about all the ways to open the **Demand forecast** page for various entities and records, see the [View and manually enter forecast lines](#manual-entry) section earlier in this article.

The upper part of the **Demand forecast** page provides a grid of demand forecast lines and a set of tabs that you can use to view and set more information about a selected forecast line. The lower part of the page provides an **Allocation** grid.

The following subsections describe all the fields that are available on each tab, and all the commands that are available on the page's Action Pane and on the toolbar on the **Overview** tab.

### Action Pane commands on the Demand forecast page

The following table describes the commands that are available on the Action Pane of the **Demand forecast** page.

| Command | Description |
|---|---|
| Save | Save your current settings. |
| Edit | Enable settings on the page to be edited. |
| New | Add a forecast line to the upper grid. |
| Delete | Remove the selected forecast line from the upper grid. |
| Forecast balances | View forecast balances that have been calculated for the selected line's model ID for the current fiscal year. The balances are split by period (month). |
| Cash flow forecast | View forecast transactions that must be allocated to the general ledger. Learn more in [Cash flow forecasting](../../finance/cash-bank-management/cash-flow-forecasting.md). |
| Display dimensions | Select the product, storage, and tracking dimensions that should be shown in the grid on the **Overview** tab. |
| General ledger preview | View the general ledger entries for the selected transaction. |
| Transfer quotation lines | Transfer quotation lines to the selected project. |

### Toolbar commands on the Overview tab of the Demand forecast page

The following table describes the commands that are available on the toolbar on the **Overview** tab of the **Demand forecast** page.

| Command | Description |
|---|---|
| Allocate forecast | If you're using an allocation method, generate the individual schedule lines for the forecast transaction. The line's quantity is then distributed by date (according to the selected time intervals), quantity, and amount for the whole time horizon. (See the [Allocate forecast](#allocate-forecast) section later in this article.)|
| Bulk update | Open the **Edit forecast transactions** page. (See the [Bulk update forecast transactions](#bulk-update) section later in this article.) |
| Inventory forecast | Open a view of the **Inventory forecast** page that is filtered for the selected item/model combination. (See the [Inventory forecast](#inventory-forecast) section later in this article.) |
| Create item requirement | Open a dialog box where you can create item requirements, and sales order or item journal lines for project-related forecast transactions. |

### The Overview tab on the Demand forecast page

The following table describes the fields on the **Overview** tab of the **Demand forecast** page.

| Field | Description |
|---|---|
| **Task name** | The name of the batch task that was used to create the forecast line. |
| **Model** | The forecast model that the transaction is associated with. |
| **Date** | The start date of the transaction. |
| **Customer account** | The customer account that the transaction is associated with. |
| **Customer group** | The customer group that the transaction is associated with. |
| **Item number** | The identifier of the item. |
| **Product name** | The description of the item. |
| **Item allocation key** | The item allocation key that is used during inventory forecast allocation. |
| **Sales quantity** | The transaction quantity in the specified sales unit. |
| **Unit** | The unit that the item is sold in. |
| **Amount** | The gross amount, excluding discounts, that the forecast transaction contributes to the forecast. |
| **Sales price** | The sales price for the number of units that is specified in the **Price unit** field. The value is retrieved from the item setup, but you can modify it. |
| **Sales currency** | The currency that is used for the forecast transaction. The default currency is automatically entered, but you can select a different currency. |
| **CW quantity** | The forecast quantity in the specified catch-weight unit. |
| **CW unit** | The catch-weight unit that the item is sold in. The value is automatically retrieved from the item setup. |
| (Other dimensions) | Additional product, storage, and tracking dimensions can be shown as columns in the grid. To select the additional dimensions that are shown, select **Display dimensions** on the Action Pane. |

### The General tab on the Demand forecast page

The **General** tab shows more information about the line that is currently selected on the **Overview** tab. Some of this information is repeated from the **Overview** tab. The following table describes the fields that are unique to the **General** tab.

| Field | Description |
|---|---|
| Demand forecast sequence number | The unique number of the demand forecast line. This number is generated by using the number sequence that is selected for demand forecasts on the **Master planning parameters** page. |
| Item group | The item group that the transaction is associated with. |
| Report | Set this option to *Yes* to include the transaction in reporting. |
| Comments | Enter any comments that you have about the forecast transaction. |
| Active | Select this checkbox to include the transaction in budget reporting. The setting of this checkbox can't be modified for reporting transactions. |
| Include in cash flow forecasts | Select this checkbox to allocate the forecast transaction to the general ledger. The setting of this checkbox can't be modified for reporting transactions. Learn more in [Cash flow forecasting](../../finance/cash-bank-management/cash-flow-forecasting.md). |
| Sales tax group | The tax group that is used to specify tax for the forecast transaction. |
| Item sales tax group | The item tax group that is used to specify tax for the forecast transaction. |
| Method | <p>Select the method that is used to allocate the forecast transaction:</p><ul><li>**None** – No allocation occurs.</li><li>**Period** – Forecast the same quantity for each period. If you select this value, specify a quantity in the **Per** field and a unit of time in the **Unit** field.</li><li>**Key** – Allocate the forecast according to the period allocation key that you specify in the **Period key** field. You can use this method when you want seasonal variation to be considered.</li><ul>|
| Per | <p>Enter the number of time intervals into the future that the forecast extends. This field is available only if you select *Period* in the **Method** field.</p><p>For example, you select *Period* in the **Method** field, enter *1* in the **Per** field, and select *Months* in the **Unit** field. In the **End** field, you specify an end date that extends one year into the future. In this case, one forecast line will be created for each month of the upcoming year, based on the item and quantity that are specified on the header line. |
| Unit | Select the unit of the time interval: *Days*, *Months*, or *Years*. Allocation then corresponds to the number of days, months, or years that you specify in the **Per** field.|
| Period key | Specify the period allocation key that is used to allocate the forecast. Learn more in [Budget planning data allocation](../../finance/budgeting/budget-planning-data-allocation.md). |
| End | Specify the end date when you use the **Per** and **Unit** fields. |

### The Item tab on the Demand forecast page

The **Item** tab shows more item information about the line that is currently selected on the **Overview** tab. Some of this information is repeated from the **Overview** tab. The following table describes the fields that are unique to the **Item** tab.

| Field | Description |
|---|---|
| Price unit | The number of sales units that the sales price applies to. The value is automatically retrieved from the Items table, but you can modify it. |
| Sales charges | Fixed charges on the sales price. The charges are independent of the quantity. |
| Cost price | The cost for the current forecast transaction per inventory unit. The value is retrieved from the Items table, but you can modify it. |
| Discount percentage | The discount as a percentage. |
| Discount amount | The discount as an amount per sales unit. |
| Gross amount | The amount when no discounts are applied. |
| Inventory quantity | The transaction quantity in the item's inventory unit. |
| Use specific BOM | The BOM number of a specific BOM. |
| Use specific route | The route number of a specific sub-route. |

### The Project tab on the Demand forecast page

The **Project** tab shows more project information about the line that is currently selected on the **Overview** tab. Some of this information is repeated from the **Overview**, **General**, or **Item** tab. The following table describes the fields that are unique to the **Project** tab.

| Field | Description |
|---|---|
| Project date | The date of the demand forecast transaction. |
| Project ID | The identifier of the project that is referenced by the current transaction. |
| Funding source | The funding source that the demand forecast is associated with. |
| Activity number | The activity that is associated with the demand forecast transaction. |
| Category | The cost category of the current transaction. |
| Line property | The status that the transaction is attached to. |
| Transaction ID | The system identifier for the demand forecast transaction. |
| Cost amount | The amount of the demand forecast transaction. |
| Unit price | The price per unit. |
| Modified By | The identifier of the worker who last modified the selected transaction. |
| Invoice date | Enter the expected invoice date. |
| Elimination date | View or modify the elimination date. When the forecast is created, the elimination date is set to the end date of the project. If the project has no end date, the project date is applied. This field applies to fixed-price projects and investment projects. |
| Cost payment date | Enter the expected date of the purchase payment. |
| Sales payment date | Enter the expected date of the sales payment. |

### The Financial dimensions tab on the Demand forecast page

The **Financial dimensions** tab shows all the financial dimension values for the line that is currently selected on the **Overview** tab.

### The Inventory dimensions tab on the Demand forecast page

The **Inventory dimensions** tab shows all the inventory dimension values for the line that is currently selected on the **Overview** tab.

### The Allocation grid on the Demand forecast page

If you're using an item allocation key, or if you've entered an item forecast for one or more future periods, you can allocate the forecast by selecting **Allocate forecast** on the toolbar on the **Overview** tab. The quantity is then distributed in the manner that is indicated by the lines in the **Allocation** grid. (See the [Allocate forecast](#allocate-forecast) section later in this article.)

## <a name="inventory-forecast"></a>Inventory forecast

The supply and demand forecast lines pages have an **Inventory forecast** button that opens a view of the **Inventory forecast** page that is filtered for the same item/model combination. The inventory forecast represents a balance between the supply and the demand that were entered for the same item. It can't be edited. The inventory forecast helps the inventory management team review expected changes to the on-hand inventory of an item during the upcoming period that has been forecasted.

### The Action Pane on the Inventory forecast page

The following table describes the commands that are available on the Action Pane of the **Inventory forecast** page.

| Action | Description |
|---|---|
| Supply forecast | Open a view of the **Supply forecast** page that is filtered for the same item/model/date combination. |
| Demand forecast | Open a view of the **Demand forecast** page that is filtered for the same item/model/date combination. |
| Inventory \> Display dimensions | Select the product, storage, and tracking dimensions that should be shown in the **Overview** grid. |

### The grid on the Inventory forecast page

The following table describes the fields in the grid on the **Inventory forecast** page.

| Field | Description |
|---|---|
| **Model** | The forecast model that the transaction is associated with. |
| **Item number** | The identifier of the item. |
| **Budget date** | The date of the forecast transaction. |
| **Forecast type** | The source of the transaction (*Demand forecast* or *Supply forecast*). |
| **CW quantity** | The forecast quantity in the catch-weight unit. |
| **Quantity** | The forecast quantity in the inventory unit. |
| **CW Accumulated** | The accumulated forecast quantity in the catch-weight unit when multiple forecast lines have been accumulated for the same item. |
| **Sub-BOM** | The BOM number of a specific sub-BOM. |
| **Subroute** | The route number of a specific sub-route. |
| (Other dimensions) | Additional dimensions can be shown as columns in the grid. To select the additional dimensions that are shown, select **Inventory \> Display dimensions** on the Action Pane. |

## <a name="allocate-forecast"></a>Allocate forecast

Use the following procedure to process selected forecast transaction lines. When you allocate a forecast, the quantity is then distributed as indicated by the lines in the **Allocation** grid.

1. Depending on the type of entity that you're creating a forecast for, and the type of forecast that you want to create, open a supply or demand forecast page as described in [View and manually enter forecast lines](#manual-entry).
1. On the supply or demand forecast lines page, select a forecast line, and then, on the **Overview** tab, select **Allocate forecast** on the toolbar.
1. In the **Allocate forecast** dialog box, set the fields that are described in the following table. (The value that you select in the **Method** field determines that other fields that are available.)

    | Field | Description |
    |---|---|
    | Method | <p>Select the method that is used to allocate the forecast transaction:</p><ul><li>**None** – No allocation occurs.</li><li>**Period** – Forecast the same quantity for each period. If you select this value, specify a quantity in the **Per** field and a unit of time in the **Unit** field.</li><li>**Key** – Allocate the forecast according to the period allocation key that you specify in the **Period key** field. You can use this method when you want seasonal variations to be considered.</li><ul>|
    | Per | <p>Enter the number of time intervals into the future that the forecast extends. This field is available only if you select *Period* in the **Method** field.</p><p>For example, you select *Period* in the **Method** field, enter *1* in the **Per** field, and select *Months* in the **Unit** field. Then, in the **End** field, you specify an end date one year into the future. In this case, one forecast line will be created for each month of the upcoming year, based on the item and quantity that are specified on the header line. |
    | Unit | Select the unit of the time interval: *Days*, *Months*, or *Years*. Allocation then corresponds to the number of days, months, or years that you specify in the **Per** field.|
    | Period key | Specify the period allocation key that is used to allocate the forecast. Learn more in [Budget planning data allocation](../../finance/budgeting/budget-planning-data-allocation.md). |
    | End | Specify the end date that applies to your settings in the **Per** and **Unit** fields. |

1. Select **OK** to confirm your settings.
1. You can review the results on the **Allocation** tab for the same line.

## <a name="bulk-update"></a>Bulk update forecast transactions

Use this procedure to process existing forecast transaction lines. You can copy, edit, and delete forecast transaction lines.

1. On the supply or demand forecast lines page, select **Bulk update**.
1. In the dialog box, select **Filter**.
1. On the **Range** tab, select the criteria that identify the source forecast data that you want to copy, edit, or delete. This data might include the forecast model, item number, and customer account.
1. Select **OK** to confirm your selection.

    After the data is selected, you can use the **Edit forecast transactions** dialog box to define how you want to copy, edit, or delete it.

    > [!NOTE]
    > The filtering step is a prerequisite for using the **Bulk edit** functionality. If you skip it, the program selects and updates **all** forecast lines. Therefore, you might unintentionally cause duplication or removal of transactions.

1. In the **Management** section, select whether you want to copy, update, or delete the selected forecast transactions.
1. Use the **Modifications in field** section to change the parameters of the forecast. Select the checkbox for a parameter, and then select among the available options. For example, select the **Model** checkbox, and then select a forecast model number. Existing forecast lines are copied to the selected forecast model.
1. Use the **Change of period** section to move the start and end dates of the forecast forward or backward. Select the checkbox, and then use the quantity and period fields to define how the forecast dates should be moved. You can enter a negative quantity to move the start date forward (that is, make it earlier).

    For example, to delay the forecast transaction start date by six months, select the checkbox, enter *6* as the quantity, and select *Months* as the period.

1. Use the **Correct field** section to update the actual forecast data. In the **Field** field, select the criterion that you want to change. In the **Factor** field, enter a multiplication factor to apply to the selected criterion, or enter a constant to add or subtract. For example, select *Quantity* as the criterion, and enter a factor of *1.5* to multiply the item quantity by 1.5. Alternatively, enter a constant of *-25* to decrease the item quantity by 25 units.
1. Use the **Financial dimensions** section to update the financial dimensions of forecast lines. Select the financial dimensions that you want to change, and then enter a value to apply to the selected dimensions.
1. Select **OK** to apply your changes.

## Use forecasts with master planning

After you enter your demand forecast and/or supply forecast, you can include the forecasts during master planning to account for expected demand and/or supply in your master planning run. When forecasts are included in master planning, gross requirements for materials and capacity are calculated, and planned orders are generated.

### Set up a master plan to include an inventory forecast

To set up a master plan so that it includes an inventory forecast, follow these steps.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select an existing plan, or create a new plan.
1. On the **General** FastTab, set the following fields:

    - **Forecast model** – Select the forecast model to apply. This model will be considered when a supply suggestion is generated for the current master plan.
    - **Include supply forecast** – Set this option to *Yes* to include the supply forecast in the current master plan. If you set it to *No*, supply forecast transactions won't be included in the master plan.
    - **Include demand forecast** – Set this option to *Yes* to include the demand forecast in the current master plan. If you set it to *No*, demand forecast transactions won't be included in the master plan.
    - **Method used to reduce forecast requirements** – Select the method that should be used to reduce forecast requirements. Learn more in [Forecast reduction keys](planning-optimization/demand-forecast.md#reduction-keys).

1. On the **Time fences in days** FastTab, you can set the following fields to specify the period that the forecast is included during:

    - **Forecast plan** – Set this option to *Yes* to override the forecast plan time fence that originates from the individual coverage groups. Set it to *No* to use the values from the individual coverage groups for the current master plan.
    - **Forecast time period** – If you set the **Forecast plan** option to *Yes*, specify the number of days (from today's date) that the demand forecast should be applied.

    > [!IMPORTANT]
    > The **Forecast plan** option isn't supported with Planning Optimization.

### Run a master plan that includes an inventory forecast

To run a master plan that includes an inventory forecast, follow these steps.

1. Go to **Master planning \> Workspaces \> Master planning**.
1. In the **Master plan** field, enter or select the master plan that you set up in the previous procedure.
1. On the **Master planning** tile, select **Run**.
1. In the **Master planning** dialog box, set the **Track processing time** option to *Yes*.
1. In the **Number of threads** field, enter a number.
1. On the **Records to include** FastTab, select **Filter**.
1. A standard query editor dialog box appears. On the **Range** tab, select the row where the **Field** field is set to *Item number*.
1. In the **Criteria** field, select the item number to include in the plan.
1. Select **OK**.

To view the requirements that are calculated, open the **Gross requirement** page. For example, on the **Released products** page, on the Action Pane, on the **Plan** tab, in the **Requirements** group, select **Gross requirement**.

To view the planned orders that are generated, go to **Master planning \> Common \> Planned orders**, and select the appropriate forecast plan.

## Related information

- [Demand forecasting overview](introduction-demand-forecasting.md)
- [Demand forecasting setup](demand-forecasting-setup.md)
- [Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)
- [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)
- [Master planning with demand forecasts](planning-optimization/demand-forecast.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
