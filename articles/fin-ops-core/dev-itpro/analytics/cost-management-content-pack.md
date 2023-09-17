---
title: Cost management Power BI content
description: This article describes what is included in the Cost management Power BI content.
author: JennySong-SH
ms.date: 03/16/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.custom: 270314
ms.assetid: 9680d977-43c8-47a7-966d-2280ba21402a
ms.search.industry: Manufacturing
ms.search.form: CostAdminWorkspace, CostAnalysisWorkspace, CostObjectWithLowestAccuracy, CostVarianceChart, CostObjectWithLowestTurn
---

# Cost management Power BI content

[!include [banner](../includes/banner.md)]

## Overview

The **Cost management** Microsoft Power BI content is intended for inventory accountants or individuals in the organization who are responsible for or interested in the status of inventory or work in progress (WIP), or who are responsible for or interested in analyzing standard cost variances.

This Power BI content provides a categorized format that helps you monitor the performance of inventories and visualize how cost flows through them. You can gain managerial insights such as the turnover ratio, number of days that inventory is on hand, accuracy, and "ABC classification" at your preferred aggregated level (company, item, item group, or site). The information that is made available can also be used as a detailed supplement to the financial statement.

The Power BI content is built on the **CostObjectStatementCacheMonthly** aggregated measurement, which has the **CostObjectStatementCache** table as its primary data source. This table is managed by the Data set cache framework. By default, the table is updated every 24 hours, but you can change the update frequency or enable manual updates in the configuration of the data set cache. Manual updates can be run in either the **Cost administration** workspace or the **Cost analysis** workspace.

After every update of the **CostObjectStatementCache** table, the **CostObjectStatementCacheMonthly** aggregated measurement must updated before data in the Power BI visualizations is updated.

## Accessing the Power BI content

The **Cost management** Power BI content is shown in the **Cost administration** and **Cost analysis** workspaces.

The **Cost administration** workspace contains the following tabs:

- **Overview** – This tab shows application data.
- **Inventory accounting status** – This tab shows Power BI content.
- **Manufacturing accounting status** – This tab shows Power BI content.

The **Cost analysis** workspace contains the following tabs:

- **Overview** – This tab shows application data.
- **Inventory accounting analysis** – This tab shows Power BI content.
- **Manufacturing accounting analysis** – This tab shows Power BI content.
- **Std. cost variance analysis** – This tab shows Power BI content.

## Report pages that are included in the Power BI content

The **Cost management** Power BI content includes a set of report pages that consist of a set of metrics. These metrics are visualized as charts, tiles, and tables. 

The following tables provide an overview of the visualizations in the **Cost management** Power BI content.

### Inventory accounting status

| Report page                               | Visualization                                   |
|-------------------------------------------|-------------------------------------------------|
| Inventory overview                        | Beginning balance                               |
|                                           | Net change                                      |
|                                           | Net change %                                    |
|                                           | Ending balance                                  |
|                                           | Inventory accuracy                              |
|                                           | Inventory turnover ratio                        |
|                                           | Days inventory on-hand                          |
|                                           | Active product in period                        |
|                                           | Active cost objects in period                   |
|                                           | Balance by item group                           |
|                                           | Balance by site                                 |
|                                           | Statement by category                           |
|                                           | Net change by quarter                           |
| Inventory overview by site and item group | Inventory accuracy by site                      |
|                                           | Inventory turnover ratio by site                |
|                                           | Inventory ending balance by site                |
|                                           | Inventory accuracy by item group                |
|                                           | Inventory turnover ratio by item group          |
|                                           | Inventory ending balance by site and item group |
| Inventory statement                       | Inventory statement                             |
| Inventory statement by site               | Inventory statement by site                     |
| Inventory statement by product hierarchy  | Inventory statement                             |
| Inventory statement by product hierarchy  | Inventory statement by site                     |

### Manufacturing accounting status

| Report page                | Visualization                       |
|----------------------------|-------------------------------------|
| WIP overview YTD           | Beginning balance                   |
|                            | Net change                          |
|                            | Net change %                        |
|                            | Ending balance                      |
|                            | WIP turnover ratio                  |
|                            | Days WIP on-hand                    |
|                            | Active cost object in period        |
|                            | Net change by resource group        |
|                            | Balance by site                     |
|                            | Statement by category               |
|                            | Net change by quarter               |
| WIP statement              | Beginning balance                   |
|                            | Ending balance                      |
|                            | WIP statement by category           |
| WIP statement by site      | Beginning balance                   |
|                            | Ending balance                      |
|                            | WIP statement by category and site  |
| WIP statement by hierarchy | Beginning balance                   |
|                            | Ending balance                      |
|                            | WIP statement by category hierarchy |

### Inventory accounting analysis

| Report page        | Visualization                                                                |
|--------------------|------------------------------------------------------------------------------|
| Inventory details  | Top 10 resources by ending balance                                           |
|                    | Top 10 resources by net change increase                                      |
|                    | Top 10 resources by net change decrease                                      |
|                    | Top 10 resources by inventory turnover ratio                                 |
|                    | Resources by low inventory turnover ratio and ending balance above threshold |
|                    | Top 10 resources by low accuracy                                             |
| ABC classification | Inventory ending balance                                                     |
|                    | Consumed material                                                            |
|                    | Sold (COGS)                                                                  |
| Inventory trends   | Inventory ending balance                                                     |
|                    | Inventory net change                                                         |
|                    | Inventory turnover ratio                                                     |
|                    | Inventory accuracy                                                           |

### Manufacturing accounting analysis

| Report page | Visualization      |
|-------------|--------------------|
| WIP trends  | WIP ending balance |
|             | WIP net change     |
|             | WIP turnover ratio |

### Std. cost variance analysis

| Report page                             | Visualization                                        |
|-----------------------------------------|------------------------------------------------------|
| Purchase price variance (Std. cost) YTD | Procured balance                                     |
|                                         | Purchase price variance                              |
|                                         | Purchase price variance ratio                        |
|                                         | Variance by item group                               |
|                                         | Variance by site                                     |
|                                         | Purchase price by quarter                            |
|                                         | Purchase price by quarter and Item group             |
|                                         | Top 10 resources by unfavorable purchase price ratio |
|                                         | Top 10 resources by favorable purchase price ratio   |
| Production variance (Std. cost) YTD     | Manufactured cost                                    |
|                                         | Production variance                                  |
|                                         | Production variance ratio                            |
|                                         | Variance by item group                               |
|                                         | Variance by site                                     |
|                                         | Production variance by quarter                       |
|                                         | Production variance by quarter and variance type     |
|                                         | Top 10 resources by unfavorable production variance  |
|                                         | Top 10 resources by favorable production variance    |

## Understanding the data model and entities

Data from the application is used to fill the report pages in the **Cost management** Power BI content. This data is represented as aggregate measurements that are staged in the entity store, which is a Microsoft SQL Server database that is optimized for analytics. For more information, see [Power BI integration with Entity store](power-bi-integration-entity-store.md).

The key aggregate measurements of the following objects are used as the basis of the Power BI content.

| Object                          | Key aggregate measurements | Data source for finance and operations | Field               |
|---------------------------------|----------------------------|----------------------------------------|---------------------|
| CostObjectStatementCacheMonthly | Amount                     | CostObjectStatementCache               | Amount              |
| CostObjectStatementCacheMonthly | Quantity                   | CostObjectStatementCache               | Qty                 |
| CostInventoryAccountingKPIGoal  | AnnualInventoryTurn        | CostInventoryAccountingKPIGoal         | AnnualInventoryTurn |
| CostInventoryAccountingKPIGoal  | InventoryAccuracy          | CostInventoryAccountingKPIGoal         | InventoryAccuracy   |

The following table shows the key calculated measurements in the Power BI content.

| Measure                            | Calculation |
|------------------------------------|-------------|
| Beginning balance                  | Beginning balance = \[Ending balance\]-\[Net change\] |
| Beginning balance qty.             | Beginning balance qty. = \[Ending balance qty.\]-\[Net change qty.\] |
| Ending balance                     | Ending balance = (CALCULATE(SUM(\[Amount\]), FILTER(ALL(FiscalCalendar) ,FiscalCalendar\[MONTHSTARTDATE\] \<= MAX(FiscalCalendar\[MONTHSTARTDATE\])))) |
| Ending balance qty.                | Ending balance qty. = CALCULATE(SUM(\[QTY\]), FILTER(ALL(FiscalCalendar),FiscalCalendar\[MONTHSTARTDATE\] \<= MAX(FiscalCalendar\[MONTHSTARTDATE\]))) |
| Net change                         | Net change = SUM(\[AMOUNT\]) |
| Net change qty.                    | Net change qty. = SUM(\[QTY\]) |
| Inventory turnover ratio by amount | Inventory turnover ratio by amount = if(OR(\[Inventory average balance\] \<= 0, \[Inventory sold or consumed issues\] \>= 0), 0, ABS(\[Inventory sold or consumed issues\])/\[Inventory average balance\]) |
| Inventory average balance          | Inventory average balance = ((\[Ending balance\] + \[Beginning balance\]) / 2) |
| Days inventory on-hand             | Days inventory onhand = 365 / CostObjectStatementEntries\[Inventory turnover ratio by amount\] |
| Inventory accuracy                 | Inventory accuracy by amount = IF(\[Ending balance\] \<= 0, IF(OR(\[Inventory counted amount\] \<\> 0, \[Ending balance\] \< 0), 0, 1), MAX(0, (\[Ending balance\] - ABS(\[Inventory counted amount\]))/\[Ending balance\])) |

The following key dimensions are used as filters to slice the aggregate measurements, so that you can achieve greater granularity and gain deeper analytical insights.


| Entity                                                  | Examples of attributes                          |
|---------------------------------------------------------|-------------------------------------------------|
| Products                                                | Product number, Product name, Unit, Item groups |
| Category hierarchies (Assigned to role Cost management) | Category hierarchy, Category level              |
| Legal entities                                          | Legal entity names                              |
| Fiscal calendars                                        | Fiscal calendar, Year, Quarter, Period, Month   |
| Site                                                    | ID, Name, Address, State, Country/Region               |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

