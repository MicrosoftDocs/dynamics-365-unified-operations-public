---
title: Practice manager Power BI content
description: Learn about what is included in the Practice manager Power BI content, including a table outlining reports that are included in the Power BI content.
author: sericks007
ms.author: kfend
ms.topic: article
ms.date: 12/18/2017
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.search.form: ProjManagementWorkspace
ms.dyn365.ops.version: July 2017 update
ms.assetid: 
---

# Practice manager Power BI content

[!include [banner](../includes/banner.md)]

This article describes what is included in the **Practice manager** Microsoft Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the content.

## Overview

The **Practice manager** Power BI content was created for practice managers and project managers. It provides key metrics that are related to the projects that the organization is working on. The dashboard gives an overview of the projects and related customers. A report-level filter can be used to report for specific legal entities. This Power BI content pulls data from the project accounting aggregate measurements.

The **Practice manager** Power BI content contains five report pages: one overview page, and four pages that provide details about project costs, revenues, earned value management, and hour metrics that are broken down across various dimensions.

All the amounts in the content are shown in the system currency. You can set the system currency on the **System parameters** page.

## Accessing the Power BI content

The **Practice manager** Power BI content is shown in the **Project management** workspace.

## Reports that are included in the Power BI content

The following table provides details about the metrics that are found on each report page in the **Practice manager** Power BI content.

| Report page       | Metrics |
|-------------------|---------|
| Projects overview | <ul><li>Created projects</li><li>Estimated projects</li><li>In-process projects</li><li>Actual revenue by customer</li><li>Budget gross margin by project</li><li>Earned value management overview</li></ul> |
| Cost              | <ul><li>Actual vs. budget cost by month</li><li>Actual vs. budget cost by year</li><li>Actual vs. budget cost by category</li><li>Actual cost by transaction type</li></ul> |
| Revenue           | <ul><li>Actual revenue by month</li><li>Actual revenue by postal code</li><li>Actual vs. budget revenue by category</li><li>Actual revenue by customer industry</li></ul> |
| EVM               | Cost and schedule performance index by project |
| Hours             | <ul><li>Actual billable utilized hours vs. actual billable burden hours vs. budget hours</li><li>Actual billable utilized hours vs. actual billable burden hours by project</li><li>Actual billable utilized hours vs. actual billable burden hours by resource</li><li>Actual billable hours ratio by project</li><li>Actual billable hours ratio by resource</li></ul> |

The charts and tiles on all these reports can be filtered and pinned to the dashboard. For more information about how to filter and pin 
in Power BI, see [Create and configure a dashboard](https://powerbi.microsoft.com/guided-learning/powerbi-learning-4-2-create-configure-dashboards/). You can also use the Export underlying data functionality to export the underlying data that is summarized in a visualization.

## Understanding the data model and entities

The following data is used to fill the report pages in the **Practice manager** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store. The Entity store is a Microsoft SQL Server database that is optimized for analytics. For more information, see [Power BI integration with Entity store](power-bi-integration-entity-store.md).

The following sections describe the aggregate measurements that are used in each entity.

### Entity: ProjectAccountingCube\_ActualHourUtilization
**Data source:** ProjEmplTrans

| Key aggregate measurement      | Field                              | Description |
|--------------------------------|------------------------------------|-------------|
| Actual billable utilized hours | Sum(ActualUtilizationBillableRate) | The total of actual billable utilized hours. |
| Actual billable burden hours   | Sum(ActualBurdenBillableRate)      | The total of the actual burden rate. |

### Entity: ProjectAccountingCube\_Actuals
**Data source:** ProjTransPosting

| Key aggregate measurement | Field              | Description |
|---------------------------|--------------------|-------------|
| Actual revenue            | Sum(ActualRevenue) | The total of posted revenue for all transactions. |
| Actual cost               | Sum(ActualCost)    | The total of posted cost for all transaction types. |

### Entity: ProjectAccountingCube\_Customer
**Data source:** CustTable

| Key aggregate measurement | Field                                             | Description |
|---------------------------|---------------------------------------------------|-------------|
| Number of projects        | COUNTA(ProjectAccountingCube\_Projects\[PROJECTS\]) | The count of available projects. |

### Entity: ProjectAccountingCube\_Forecasts
**Data source:** ProjTransBudget

| Key aggregate measurement | Field                  | Description |
|---------------------------|------------------------|-------------|
| Budget cost               | Sum(BudgetCost)        | The total of forecast cost for all transaction types. |
| Budget revenue            | Sum(BudgetRevenue)     | The total of forecast accrued/invoiced revenue. |
| Budget gross margin       | Sum(BudgetGrossMargin) | The difference between the sum of total forecast revenue and the sum of total forecast cost. |

### Entity: ProjectAccountingCube\_ProjectPlanCostsView
**Data source:** Project

| Key aggregate measurement | Field                    | Description |
|---------------------------|--------------------------|-------------|
| Planned cost              | Sum(SumOfTotalCostPrice) | The total cost price in estimates for all project transaction types that have planned tasks. |

### Entity: ProjectAccountingCube\_Projects
**Data source:** Project

| Key aggregate measurement    | Field | Description |
|------------------------------|-------|-------------|
| Cost performance index       | ProjectAccountingCube\_Projects\[Earned value\] ÷ ProjectAccountingCube\_Projects\[Total actual cost of completed tasks\] | The calculation of the total earned value divided by the total actual cost. |
| Schedule performance index   | ProjectAccountingCube\_Projects\[Earned value\] ÷ ProjectAccountingCube\_Projects\[Total planned cost of completed tasks\] | The calculation of the total earned value divided by the total planned cost. |
| Percentage of work completed | Percentage of work completed = ProjectAccountingCube\_Projects\[Total actual cost of completed tasks\] ÷ (ProjectAccountingCube\_Projects\[Total actual cost of completed tasks\] + ProjectAccountingCube\_Projects\[Total planned cost of project\] – ProjectAccountingCube\_Projects\[Total planned cost of completed tasks\]) | The total percentage of completed work, based on the total actual cost of completed tasks and the planned cost of the project. |
| Actual billable hours ratio  | ProjectAccountingCube\_Projects\[Project total actual billable utilized hours\] ÷ (ProjectAccountingCube\_Projects\[Project total actual billable utilized hours\] + ProjectAccountingCube\_Projects\[Project total actual billable burden hours\]) | The total actual billable hours, based on the utilized hours and the burden hours. |
| Earned value                 | ProjectAccountingCube\_Projects\[Total planned cost of project\] × ProjectAccountingCube\_Projects\[Percentage of work completed\] | The total planned cost multiplied by the percentage of completed work. |

### Entity: ProjectAccountingCube\_TotalEstimatedCosts 
**Data source:** ProjTable

| Key aggregate measurement       | Field               | Description |
|---------------------------------|---------------------|-------------|
| Completed activity planned cost | Sum(TotalCostPrice) | The total cost price in estimates for all project transaction types that have completed tasks. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
