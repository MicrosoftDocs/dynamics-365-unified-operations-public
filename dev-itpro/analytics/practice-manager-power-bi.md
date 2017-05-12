---
# required metadata

title: Practice manager Power BI content
description: This topic describes what is included in the Practice manager Power BI content. It explains how to access the reports that are included in the content pack, and provides information about the data model and entities that are used to build the content pack.
author: knelson
manager: AnnBe
ms.date: 04/28/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer/IT Pro
# ms.devlang: 
# ms.reviewer: sericks007
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson
ms.dyn365.intro: 2017/04/27
ms.dyn365.version:

---

[!include[banner](../includes/banner.md)]

# Practice manager Power BI content

This topic describes what is included in the **Practice manager** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.

## Overview

The **Practice manager** Power BI content was created for practice managers and project managers. It provides key metrics that are related to the projects that the organization is working on. The dashboard gives an overview of the projects and related customers. A report-level filter can be used to report for specific legal entities. This Power BI content pulls data from the project accounting aggregate measurements for Microsoft Dynamics 365 for Operations.

The **Practice manager** Power BI content contains five report pages: one overview page and four pages that provide details of project costs, revenues, earned value management, and hour metrics that are sliced and diced across various dimensions.

All the amounts in the content are shown in the system currency. You can set the system currency on the **System parameters** page.

## Accessing the Power BI content

You can find the **Practice manager** Power BI content in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content pack and connect it to your Dynamics 365 for Operations data, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md).

To watch a demo that shows how to implement the Power BI content, see the [Power BI content from Microsoft and your partners in Dynamics Lifecycle Services](https://mix.office.com/watch/9puyb1b2xs1w) Office mix.

## Reports that are included in the Power BI content

The following table provides details about the metrics that are found on each report page in the **Practice manager** Power BI content.

| Report page                                          | Metrics               |
|------------------------------------------------------|-----------------------------------------------|
| Dashboard  | Created projects<br>Estimated projects<br>In-process projects<br>Number of projects by stage<br>Number of projects by city<br>Actual revenue by customer<br>Budget gross margin by project<br>Earned value management overview |
| Cost                                                 | Actual vs budget cost by month<br>Actual vs budget cost by year<br>Actual vs budget cost by category<br>Actual cost by transaction type       |
| Revenue                                              | Actual revenue by month<br>Actual revenue by postal code<br>Actual vs budget revenue by category<br>Actual revenue by customer industry        |
| EVM                                                  | Cost and schedule performance index by project                 |
| Hours                                                | Actual billable utilized hours vs actual billable burden hours vs budget hours<br>Actual billable utilized hours vs actual billable burden hours by project<br>Actual billable utilized hours vs actual billable burden hours by resource<br>Actual billable hours ratio by project<br>Actual billable hours ratio by resource |

The charts and tiles on all these reports can be filtered and pinned to the dashboard. For more information about how to filter and pin 
in Power BI, see [Create and configure a dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards/). You can also use the Export underlying data functionality to export the underlying data that is summarized in a visualization.

## Understanding the data model and entities

Dynamics 365 for Operations data is used to fill the report pages in the **Practice manager** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store, which is a Microsoft SQL database that is optimized for analytics. For more information, see [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md).

### Entity: ProjectAccountingCube_ActualHourUtilization
**Data source**: ProjEmplTrans

| Key aggregate measurement                | Field                                | Description                            | 
|------------------------------------------|--------------------------------------|----------------------------------------|
| ActualBillableUtilizedHours              | Sum(ActualUtilizationBillableRate)   | Total of actual billable utilized hours |
| ActualBillableBurdenHours                | Sum(ActualBurdenBillableRate)        | Total of actual burden rate             |

### Entity: ProjectAccountingCube_Actuals
**Data source**: ProjTransPosting

| Key aggregate measurement                | Field                                | Description                            | 
|------------------------------------------|--------------------------------------|----------------------------------------|
| ActualRevenue                            |     Sum(ActualRevenue)               |  Total of posted revenue for all transaction |   
| ActualCost   |                             Sum(ActualCost)           |    Total of posted cost for all transaction types    |

### Entity: ProjectAccountingCube_Customer
**Data source**: CustTable

| Key aggregate measurement                | Field                                | Description                            | 
|------------------------------------------|--------------------------------------|----------------------------------------|
|    Number of projects        |   COUNTA(ProjectAccountingCube_Projects[PROJECTS])       |         Count of available Projects    |


### Entity: ProjectAccountingCube_Forecasts
**Data source**: ProjTransBudget

| Key aggregate measurement                | Field                                | Description                            | 
|------------------------------------------|--------------------------------------|----------------------------------------|
|    BudgetCost    |       Sum(BudgetCost)  |       Total of forecasted cost for all transaction types     |
|     BudgetRevenue    |         Sum(BudgetRevenue)    |    Total of forecast accrued/invoiced revenue         |
|BudgetGrossMargin | Sum(BudgetGrossMargin) |Difference between sum of total forecast revenue and sum of total forecast cost

### Entity: 
**Data source**: 

| Key aggregate measurement                | Field                                | Description                            | 
|------------------------------------------|--------------------------------------|----------------------------------------|
|                                          |                                      |                                        |
|                                          |                                      |                                        |

### Entity: 
**Data source**: 

| Key aggregate measurement                | Field                                | Description                            | 
|------------------------------------------|--------------------------------------|----------------------------------------|
|                                          |                                      |                                        |
|                                          |                                      |                                        |

### Entity: 
**Data source**: 

| Key aggregate measurement                | Field                                | Description                            | 
|------------------------------------------|--------------------------------------|----------------------------------------|
|                                          |                                      |                                        |
|                                          |                                      |                                        |

## Additional resources

Here are some helpful links that are related to entities and building Power BI content:

- [Data entities](/dynamics365/operations/dev-itpro/data-entities/data-entities)
- [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
- [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
- [Configure Power BI integration for workspaces](configure-power-bi-integration.md)
