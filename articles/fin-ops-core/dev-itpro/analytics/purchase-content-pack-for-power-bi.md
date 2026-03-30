---
title: Purchase spend analysis Power BI content
description: Learn about what is included in the Purchase spend analysis Power BI content, including various metrics that are included in the Power BI content.
author: FrankDahl
ms.author: kamaybac
ms.topic: article
ms.date: 01/15/2026
ms.reviewer: kamaybac
audience: IT Pro
ms.search.region: global
ms.search.validFrom: 2016-11-30
ms.search.form: PurchaseSpendAnalysisPowerBI
ms.dyn365.ops.version: Version 1611
ms.assetid: 3cd9dfce-2687-4303-bc78-349e7cb5ea75
---

# Purchase spend analysis Power BI content

[!include [banner](../includes/banner.md)]

This article describes what the **Purchase spend analysis** Microsoft Power BI content includes. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.

## Overview

The **Purchase spend analysis** Power BI content helps purchasing managers and managers who are responsible for budgets keep track of purchase spending. Managers can analyze purchase spending in the following ways:

- Year-to-date purchase (by vendor group and individual vendors, procurement category and individual products, and vendor location)
- Year-over-year purchase change (by vendor group and procurement category)

The content uses purchase transactional data, and provides both an aggregate view of the company-wide purchase figures and a breakdown of purchase spending by vendor and product. Reports highlight changes in purchase spending over time. Therefore, the reports can alert managers about positive and negative spending trends for individual vendors and products. Additionally, charts show purchase spending for different procurement categories and vendor groups. Therefore, category and regional managers can use the charts to help identify changes in spending behavior.

## Accessing the Power BI content

You can view the **Purchase spend analysis** Power BI content on the **Purchase and spend analysis** page (**Procurement and sourcing** \> **Inquiries and reports** \> **Purchase performance analysis** \> **Purchase and spend analysis**).

## Metrics that the Power BI content includes

The **Purchase spend analysis** Power BI content includes a report that consists of a set of metrics. The report visualizes these metrics as charts, tiles, and tables.

The following sections provide an overview of the visualizations.

### Purchase by vendor report page

#### Charts

- Top 10 vendors by purchase (stacked bar chart)
- Total purchase by vendor group, country/region, or name (pie chart)
- Purchase by vendor group, country/region, or name (column chart)
- Average purchase by vendor group, country/region, or name (column chart)

#### Tiles

- Total purchase
- Year-over-year purchase growth
- Total number of vendors
- Total number of active vendors

#### Example

:::image type="content" source="media/spend1.png" alt-text="Screenshot of Purchase by vendor.":::

### Purchase by product report page

#### Charts

- Purchase by procurement category and product name (column chart)
- Total purchase by procurement category and product name (pie chart)
- Top 10 products by purchase (stacked bar chart)

#### Tiles

- Total number of products
- Total active products as a percentage of total number of products
- Number of products accounting for 80% purchase

#### Example

:::image type="content" source="media/purchaseByProduct.png" alt-text="Screenshot of Purchase by Product.":::

### Purchase by period report page

This page shows purchases for the current and previous years, and growth by procurement category.

#### Charts

- Purchase by month or day (column chart)
- Cumulative purchase year-over-year variance (waterfall chart)
- Total purchase year-over-year growth (column chart)
- Procurement statement (matrix)

#### Tiles

- Year-over-year purchase growth
- Year-over-year purchase growth percentage

#### Example

:::image type="content" source="media/purchaseByPeriod.png" alt-text="Screenshot of Purchase by Period.":::

### Purchase by vendor location report page

#### Charts

- Purchase by city
- Purchase YOY growth %
- Purchase by country/region

#### Example

:::image type="content" source="media/purchByVendorLocation.png" alt-text="Screenshot of Purchase by Vendor Location.":::

### Purchase spend analysis by time report page

#### Charts

- Purchase current year by month or day (line chart)
- Purchase current and last year (line and column chart)

#### Example

:::image type="content" source="media/PurchByTIme.png" alt-text="Screenshot of Purchase by Time.":::

### Purchase spend analysis by vendor report page

#### Charts

- Top 10 vendor purchase percentage of purchase (funnel)
- Top 10 vendors with increased spending year over year
- Top 10 vendors with decreased spending year over year

#### Example

:::image type="content" source="media/PurchSpendAnalysisByVendor.png" alt-text="Screenshot of Purchase spend by vendor.":::

## Data model and entities

The report pages in the **Purchase spend analysis** Power BI content use the following data. The data appears as aggregate measurements staged in the Entity store. The Entity store is a Microsoft SQL Server database that's optimized for analytics. For more information, see [Power BI integration with Entity store](power-bi-integration-entity-store.md).

The aggregate measurements in this content are a subset of the aggregate measurements that were available in the Purchase Cube in Microsoft Dynamics AX 2012 and Microsoft Dynamics AX 2012 R3. To stage the cube's aggregate measurements in the Entity store, you must make them deployable. For more information, see the procedure for staging aggregate measurements in the Entity store in [Power BI integration with Entity store](power-bi-integration-entity-store.md). The following key aggregate measurements are available directly from the Invoice lines entity and are used as the basis of the content.

| Entity        | Key aggregate measurements | Data source                                 | Field              | Description                            |
|---------------|----------------------------|---------------------------------------------|--------------------|----------------------------------------|
| Invoice lines | Purchase                   | VendInvoiceTrans                            | SUM(LineAmountMST) | The amount in the accounting currency. |

The following table shows the key measurements in the content that are calculated from the Invoice lines entity.

| Measure               | Calculation                                                                                         |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| Purchase current year | Purchase current year = SUM('Invoice lines'\[Purchase\])                                            |
| Purchase last year    | Purchase last year = CALCULATE(SUM('Invoice lines'\[Purchase\]), SAMEPERIODLASTYEAR(Dates\[Date\])) |
| YOY purchase growth   | YOY purchase growth = \[Purchase current year\] – \[Purchase last year\]                            |

Use the following key dimensions as filters to slice the aggregate measurements. By using these filters, you can achieve more granularity and gain deeper analytical insights.

| Entity                 | Examples of attributes                                |
|------------------------|-------------------------------------------------------|
| Vendors                | Vendor groups, Vendor country or regions, Vendor name |
| Products               | Product number, Product name, Item groups name        |
| Procurement categories | Procurement category, Procurement category names      |
| Legal entities         | Legal entity name                                     |
| Dates                  | Dates, Year offset                                    |

By default, the content shows data for the current calendar year. However, you can change the date filter in the report filters section. You can also change the company filter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
