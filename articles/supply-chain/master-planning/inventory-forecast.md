---
# required metadata

title: Supply and demand forecast
description: This topic describes the supply and demand forecast functionality that can be used to create inventory forecast in Microsoft Dynamics 365 Supply Chain Management.  
author: crytt
ms.date: 05/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EcoResProductDetailsExtended, ForecastSales, ForecastPurch
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 72653
# ms.assetid: c5fa4b09-512d-4349-ac51-cc13da69a160
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: kamaybac
ms.search.validFrom: 2021-05-12
ms.dyn365.ops.version: AX 7.0.0

---

# Supply and demand forecast

[!include [banner](../includes/banner.md)]

This topic describes the functionality that can be used to create inventory forecast in Microsoft Dynamics 365 Supply Chain Management.

This functionality allows to create and view supply and demand forecast lines, respectively, for items, item groups, item allocation keys, customer accounts, customer groups, vendor accounts, and vendor groups.

For each forecast line, you can select the forecast model to use and then specify the item/item group plus the quantity or the transaction amount. You can also set up a time schedule for allocating the forecast quantity.

## Supply forecast lines
The supply forecast allows you to create a plan for items to be purchased. The supply forecast is used to help the procurement and sourcing clerks by showing them what is expected to order.

Supply forecast can be entered by item, item group, item allocation key, vendor, and vendor group.

The page contains the following fields:

| **Field** | **Description** |
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
| **Method** | - The method of allocating the forecast transaction. Select one of the following options:    **None**  (no allocation takes place); **Period** (use this method to forecast the same quantity per period. When you select this option, you use it along with the  **Per**  field where you specify a quantity, and the  **Unit**  field, where you select the unit of time); **Key** (the forecast is allocated according to the period allocation key that you specify in the  **Period key**  field. You can use this method when you want to take seasonal variation into account).|
| **Per** | Enter the number of time intervals that the forecast extends into the future. This field is enabled when you select  **Period**  in the  **Method**  field. For example, if you select **Period** in the **Method** field, enter 1 in the  **Per**  field, and select **Months** in the **Unit** field, while specifying an ending date in the  **End** field that extends one year into the future, the program will create one forecast line for each month of the coming year, based on the item and quantity stated in the header line. |
| **Unit** | The unit of time interval. Select one of the following options: **Days**, **Months**, **Years** - allocation corresponds to the number of days/months/years respectively that you specify in the  **Per**  field.|
| **Period key** | The period allocation key. |
| **End** | The ending date when you use the  **Per**  and  **Unit**  fields. |
| **Report** | Select the check box to include the transaction in reporting. |
| **Comments** | Enter any comments regarding the forecast transaction. |
| **Active** | Select the check box to include the transaction in budget reporting. |
| **Include in cash flow forecasts** | Select the check box to allocate the forecast transaction to  **General ledger**. The field cannot be modified for reporting transactions. |
| **Sales tax group** | The tax group that is used to specify tax for the forecast transaction. |
| **Item sales tax group** | The item tax group that is used to specify tax for the forecast transaction. |
| **Unit price** | The purchase price per number of units specified in the **Unit** field. The information is retrieved automatically from the item, but you can modify it. |
| **Inventory dimensions** | The inventory dimensions that are tracked for this item. |
| **Financial dimensions** | The financial dimensions that are tracked for this item. |
| **Allocation** | When an item allocation key is used, or when an item forecast is entered for a number of periods ahead, it can be allocated by using the **Allocate forecast** function. In that case, the quantity is distributed to several lines represented in this grid.|

## Demand forecast lines
The demand forecast allows you to enter or generate demand for a customer. The demand forecast helps the sales and marketing clerks to provide data to the master planning clerks with what the expected demand will be over the upcoming period of time forecasted.

Demand forecasts can be entered by item, item group, item allocation key, customer, and customer group.

The page contains the following fields:

| **Field** | **Description** |
| --- | --- |
| **Task name** | The batch task name that was used to create this forecast line. |
| **Model** | The forecast model that the transaction is associated with. |
| **Date** | The date that the transaction starts. |
| **Customer account** | The customer account that the transaction is associated with. |
| **Customer group** | Customer group that the transaction is attached to. |
| **Item group** | The item group that the transaction is associated with. |
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
| **Method** | The method of allocating the forecast transaction. Select one of the following options:    **None**  (no allocation takes place); **Period** (use this method to forecast the same quantity per period. When you select this option, you use it along with the  **Per**  field where you specify a quantity, and the  **Unit**  field, where you select the unit of time); **Key** (the forecast is allocated according to the period allocation key that you specify in the  **Period key**  field. You can use this method when you want to take seasonal variation into account).|
| **Per** | Enter the number of time intervals that the forecast extends into the future. This field is enabled when you select  **Period**  in the  **Method**  field. For example, if you select **Period** in the **Method** field, enter 1 in the  **Per**  field, and select **Months** in the **Unit** field, while specifying an ending date in the  **End** field that extends one year into the future, the program will create one forecast line for each month of the coming year, based on the item and quantity stated in the header line. |
| **Unit** | The unit of time interval. Select one of the following options: **Days**, **Months**, **Years** - allocation corresponds to the number of days/months/years respectively that you specify in the  **Per**  field.|
| **Period key** | The period allocation key for allocating the forecast. See also [Budget planning data allocation](https://docs.microsoft.com/en-us/dynamics365/finance/budgeting/budget-planning-data-allocation). |
| **End** | The ending date when you use the  **Per**  and  **Unit**  fields. |
| **Report** | Select the check box to include the transaction in reporting. |
| **Comments** | Enter any comments that pertain to the forecast transaction. |
| **Active** | Select the check box to include the transaction in budget reporting. This field cannot be modified for reporting transactions. |
| **Include in cash flow forecasts** | Select the check box to allocate the forecast transaction to the general ledger. This field cannot be modified for reporting transactions. See also [Cash flow forecasting](https://docs.microsoft.com/en-us/dynamics365/finance/cash-bank-management/cash-flow-forecasting). |
| **Sales tax group** | The tax group that is used to specify tax for the forecast transaction. |
| **Item sales tax group** | The item tax group that is used to specify tax for the forecast transaction. |
| **Price unit** | The number of sales units for which the sales price applies. The number is retrieved automatically from the items table, but you can modify it. |
| **Sales charges** | Fixed charges on the sales price. The charges are independent of quantity. |
| **Cost price** | The cost for the current forecast transaction per inventory unit. The cost is retrieved from the Items table, but you can modify it. |
| **Discount percentage** | The discount expressed as a percentage. |
| **Discount amount** | The discount expressed in amount per sales unit. |
| **Gross amount** | The amount without discounts applied. |
| **Inventory quantity** | The transaction quantity expressed in the inventory unit of the item. |
| **Use specific BOM** | The BOM number of a specific BOM. |
| **Use specific route** | The route number of a specific sub-route. |
| **Project ID** | The identification of the project that is referenced by the current transaction. |
| **Category** | The cost category of the current transaction. |
| **Line property** | The status that the transaction is attached to. |
| **Unit price** | The price per unit. |
| **Modified By** | The identification of the worker who last modified the selected transaction. |
| **Invoice date** | Enter the expected invoice date. |
| **Elimination date** | View or modify the elimination date. When the forecast is created, the elimination date is set to the end date of the project. If the project has no end date, the project date is applied. Applies to fixed-price projects and investment projects. |
| **Cost payment date** | Enter the expected date for the purchase payment. |
| **Sales payment date** | Enter the expected date for the sales payment. |
| **Project date** | Date of the demand forecast transaction. |
| **Funding source** | Funding source that the demand forecast is associated with. |
| **Activity number** | The activity associated with the demand forecast transaction. |
| **Category** | Cost category of the current transaction. |
| **Line property** | Status that the transaction is attached to. |
| **Transaction ID** | System identification for the demand forecast transaction. |
| **Cost amount** | Demand forecast transaction amount. |
| **Inventory dimensions** | The inventory dimensions that are tracked for this item. |
| **Financial dimensions** | The financial dimensions that are tracked for this item. |
| **Allocation** | When an item allocation key is used, or when an item forecast is entered for a number of periods ahead, it can be allocated by using the **Allocate forecast** function. In that case, the quantity is distributed to several lines represented in this grid.|

## Inventory forecast
The supply and demand forecast lines pages have a link to the **Inventory forecast** page filtered for the same item/model combination. It represents a balance between supply and demand entered for the same item. It cannot be edited. The inventory forecast helps the inventory management team to review what changes are expected to the on-hand inventory of an item over the upcoming period of time forecasted.

The page contains the following fields:

| **Field** | **Description** |
| --- | --- |
| **Model** | The forecast model that the transaction is associated with. |
| **Item number** | The identification of the item. |
| **Inventory dimensions** | The inventory dimensions that are tracked for this item. |
| **Budget date** | The date for the forecast transaction. |
| **Forecast type** | The source of the transaction (Demand forecast or Supply forecast). |
| **CW quantity** | The forecast quantity in the catch-weight unit. |
| **Quantity** | The forecast quantity in the inventpry unit. |
| **Sub-BOM** | The BOM number of a specific sub-BOM. |
| **Subroute** | The route number of a specific sub-route. |

## Manual forecast entry
Use this procedure to create new forecast lines for products. You can refer to the information in the table below on other ways to access these pages (instead of the first two steps).

1. Go to  **Product information management > Products > Released products** or **Released product variants** pages.
1. Select **Supply forecast** to open the **Supply forecast** page, or **Demand forecast**  to open the  **Demand forecast**  page on the **Plan > Forecasting** tab.
1. Create a new forecast line.
1. Select the forecast **Model** to use, and then enter detailed information, such as the item, item group, customer/vendor account or group, item quantity, or total transaction amount.
1. Select **Allocate forecast** to distribute the entered forecast over the period.
1. Use the  **Allocation**  grid to review the time horizon and the time intervals that are used to distribute the forecast quantities.

The following table lists additional paths that you can use to access the **Supply forecast lines** or **Demand forecast lines** pages.

| **Forecast** | **Path** |
| --- | --- |
| Item groups | **Inventory management > Setup > Inventory > Item groups**. Select  **Forecasting > Supply** to open the **Supply forecast lines** page, or **Demand** to open the **Demand forecast lines** page. |
| Item allocation keys | **Inventory management > Setup > Forecast**. Select  **Demand forecast** to open the **Demand forecast lines** page. |
| Customers | **Master planning > Forecasting > Manual forecast entry > Customers**. Select a customer, and then select  **Define demand forecast** to open the **Demand forecast lines** page. |
| Customer groups | **Master planning > Forecasting > Manual forecast entry > Customer groups**. Select a customer group, and then select  **Define demand forecast** to open the **Demand forecast lines** page. |
| Vendors | **Master planning > Forecasting > Manual forecast entry > Vendors**. Select a vendor, and then select  **Entry** to open the  **Supply forecast lines**  page. |
| Vendor groups | **Master planning > Forecasting > Manual forecast entry > Vendor groups**. Select a vendor group, and then select  **Entry** to open the  **Supply forecast lines**  page. |

Additional resources
--------

[Demand forecasting overview](introduction-demand-forecasting.md)

[Demand forecasting setup](demand-forecasting-setup.md)

[Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)

[Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]