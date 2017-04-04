---
# required metadata

title: Cost accounting analysis Power BI content
description: This topic describes what is included in the Cost accounting analysis Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content.
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
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
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 270274
ms.assetid: b74549df-35d5-4f2f-b3c7-405b0d38ea78
ms.search.region: Global
# ms.search.industry: 
ms.author: yuyus
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Cost accounting analysis Power BI content

This topic describes what is included in the Cost accounting analysis Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that were used to build the content.

Overview
--------

The **Cost accounting analysis** Microsoft Power BI content is intended for cost controllers or anyone who is responsible for performing cost control of an organization. It includes the key metrics, such as cost, magnitude, and cost rate by actual cost, budget cost, and flexible budget cost. It uses transaction data from Cost accounting in Microsoft Dynamics 365 for Operations and provides an aggregate view of costs for the whole organization in one reporting currency. Managers can filter the data by cost objects to perform cost control of their organizational units, even if the organization can have several legal entities. Because the **Cost accounting analysis** Power BI content highlights variances between the actual costs and budgeted costs, managers can be notified about positive and negative trends for their operational units. Managers can drill down to the cost element hierarchies or individual cost elements to gain detailed insight into how cost variances have occurred, and then take effective action. The **Cost accounting analysis** Power BI content lets cost accountants analyze how cost flows through the cost objects of the whole organization. To learn more about Cost accounting, see [Cost accounting home page](/dynamics365/operations/financials/cost-accounting/cost-accounting-home-page). By defining access-level security in Cost accounting and combining it with row-level security in Power BI, you can grant all cost object owners access to the **Cost accounting analysis** Power BI content. All data in the visualizations will then be filtered based on the access level that is controlled in Cost accounting. To learn more about access-level security and row-level security, see [Set up security for Cost accounting content for Power BI](setup-security-cost-accounting-content-pack.md).

## Accessing the Power BI content
You can find the **Cost accounting analysis** Power BI content in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content and connect it to your Dynamics 365 for Operations data, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md). 

> [!NOTE]
> **KB4011327** is a prerequisite for the **Cost accounting analysis** Power BI content. After you sign in to Lifecycle Services, you can access the KB here: <https://fix.lcs.dynamics.com/issue/results/?q=kb4011327>.

## Metrics that are included in the Power BI content
The content includes a set of report pages. Each page consists of a set of metrics that are visualized as charts, tiles, and tables. The following table provides an overview of the visualizations in the **Cost accounting analysis** Power BI content.

| Report page                      | Chart                                                                                                                         | Tile                                          |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| Cost control by fiscal period    | Actual cost and Budget cost by Cost element hierarchy level                                                                   | Actual cost vs Budget cost                    |
|                                  | Budget variance by Cost element hierarchy level                                                                               | Actual cost rate vs Budget cost rate          |
|                                  | Top 10 Budget variance in percentage by Cost element                                                                          | Actual magnitude vs Budget magnitude          |
| Cost control by Year to date     | Actual cost and Budget cost by Calendar Year Period                                                                           | Actual cost vs Budget cost                    |
|                                  | Budget variance by Calendar Year Period                                                                                       | Actual cost rate vs Budget cost rate          |
|                                  | Top 10 Budget variance in percentage by Cost element                                                                          | Actual magnitude vs Budget magnitude          |
| Cost rate by fiscal year         | Actual cost rate by Cost behavior                                                                                             | Actual cost rate vs Budget cost rate          |
|                                  | Actual cost rate, Budget cost rate variance, Budget cost rate percentage and Budget cost rate by Cost element hierarchy level | Actual magnitude vs Budget magnitude          |
|                                  | Budget variance by Cost element hierarchy level                                                                               |                                               |
|                                  | Top 10 Budget variance in percentage by Cost element                                                                          |                                               |
| Flexible budget by fiscal period | Actual cost, Budget cost and Flexible budget cost by Cost element hierarchy level                                             | Actual magnitude vs Budget magnitude          |
|                                  | Budget variance and Flexible budget variance by Cost element hierarchy level                                                  | Actual cost vs Flexible budget cost           |
|                                  | Actual cost, Budget cost and Flexible cost by Cost behavior and Cost element hierarchy level                                  | Actual cost rate vs Flexible budget cost rate |
| Cost statement by fiscal period  | Actual cost by Cost element hierarchy level and Cost object dimension member name                                             |                                               |
|                                  | Actual cost by Cost object dimension member name and Cost element dimension member name                                       |                                               |

## Understanding the data model and entities
Dynamics 365 for Operations data is used to fill the report pages in the **Cost accounting analysis** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store, which is a Microsoft SQL database that is optimized for analytics. For more information, see [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md). The following key aggregate measurements are used as the basis of the content.

| Entity                  | Key aggregate measurement | Data source for Dynamics 365 for Operations | Field     | Description                                   |
|-------------------------|---------------------------|---------------------------------------------|-----------|-----------------------------------------------|
| Cost accounting entries | SUM(Amount)               | CAMDATAAggregatedCostEntry                  | Amount    | Amount in the Cost accounting ledger currency |
| Statistical entries     | SUM(Magnitude)            | CAMDATAAggregatedStatisctialEntry           | Magnitude |                                               |

The following table shows how the key aggregate measurements are used to create several calculated measures in the content's dataset.

| Measure                                       | How the measure is calculated                                                                                          |
|-----------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Actual cost                                   | CALCULATE('Cost accounting entries'\[Measure\], 'Transaction versions'\[ISSOURCEVERSIONBUDGET\_VALUE\] = 0)            |
| Budget cost                                   | CALCULATE('Cost accounting entries'\[Measure\], 'Transaction versions'\[ISSOURCEVERSIONBUDGET\_VALUE\] = 1)            |
| Budget cost variance                          | \[Budget cost\] - \[Actual cost\]                                                                                      |
| Budget variance percentage                    | IF(\[Budget cost\] = 0, blank(), \[Budget variance\] / \[Budget cost\])                                                |
| Actual magnitude                              | CALCULATE('Statistical entries'\[FullMagnitude\], 'Transaction versions'\[ISSOURCEVERSIONBUDGET\_VALUE\] = 0)          |
| Budget magnitude                              | CALCULATE(\[FullMagnitude\], 'Transaction versions'\[ISSOURCEVERSIONBUDGET\_VALUE\] = 1)                               |
| Statistical budget variance                   | \[Budget magnitude\] - \[Actual magnitude\]                                                                            |
| Statistical budget variance percentage        | IF(\[Budget magnitude\] = 0, blank(), \[Statistical budget variance\] / \[Budget magnitude\])                          |
| Actual cost rate                              | IF(\[Actual magnitude\] = 0, BLANK(), \[Actual cost\] / \[Actual magnitude\])                                          |
| Budget cost rate                              | IF(\[Budget magnitude\] = 0, BLANK(), \[Budget cost\] / \[Budget magnitude\])                                          |
| Budget cost rate variance                     | \[Budget cost rate\] - \[Actual cost rate\]                                                                            |
| Budget cost rate variance percentage          | IF(\[Budget cost\] = 0, blank(), \[Budget cost rate variance\] / \[Budget cost rate\])                                 |
| Fixed budget cost                             | CALCULATE(\[Budget cost\], 'Cost accounting entries'\[COSTBEHAVIOR\] = 1)                                              |
| Variable budget cost                          | CALCULATE(\[Budget cost\], 'Cost accounting entries'\[COSTBEHAVIOR\] = 2)                                              |
| Fixed flexible budget cost                    | \[Fixed budget cost\]                                                                                                  |
| Variable flexible budget cost                 | IF(\[Budget magnitude\] = 0, BLANK(), (\[Variable budget cost\] / \[Budget magnitude\]) \* \[Actual magnitude\])       |
| Flexible budget cost                          | \[Fixed flexible budget cost\] + \[Variable flexible budget cost\]                                                     |
| Flexible budget variance                      | \[Flexible budget cost\] - \[Actual cost\]                                                                             |
| Flexible budget variance percentage           | IF(\[Flexible budget cost\] = 0, BLANK(), \[Flexible budget variance\] / \[Flexible budget cost\])                     |
| Flexible budget cost rate                     | IF(\[Actual magnitude\] = 0, BLANK(), \[Flexible budget cost\] / \[Actual magnitude\])                                 |
| Flexible budget cost rate variance            | \[Flexible budget cost rate\] - \[Actual cost rate\]                                                                   |
| Flexible budget cost rate variance percentage | IF(\[Flexible budget cost rate\] = 0, BLANK(), \[Flexible budget cost rate variance\] / \[Flexible budget cost rate\]) |

The following key dimensions are used as filters to slice the aggregate measurements to achieve greater granularity and provide deeper analytical insights.

| Entity                             | Examples of attributes                                                                                               |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Cost accounting ledgers            | Cost accounting ledger                                                                                               |
| Cost control units                 | Cost control unit name                                                                                               |
| Cost element dimensions            | Cost elements dimension name, Cost element dimension member name, Cost element dimension member description          |
| Cost object dimensions             | Cost object dimension name, Cost object dimension member name, Cost object dimension member description              |
| Statistical dimensions             | Statistical dimension name, Statistical dimension member name, Statistical dimension member description              |
| Cost object dimension hierarchies  | Cost object dimension hierarchy name, Cost object dimension hierarchy level, Cost object dimension hierarchy tree    |
| Cost element dimension hierarchies | Cost element dimension hierarchy name, Cost element dimension hierarchy level, Cost element dimension hierarchy tree |
| Statistical dimension hierarchies  | Statistical dimension hierarchy name, Statistical dimension hierarchy level, Statistical dimension hierarchy tree    |
| Transaction versions               | Version name                                                                                                         |
| Fiscal calendars                   | Calendar, Calendar description                                                                                       |
| Fiscal years                       | Calendar year                                                                                                        |
| Fiscal periods                     | Calendar year period                                                                                                 |

## Additional resources
Here are some helpful links that are related to entities and building Power BI content:

-   [Data entities](..\data-entities\data-entities.md)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Adding Power BI tiles to workspaces](configure-power-bi-integration.md)
-   [Setting up security for Cost accounting content for Power BI](setup-security-cost-accounting-content-pack.md)

