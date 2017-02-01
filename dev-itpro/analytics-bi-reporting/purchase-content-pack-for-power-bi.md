---
# required metadata

title: Purchase spend analysis content pack for Power BI | Microsoft Docs
description: This topic describes what is included in the Purchase spend analysis content pack for Microsoft Power BI. It explains how to access the reports that are included in the content pack, and provides information about the data model and entities that are used to build the content pack.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-12-30 09:40:51
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 121
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 265434
ms.assetid: 368b0cad-0089-4ef6-b7c1-87abe17bcf8f
ms.region: global
# ms.industry: 
ms.author: fdahl

---

# Purchase spend analysis content pack for Power BI

This topic describes what is included in the Purchase spend analysis content pack for Microsoft Power BI. It explains how to access the reports that are included in the content pack, and provides information about the data model and entities that are used to build the content pack.

Overview
--------

The Purchase spend analysis content pack for Microsoft Power BI was created for purchasing managers and managers who are responsible for budgets. It's designed to help them keep an eye on purchase spending. It uses purchase transactional data from Microsoft Dynamics 365 for Operations, and provides both an aggregate view of the company-wide purchase figures and a breakdown of purchase spending by vendor and product. Reports highlight changes in purchase spending over time. Therefore, they can be used to alert managers about positive and negative spending trends for individual vendors and products. Charts show purchase spending for different procurement categories and vendor groups. Category and regional managers might find it useful to use these charts to help identify changes in spending behavior. The content pack lets purchase managers and managers who are responsible for budgets analyze purchase spending in the following ways:

-   Year-to-date purchase (by vendor group and individual vendors, procurement category and individual products, and vendor location)
-   Year-over-year purchase change (by vendor group and procurement category)

## Accessing the content pack
The Purchase spend analysis content pack is published as an implementation asset in Microsoft Dynamics Lifecycle Services (LCS) and can be accessed from Microsoft Dynamics 365 for Operations. For more information about how to access and open Power BI reports, see the [Authoring and distributing Power BI reports with Dynamics](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/23/authoring-and-distributing-power-bi-reports-with-dynamics-ax7/) blog post.

## Metrics that are included in the content pack
The Purchase spend analysis content pack includes a report that consists of a set of metrics. These metrics are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the content pack.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Report page</th>
<th>Charts</th>
<th>Tiles</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Purchase by vendor</td>
<td><ul>
<li>Top 10 vendors by purchase (stacked bar chart)</li>
<li>Total purchase by vendor group / country / name (pie chart)</li>
<li>Purchase by vendor group / country / name (column chart)</li>
<li>Average purchase by vendor group / country / name (column chart)</li>
</ul></td>
<td><ul>
<li>Total purchase</li>
<li>YOY purchase growth</li>
<li>Total # vendors</li>
<li>Total # of active vendors</li>
</ul></td>
</tr>
<tr class="even">
<td>Purchase by product</td>
<td><ul>
<li>Purchase by procurement category / product name (column chart)</li>
<li>Total purchase by procurement category / product name (pie chart)</li>
<li>Top 10 products by purchase (stacked bar chart)</li>
</ul></td>
<td><ul>
<li>Total # of products</li>
<li>Total active products percentage of total # of products</li>
<li>Number of products accounting for 80% purchase</li>
</ul></td>
</tr>
<tr class="odd">
<td>Purchase by period*</td>
<td><ul>
<li>Purchase by month / day (column chart)</li>
<li>Cumulative purchase YOY variance (waterfall chart)</li>
<li>Total purchase YOY growth (column chart)</li>
<li>Procurement statement (matrix)</li>
</ul></td>
<td><ul>
<li>YOY purchase growth</li>
<li>YOY purchase growth %</li>
</ul></td>
</tr>
<tr class="even">
<td>Purchase by vendor location</td>
<td><ul>
<li>Purchase by city</li>
<li>Purchase YOY growth %</li>
<li>Purchase by country</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td>Purchase spend analysis by time</td>
<td><ul>
<li>Purchase current year by month / day (line chart)</li>
<li>Purchase current and last year (line and column chart)</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td>Purchase spend analysis by vendor</td>
<td><ul>
<li>Top 10 vendor purchase % of purchase (funnel)</li>
<li>Top 10 vendors with increased spending YOY</li>
<li>Top 10 vendors with decreased spending YOY</li>
</ul></td>
<td></td>
</tr>
</tbody>
</table>

\* Purchase this year and last year, and growth by procurement category

## Data model and entities
Dynamics 365 for Operations data is used for the report in the Purchase spend analysis content pack. This data is represented as aggregate measurements that are staged in the Entity store, which is a Microsoft SQL database that is optimized for analytics. For more information about the Entity store, see the [Power BI integration with Entity Store in Dynamics](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/) blog post. The aggregate measurements in this content pack are the subset of aggregate measurements that were available in the Purchase Cube in Microsoft Dynamics AX 2012 and Microsoft Dynamics AX 2012 R3. To stage the cube’s aggregate measurements in the Entity store, you must make them deployable. For more information, see the procedure for staging aggregate measurements in the Entity store in the [Power BI integration with Entity Store in Dynamics](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/) blog post. The following key aggregate measurements are available directly from the Invoice lines entity and are used as the basis of the content pack.

| Entity        | Key aggregate measurements | Data source for Dynamics 365 for Operations | Field              | Description                           |
|---------------|----------------------------|---------------------------------------------|--------------------|---------------------------------------|
| Invoice lines | Purchase                   | VendInvoiceTrans                            | SUM(LineAmountMST) | The amount in the accounting currency |

The following table shows the key measurements that are calculated in the content pack from the Invoice lines entity.

| Measure               | Calculation                                                                                         |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| Purchase current year | Purchase current year = SUM('Invoice lines'\[Purchase\])                                            |
| Purchase last year    | Purchase last year = CALCULATE(SUM('Invoice lines'\[Purchase\]), SAMEPERIODLASTYEAR(Dates\[Date\])) |
| YOY purchase growth   | YOY purchase growth = \[Purchase current year\] – \[Purchase last year\]                            |

The following key dimensions in the content pack are used as filters to slice the aggregate measurements, so that you can achieve more granularity and deeper analytical insights.

| Entity                 | Examples of attributes                                |
|------------------------|-------------------------------------------------------|
| Vendors                | Vendor groups, Vendor country or regions, Vendor name |
| Products               | Product number, Product name, Item groups name        |
| Procurement categories | Procurement category, Procurement category names      |
| Legal entities         | Legal entity name                                     |
| Dates                  | Dates, Year offset                                    |

By default, the content pack shows data for the current calendar year. However, you can change the date filter in the report filters section. You can also change the company filter.

## Additional resources
Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/data-entities)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics-bi-reporting/configuring-powerbi-integration)


