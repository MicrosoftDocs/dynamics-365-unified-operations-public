---
# required metadata

title: Sales and profitability performance content pack for Power BI
description: This topic describes what's included in the Dynamics 365 for Operations - Sales and profitability performance content pack for Microsoft Power BI. It explains how to access the reports included in the content pack and provides information about the data model and entities that are used to build the content pack.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-12-01 12 - 21 - 14
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 121
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 260674
ms.assetid: ab457f02-929e-4d34-b813-335be3092287
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Sales and profitability performance content pack for Power BI

This topic describes what's included in the Dynamics 365 for Operations - Sales and profitability performance content pack for Microsoft Power BI. It explains how to access the reports included in the content pack and provides information about the data model and entities that are used to build the content pack.

Overview
--------

This content pack was created for sales managers to monitor the key sales metrics of revenue, gross profit, and profit margins. It uses sales transactional data from Dynamics 365 for Operations, and provides both an aggregate view of the company-wide sales figures and a breakdown of sales performance for customers and products. By highlighting changes in the revenue and profit growth over time, reports can be used to alert managers about positive and negative trends for individual customers and products. Category and regional managers will find it useful to have charts that compare revenue and profitability of different product categories and customer groups to each other to single out laggards and leaders. A comprehensive report that plots individual customer’s revenue versus profit margin offers account managers a data-backed foundation to attune their sales and marketing efforts to each customer’s respective profile. The Sales and profitability performance content pack enables Sales managers to analyze sales performance by:

-   Revenue, year-to-date (by customer group and individual customers, sales categories, and individual products and geographies)
-   Revenue change, year-over-year (by customer regions and sales categories)

Profitability can be analyzed by:

-   Gross profit and profit margin (by customer groups and product sales categories)
-   Gross profit change, year-over-year
-   Customer profitability (by revenue versus gross margin)

## Accessing the content pack
The Sales and profitability performance Power BI content pack is published as an implementation asset in Lifecycle Services (LCS) and can be accessed from Dynamics 365 for Operations. For more information about how to access and launch Power BI reports, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md).

## Metrics included in the content pack
The content pack includes a report that consists of a set of metrics visualized as charts, tiles, and tables. The following table provides an overview of the visualisations in the content pack.

|                        |                                            |                                                         |
|------------------------|--------------------------------------------|---------------------------------------------------------|
| **Report page**        | **Charts**                                 | **Tiles**                                               |
| Revenue by customer    | Top 10 customers by revenue                | Total revenue                                           |
|                        | Total revenue by customer group            | YOY revenue growth                                      |
|                        | Average customer revenue by customer group | Gross margin                                            |
|                        | Revenue & gross profit by customer group   |                                                         |
| Revenue by product     | Revenue & gross profit by sales category   | Total \# of products                                    |
|                        | Top 10 products by revenue                 | Total number of active products and percentage of total |
|                        | Total revenue by sales category            | Number of products accounting for 80% revenue           |
| Revenue by period\*    | Revenue by month                           | YOY revenue growth                                      |
|                        | Trailing revenue variance, YOY             | YOY revenue growth %                                    |
|                        | Total sales variance by customer region    |                                                         |
| Revenue by location    | Sales revenue by city                      |                                                         |
|                        | YOY revenue growth %                       |                                                         |
|                        | Sales revenue by region                    |                                                         |
| Customer profitability | Gross margin versus revenue, by customer   | Gross profit, gross margin, YOY revenue growth          |
| Profitability analysis | Revenue and gross profit by month          |                                                         |
|                        | Top 15 customers by gross margin           |                                                         |
|                        | Gross profit by month, YOY                 |                                                         |

\* Revenue this and last year, and growth by sales category.

## Understanding the data model and entities
Dynamics 365 for Operations data is used to populate the report in the Sales and profitability performance content pack. This is represented as aggregate measurements that are staged in the Entity store, which is a Microsoft SQL database optimized for analytics. Read more about it in the blog [Power BI integration with Entity Store in Dynamics](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/). The aggregate measurements in this content pack are the subset of the aggregate measurements that were available in the Sales Cube in Dynamics AX 2012 and AX 2012 R3. To stage the cube's aggregate measurements in the Entity store you must make them deployable. For more information, see the procedure on how to stage aggregate measurements into the Entity store in the blog [Power BI integration with Entity Store in Dynamics](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/). The following key aggregate measurements of the Invoice lines entity are used as the basis of the content pack.

|               |                                              |                                                 |                                              |                                          |
|---------------|----------------------------------------------|-------------------------------------------------|----------------------------------------------|------------------------------------------|
| **Entity**    | **Key aggregate measurements**               | **Data source for Dynamics 365 for Operations** | **Field**                                    | **Description**                          |
| Invoice lines | Revenue                                      | CustInvoiceTrans                                | SUM(LineAmountMST)                           | Amount in accounting currency            |
|               | Cost of goods sold                           | InventTrans                                     | SUM(CostAmountPosted + CostAmountAdjustment) | Cost amount + adjustment                 |
|               | Commission line amount – accounting currency | CustInvoiceTrans                                | SUM(CommissAmountMST)                        | Commission amount in accounting currency |

The following table shows the key aggregate measurements of the invoice lines entity that are used to create several calculated measures in the content pack’s dataset.

|                   |                                                                                                  |
|-------------------|--------------------------------------------------------------------------------------------------|
| **Measure**       | **Calculated as**                                                                                |
| Gross profit      | SUM(Revenue – COGS – Commission – Sales tax (included in customer invoice line amount))          |
| Gross margin      | SUM(Gross profit / (Revenue - Sales tax (included in customer invoice line amount)))             |
| Revenue last year | Revenue last year = CALCULATE(SUM('Invoice lines'\[Revenue\]), SAMEPERIODLASTYEAR(Dates\[Date\]) |

The following key dimensions in the **Sales cube** are used as filters to slice the aggregate measurements to achieve greater granularity and deeper analytical insights.

|                  |                                                      |
|------------------|------------------------------------------------------|
| **Entity**       | **Examples of attributes**                           |
| Customers        | Customer groups, Customer regions, Address, Industry |
| Products         | Product number, Product name, Item groups name       |
| Sales categories | Sales category names                                 |
| Legal entities   | Legal entity names                                   |
| Dates            | Dates                                                |

By default, the content pack displays data for the current calendar year, but you can open the report filters section and change the date filter. You can also change the company filter.

## Additional resources
Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](data-entities.md)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](configure-power-bi-integration.md)


