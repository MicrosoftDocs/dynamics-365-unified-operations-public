---
# required metadata

title: Production performance Power BI content
description: This topic describes what is included in the Production performance Power BI content.
author: AndersGirke
ms.date: 12/19/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  ProductionPerformancePowerBI
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: 
ms.author: aevengir
ms.search.validFrom: 2016-11-30 
ms.dyn365.ops.version: Version 1611 
---

# Production performance Power BI content

[!include [banner](../includes/banner.md)]

This topic describes what is included in the **Production performance** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content.

## Overview

The **Production performance** Power BI content is for production managers or individuals in the organization who are responsible for production control.

The reports that are included let you use Power BI to monitor the performance of manufacturing operations with regard to timely execution, quality, and cost. The reports use transactional data from production orders and batch orders, and provide both an aggregate view of company-wide production metrics and a breakdown of metrics by product and resource.

The Power BI content highlights the organization's ability to complete production on time and in full. Future performance is projected based on the production plans. Comprehensive reports provide detailed insights into product defects that are caused by production, and also the defect rates for resources and operations.

This Power BI content also lets you analyze production variances. Production variances are calculated as the difference between estimated cost and realized cost. Production variances are calculated when production orders or batch orders reach **Ended** status.

The **Production performance** Power BI content includes data that originates from production orders and batch orders. The reports don't include data that is related to kanban productions.

## Accessing the Power BI content
The **Production performance** Power BI content is shown on the **Production performance** page (**Production control** \> **Inquiries and reports** \> **Production performance analysis** \> **Production performance**). 

## Metrics that are included in the Power BI content

The **Production performance** Power BI content includes a set of report pages. Each page consists of a set of metrics that are visualized as charts, tiles, and tables.

The following table provides an overview of the visualizations that are included.

| Report page                                | Charts | Tiles |
|--------------------------------------------|--------|-------|
| Production performance                     | <ul><li>Number of production by date</li><li>Number of productions by product and item group</li><li>Number of planned productions by date</li><li>Bottom 10 products by on-time &amp; in-full</li></ul> | <ul><li>Total orders</li><li>On-time &amp; in full %</li><li>Incomplete %</li><li>Early %</li><li>Late %</li></ul> |
| Defects by product                         | <ul><li>Defective rate (ppm) by date</li><li>Defective rate (ppm) by product and item group</li><li>Quantity produced by date</li><li>Top 10 products by effective rate</li></ul> | <ul><li>Defective rate (ppm)</li><li>Defective quantity</li><li>Total quantity</li></ul> |
| Defects trend by product                   | Defect rate (ppm) by quantity produced | Defect rate (ppm) |
| Defects by resource                        | <ul><li>Defect rate (ppm) by date</li><li>Defect rate (ppm) by resource and Site</li><li>Defect rate (ppm) by operation</li><li>Top 10 resources by defect rate</li></ul> | Defective quantity |
| Defects trend by resource                  | Defect rate (ppm) by quantity processed | |
| Production variances for job order costing | <ul><li>Production variance by date and cost group type</li><li>Production variance by site and cost group type</li><li>Top 10 products with unfavorable production variance</li><li>Top 10 unfavorable production variance by resource</li></ul> | <ul><li>Realized cost</li><li>Production variance</li><li>Production variance %</li></ul> |


## Understanding the data model and entities

The following data is used for the report pages in the **Production performance** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store. The Entity store is a Microsoft SQL Server database that is optimized for analytics. To learn more about the entity store, see [Power BI integration with Entity store](power-bi-integration-entity-store.md).

The following table shows the key aggregate measurements that are used as the basis of the Power BI content.

| Entity                   | Key aggregate measurements  | Data source for Finance and Operations apps | Field              |
|--------------------------|-----------------------------|----------------------------------------|--------------------|
| CostCalculation          | CostAmount                  | ProdCalcTransExpanded                  | CostAmount         |
| CostCalculation          | CostMarkup                  | ProdCalcTransExpanded                  | CostMarkup         |
| CostCalculation          | ActualCostAmount            | ProdCalcTransExpanded                  | RealCostAmount     |
| CostCalculation          | RealCostAdjustment          | ProdCalcTransExpanded                  | RealCostAdjustment |
| RouteTransactions        | ErrorQuantity               | ProdRouteTransExpanded                 | QtyError           |
| RouteTransactions        | GoodQuantity                | ProdRouteTransExpanded                 | QtyGood            |
| ProductionOrder          | DaysDelayed                 | ProdTableExpanded                      | DaysDelayed        |
| ProductionOrder          | LeadTime                    | ProdTableExpanded                      | LeadTime           |
| ProductionOrder          | PlannedLeadTime             | ProdTableExpanded                      | PlannedLeadTime    |
| ProductionOrder          | ProductionOrderCount        | ProdTableExpanded                      |                    |
| CoproductCostCalculation | CoproductCostAmount         | PmfCoByProdCalcTransExpanded           | CostAmount         |
| CoproductCostCalculation | CoproductCostMarkup         | PmfCoByProdCalcTransExpanded           | CostMarkup         |
| CoproductCostCalculation | CoproductRealCostAdjustment | PmfCoByProdCalcTransExpanded           | RealCostAdjustment |
| CoproductCostCalculation | CoproductActualCostAmount   | PmfCoByProdCalcTransExpanded           | RealCostAmount     |

The following table shows how the key aggregate measurements are used to create several calculated measures in the content's dataset.

| Measure                  | How the measure is calculated |
|--------------------------|-------------------------------|
| Production variance, %   | SUM('Production variance'\[Production variance\]) / SUM('Production variance'\[Estimated cost\]) |
| All planned orders       | COUNTROWS('Planned production order') |
| Early                    | COUNTROWS(FILTER('Planned production order', 'Planned production order'\[Scheduled end date\] \< 'Planned production order'\[Requirement date\])) |
| Late                     | COUNTROWS(FILTER('Planned production order', 'Planned production order'\[Scheduled end date\] \> 'Planned production order'\[Requirement date\])) |
| On-time                  | COUNTROWS(FILTER('Planned production order', 'Planned production order'\[Scheduled end date\] = 'Planned production order'\[Requirement date\])) |
| On-time %                | IF ( 'Planned production order'\[On-time\] \<\> 0, 'Planned production order'\[On-time\], IF ('Planned production order'\[All planned orders\] \<\> 0, 0, BLANK()) ) / 'Planned production order'\[All planned orders\] |
| Completed                | COUNTROWS(FILTER('Production order', 'Production order'\[Is RAF'ed\] = TRUE)) |
| Defective rate (ppm)     | IF( 'Production order'\[Total quantity\] = 0, BLANK(), (SUM('Production order'\[Defective quantity\]) / 'Production order'\[Total quantity\]) \* 1000000) |
| Delayed production rate  | 'Production order'\[Late \#\] / 'Production order'\[Completed\] |
| Early & in full          | COUNTROWS(FILTER('Production order', 'Production order'\[Is in full\] = TRUE && 'Production order'\[Is early\] = TRUE)) |
| Early \#                 | COUNTROWS(FILTER('Production order', 'Production order'\[Is early\] = TRUE)) |
| Early %                  | IFERROR( IF('Production order'\[Early \#\] \<\> 0, 'Production order'\[Early \#\], IF('Production order'\[Total orders\] = 0, BLANK(), 0)) / 'Production order'\[Total orders\], BLANK()) |
| Incomplete               | COUNTROWS(FILTER('Production order', 'Production order'\[Is in full\] = FALSE && 'Production order'\[Is RAF'ed\] = TRUE)) |
| Incomplete %             | IFERROR( IF('Production order'\[Incomplete\] \<\> 0, 'Production order'\[Incomplete\], IF('Production order'\[Total orders\] = 0, BLANK(), 0)) / 'Production order'\[Total orders\], BLANK()) |
| Is delayed               | 'Production order'\[Is RAF'ed\] = TRUE && 'Production order'\[Delayed value\] = 1 |
| Is early                 | 'Production order'\[Is RAF'ed\] = TRUE && 'Production order'\[Days delayed\] \< 0 |
| Is in full               | 'Production order'\[Good quantity\] \>= 'Production order'\[Scheduled quantity\] |
| Is RAF'ed                | 'Production order'\[Production status value\] = 5 \|\| 'Production order'\[Production status value\] = 7 |
| Late & in full           | COUNTROWS(FILTER('Production order', 'Production order'\[Is in full\] = TRUE && 'Production order'\[Is delayed\] = TRUE)) |
| Late \#                  | COUNTROWS(FILTER('Production order', 'Production order'\[Is delayed\] = TRUE)) |
| Late %                   | IFERROR( IF('Production order'\[Late \#\] \<\> 0, 'Production order'\[Late \#\], IF('Production order'\[Total orders\] = 0, BLANK(), 0)) / 'Production order'\[Total orders\], BLANK()) |
| On-time & in full        | COUNTROWS(FILTER('Production order', 'Production order'\[Is in full\] = TRUE && 'Production order'\[Is delayed\] = FALSE && 'Production order'\[Is early\] = FALSE)) |
| On-time & in full %      | IFERROR( IF('Production order'\[On-time & in full\] \<\> 0, 'Production order'\[On-time & in full\], IF('Production order'\[Completed\] = 0, BLANK(), 0)) / 'Production order'\[Completed\], BLANK()) |
| Total orders             | COUNTROWS('Production order') |
| Total quantity           | SUM('Production order'\[Good quantity\]) + SUM('Production order'\[Defective quantity\]) |
| Defect rate (ppm)        | IF( 'Route transactions'\[Processed quantity\] = 0, BLANK(), (SUM('Route transactions'\[Defective quantity\]) / 'Route transactions'\[Processed quantity\]) \* 1000000) |
| Defect ratio mixed (ppm) | IF( 'Route transactions'\[Total mixed quantity\] = 0, BLANK(), (SUM('Route transactions'\[Defective quantity\]) / 'Route transactions'\[Total mixed quantity\]) \* 1000000) |
| Processed quantity       | SUM('Route transactions'\[Good quantity\]) + SUM('Route transactions'\[Defective quantity\]) |
| Total mixed quantity     | SUM('Production order'\[Good quantity\]) + SUM('Route transactions'\[Defective quantity\]) |

The following table shows the key dimensions that are used as filters to slice the aggregate measurements, so that you can achieve greater granularity and gain deeper analytical insights.

| Entity                    | Examples of attributes                                        |
|---------------------------|---------------------------------------------------------------|
| Reported as finished date | Completion (RAF) date, Month, and Year offset                 |
| Ended date                | Ended month offset and Month                                  |
| Requirement date          | Requirement date month offset and Requirement date            |
| Route transaction date    | Route transaction month offset and Date                       |
| Sites                     | Sites ID, Site name, State, and City                          |
| Entities                  | Id and Name                                                   |
| Resources                 | Resource ID, Resource name, Resource type, and Resource group |
| Products                  | Product number, Product name, Item ID, and Item group         |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]