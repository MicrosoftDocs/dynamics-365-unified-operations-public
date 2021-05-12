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
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Supply and demand forecast

[!include [banner](../includes/banner.md)]

This topic describes the functionality that can be used to create inventory forecast in Microsoft Dynamics 365 Supply Chain Management.

This functionality allows to create and view supply and demand forecast lines, respectively, for items, item groups, item allocation keys, customer accounts, customer groups, vendor accounts, and vendor groups.

For each forecast line, you can select the forecast model to use and then specify the item/item group plus the quantity or the transaction amount. You can also set up a time schedule for allocating the forecast quantity.

## Supply forecast
The supply forecast allows you to create a plan for items to be purchased. The supply forecast is used to help the procurement and sourcing clerks by showing them what is expected to order.

Supply forecast can be entered by item, item group, item allocation key, vendor, and vendor group.

The page contains the following fields:

| **Field** | **Description** |
| --- | --- |
|
| |
|
| |
| **Model** | The forecast model with which the transaction is associated. |
| --- | --- |
| **Date** | The starting date of the transaction. |
| **Vendor account** | The vendor account with which the transaction is associated. |
| **Vendor group** | The vendor group with which the transaction is associated. |
| **Item number** | The item identification. |
| **Item group** | The item group with which the transaction is associated. |
| **Item allocation key** | The item allocation key that is associated with the forecast. |
| **Quantity** | The forecast quantity in the given purchase unit. |
| **Unit** | The unit in which the item is purchased. This is retrieved automatically from the item setup, but you can modify it if  **Unit conversions**  are set up. |
| **Amount** | The gross amount, less discounts, that the forecast transaction contributes to the forecast. |
| **Currency** | The currency used in the forecast transaction. The default currency is entered automatically, but you can change it. |
| **Method** | The method of allocating the forecast transaction. Select one of the following options:
- **None**  - No allocation takes place.
- **Period**  - Use this method to forecast the same quantity per period. When you select this option, you use it along with the  **Per**  field where you specify a quantity, and the  **Unit**  field, where you select the unit of time.
- **Key**  - The forecast is allocated according to the period allocation key that you specify in the  **Period key**  field. You can use this method when you want to take seasonal variation into account.
 |
| **Per** | Enter the number of time intervals that the forecast extends into the future. This field is enabled when you select  **Period**  in the  **Method**  field. **Example**
1. Select  **Period**  in the  **Method**  field.
2. Enter 1 in the  **Per**  field.
3. Select  **Months**  in the  **Unit**  field.
4. Specify an ending date in the  **End**  field that extends one year into the future.
The program creates one forecast line for each month of the coming year, based on the item and quantity stated in the header line. |
| **Unit** | The unit of time interval. Select one of the following options:
- **Days**  - Allocation corresponds to the number of days that you specify in the  **Per**  field.
- **Months**  - Allocation corresponds to the number of months that you specify in the  **Per**  field.
- **Years**  - Allocation corresponds to the number of years that you specify in the  **Per**  field.
 |
| **Period key** | The period allocation key. |
| **End** | The ending date when you use the  **Per**  and  **Unit**  fields. |
| **Report** | Select the check box to include the transaction in reporting. |
| **Comments** | Enter any comments regarding the forecast transaction. |
| **Active** | Select the check box to include the transaction in budget reporting. |
| **Cash flow forecasts** | Select the check box to allocate the forecast transaction to  **General ledger**. The field cannot be modified for reporting transactions. |
| **Sales tax group** | The tax group that is used to specify tax for the forecast transaction. |
| **Item sales tax group** | The item tax group that is used to specify tax for the forecast transaction. |
| **Unit price** | The purchase price per number of units specified in the  **Price unit**  field. The information is retrieved automatically from the item, but you can modify it. |
| **Price unit** | The number of purchase units for which the purchase price applies. The information is retrieved automatically from the item, but you can modify it. |
| **Charges on purchases** | The fixed purchase charges that are independent of quantity. The information is retrieved automatically from the item, but you can modify it. |
| **Discount percentage** | The discount expressed as a percentage. |
| **Cash discount amount** | The discount amount per purchase unit. |
| **Inventory** | The transaction quantity in item units. |
| **Sub-BOM** | The BOM number of a specific sub-BOM. When blank, the active number is used. |
| **Subroute** | The route number of a specific subroute. When blank, the active number is used. |
| **Configuration** | Select an item configuration to specify an item with specific attributes. |
| **Size** | Select the size of the item. |
| **Color** | Select the color of the item. |
| **Warehouse** | Select the warehouse where you store the items. |
| **Batch number** | Select the batch number. |
| **Location** | The location inside the warehouse. |
| **Pallet ID** | The pallet identification. |
| **Serial number** | Select the serial number. |
| **Financial dimensions** | The financial dimensions that were set up in the  **Financial dimensions**  form. |
| **Where the %1 dimension is used** | The account structures and advanced rule structures that use the financial dimensions that you selected in the  **Financial dimensions**  or  **Default financial dimensions**  field group. |

## Demand forecast
The demand forecast allows you to enter or generate demand for a customer. The demand forecast helps the sales and marketing clerks to provide data to the master planning clerks with what the expected demand will be over the upcoming period of time forecasted.

Demand forecasts can be entered by item, item group, item allocation key, customer, and customer group.

The page contains the following fields:

| **Field** | **Description** |
| --- | --- |
|
| |
|
| |
| **Model** | The forecast model that the transaction is associated with. |
| --- | --- |
| **Date** | The date that the transaction starts. |
| **Customer account** | The customer account that the transaction is associated with. |
| **Customer group** | Customer group that the transaction is attached to. |
| **Item number** | The identification of the item. |
| **Item group** | The item group that the transaction is associated with. |
| **Item allocation key** | The item allocation key that is used in inventory forecast allocation. |
| **Sales quantity** | The transaction quantity in the specified sales unit. |
| **Unit** | The unit that the item is sold in. |
| **Amount** | The gross amount, less discounts, that the forecast transaction contributes to the forecast. |
| **Currency** | The currency for the current forecast transaction. The default currency is entered by the system, but you can select a different currency from the drop-down list. |
| **Method** | The method used to allocate forecast transactions. Select one of the following options:
- **None**  - No allocation occurs.
- **Period**  – Use to forecast the same quantity per period. Use this option together with the  **Per**  field, to specify a quantity; the  **Unit**  field, to select the unit of time; and the  **End**  field, to specify the end date for the forecast horizon.
- **Key**  - The forecast quantity is allocated according to the period allocation key that you specify in the  **Period key**  field. You can use this method when you want to consider seasonal variation.
 |
| **Per** | Enter the number of time intervals that the forecast extends into the future. This field is enabled when you select  **Period**  in the  **Method**  field. **Example**
1. Select  **Period**  in the  **Method**  field.
2. Enter 1 in the  **Per**  field.
3. Select  **Months**  in the  **Unit**  field.
4. Specify an ending date in the  **End**  field that extends one year into the future.
One forecast line is generated for each month of the coming year, based on the item and quantity stated in the header line. |
| **Unit** | The unit of time interval. Select one of the following options:
- **Days**  - Allocation corresponds to the number of days that you specify in the  **Per**  field.
- **Months**  - Allocation corresponds to the number of months that you specify in the  **Per**  field.
- **Years**  -Allocation corresponds to the number of years that you specify in the  **Per**  field.
 |
| **Period key** | The period allocation key for allocating the forecast. See also [Period allocation categories (form)](https://docs.microsoft.com/en-us/dynamicsax-2012/period-allocation-categories-form). |
| **End** | The ending date when you use the  **Per**  and  **Unit**  fields. |
| **Report** | Select the check box to include the transaction in reporting. |
| **Comments** | Enter any comments that pertain to the forecast transaction. |
| **Active** | Select the check box to include the transaction in budget reporting. This field cannot be modified for reporting transactions. |
| **Cash flow forecasts** | Select the check box to allocate the forecast transaction to the general ledger.This field cannot be modified for reporting transactions. See also [Cash flow forecast transactions (form)](https://docs.microsoft.com/en-us/dynamicsax-2012/cash-flow-forecast-transactions-form). |
| **Sales tax group** | The tax group that is used to specify tax for the forecast transaction. |
| **Item sales tax group** | The item tax group that is used to specify tax for the forecast transaction. |
| **Unit price** | The sales price per number of units specified in the  **Price unit**  field. The information is retrieved from the item, but you can modify it. |
| **Price unit** | The number of sales units for which the sales price applies. The number is retrieved automatically from the items table, but you can modify it. |
| **Sales charges** | Fixed charges on the sales price. The charges are independent of quantity. |
| **Cost price** | The cost for the current forecast transaction per inventory unit. The cost is retrieved from the Items table, but you can modify it. |
| **Discount percentage** | The discount expressed as a percentage. |
| **Cash discount amount** | The discount expressed in amount per sales unit. |
| **Inventory quantity** | The transaction quantity expressed in the inventory unit of the item. |
| **Sub-BOM** | The BOM number of a specific sub-BOM. When this field is blank, the active number is used. |
| **Subroute** | The route number of a specific sub-route. When this field is blank, the active number is used. |
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
| **Unit price** | Price per unit. |
| **Modified by** | The identification of the worker who last modified the selected transaction. |
| **Invoice date** | Enter the expected invoice date. |
| **Elimination date** | View or modify the elimination date. When the forecast is created, the elimination date is set to the end date of the project. If the project has no end date, the project date is applied. Applies to fixed-price projects and investment projects. |
| **Cost payment date** | Enter the expected date for the purchase payment. |
| **Sales payment date** | Enter the expected date for the sales payment. |
| **Financial dimensions** | The financial dimensions that were set up in the  **Financial dimensions**  form. |
| **Where the %1 dimension is used** | The account structures and advanced rule structures that use the financial dimensions that you selected in the  **Financial dimensions**  or  **Default financial dimensions**  field group.  **Note** The name of the field depends on the selection in the  **Financial dimensions**  or  **Default financial dimensions**  field group. |
| **Configuration** | Select an item configuration to specify an item with specific attributes. |
| **Size** | The size of the item |
| **Color** | The color of the item. |
| **Warehouse** | Enter the warehouse where you store the items. |
| **Batch number** | Enter the batch number dimension. If you select  **Edit lines**  and  **Explode lines**  in the upper section of the  **Shipment** / **Receive**  form, you can modify the batch number for the transfer order line. |
| **Location** | The location inside a warehouse. If you select  **Edit lines**  and  **Explode lines**  in the upper section of the  **Shipment** / **Receive**  form, you can modify the location number for the transfer order line. |
| **Pallet ID** | The unique identification for the pallet. This is also the serial shipping container code. |
| **Serial number** | The serial number dimension. If you select  **Edit lines**  and  **Explode lines**  in the upper section of the  **Shipment** / **Receive**  form, you can modify the serial number for the transfer order line. |

## Manual forecast entry
Use this procedure to create new forecast lines for products.

1. Go to  **Product information management**  \&gt;  **Products**  \&gt;  **Released products** or **Released product variants** pages.
1. Select **Supply forecast**  to open the  **Supply forecast**  page, or **Demand forecast**  to open the  **Demand forecast**  page on the **Plan**** \&gt; ****Forecasting** tab.
1. Create a new forecast line.
1. Select the forecast **Model** to use, and then enter detailed information, such as the item, item group, customer/vendor account or group, item quantity, or total transaction amount.
1. Select **Allocate forecast** to distribute the entered forecast over the period.
1. Use the  **Allocation**  grid to review the time horizon and the time intervals that are used to distribute the forecast quantities.

The following table lists additional paths that you can use to access the  **Supply forecast**  or  **Demand forecast**  form.

| **Forecast** | **Path** |
| --- | --- |
|
| |
|
| |
| Item groups | **Inventory management**  \&gt;  **Setup** \&gt;  **Inventory**  \&gt;  **Item groups**. Select  **Forecasting \&gt;**** Supply ** to open the ** Supply forecast ** page, or** Demand ** to open the ** Demand forecast** page. |
| --- | --- |
| Customers | **Master planning**  \&gt;  **Forecasting**  \&gt;  **Manual forecast entry**  \&gt;  **Customers**. Select a customer, and then select  **Define**** demand forecast **to open the ** Demand forecast** page. |
| Customer groups | **Master planning**  \&gt;  **Forecasting**  \&gt;  **Manual forecast entry**  \&gt;  **Customer groups**. Select a customer group, and then select  **Define**** demand forecast **to open the ** Demand forecast** page. |
| Vendors | **Master planning**  \&gt;  **Forecasting**  \&gt;  **Manual forecast entry**  \&gt;  **Vendors**. Select a vendor, and then select  **Entry** to open the  **Supply forecast**  page. |
| Vendor groups | **Master planning**  \&gt;  **Forecasting**  \&gt;  **Manual forecast entry**  \&gt;  **Vendor groups**. Select a vendor group, and then select  **Entry** to open the  **Supply forecast**  page. |

Additional resources
--------

[Demand forecasting overview](introduction-demand-forecasting.md)

[Demand forecasting setup](demand-forecasting-setup.md)

[Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)

[Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]