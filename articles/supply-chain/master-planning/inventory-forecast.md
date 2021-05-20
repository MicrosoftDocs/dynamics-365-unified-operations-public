---
title: Supply and demand forecast
description: This topic describes the supply and demand forecast functionality that can be used to create inventory forecast in Microsoft Dynamics 365 Supply Chain Management.  
author: crytt
ms.date: 05/12/2021
ms.topic: article
ms.search.form: EcoResProductDetailsExtended, ForecastSales, ForecastPurch
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-05-12
ms.dyn365.ops.version: AX 7.0.0
---

# Supply and demand forecast

[!include [banner](../includes/banner.md)]

This topic describes how to view and create inventory forecasts. You can create and view supply and demand forecast lines for items, item groups, item allocation keys, customer accounts, customer groups, vendor accounts, and vendor groups.

For each forecast line, you can select the forecast model to use and then specify the item or item group plus the quantity or the transaction amount. You can also set up a time schedule for allocating the forecast quantity.

<!-- KFM: Let's add a mention here about the inventory forecast. -->

<a name="manual-entry"></a>

## View and enter forecast lines manually
<!-- KFM: How else can a forecast be created, besides "manually"? Is there also an automatic way? If so, mention it here or add a new section that briefly describes how it works. -->

Use this procedure to create new forecast lines for products. You can refer to the information in the table below on other ways to access these pages (instead of the first two steps).

1. Depending on which type of entity you want to create a forecast for, and which type of forecast you want to create, open a supply, demand, or inventory forecast page as described in the following table.
    | **Entity** | **Instructions** |
    | --- | --- |
    | Released products | <ol><li>Go to  **Product information management > Products > Released products**.</li><li>Select the product you want to create a forecast for.</li><li>On the Action Pane, open the **Plan** tab and, from the **Forecast** group, select **Demand forecast**,  **Supply forecast**, or **Inventory forecast** depending on which type of forecast you want to work with.</li></ol> |
    | Released product variants | <ol><li>Go to  **Product information management > Products > Released product variants**.</li><li>Select the variant you want to create a forecast for.</li><li>On the Action Pane, open the **Plan** tab and, from the **Forecast** group, select **Demand forecast**,  **Supply forecast**, or **Inventory forecast** depending on which type of forecast you want to work with.</li></ol> |
    | Item groups | <ol><li>Go to **Inventory management > Setup > Inventory > Item groups**.</li><li>Select the item group you want to create a forecast for.</li><li>On the Action Pane, select **Forecasting \> Demand**,  **Forecasting \> Supply**, or **Forecasting \> Inventory forecast**, depending on which type of forecast you want to work with.</li></ol> |
    | Item allocation keys | <ol><li>Go to **Inventory management > Setup > Forecast**.</li><li>Select the item allocation key you want to create a forecast for.</li><li>On the Action Pane, select **Demand forecast**.</li></ol> |
    | Customers | <ol><li>Go to **Master planning > Forecasting > Manual forecast entry > Customers**.</li><li>Select the customer you want to create a forecast for.</li><li>On the Action Pane, select **Define demand forecast**.</li></ol> |
    | Customer groups | <ol><li>Go to **Master planning > Forecasting > Manual forecast entry > Customer groups**.</li><li>Select the customer group you want to create a forecast for.</li><li>On the Action Pane, select **Define demand forecast**.</li></ol> |
    | Vendors | <ol><li>Go to **Master planning > Forecasting > Manual forecast entry > Vendors**.</li><li>Select the vendor you want to create a forecast for.</li><li>On the Action Pane, select **Entry** to open the **Supply forecast**  page.</li></ol> |
    | Vendor groups | <ol><li>Go to **Master planning > Forecasting > Manual forecast entry > Vendor groups**.</li><li>Select the vendor group you want to create a forecast for.</li><li>On the Action Pane, select **Entry** to open the **Supply forecast**  page.</li></ol> | <!-- KFM: We can also open **Master planning \> Forecasting \> Demand forecast lines** and **Master planning \> Forecasting \> Demand forecast lines** directly. I suppose they show forecast lines for all entities and records. Shouldn't we also describe those in this table? -->
1. Depending on your selection, the **Supply forecast** or **Demand forecast** page opens, showing any existing forecast lines for the record you selected before opening the page.
1. Select **New** from the Action pane to add a new forecast line to the top grid.
1. For the new line, select the forecast **Model** to use, and then enter other details as needed, such as the item, item group, customer/vendor account or group, item quantity, or total transaction amount. See the later sections in this topic for complete details about each of the settings available on these pages.
1. To distribute the entered forecast over the period, select **Allocate forecast** from the toolbar on the **Overview** tab.
1. Use the **Allocation** grid to review the time horizon and the time intervals that are used to distribute the forecast quantities.

## Supply forecast lines

The supply forecast lets you create a plan for items to be purchased. It tells procurement and sourcing clerks what they are expected to order.

You can enter supply forecast by item, item group, item allocation key, vendor, and vendor group. See [Enter forecast lines manually](#manual-entry) for details about all the ways to open the **Supply forecast** page for various entities and records.

The **Supply forecast** page provides a grid of supply forecast lines at the top and an **Allocation** grid at the bottom. The top grid provides a set of tabs that you can use to view and set more information for a selected forecast line. The following subsections describe all of the settings available on each tab, and all of the commands available in the Action Pane and toolbar.

### Action Pane commands on the Supply forecast page

The following table describes each of the commands available in the Action Pane of the **Supply forecast** page.

| Action | Description |
|---|---|
| **Save** | Save your current settings. |
| **Edit** | Allow settings on this page to be edited. |
| **New** | Add a new forecast line to the top grid. |
| **Delete** | Remove the selected forecast line from the top grid. |
| **Forecast balances** | <!-- KFM: description needed --> |
| **Cash flow forecasts** | <!-- KFM: description needed --> |
| **Inventory \> Display dimensions** | Choose which inventory dimensions to include in the **Overview** grid. |

### The Overview tab toolbar for the Supply forecast page

The following table describes each of the commands available in the toolbar of the **Overview** tab on the **Supply forecast** page.

| Command | Description |
|---|---|
| **Allocate forecast** | <!-- KFM: description needed --> |
| **Bulk update** | <!-- KFM: description needed --> |
| **Inventory forecast** | <!-- KFM: description needed --> |
| **Create item requirement** | <!-- KFM: description needed --> |

### The Overview tab of the Supply forecast page

The following table describes each of the columns on the **Overview** tab on the **Supply forecast** page.

| Field | Description |
| --- | --- |
| **Model** | The forecast model with which the transaction is associated. |
| **Date** | The starting date of the transaction. |
| **Vendor account** | The vendor account with which the transaction is associated. |
| **Vendor group** | The vendor group with which the transaction is associated. |
| **Item number** | The item identification. |
| **Item group** | The item group with which the transaction is associated. |
| **Item allocation key** | The item allocation key that is associated with the forecast. |
| **CW quantity** | The forecast quantity in the given catch-weight unit. |
| **CW unit** | The catch-weight unit in which the item is purchased. This is retrieved automatically from the item setup. |
| **Quantity** | The forecast quantity in the given purchase unit. |
| **Unit** | The unit in which the item is purchased. This is retrieved automatically from the item setup, but you can modify it if  **Unit conversions**  are set up. |
| **Amount** | The gross amount, less discounts, that the forecast transaction contributes to the forecast. |
| **Currency** | The currency used in the forecast transaction. The default currency is entered automatically, but you can change it. |
| *(Other dimensions)* | Additional columns may be shown if you have chosen to include them. Select **Display dimensions** from the Action Pane to choose which additional dimensions are shown.

### The General tab of the Supply forecast page

The **General** tab shows more information about the line currently selected on the **Overview** tab. Some of this information is repeated from the **Overview** tab. The following table describes the fields that are unique to the **General** tab.

| Field | Description |
| --- | --- |
| **Report** | Set this to *Yes* to include the transaction in reporting. |
| **Comments** | Enter any comments regarding the forecast transaction. |
| **Active** | Select the check box to include the transaction in budget reporting. |
| **Include in cash flow forecasts** | Select the check box to allocate the forecast transaction to  **General ledger**. The field cannot be modified for reporting transactions. |
| **Sales tax group** | The tax group that is used to specify tax for the forecast transaction. |
| **Item sales tax group** | The item tax group that is used to specify tax for the forecast transaction. |
| **Method** | The method of allocating the forecast transaction. Select one of the following options:<ul><li>**None** – No allocation takes place.</li><li>**Period** – Use this method to forecast the same quantity per period. When you select this option, you use it along with the  **Per**  field where you specify a quantity, and the  **Unit**  field, where you select the unit of time)</li><li>**Key** – The forecast is allocated according to the period allocation key that you specify in the  **Period key**  field. You can use this method when you want to take seasonal variation into account.</li></ol>|
| **Per** | Enter the number of time intervals that the forecast extends into the future. This field is enabled when you select  **Period**  in the  **Method**  field. For example, if you select **Period** in the **Method** field, enter 1 in the  **Per**  field, and select **Months** in the **Unit** field, while specifying an ending date in the  **End** field that extends one year into the future, the program will create one forecast line for each month of the coming year, based on the item and quantity stated in the header line. |
| **Unit** | The unit of time interval. Select one of the following options: **Days**, **Months**, **Years** - allocation corresponds to the number of days/months/years respectively that you specify in the  **Per**  field.|
| **Period key** | The period allocation key. |
| **End** | The ending date when you use the  **Per**  and  **Unit**  fields. |

### The Item tab of the Supply forecast page

The **Item** tab shows more item information for the line currently selected on the **Overview** tab. 

The grid at the top of the **Item** tab repeats item information also shown on the  **Overview** tab. In addition, it shows the **Unit price**, which is the purchase price per number of units specified in the **Unit** field. The unit prices is retrieved automatically from the item, but you can modify it.

The fields below the grid provide more item details. Some of this information is repeated from the **Overview** tab. The following table describes the fields that are unique to the **Item** tab.

<!-- KFM: I adopted the following table from the similar section in the Demand forecast section. Please review carefully to make sure these descriptions don't need to be updated for the Supply page. -->

| Field | Description |
| --- | --- |
| **Price unit** | The number of units for which the purchase price applies. The number is retrieved automatically from the items table, but you can modify it. |
| **Charges on purchases** | Fixed charges on the purchase price. The charges are independent of quantity. |
| **Discount percentage** | The discount expressed as a percentage. |
| **Discount amount** | The discount expressed in amount per sales unit. |
| **Gross amount** | The amount without discounts applied. |
| **Quantity** | The transaction quantity expressed in the inventory unit of the item. |
| **Sub-BOM** | <!-- KFM: Description needed --> |
| **Subroute** | <!-- KFM: Description needed --> |

### The Financial dimensions tab of the Supply forecast page

The **Financial dimensions** tab shows the complete financial dimension values for the line currently selected on the **Overview** tab.

### The Inventory dimensions tab of the Supply forecast page

The **Inventory dimensions** tab shows the complete inventory dimension values for the line currently selected on the **Overview** tab.

### The Allocation grid of the Supply forecast page

If you are using an item allocation key, or if you have entered an item forecast for one or more future periods, you can allocate the forecast by selecting **Allocate forecast** from the **Overview** tab toolbar. The quantity is then distributed as indicated by the lines in this grid.

## Demand forecast lines

The demand forecast lets you enter or generate demand for a customer. It helps sales and marketing clerks tell the master planning clerks what the expected demand will be over the upcoming forecast period.

You can enter demand forecast by item, item group, item allocation key, customer, and customer group. See [Enter forecast lines manually](#manual-entry) for details about all the ways to open the **Demand forecast** page for various entities and records.

The **Demand forecast** page provides a grid of demand forecast lines at the top and an **Allocation** grid at the bottom. The top grid provides a set of tabs that you can use to view and set more information for a selected forecast line. The following subsections describe all of the settings available on each tab, and all of the commands available in the Action Pane and toolbar.

### Action Pane commands on the Demand forecast page

The following table describes each of the commands available in the Action Pane of the **Demand forecast** page.

| Action | Description |
|---|---|
| **Save** | Save your current settings. |
| **Edit** | Allow settings on this page to be edited. |
| **Delete** | Remove the selected forecast line from the top grid. |
| **Forecast balances** | <!-- KFM: description needed --> |
| **Cash flow forecast** | <!-- KFM: description needed --> |
| **Display dimensions** | Choose which product, storage, and tracking dimensions to show in the **Overview** grid. |
| **General ledger preview** | <!-- KFM: description needed --> |
| **Transfer quotation lines** | <!-- KFM: description needed --> |

### The Overview tab toolbar on the Demand forecast page

The following table describes each of the commands available in the toolbar of the **Overview** tab on the **Demand forecast** page.

| Command | Description |
|---|---|
| **Allocate forecast** | <!-- KFM: description needed --> |
| **Bulk update** | <!-- KFM: description needed --> |
| **Inventory forecast** | <!-- KFM: description needed --> |
| **Create item requirement** | <!-- KFM: description needed --> |

### The Overview tab of the Demand forecast page

The following table describes each of the columns on the **Overview** tab on the **Demand forecast** page.

| Field | Description |
| --- | --- |
| **Task name** | The batch task name that was used to create this forecast line. |
| **Model** | The forecast model that the transaction is associated with. |
| **Date** | The date that the transaction starts. |
| **Customer account** | The customer account that the transaction is associated with. |
| **Customer group** | Customer group that the transaction is attached to. |
| **Item number** | The identification of the item. |
| **Product name** | The description of the item. |
| **Item allocation key** | The item allocation key that is used in inventory forecast allocation. |
| **Sales quantity** | The transaction quantity in the specified sales unit. |
| **Unit** | The unit that the item is sold in. |
| **Amount** | The gross amount, less discounts, that the forecast transaction contributes to the forecast. |
| **Sales price** | The sales price per number of units specified in the  **Price unit**  field. The information is retrieved from the item, but you can modify it. |
| **Sales currency** | The currency for the current forecast transaction. The default currency is entered by the system, but you can select a different currency from the drop-down list. |
| **CW quantity** | The forecast quantity in the given catch-weight unit. |
| **CW unit** | The catch-weight unit in which the item is sold. This is retrieved automatically from the item setup. |
| *(Other dimensions)* | Additional product, storage, and tracking dimensions may be shown in the gird if you have chosen to include them. Select **Display dimensions** from the Action Pane to choose which additional dimensions are shown. |

### The General tab of the Demand forecast page

The **General** tab shows more information about the line currently selected on the **Overview** tab. Some of this information is repeated from the **Overview** tab. The following table describes the fields that are unique to the **General** tab.

| Field | Description |
| --- | --- |
| **Demand forecast sequence number** | <!-- KFM: Description needed --> |
| **Item group** | The item group that the transaction is associated with. |
| **Report** | Set this to *Yes* to include the transaction in reporting. |
| **Comments** | Enter any comments that pertain to the forecast transaction. |
| **Active** | Select the check box to include the transaction in budget reporting. This field cannot be modified for reporting transactions. |
| **Include in cash flow forecasts** | Select the check box to allocate the forecast transaction to the general ledger. This field cannot be modified for reporting transactions. See also [Cash flow forecasting](articles\finance\cash-bank-management\cash-flow-forecasting.md). |
| **Sales tax group** | The tax group that is used to specify tax for the forecast transaction. |
| **Item sales tax group** | The item tax group that is used to specify tax for the forecast transaction. |
| **Method** | The method of allocating the forecast transaction. Select one of the following options:<ul><li>**None** – No allocation takes place.</li><li>**Period** – Use this method to forecast the same quantity per period. When you select this option, you use it along with the **Per** field where you specify a quantity, and the  **Unit**  field, where you select the unit of time.</li><li>**Key** – The forecast is allocated according to the period allocation key that you specify in the  **Period key**  field. You can use this method when you want to take seasonal variation into account.</li><ul>|
| **Per** | Enter the number of time intervals that the forecast extends into the future. This field is enabled when you select  **Period**  in the  **Method**  field. For example, if you select **Period** in the **Method** field, enter 1 in the  **Per**  field, and select **Months** in the **Unit** field, while specifying an ending date in the  **End** field that extends one year into the future, the program will create one forecast line for each month of the coming year, based on the item and quantity stated in the header line. |
| **Unit** | The unit of time interval. Select one of the following options: **Days**, **Months**, **Years** - allocation corresponds to the number of days/months/years respectively that you specify in the  **Per**  field.|
| **Period key** | The period allocation key for allocating the forecast. See also [Budget planning data allocation](articles\finance\budgeting\budget-planning-data-allocation.md). |
| **End** | The ending date when you use the  **Per**  and  **Unit**  fields. |

### The Item tab of the Demand forecast page

The **Item** tab shows more item information for the line currently selected on the **Overview** tab. Some of this information is repeated from the **Overview** tab. The following table describes the fields that are unique to the **Item** tab.

| Field | Description |
| --- | --- |
| **Price unit** | The number of sales units for which the sales price applies. The number is retrieved automatically from the items table, but you can modify it. |
| **Sales charges** | Fixed charges on the sales price. The charges are independent of quantity. |
| **Cost price** | The cost for the current forecast transaction per inventory unit. The cost is retrieved from the Items table, but you can modify it. |
| **Discount percentage** | The discount expressed as a percentage. |
| **Discount amount** | The discount expressed in amount per sales unit. |
| **Gross amount** | The amount without discounts applied. |
| **Inventory quantity** | The transaction quantity expressed in the inventory unit of the item. |
| **Use specific BOM** | The BOM number of a specific BOM. |
| **Use specific route** | The route number of a specific sub-route. |

### The Project tab of the Demand forecast page

The **Project** tab shows more project information for the line currently selected on the **Overview** tab. Some of this information is repeated from the **Overview**, **General** or **Item** tabs. The following table describes the fields that are unique to the **Project** tab.

| Field | Description |
| --- | --- |
| **Project date** | Date of the demand forecast transaction. |
| **Project ID** | The identification of the project that is referenced by the current transaction. |
| **Funding source** | Funding source that the demand forecast is associated with. |
| **Activity number** | The activity associated with the demand forecast transaction. |
| **Category** | The cost category of the current transaction. |
| **Line property** | The status that the transaction is attached to. |
| **Transaction ID** | System identification for the demand forecast transaction. |
| **Cost amount** | Demand forecast transaction amount. |
| **Unit price** | The price per unit. |
| **Modified By** | The identification of the worker who last modified the selected transaction. |
| **Invoice date** | Enter the expected invoice date. |
| **Elimination date** | View or modify the elimination date. When the forecast is created, the elimination date is set to the end date of the project. If the project has no end date, the project date is applied. Applies to fixed-price projects and investment projects. |
| **Cost payment date** | Enter the expected date for the purchase payment. |
| **Sales payment date** | Enter the expected date for the sales payment. |

### The Financial dimensions tab of the Demand forecast page

The **Financial dimensions** tab shows the complete financial dimension values for the line currently selected on the **Overview** tab. 

### The Inventory dimensions tab of the Demand forecast page

The **Inventory dimensions** tab shows the complete inventory dimension values for the line currently selected on the **Overview** tab. 

### The Allocation grid of the Demand forecast page

If you are using an item allocation key, or if you have entered an item forecast for one or more future periods, you can allocate the forecast by selecting **Allocate forecast** from the **Overview** tab toolbar. The quantity is then distributed as indicated by the lines in this grid.

## Inventory forecast

The supply and demand forecast lines pages have a link to the **Inventory forecast** page filtered for the same item/model combination. It represents a balance between supply and demand entered for the same item. It cannot be edited. The inventory forecast helps the inventory management team to review what changes are expected to the on-hand inventory of an item over the upcoming period of time forecasted.

### Action Pane commands on the Inventory forecast page

The following table describes each of the commands available in the Action Pane of the **Demand forecast** page.

| Action | Description |
|---|---|
| **Supply forecast** | <!-- KFM: description needed --> |
| **Demand forecast** | <!-- KFM: description needed --> |
| **Inventory \> Display dimensions** | Choose which product, storage, and tracking dimensions to show in the **Overview** grid. |

### Information on the Inventory forecast page 

The **Inventory forecast** page provides a grid with the following columns of information:

| **Field** | **Description** |
| --- | --- |
| **Model** | The forecast model that the transaction is associated with. |
| **Item number** | The identification of the item. |
| **Budget date** | The date for the forecast transaction. |
| **Forecast type** | The source of the transaction (Demand forecast or Supply forecast). |
| **CW quantity** | The forecast quantity in the catch-weight unit. |
| **Quantity** | The forecast quantity in the inventory unit. |
| **CW Accumulated** | <!-- KFM: Description needed --> |
| **Sub-BOM** | The BOM number of a specific sub-BOM. |
| **Subroute** | The route number of a specific sub-route. |
| *(Other dimensions)* | Additional columns may be shown if you have chosen to include them. Select **Inventory \> Display dimensions** from the Action Pane to choose which additional dimensions are shown. |

## Additional resources

- [Demand forecasting overview](introduction-demand-forecasting.md)
- [Demand forecasting setup](demand-forecasting-setup.md)
- [Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)
- [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]