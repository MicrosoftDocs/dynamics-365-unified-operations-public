---
# required metadata

title: Cost management Power BI content
description: This topic describes what is included in the Cost management Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.
author: YuyuScheller
manager: AnnBe
ms.date: 2017-02-10 15 - 44 - 04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 270314
ms.assetid: 9680d977-43c8-47a7-966d-2280ba21402a
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yuyus
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Cost management Power BI content

This topic describes what is included in the Cost management Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.

# Overview

The **Cost management** Microsoft Power BI content is intended for inventory accountants or individuals in the organization who are responsible for inventory. The **Cost management** Power BI content provides managerial insight into inventory and work-in-progress (WIP) inventory, and how cost flows through them by category over time. The information can also be used as a detailed supplement to the financial statement.

## Key measures

+ Beginning balance
+ Ending balance
+ Net change
+ Net change in %
+ Aging

## Key performance indicators
+ Inventory turn
+ Inventory accuracy

The primary data source for CostAggregatedCostStatementEntryEntity is the CostStatementCache table. This table is managed by the Data set cache framework. By default, the table is updated every 24 hours, but you can enable manual updates in the data cache configuration. You can then do a manual update in the **Cost management** or **Cost analysis** workspace. After the update of CostStatementCache is run, you must update the OData connection on Power BI.com to see updated data on the site. The variance (purchase, production) measures in this Power BI content pertain only to items that are valuated by the Standard cost inventory method. Production variance is calculated as the difference between active cost and realized cost. The production variance is calculated when the production order has a status of **Ended**. For more information about production variance types and how each type is calculated, see [About analyzing variances for a completed production order](https://technet.microsoft.com/en-us/library/gg242850.aspx).

## Accessing the Power BI content
The **Cost management** Power BI content is available from PowerBI.com. For more information about how to connect and load your Microsoft Dynamics 365 for Operations data, see [Access Power BI content from PowerBI.com](power-bi-home-page.md#access-power-bi-content-from-powerbi-com).

## Metrics that are included in the Power BI content
The content includes a set of report pages. Each page consists of a set of metrics that are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the **Cost management** Power BI content.

| Report page | Charts | Titles |
|---|---|---|
|Inventory overall (Default by current period) |Accuracy |Inventory measures:<br>Inventory ending balance<br>Inventory net change<br>Inventory net change %<br>|
| |Inventory turn | |
| |Inventory ending balance by Resource group | |
| |Inventory net change by Category name level 1 and Category name level 2| |
| |Purchase variances by Resource group and Category name level 3 | |
|Inventory by site (Default by current period) |Inventory ending balance by Site name and Resource group | |
| |Inventory turn by Site name and Resource group | |
| |Inventory ending balance by City and Resource group | |
|Inventory by resource group (Default by current period) |Inventory measures | |
| |Inventory accuracy by amount by Resource group | |
| |Inventory turn by amount by Resource group | |
|Inventory YOY (Default current year vs previous year) |Inventory measures | |
| |Inventory KPIs:<br>Inventory turn<br>Inventory accuracy | |
| |Inventory ending balance by Year and Resource group | |
| |Purchase variances by Year and Category name level 3 | |
|Inventory aging (Default by current year) |Inventory aging by Quarter and Resource group | |
| |Inventory aging by Quarter and Site name | |
|WIP overall (Default by current period) |WIP net change by Category name level 1 and Category name level 2 |Work in progress WIP measures:<br>WIP ending balance<br>WIP net change<br>WIP net change %<br> |
| |Production variances by Resource group and Category name level 3 | |
| |WIP net change by Resource group | |
|WIP by site (Default by current period) |Work in progress WIP measures | |
| |WIP net change by Site name and Category name level 2 | |
| |Production variances by Site name and Category name level 3 | |

## Understanding the data model and entities
Dynamics 365 for Operations data is used to populate the report pages in the **Cost management** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store, which is a Microsoft SQL database that is optimized for analytics. For more information, see [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md). The following key aggregate measurements are used as the basis of the content.

| Entity            | Key aggregate measurement | Data source for Dynamics 365 for Operations | Field             | Description                       |
|-------------------|---------------------------|---------------------------------------------|-------------------|-----------------------------------|
| Statement entries | Net change                | CostAggregatedCostStatementEntryEntity      | sum(\[Amount\])   | Amount in the accounting currency |
| Statement entries | Net change quantity       | CostAggregatedCostStatementEntryEntity      | sum(\[Quantity\]) |                                   |

The following table shows how the key aggregate measurements are used to create several calculated measures in the content's dataset.

| Measure                                 | How the measure is calculated                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Beginning balance                       | \[Ending balance\]-\[Net change\]                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Beginning balance quantity              | \[Ending balance quantity\]-\[Net change quantity\]                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Ending balance                          | CALCULATE(SUM(\[Amount\]), FILTER(ALLEXCEPT('Fiscal calendars', 'Fiscal calendars'\[LedgerRecId\], 'entities'\[ID\], 'entities'\[Name\], 'Ledgers'\[Currency\], 'Ledgers'\[Description\], 'Ledgers'\[Name\]), 'Fiscal calendars'\[Date\] &lt;= MAX('Fiscal calendars'\[Date\])))                                                                                                                                                                                           |
| Ending balance quantity                 | CALCULATE(SUM(\[Quantity\]), FILTER(ALLEXCEPT('Fiscal calendars', 'Fiscal calendars'\[LedgerRecId\], 'entities'\[ID\], 'entities'\[Name\], 'Ledgers'\[Currency\], 'Ledgers'\[Description\], 'Ledgers'\[Name\]), 'Fiscal calendars'\[Date\] &lt;= MAX('Fiscal calendars'\[Date\])))                                                                                                                                                                                         |
| Inventory beginning balance             | CALCULATE(\[Beginning balance\], 'Statement entries'\[Statement Type\] = "Inventory")                                                                                                                                                                                                                                                                                                                                                                                      |
| Inventory ending balance                | CALCULATE(\[Ending balance\], 'Statement entries'\[Statement Type\] = "Inventory")                                                                                                                                                                                                                                                                                                                                                                                         |
| Inventory net change                    | CALCULATE(\[Net change\], 'Statement entries'\[Statement type\] = "Inventory")                                                                                                                                                                                                                                                                                                                                                                                             |
| Inventory net change quantity           | CALCULATE(\[Net change quantity\], 'Statement entries'\[Statement type\] = "Inventory")                                                                                                                                                                                                                                                                                                                                                                                    |
| Inventory net change %                  | IF(\[Inventory ending balance\] = 0, 0, \[Inventory net change\] / \[Inventory ending balance\])                                                                                                                                                                                                                                                                                                                                                                           |
| Inventory turn by amount                | if(OR(\[Inventory average balance\] &lt;= 0, \[Inventory sold or consumed issues\] &gt;= 0), 0, ABS(\[Inventory sold or consumed issues\])/\[Inventory average balance\])                                                                                                                                                                                                                                                                                                  |
| Inventory average balance               | (\[Inventory ending balance\] + \[Inventory beginning balance\]) / 2                                                                                                                                                                                                                                                                                                                                                                                                       |
| Inventory sold or consumed issues       | \[Inventory sold\] + \[Inventory consumed material cost\]                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Inventory consumed material cost        | CALCULATE(\[Inventory net change\], 'Statement entries'\[Category name - level 2\_\] = "ConsumedMaterialsCost")                                                                                                                                                                                                                                                                                                                                                            |
| Inventory sold                          | CALCULATE(\[Inventory net change\], 'Statement entries'\[Category name - level 2\_\] = "Sold")                                                                                                                                                                                                                                                                                                                                                                             |
| Inventory accuracy by amount            | IF(\[Inventory ending balance\] &lt;= 0, IF(OR(\[Inventory counted amount\] &lt;&gt; 0, \[Inventory ending balance\] &lt; 0), 0, 1), MAX(0, (\[Inventory ending balance\] - ABS(\[Inventory counted amount\]))/\[Inventory ending balance\]))                                                                                                                                                                                                                              |
| Inventory counted amount                | CALCULATE(\[Inventory net change\], 'Statement entries'\[Category name - level 3\_\] = "Counting")                                                                                                                                                                                                                                                                                                                                                                         |
| Inventory aging                         | if(ISBLANK(max('Fiscal calendars'\[Date\])), blank(), MAX(0, MIN(\[Inventory aging receipts quantity\], \[Inventory aging ending balance quantity\] - \[Inventory aging receipts quantity in the future\]))) \* \[Inventory avg unit cost\]                                                                                                                                                                                                                                |
| Inventory aging receipts quantity       | IF(\[minDate\] = \[minDateAllSelected\], CALCULATE(\[Inventory net change quantity\], 'Statement entries'\[Quantity\] &gt; 0, FILTER(ALLEXCEPT('Fiscal calendars', 'Fiscal calendars'\[LedgerRecId\], 'entities'\[ID\], 'entities'\[Name\], 'Ledgers'\[Currency\], 'Ledgers'\[Description\], 'Ledgers'\[Name\]), 'Fiscal calendars'\[Date\] &lt;= MAX('Fiscal calendars'\[Date\]))), CALCULATE(\[Inventory net change quantity\], 'Statement entries'\[Quantity\] &gt; 0)) |
| Inventory aging ending balance quantity | \[Inventory ending balance quantity\] + CALCULATE(\[Inventory net change quantity\], FILTER(ALLEXCEPT('Fiscal calendars', 'Fiscal calendars'\[LedgerRecId\], 'entities'\[ID\], 'entities'\[Name\], 'Ledgers'\[Currency\], 'Ledgers'\[Description\], 'Ledgers'\[Name\]), 'Fiscal calendars'\[Date\] &gt; max('Fiscal calendars'\[Date\]) ))                                                                                                                                 |
| Inventory aging receipts in the future  | CALCULATE(\[Inventory net change\], 'Statement entries'\[Amount\] &gt; 0, FILTER(ALLEXCEPT('Fiscal calendars', 'Fiscal calendars'\[LedgerRecId\], 'entities'\[ID\], 'entities'\[Name\], 'Ledgers'\[Currency\], 'Ledgers'\[Description\], 'Ledgers'\[Name\]), 'Fiscal calendars'\[Date\] &gt; MAX('Fiscal calendars'\[Date\])))                                                                                                                                             |
| Inventory avg unit cost                 | CALCULATE(\[Inventory ending balance\] / \[Inventory ending balance quantity\],ALLEXCEPT('Fiscal calendars', 'Fiscal calendars'\[LedgerRecId\], 'entities'\[ID\], 'entities'\[Name\], 'Ledgers'\[Currency\], 'Ledgers'\[Description\], 'Ledgers'\[Name\]))                                                                                                                                                                                                                 |
| Purchase variances                      | CALCULATE(SUM(\[Amount\]), 'Statement entries'\[Category name - level 2\_\] = "Procured", 'Statement entries'\[Statement type\] = "Variance")                                                                                                                                                                                                                                                                                                                              |
| WIP beginning balance                   | CALCULATE(\[Beginning balance\], 'Statement entries'\[Statement Type\] = "WIP")                                                                                                                                                                                                                                                                                                                                                                                            |
| WIP ending balance                      | CALCULATE(\[Ending balance\], 'Statement entries'\[Statement Type\] = "WIP")                                                                                                                                                                                                                                                                                                                                                                                               |
| WIP net change                          | CALCULATE(\[Net change\], 'Statement entries'\[Statement type\] = "WIP")                                                                                                                                                                                                                                                                                                                                                                                                   |
| WIP net change %                        | IF(\[WIP ending balance\] = 0, 0, \[WIP net change\] / \[WIP ending balance\])                                                                                                                                                                                                                                                                                                                                                                                             |
| Production variances                    | CALCULATE(SUM(\[Amount\]), 'Statement entries'\[Category name - level 2\_\] = "ManufacturedCost", 'Statement entries'\[Statement type\] = "Variance")                                                                                                                                                                                                                                                                                                                      |
| Category name - level 1                 | switch(\[Category name - level 1\_\], "None", "None", "NetSourcing", "Net sourcing", "NetUsage", "Net usage", "NetConversionCost", "Net conversion cost", "NetCostOfGoodsManufactured", "Net cost of goods manufactured", "BeginningBalance", "Beginning balance")                                                                                                                                                                                                         |
| Category name - level 2                 | switch(\[Category name - level 2\_\], "None", "None", "Procured", "Procured", "Disposed", "Disposed", "Transferred", "Transferred", "Sold", "Sold", "ConsumedMaterialsCost", "Consumed material cost", "ConsumedManufacturingCost", "Consumed manufacturing cost", "ConsumedOutsourcingCost", "Consumed outsourcing cost", "ConsumedIndirectCost", "Consumed indirect cost", "ManufacturedCost", "Manufactured cost", "Variances", "Variances")                            |
| Category name - level 3                 | switch(\[Category name - level 3\_\], "None", "None", "Counting", "None", "ProductionPriceVariance", "Production price", "QuantityVariance", "Quantity", "SubstitutionVariance", "Substitution", "ScrapVariance", "Scrap", "LotSizeVariance", "Lot size", "RevaluationVariance", "Revaluation", "PurchasePriceVariance", "Purchase price", "CostChangeVariance", "Cost change", "RoundingVariance", "Rounding variance")                                                   |

The following key dimensions are used as filters to slice the aggregate measurements to achieve greater granularity and provide deeper analytical insights.

| Entity           | Examples of attributes                       |
|------------------|----------------------------------------------|
| Entities         | ID, Name                                     |
| Fiscal calendars | Calendar, Month, Period, Quarter, Year       |
| KPI goals        | Inventory accuracy goal, Inventory turn goal |
| Ledgers          | Currency, Name, Description                  |
| Sites            | ID, Name, Country, City                      |

## Additional resources
Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](..\data-entities\data-entities.md)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](configure-power-bi-integration.md)


