---
title: Power BI reports for risks analysis and performance ranking
description: Discover risks in your planned supply and analyze past performance of vendors and products.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: conceptual
ms.date: 10/17/2022
ms.custom: bap-template
---

# Power BI reports for risks analysis and performance ranking

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The **Supply risk assessment** workspace offers embedded Power BI reports that are based on the same metrics as the workspace. Yet it offers rich filtering and data slicing options to identify the most pressing supplier performance issues and potential risks for planned supply.

The metric and KPI tiles at the top of each report page show relevant key figures that summarize the performance in each currently selected filter scope. These include the total number of purchase orders and order lines in scope for the performance assessment. On some risk assessment reports you will find information on the planned order volume.

You also typically find the performance rates across those for percentage of order lines with delivery data on or before requested date, based on order line receipts the rates of On-Time (OT), In-Full (IF) and On-Time In-Full (OTIF) delivered order lines.

The metric and KPI tiles will update when you filter or select vendors, products, regions, delivery methods which help you to identify correlations with different factors impacting the supply performance.

<!--KFM: We should explain how to open each of these reports, either within each section or in a section by itself (depending on the steps required). -->

<!--KFM: We have a page that doesn't seem to be documented: **Procurement and sourcing \> Inquiries and reports \> Supply risk assessment \> Supply risk assessment**. We should explain what this is for and what to do with it. For me, it's just blank.
. -->

## Supplier performance analysis

All supply performance analysis reports carry a header with slicers and filters. Use these to select the relevant legal companies, regions, vendors, item groups or select products if your want to limit your analysis. The filter will carry through the different report pages so you do not have to reapply the filter settings repeatedly.

### Vendor and product ranking report

Use the two similar reports for product and vendor ranking to study the historic order performance in terms of on-time and in-full deliveries. Find OTIF trends and outliers in the timeline of deliveries and see that in relation to the total line amounts.

You can zoom in on the timeline, and select individual data points to see vendors or products behind. Alternatively select one or more vendors based on their ranking and see the respective performance timeline.

[<img src="media/sra-perf-supplier-rating.png" alt="Performance ranking report for products, screenshot." title="Performance ranking report for products, screenshot" width="720" />](media/sra-perf-supplier-rating.png)

### Multi perspective OTIF ranking

In this report the worst OTIF ranking is calculated from different perspectives and shown side by side for products, vendors, delivery ,methods and sites. Use individual or combinations of the dimensions to identify bottlenecks that may lead to drop in supply performance.

[<img src="media/sra-otif-analysis.png" alt="Multi dimensional OTIF ranking report, screenshot." title="Multi dimensional OTIF ranking report, screenshot" width="720" />](media/sra-otif-analysis.png)

## Supply risk assessment analysis

Risk assessment report turn the performance observations based on purchase order receipts into a risk calculation for planned orders.

All supply risk analysis reports carry a slicer and filter header that includes the Master Plan selector. Use this filter to select only one or your master plans to prevent unwanted double accounting planned orders from multiple plans.

### Risk assessment overview report

find all calculated risks for your planned purchase in this report. After filtering to the desired scope see the top 10 products ranked by risk in their aggregated quantity and amount at high and low risk. The high-risk classification is derived from the planned product quantity and amount multiplied by the observed OTIF rate of past orders. The low OTIF risk is the remaining from the total quantity or amount.

> [!NOTE]
> The risk assessment is statically more significant if you have more order lines in a  observation time frame where not many fundamental changes to surrounding factors can be expected.

Once you circle in on a group of planned product supply you can study additional performance statistics for the products and vendors assigned to the planned orders.

[<img src="media/sra-risk-planned-purchase.png" alt="Risk assessment report for planned purchase, screenshot." title="Risk assessment report for planned purchase, screenshot" width="720" />](media/sra-risk-planned-purchase.png)

### Detailed sourcing risk breakdown

In the detailed planned purchase risk breakdown lists you can find all products at risk within their item groups with planned quantity and amount and the respective risk amounts.

Helpful is here to study vendors used in past orders that led to bad performance and the risk assessment and the vendors assigned in planned orders. Consider using other or additional vendors may reduce the risk for planned purchase.

[<img src="media/sra-risk-sourcing.png" alt="Sourcing risk report, screenshot." title="Sourcing risk report, screenshot" width="720" />](media/sra-risk-sourcing.png)

### Compare vendor locations between past order and planned orders

To better compare the overall supply originating location (vendor location) study the geographic maps that highlight side by side on heatmaps  where supply was coming from in purchase orders versus planned supply orders.

[<img src="media/sra-risk-past-vs-planned-purchase.png" alt="Risk assessment by comparing past orders and planned sourcing, screenshot." title="Risk assessment by comparing past orders and planned sourcing, screenshot" width="720" />](media/sra-risk-past-vs-planned-purchase.png)

### Supply flow comparison from the past against  planned supply

Dive deeper on the supply from source to delivery location in comparison of past purchase and planned supply. Filter by items identified at risk and delivery methods to identify potential risks imposed by the  route and  method of delivery.

[<img src="media/sra-risk-supply-flow.png" alt="Risk assessment comparing supply flow, screenshot." title="Risk assessment comparing supply flow, screenshot" width="720" />](media/sra-risk-supply-flow.png)

## Use date range filtering

A typical filter is the data range filter that you can access in the filter side bar. Select the Date field in the filter side panel and control the time range to look back at when accounting past purchase order lines used for the performance metrics of past order fulfillment. You could, for example, filter on only looking at order lines and receipts of the last 6 month.

## Next steps

You may use additional filters in the reports to reduce the calculation scope of the metrics within the reports.
<!--KFM: I think we can probably remove this section. I moved the section about the date filter out of here. We could maybe add a couple more sections of general advice (that applies to all reports) like that one. -->