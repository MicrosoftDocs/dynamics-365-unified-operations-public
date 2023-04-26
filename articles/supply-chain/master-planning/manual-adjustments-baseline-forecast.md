---
# required metadata

title: Make manual adjustments to the baseline forecast
description: This article explains how you can make manual adjustments to a baseline forecast and view details of the forecast. 
author: t-benebo
ms.date: 01/07/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqDemPlanForecastViewer
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 72704
ms.assetid: e7c5d44e-07bc-40b1-a4b3-8ba46483ef9e
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Make manual adjustments to the baseline forecast

[!include [banner](../includes/banner.md)]

This article explains how you can make manual adjustments to a baseline forecast and view details of the forecast. 

Before you make manual adjustments, it's important that you understand a few concepts on various pages.

## Grid on the Adjusted demand forecast page
The **Adjusted demand forecast** page includes a grid that has the following structure:

-   The first column shows the items, item allocation keys, companies, and so on, that the forecast has been generated for. The subtitle of the page provides a description of the current forecast dimensions that are shown in the grid. For example, if the subtitle of the page is **Company / Site / Item allocation key**, and one of the row headers in the grid is **USMF / 1 / D\_Alloc**, that row shows the forecast for the USMF company, site 1, and the **D\_Alloc** item allocation key.
-   Subsequent columns represent the forecast buckets that the forecast has been generated for. Each column header is the first date of the forecast bucket that the column shows.
-   The values in the cells represent the forecast for one item, item allocation key, and so on, for that specific forecast bucket.

## Forecast aggregation and de-aggregation
The subtitle of the page shows the level of forecast aggregation. 

For example, if the subtitle of the page is **Company / Site / Allocation key / Item number / Color / Size / Configuration / Style**, there is no forecast aggregation, and the forecast is shown at the level of the item and its dimensions. To change the aggregation, use the **Change forecast dimensions** page, which you can open from the application menu. 

To modify the forecast, click in any of the cells that are available, and type the adjusted forecast value. The edited cell immediately becomes bold to indicate that the forecast that it shows isn't the forecast that the demand forecasting service created, but has been manually adjusted. 

If you change the aggregation to make the page show more aggregated data, you can use the **Demand forecast lines** page to see the individual forecast lines that make up the aggregated forecast. 

For example, you've generated the forecast at the item level, but you know that the demand for this item will increase across all sites because of a promotion or another similar event. In this case, you can set the aggregation to **Company / Item allocation key / Item** on the **Change forecast dimensions** page. You can adjust the global forecast for the item across all sites in the **Adjusted demand forecast** grid. To see the effect of your change across all sites, open the **Demand forecast lines** page. On this page, you will see one line for the item for each site, the adjusted forecast quantity, and the original forecast quantity. 

When the adjustment of the forecasted quantity is made at an aggregated level, the system uses weighted allocation to distribute the change among the lines that create the aggregation. 

You can also make manual adjustments on the **Demand forecast lines** page, by modifying either the **Total quantity** value or the **Quantity** cells in the de-aggregation grid.

## Viewing details of the forecast
You can open the **Demand forecast details** page to view more information about the forecast. 

The **Demand forecast details** page shows the following information in graphical and tabular formats:

-   The historical demand that the forecast predictions are based on.
-   The current forecast that is used by Master planning.
-   The new demand forecast values and the amounts they have been manually adjusted by.
-   The confidence interval for the forecasted values.
-   The forecast model that was used to generate the forecast. If you're viewing aggregated data, you will see the list of all the methods that were used for all the aggregated time series.
-   The internal model accuracy (MAPE). For more information about forecast accuracy, see [Monitor forecast accuracy](monitor-forecast-accuracy.md).

**Notes:**

- The *Forecast model selection on Demand forecast details* feature adds settings on the **Demand forecast details** page that let you select the forecast models to be included. As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Forecast model selection on Demand forecast details* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.
- The confidence interval that appears in the **Forecast** section of the page represents the difference between the confidence interval upper limit and the confidence interval lower limit. To see the values for the upper and lower limits, hover over the chart in the **Historical demand and forecast graphically** section.
- If you use the Demand forecasting Microsoft Azure Machine Learning, you can specify the confidence level percentage that the forecast that is generated should have. A confidence interval consists of a range of values that act as good estimates for the demand forecast. A 95-percent confidence level percentage indicates that there is a 5-percent risk that the demand forecast falls outside the confidence interval range.

You can also make manual adjustments to the forecast on the **Demand forecast details** page, by modifying the values in the **Forecast** row in the **Forecast** section.

## Additional resources

- [Monitor forecast accuracy](monitor-forecast-accuracy.md)
- [Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]