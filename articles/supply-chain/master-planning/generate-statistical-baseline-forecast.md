---
# required metadata

title: Generate a statistical baseline forecast
description: This article provides information about the parameters and filters that are used in the calculation of demand forecasting. 
author: t-benebo
ms.date: 07/08/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqDemPlanCreateForecastDialog
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 42190463-2a64-4f63-b653-10cac3df0692
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Generate a statistical baseline forecast

[!include [banner](../includes/banner.md)]

This article provides information about the parameters and filters that are used in the calculation of demand forecasting. 

When you create a baseline forecast, you must first specify the parameters and filters that are used in the calculation. For example, you can create a baseline forecast that estimates demand based on transaction data from the past year for a specific company, for the coming month, and for a selected group of items. 

To generate a demand forecast, go to **Master planning &gt; Forecasting &gt; Demand forecasting &gt; Generate statistical baseline forecast**. 

The forecast bucket can be selected at forecast generation time. The available values are: Day, Week, and Month. 

The number of buckets to generate a forecast for is set in the **Forecast horizon** field. 

When the forecast strategy is set to **Copy over historical demand**, the end of the historical horizon is ignored. The system copies the number of buckets specified in the **Forecast horizon** field to the forecast demand, starting from the date set in the **From date** field under **Historical horizon**. By copying historical demand from a certain date forward, production planners can make the plan for the next quarter in two ways:

-   By copying the demand from the same quarter last year.
-   By copying the demand from the previous quarter.

To prevent confusion in the production plans, a certain number of forecast buckets can be frozen. This number is set in the **Freeze time fence** field. On the **Adjusted demand forecast** page, the cells for the frozen buckets are disabled, to give a visual indication that those values should not be changed. 

The start date for the baseline demand forecast doesn’t have to be the current date or a date in the future. To set a different start date, use the **Baseline forecast start date - From date** field. For example, in June, users can generate a forecast for the next year. Because the forecast buckets between the end of historical demand and the start of the baseline are missing, the predictions might not be accurate. If you are using the Demand forecasting service, there are four ways in which you can fill in the missing gaps. You can choose the method that you want by setting the MISSING\_VALUE\_SUBSTITUTION parameter on the **Demand forecasting parameters** page. 

> [!NOTE]
> Missing value substitution only works for the gaps in data in between the start and end dates for historical data. It will not fill in data before or after the last physical data point, it only acts as extrapolation between actual existing data points. 

The **Baseline forecast start date** - **From date** field has to be set to the beginning of a forecast bucket, for example, in the United States, a Sunday if the forecasting bucket is the week. The system automatically adjusts the **Baseline forecast start date** - **From date** field to match the beginning of a forecast bucket. 

The **Baseline forecast start date** - **From date** field can be set to a date in in the past. In other words, it is possible to generate a demand forecast in the past. This is useful, because it lets users adjust the forecast service parameters so that the statistical forecast generated in the past matches the actual historical demand. Users can then continue using these parameter settings to generate a statistical baseline forecast for the future. 

Manual adjustments made in previous demand forecasting iterations can be automatically applied to the new baseline forecast if the **Transfer manual adjustments to the demand forecas**t check box is selected. If the check box is cleared, the manual adjustments are not added to the baseline forecast – but they are not deleted. Manual adjustments made to a forecast can be deleted only at forecast import time, by clearing the **Save the manual adjustments made to the baseline demand forecast** check box. Manual adjustments are saved at authorization time. Therefore, if a user makes manual adjustments to the forecast, but doesn’t authorize the forecast back to Supply Chain Management, the changes are lost. For more information about manual adjustments and how they work, see [Authorize an adjusted forecast](authorize-adjusted-forecast.md). 

A demand forecast generation can have a name and comments to help users identify the forecast that has been generated. These values are visible in forecast generation history on the **Statistical baseline forecast generation history** page. 

The intercompany planning group, item allocation keys, and other filters can be applied at forecast generation time. These can be used to improve performance or to split the data into manageable chunks. However, note that a demand forecast is not generated for the members of any item allocation key that is not associated with an intercompany planning group, even if the item allocation key is selected in the query. 

> [!TIP]
> Sometimes users might receive errors while generating a demand forecast, or forecast generation is completed with no session log. This can happen because of leftover data in the query that was previously used for forecast generation. To resolve this issue, click **Select** to open the **Query** page, select **Reset**, and then regenerate the baseline forecast. 

If the forecast is not generated for a big set of items, but, for example, for one item or one item allocation key at a time, then in order to get better performance, you can select the **Use request response mode** check box on the **Master planning - Setup - Demand forecasting** - **Demand forecasting parameters - Azure Machine Learning** tab.

> [!NOTE]
> A potentially flat looking forecast can be due to the historical data that has to be of a longer historical timeframe (a minimum 3 of time periods in order to pick out patterns, such as 3 years with monthly forecast). To get a better result, you can try changing the granularity of the time range or increase the time range.

## Additional resources

- [Demand forecasting setup](demand-forecasting-setup.md)
- [Make manual adjustments to the baseline forecast](manual-adjustments-baseline-forecast.md)
- [Authorize an adjusted forecast](authorize-adjusted-forecast.md)
- [Webinar: Demand Forecasting with Azure Machine Learning Series](https://aka.ms/DemandForecastingwithAzureMachineLearningSeries)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
