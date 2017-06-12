---
# required metadata

title: Sales and profitability performance Power BI content
description: This topic describes what's included in the Sales and profitability performance Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.
author: YuyuScheller
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: SalesProfitabilityPerformancePowerBI 
# ROBOTS: 
audience: Application User, IT Pro
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

# Sales and profitability performance Power BI content

[!include[banner](../includes/banner.md)]

This topic describes what is included in the **Sales and profitability performance** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.

## Overview

The **Sales and profitability performance** Power BI content was created so that sales managers can monitor the key sales metrics of revenue, gross profit, and profit margins. It uses sales transactional data, and provides both an aggregate view of the company-wide sales figures and a breakdown of sales performance for customers and products.

Reports highlight changes in revenue and profit growth over time. Therefore, the reports can be used to alert managers about positive and negative trends for individual customers and products. Additionally, charts compare the revenue and profitability of different product categories and customer groups to each other. Therefore, category and regional managers can identify laggards and leaders. Finally, a comprehensive report plots an individual customer’s revenue versus profit margin. Therefore, account managers have a data-backed foundation that they can use to tune their sales and marketing efforts to each customer’s profile. 

The **Sales and profitability performance** content lets sales managers analyze sales performance in the following ways:

-   Revenue, year-to-date (by customer group and individual customers, sales categories, and individual products and geographies)
-   Revenue change, year-over-year (by customer regions and sales categories)

Profitability can be analyzed in these ways:

-   Gross profit and profit margin (by customer groups and product sales categories)
-   Gross profit change, year-over-year
-   Customer profitability (by revenue versus gross margin)

## Accessing the Power BI content
If you're using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, the **Sales and profitability performance** Power BI content is shown on the **Sales and profitability performance** page (**Sales and marketing** > **Inquiries and reports** > **Sales performance analysis** > **Sales and profitability performance**). 

## Metrics that are included in the Power BI content
The **Sales and profitability performance** Power BI content includes a report that consists of a set of metrics. These metrics are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the content.

| Report page            | Charts                                     | Tiles                                                   |
|------------------------|--------------------------------------------|---------------------------------------------------------|
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

## Extending the Power BI content
By using the content packs that are available in Microsoft Dynamics Lifecycle Services (LCS), you can provide great analytics to people who don't sign in to Microsoft Dynamics 365. You can modify these content packs so that they include other reports or visuals, and then publish the content packs to your Power BI.com tenant for analysis.

You can find the **Sales and profitability performance** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

Be sure to download the **Sales and profitability performance** content that applies to the version of Dynamics 365 that you're using.

> [!NOTE]
> If you're using Microsoft Dynamics 365 for Operations version 1611, KB 4011327 is a prerequisite for this Power BI content. After you sign in to LCS, you can access the KB at https://fix.lcs.dynamics.com/issue/results/?q=kb4011327.

## Understanding the data model and entities
The following data is used to fill the report in the **Sales and profitability performance** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store. The Entity store is a Microsoft SQL Server database that is optimized for analytics. For more information, see [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md). 

The aggregate measurements in this content are the subset of aggregate measurements that were available in the Sales Cube in Microsoft Dynamics AX 2012 and Microsoft Dynamics AX 2012 R3. To stage the cube's aggregate measurements in the Entity store, you must make them deployable. For more information, see the procedure for staging aggregate measurements in the Entity store in the [Power BI integration with Entity Store in Dynamics](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/) blog post. 

The following key aggregate measurements of the Invoice lines entity are used as the basis of the content.

| Entity        | Key aggregate measurements                   | Data source for Dynamics 365                    | Field                                        | Description                                   |
|---------------|----------------------------------------------|-------------------------------------------------|----------------------------------------------|----------------------------------------------|
| Invoice lines | Revenue                                      | CustInvoiceTrans                                | SUM(LineAmountMST)                           | The amount in the accounting currency.            |
|               | Cost of goods sold                           | InventTrans                                     | SUM(CostAmountPosted + CostAmountAdjustment) | The sum of the cost amount and the adjustment.    |
|               | Commission line amount – accounting currency | CustInvoiceTrans                                | SUM(CommissAmountMST)                        | The commission amount in the accounting currency. |

The following table shows the key aggregate measurements of the Invoice lines entity that are used to create several calculated measures in the content’s dataset.

| Measure           | Calculation                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
| Gross profit      | SUM(Revenue – COGS – Commission – Sales tax (included in customer invoice line amount))          |
| Gross margin      | SUM(Gross profit / (Revenue - Sales tax (included in customer invoice line amount)))             |
| Revenue last year | Revenue last year = CALCULATE(SUM('Invoice lines'\[Revenue\]), SAMEPERIODLASTYEAR(Dates\[Date\]) |

The following key dimensions in the Sales Cube are used as filters to slice the aggregate measurements, so that you can achieve greater granularity and gain deeper analytical insights.

| Entity           | Examples of attributes                               |
|------------------|------------------------------------------------------|
| Customers        | Customer groups, Customer regions, Address, Industry |
| Products         | Product number, Product name, Item groups name       |
| Sales categories | Sales category names                                 |
| Legal entities   | Legal entity names                                   |
| Dates            | Dates                                                |

By default, the content shows data for the current calendar year. However, you can change the date filter in the report filters section. You can also change the company filter.
