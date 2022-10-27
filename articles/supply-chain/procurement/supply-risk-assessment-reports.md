---
title: Power BI reports for risks analysis and performance ranking
description: Discover risks in your planned supply and analyze past performance of vendors and products.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to 
ms.date: 10/27/2022 
ms.custom: bap-template
---

# Power BI reports for risks analysis and performance ranking

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.31 GA -->

Supply Chain Management provides both an integrated risk and performance report and two reports that are embedded into the **Supply risk assessment** workspace (supplier performance analysis and risk assessment analysis). All three reports use Power BI and are based on the same metrics as the workspace. Each report offers rich filtering and data slicing options to identify the most pressing supplier performance issues and potential risks for planned supply.

The metric and KPI tiles at the top of each report page show relevant key figures that summarize the performance in each currently selected filter scope (including the total number of purchase orders and order lines). Some risk assessment reports show information about the planned order volume. You'll also typically find performance rates for the percentage of order lines with delivery data on or before requested date, based on order line receipts the rates of on-time (OT), in-full (IF) and on-time in-full (OTIF) delivered order lines.

The metrics and KPI tiles update when you filter or select different vendors, products, regions or delivery methods. This changing information can help you to identify correlations with different factors that impact supply performance.

## Integrated risk and performance report

The integrated risk and performance report only shows information about planned orders and is therefore most relevant for risk assessment. It combines elements of the two embedded reports. See the later sections of this article for information about how to use and interpret its various views.

You can open the integrated risk and performance report in either of the following ways:

- Go to **Procurement and sourcing \> Inquiries and reports \> Supply risk assessment \> Supply risk assessment**.
- Go to **Procurement and sourcing \> Workspaces \> Supply risk assessment**, expand the Links FastTab and then select the **Supply risk assessment** link.

## Embedded supplier performance analysis

The workspace-embedded supplier performance report shows a holistic performance assessment, not only for planned orders, but also for all products that have been purchased previously.

To open the embedded supplier performance analysis report, go to **Procurement and sourcing \> Workspaces \> Supply risk assessment** and then open the **Performance** tab.

All supply performance analysis reports provide a header with slicers and filters. To limit your analysis, select products and use the slicers and filters to select the relevant legal companies, regions, vendors, and item groups. The filter will carry through the different report pages so you don't have to reapply the filter settings repeatedly.

### Vendor and product ranking report

Use the two similar reports for product and vendor ranking to study the historic order performance in terms of OTIF deliveries. Find OTIF trends and outliers in the timeline of deliveries and see them in relation to the total line amounts.

Zoom in on the timeline and select individual data points to see the related vendors or products. Alternatively, select one or more vendors based on their ranking and see the respective performance timeline.

[<img src="media/sra-perf-supplier-rating.png" alt="Performance ranking report for products, screenshot." title="Performance ranking report for products, screenshot" width="720" />](media/sra-perf-supplier-rating.png)

### Multi perspective OTIF ranking

In this report, the worst OTIF rankings are calculated from various perspectives and are shown side-by-side for products, vendors, delivery methods, and sites. Use individual or combined dimensions to identify bottlenecks that may lead to a drop in supply performance.

[<img src="media/sra-otif-analysis.png" alt="Multi dimensional OTIF ranking report, screenshot." title="Multi dimensional OTIF ranking report, screenshot" width="720" />](media/sra-otif-analysis.png)

## Embedded supply risk assessment analysis

The workspace-embedded supply risk assessment report shows a holistic performance assessment, not only for planned orders, but also for all products that have been purchased previously.

To open the embedded supplier performance analysis report, go to **Procurement and sourcing \> Workspaces \> Supply risk assessment** and then open the **Risk** tab.

The risk assessment report turns the performance observations based on purchase order receipts into a risk calculation for planned orders.

All supply risk analysis reports carry a slicer and filter header that includes a master plan selector. Use this filter to select a single master plans to prevent the unwanted double accounting of planned orders from multiple plans.

### Risk assessment overview report

This report helps you analyze the calculated risks for your planned purchases. After filtering to the desired scope, you'll see the top-10 products ranked by risk in their aggregated quantity and amount. The high-risk classification is derived from the planned product quantity and amount multiplied by the observed OTIF rate of past orders. The low OTIF risk is the remaining total quantity or amount.

> [!NOTE]
> The risk assessment is most statically significant when most of the order lines in the observed time frame are for products where few fundamental changes to surrounding factors are expected.

Once you zoom in on a group of planned product supplies, you can study additional performance statistics for the products and vendors assigned to the planned orders.

[<img src="media/sra-risk-planned-purchase.png" alt="Risk assessment report for planned purchase, screenshot." title="Risk assessment report for planned purchase, screenshot" width="720" />](media/sra-risk-planned-purchase.png)

### Detailed sourcing risk breakdown

The detailed planned purchase risk breakdown lists show all at-risk products within their item groups, with planned quantity and amount and the respective risk amounts.

This view can help you to study vendors used in past orders that led to bad performance. Consider using other or additional vendors to reduce the risk for future planned purchases.

[<img src="media/sra-risk-sourcing.png" alt="Sourcing risk report, screenshot." title="Sourcing risk report, screenshot" width="720" />](media/sra-risk-sourcing.png)

### Compare vendor locations between past order and planned orders

To better compare the overall supply originating location (vendor location) study the geographic maps that highlight side-by-side heat maps, where supply was coming from purchase orders versus planned supply orders.

[<img src="media/sra-risk-past-vs-planned-purchase.png" alt="Risk assessment by comparing past orders and planned sourcing, screenshot." title="Risk assessment by comparing past orders and planned sourcing, screenshot" width="720" />](media/sra-risk-past-vs-planned-purchase.png)

### Supply flow comparison from the past against planned supply

Dive deeper on the supply from source to delivery location in comparison of past purchase and planned supply. Filter by items identified to be at risk and by delivery methods to identify potential risks imposed by the route and method of delivery.

[<img src="media/sra-risk-supply-flow.png" alt="Risk assessment comparing supply flow, screenshot." title="Risk assessment comparing supply flow, screenshot" width="720" />](media/sra-risk-supply-flow.png)
