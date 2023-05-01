--- 
# required metadata 
 
title: "Guide: Create a baseline forecast"
description: A production planner can create a baseline forecast either by using time series forecast models or by copying the historical demand. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ReqIntercompanyPlanningGroupSetup, ReqIntercompanyPlanningGroupAllocKeys, ReqDemPlanForecastParameters, ReqDemPlanCreateForecastDialog, SysQueryForm, ReqDemPlanForecastViewer   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Guide: Create a baseline forecast

[!include [banner](../../includes/banner.md)]

A production planner can create a baseline forecast either by using time series forecast models or by copying the historical demand. This procedure shows how to copy the historical demand to create a baseline forecast for all products using one item allocation key.

## Set up an item allocation key

1. Go to **Master planning > Setup > Intercompany planning groups**.
2. Use the Quick Filter to find records. For example, filter on the *Name* field with a value of *10*.
    * Demand forecasting runs across legal entities. That's why you need to set up all the companies for which you want to generate forecasts in one intercompany planning group.  
3. In the list, find and select the desired record.
4. Select **Item allocation keys**.
    * Select all the item allocation keys for which you want to create forecasts.  
5. In the list, mark the selected row.
    * Select D_Aloc item allocation key.  
6. Select **>**.
7. Close the page.
8. Close the page.

## Set up the demand forecasting parameters

1. Go to **Master planning > Setup > Demand forecasting > Demand forecasting parameters**.
2. Expand the **Forecast algorithm parameters** section.
3. In the **Forecast generation strategy** field, select **Copy over historical demand**.
4. Select **Save**.

## Create a baseline forecast

1. Go to **Master planning > Forecasting > Demand forecasting > Generate statistical baseline forecast**.
2. In the **From date** field, enter a date.
    * If you have sales orders starting from January 1, 2015, enter this date. If you don't, enter the earliest date of your sales orders.  
3. In the **To date** field, enter a date.
    * Enter the last date of your sales orders, for example *2015-03-31*.  
4. In the **From date** field, enter a date.
    * Enter *2015-04-01*. This date will be automatically calculated as the start date of the next forecasting bucket.  
5. Expand the **Records to include** section.
6. Select **Filter**.
7. In the list, mark the selected row.
    * Mark the row where **Field** = *Intercompany planning group*.  
8. In the **Criteria** field, type a value.
    * Type the intercompany planning group (for example, *10*) that you used in the first task.  
9. In the list, find and select the desired record.
    * Select the row where **Field** = *Item allocation key*.  
10. In the **Criteria** field, type a value.
11. Select **OK**.
12. Expand the **Advanced parameters** section.
13. In the **Forecast bucket** field, select *Month*.
14. In the **Forecast horizon** field, enter *3*.
15. In the **Freeze time fence** field, enter *1*.
16. Select **OK**.

## Visualize the demand forecast

1. Go to **Master planning > Forecasting > Demand forecasting > Adjusted demand forecast**.
2. In the aggregated view table, select the cell in row 1, column 2. This is the second month for which you have created forecast.
3. Set **QtyCell** to *400*.
    * In the cell, enter a different number than the one that was forecasted, for example, 400.  
4. You have made a manual adjustment to the forecast. Notice the graphical indication in the next step.
5. Select **Forecast line details**.
    * In this page, you can see the accuracy values, historical demand, and forecast. You can make changes to the forecast as well.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]