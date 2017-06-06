---
# required metadata

title: Purchase spend analysis Power BI content
description: This topic describes what is included in the Purchase spend analysis Power BI content. It explains how to access the reports that are included in the content, and provides information about the data model and entities that are used to build the content.
author: FrankDahl
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 121
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 265434
ms.assetid: 3cd9dfce-2687-4303-bc78-349e7cb5ea75
ms.search.region: global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Purchase spend analysis Power BI content

[!include[banner](../includes/banner.md)]

This topic describes what is included in the **Purchase spend analysis** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.

## Overview

The **Purchase spend analysis** Power BI content was designed to help purchasing managers and managers who are responsible for budgets keep an eye on purchase spending. Managers can analyze purchase spending in the following ways:

-   Year-to-date purchase (by vendor group and individual vendors, procurement category and individual products, and vendor location)
-   Year-over-year purchase change (by vendor group and procurement category)

The content uses purchase transactional data, and provides both an aggregate view of the company-wide purchase figures and a breakdown of purchase spending by vendor and product. Reports highlight changes in purchase spending over time. Therefore, the reports can be used to alert managers about positive and negative spending trends for individual vendors and products. Additionally, charts show purchase spending for different procurement categories and vendor groups. Therefore, category and regional managers can use the charts to help identify changes in spending behavior.

## Accessing the Power BI content
If you're using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update, the **Purchase spend analysis** Power BI content is shown on the **Purchase and spend analysis** page (**Procurement and sourcing** > **Inquiries and reports** > **Purchase performance analysis** > **Purchase and spend analysis**). 

## Metrics that are included in the Power BI content
The **Purchase spend analysis** Power BI content includes a report that consists of a set of metrics. These metrics are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations.

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

## Extending the Power BI content
By using the content packs that are available in Microsoft Dynamics Lifecycle Services (LCS), you can provide great analytics to people who don't sign in to Microsoft Dynamics 365. You can modify these content packs so that they include other reports or visuals, and then publish the content packs to your Power BI.com tenant for analysis. 

You can find the **Purchase spend analysis** Power BI content in the Shared assets library in LCS. For more information about how to download the content and implement it in your organization, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office Mix.

Be sure to download the **Purchase spend analysis** content that applies to the version of Dynamics 365 that you're using.

> [!NOTE]
> If you're using Dynamics 365 for Operations version 1611, KB 4011327 is a prerequisite for this Power BI content. After you sign in to LCS, you can access the KB at https://fix.lcs.dynamics.com/issue/results/?q=kb4011327.

## Data model and entities
The following data is used to fill the report pages in the **Purchase spend analysis** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store. The Entity store is a Microsoft SQL Server database that is optimized for analytics. For more information, see [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md).

The aggregate measurements in this content are the subset of aggregate measurements that were available in the Purchase Cube in Microsoft Dynamics AX 2012 and Microsoft Dynamics AX 2012 R3. To stage the cube’s aggregate measurements in the Entity store, you must make them deployable. For more information, see the procedure for staging aggregate measurements in the Entity store in [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md). The following key aggregate measurements are available directly from the Invoice lines entity and are used as the basis of the content.

| Entity        | Key aggregate measurements | Data source                                 | Field              | Description                            |
|---------------|----------------------------|---------------------------------------------|--------------------|----------------------------------------|
| Invoice lines | Purchase                   | VendInvoiceTrans                            | SUM(LineAmountMST) | The amount in the accounting currency. |

The following table shows the key measurements in the content that are calculated from the Invoice lines entity.

| Measure               | Calculation                                                                                         |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| Purchase current year | Purchase current year = SUM('Invoice lines'\[Purchase\])                                            |
| Purchase last year    | Purchase last year = CALCULATE(SUM('Invoice lines'\[Purchase\]), SAMEPERIODLASTYEAR(Dates\[Date\])) |
| YOY purchase growth   | YOY purchase growth = \[Purchase current year\] – \[Purchase last year\]                            |

The following key dimensions in the content are used as filters to slice the aggregate measurements, so that you can achieve more granularity and gain deeper analytical insights.

| Entity                 | Examples of attributes                                |
|------------------------|-------------------------------------------------------|
| Vendors                | Vendor groups, Vendor country or regions, Vendor name |
| Products               | Product number, Product name, Item groups name        |
| Procurement categories | Procurement category, Procurement category names      |
| Legal entities         | Legal entity name                                     |
| Dates                  | Dates, Year offset                                    |

By default, the content shows data for the current calendar year. However, you can change the date filter in the report filters section. You can also change the company filter.
