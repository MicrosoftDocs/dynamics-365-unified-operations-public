---
# required metadata

title: Reduction keys
description: This articles provides examples that show how to set up a reduction key. It includes information about the various reduction key settings and the results of each. You can use a reduction key to define how to reduce forecast requirements.
author: roxanadiaconu
manager: AnnBe
ms.date: 02/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqPlanSched
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 19251
ms.assetid: aa9e0dfb-6052-4a2e-9378-89507c02fdf2
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Forecast reduction keys

[!include [banner](../includes/banner.md)]

This article explains the different methods used to reduce forecast requirements. It includes information about each of the types and examples of the results of each. The article also includes the creation, setup and use of a forecast reduction key, which is used in some methods to reduce forecast requirements. 

# Method used to reduce forecast requirements

When you include a forecast in a master plan, you can choose how the forecast requirements are reduced when actual demand is included. 
To include a forecast in a master plan and choose the method to reduce forecast requirements go to **Master planning > Setup > Plans > Master plans**. Choose the forecast desired under the field **Forecast model** and select the **Method used to reduce forecast requiments**. The available options to choose from are now shown.

## None

If you choose **None**", the forecast requirements are not reduced during master scheduling. 
This means that master planning will create planned orders to supply the forecasted demand (forecast requirements). These planned orders will keep the quantity suggested regardless of other types of demand. For example, if sales orders are placed, master planning will create additional planned orders to supply the sales orders. The forecast requirements will not be reduced in quantity. 

## Percent - reduction key

If you choose **Percent - reduction key**, the forecast requirements are reduced according to the percentages and time periods that are defined by the reduction key. Therefore, master planning will create planned orders that will have a quantity = forecasted quantity * reduction key in each time period. 
If there are other types of demand, master planning will also create planned orders to supply those. 

### Example : Percent - reduction key 

This example shows how a reduction key reduces demand forecast requirements according to the percentages and periods that are defined by the reduction key.

1. Include a **Forecast** as the one shown.

   | Month     | Demand forecast |
   |---------- |-------   |
   |  January  |   1000   |   
   |  February |   1000   |   
   |  March    |   1000   |  
   |   April   |   1000   |   
   
2. On the **Reduction keys** page, set up the following lines.

   | Change | Unit  | Percent |
   |--------|-------|---------|
   |   1    | Month |   100   |
   |   2    | Month |   75    |
   |   3    | Month |   50    |
   |   4    | Month |   25    |

3. Link the reduction key to the item's coverage group.
3. On the **Master plans** page, in the **Method used to reduce forecast requirements** field, select **Percent - reduction key**.

If you run forecast scheduling on January 1, the demand forecast requirements are consumed according to the percentages that you set up on the **Reduction keys** page. The following requirement quantities are transferred to the master plan.

| Month                | Planned order quantity    | Calculation  |
|----------------------|---------------------------| -----------  |
| January              | 0                         | = 0% * 1000  |  
| February             | 250                       | = 25% * 1000 | 
| March                | 500                       | = 50% * 1000 |
| April                | 750                       | = 75% * 1000 |
| May through December | 1000                      | = 100% * 1000|

## Transactions - reduction key

If you choose **Transactions - reduction key**, the forecast requirements are reduced by the transactions that occur during the time periods that are defined by the reduction key. 

### Example: Transactions - reduction key 

This example shows how actual orders that occur during the periods that are defined by the reduction key reduce demand forecast requirements.

On the **Master plans** page, in the **Reduction principle** field, select **Transactions - reduction key**.

The following sales orders exist on January 1.

| Month    | Number of pieces ordered |
|----------|--------------------------|
| January  | 956                      |
| February | 1,176                    |
| March    | 451                      |
| April    | 119                      |

If you use the same demand forecast of 1,000 pieces per month, the following requirement quantities are transferred to the master plan.

| Month                | Number of pieces required |
|----------------------|---------------------------|
| January              | 44                        |
| February             | 0                         |
| March                | 549                       |
| April                | 881                       |
| May through December | 1000                      |

## Transactions - dynamic period

If you choose **Transactions - dynamic period**, the forecast requirements are reduced by the actual order transactions that occur during the dynamic period. The dynamic period covers the current forecast dates and ends with the start of the next forecast. 

In other words, master planning will create planned orders to supply the forecasted demand (forecast requirements). But, when actual order transactions are placed, the forecast requirements will be reduced. The actual transactions "consume" part of the forecasted requirements.

When this option is used, the following behavior occurs:
- Reduction keys are not required nor used. 
- If the forecast is reduced completely, the forecast requirements for the current forecast become zero
- If there is no future forecast, forecast requirements from the last forecast that was entered are reduced
- Time fences are included in the forecast reduction calculation
- Positive days are included in the forecast reduction calculation
- If actual order transactions are greater than the forecasted requirements, the remaining transactions are not forwarded to the next forecast period.

### Example 1: Transactions - dynamic period

Here a simple example of how Transactions - dynamic period works is shown.

1. Include a **Forecast** as the one shown.

   | Date       | Demand forecast |
   |------------|-----------------|
   | January 1  | 1,000           |
   | February 1 | 500             |
   
2. Create **sales orders** as follows.

   | Date        | Sales order quantity |
   |-------------|----------------------|
   | January 15  | 500                  |
   | Febrary 15  | 100                  |
   
3. The following planned orders will be created:

| Demand forecast date | Quantity         | Explanation                                 |
|--------------------- |------------------| ------------------------------------------- |
| January 1            | 800              | Forecast requirements (=1000-200)           |
| January 15           | 200              | Sales orders requirements                   |
| February 1           | 600              | Forecast requirements (=1000-400)           |
| February 15          | 400              | Sales orders requirements                   |

### Example 2: Transactions - dynamic period

In most cases, systems are set up so that transactions reduce demand forecast within specific forecast periods: weeks, months, and so on. These periods are defined in the reduction key. However, the time between two demand forecast lines can also *imply* a period.

1. Create a **demand forecast** for the following dates and quantities.

   | Date       | Demand forecast |
   |------------|-----------------|
   | January 1  | 1,000           |
   | January 5  | 500             |
   | January 12 | 1,000           |

In this forecast, there isn't a clear period between the forecast dates: between the first and second dates there is a four-day span, and between the second and third dates there is a seven-day span. These various spans are the dynamic periods.

2. Create **sales order lines** as follows.

   | Date                             | Sales order quantity |
   |----------------------------------|----------------------|
   | December 15 in the previous year | 500                  |
   | January 3                        | 100                  |
   | January 10                       | 200                  |

The forecast will be reduced as follows:

-   The first sales order isn't within any period, so it won't reduce any forecast.
-   The second sales order is between January 1 and January 5, so it will reduce the forecast for January 1 by 100.
-   The third sales order is between January 5 and January 12, so it will reduce the forecast for January 5 by 200.

Therefore, the following planned orders will be created:

| Demand forecast date              | Quantity         | Explanation                                                    |
|----------------------             |------------------| -------------------------------------------------------------  |
| December 15 in the previous year  | 500              | Sales order requirements                                       |
| January 1                         | 900              | Forecast requirments period January 1 to January 5 (=1000-100) |
| January 3                         | 100              | Sales order requirements                                       |
| January 5                         | 300              | Forecast requirements period January 5 to January 10 (=500-200)|
| January 12                        | 1000             | Forecast requirements period January 12 to end                 |


# Create and set up a forecast reduction key

The reduction key is used in **Transactions - reduction key** and **Percent- reduction key** methods of reducing the forecast requirements. Follow these steps to create and setup a reduction key.

1. Go to **Master planning > Setup > Coverage > Reduction keys.
2. Click New or press CTRL+N to create a new reduction key.
3. Enter an identifier for the key in the **Reduction key** field, and then enter a name for it in the **Name** field. It is a unique ID for the forecast reduction key.
4. Define the time periods and the reduction key percentage in each of them:
   - The **effective date** indicates the date from which to start the creation of the periods. When set to yes, the periods will start from the effective date. When set to No, the periods will start from the date that master planning is run. 
   - Define the time periods during which you want the forecast reduction to occur. 
   - For a particular time period, specify the **percentages** by which you want to reduce the forecast requirements. You can enter positive values to decrease requirements or negative values to increase requirements. 

# Use a reduction key

The forecast reduction key must be assigned to the coverage group of the item. Follow these steps to assign it to the coverage group:
1. Click **Master planning > Setup > Coverage > Coverage groups**.
2. In the **Reduction key** field on the Other tab, select a reduction key to assign to the coverage group. The reduction key then applies for the items that belong to the coverage group.
3. To use a reduction key to calculate forecast reduction during master scheduling, you must define this setting in the forecast plan or the master plan setup.
Click **Master planning > Setup > Plans > Forecast plans**.
–or–
Click **Master planning > Setup > Plans > Master plans**.
	4. In the Reduction principle field on the General tab, select the **Percent - reduction key** option or the **Transactions - reduction** key option.

# Reduce a forecast by transactions

When you select **Transactions - reduction key** or **Transactions - dynamic period** as the method to reduce forecast requirements, you can select whether you want all transcations to reduce the forecast (**All transactions**) or only the sales orders (**Orders**). 
You can choose the desired option under **Reduce forecast by** field in the Released products page, under the Other tab. 


Additional resources
--------

[Master plans](master-plans.md)



