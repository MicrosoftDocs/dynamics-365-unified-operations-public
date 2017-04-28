---
# required metadata

title: Practice manager content pack for Power BI
description: This topic describes what's included in the Practice Manager BI Report Dynamics 365 for Operations content pack for Microsoft Power BI. It explains how to access the reports included in the content pack and provides information about the data model and entities that are used to build the content pack.
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

[!includebanner]

# Practice manager Power BI content

This topic describes what's included in the **Practice manager** Power BI content. It explains how to access the Power BI reports, and provides information about the data model and entities that are used to build the  content.

**Overview**

The **Practice manager** Power BI content was created for practice managers and project managers to provide them with key metrics related to the projects the organization is working on. The dashboard will provide an overview of the projects and related customers. A report-level filter can be used to report for specific legal entities. This Power BI content pulls data from the project accounting aggregate measurements for Dynamics 365 for Operations.

The **Practice manager** Power BI content contains five report pages: one overview page and four pages providing details of project costs, revenues, earned value management, and hour metrics sliced and diced across different dimensions.

All the amounts in the content are shown in the system currency. You can set the system currency on the Systems parameters page.

**Accessing the Power BI content**

You can find the **Practice manager** Power BI content in the Shared assets library in Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download the content pack and connect it to your Microsoft Dynamics 365 for Operations data, see [Power BI content in LCS from Microsoft and your partners](power-bi-content-microsoft-partners.md).

To watch a demo of how to implement the Power BI content, see this [Office mix](https://mix.office.com/watch/9puyb1b2xs1w).

**Reports that are included in the Power BI content**

The following table provides details about the metrics found on each report pages in the **Practice manager** Power BI content.

| **Report page**                                      | **Metrics**               |
|------------------------------------------------------|-----------------------------------------------|
| Dashboard  | Created projects, Estimated projects, In-process projects, Number of projects by stage, Number of projects by city,  Actual revenue by customer, Budget gross margin by project, Earned value management overview |
| Cost                                                 | Actual vs budget cost by month, Actual vs budget cost by year, Actual vs budget cost by category, Actual cost by transaction type       |
| Revenue                                              | Actual revenue by month, Actual revenue by postal code, Actual vs budget revenue by category, Actual revenue by customer industry        |
| EVM                                                  | Cost and schedule performance index by project                 |
| Hours                                                | Actual billable utilized hours vs actual billable burden hours vs budget hours, Actual billable utilized hours vs actual billable burden hours by project, Actual billable utilized hours vs actual billable burden hours by resource, Actual billable hours ratio by project, Actual billable hours ratio by resource |

The charts and tiles on all these reports can be filtered and pinned to the dashboard. For more information about how to filter and pin 
in Power BI, see [Create and configure a dashboard](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-4-2-create-configure-dashboards/). You can also use the export underlying data functionality to export underlying data 
that is summarized on a visualization.

**Understanding the data model and entities**

Dynamics 365 for Operations data is used to fill the report pages in the **Practice manager** Power BI content. This data is represented as aggregate measurements that are staged in the Entity store, which is a Microsoft SQL database that is optimized for analytics. For more information, see [Overview of Power BI integration with Entity store](power-bi-integration-entity-store.md).

The following key aggregate measurements are used as the basis of the content.

| **Entity**   | **Key aggregate measurements**   | **Data source for Dynamics 365 for Operations** | **Field**  | **Description**     |
|--------------|----------------------------------|-------------------------------------------------|------------|---------------------|
| ProjectAccountingCube_ActualHourUtilization | ActualBillableUtilizedHours, ActualBillableBurdenHours,| ProjEmplTrans | Sum(ActualUtilizationBillableRate), Sum(ActualBurdenBillableRate)| Total of actual billable utilized hours, Total of actual burden rate |
| ProjectAccountingCube\_Actuals        | ActualRevenue, ActualCost, | ProjTransPosting                                | Sum(ActualRevenue), Sum(ActualCost)        | Total of posted revenue for all transaction types, Total of posted cost for all transaction types | 
| ProjectAccountingCube\_Customer | Number of projects    | CustTable | COUNTA(ProjectAccountingCube\_Projects[PROJECTS])  | Count of available Projects | 
| ProjectAccountingCube\_Forecasts  | BudgetCost, BudgetRevenue, BudgetGrossMargin  | ProjTransBudget      | Sum(BudgetCost), Sum(BudgetRevenue), Sum(BudgetGrossMargin)     | Total of forecasted cost for all transaction types, Total of forecast accrued/invoiced revenue, Difference between sum of total forecast revenue and sum of total forecast cost  |   
| ProjectAccountingCube\_ProjectPlanCostsView  | PlannedCost  | Project  | Sum(SumOfTotalCostPrice)  | Total cost price in estimates for all project transaction types with planned tasks|   
| ProjectAccountingCube\_Projects | Cost performance index, Schedule performance index, Percentage of work completed, Project actual billable Hours ratio Earned value | Project | ProjectAccountingCube\_Projects[Earned value] / ProjectAccountingCube\_Projects[Total actual cost of completed tasks], ProjectAccountingCube\_Projects[Earned value] / ProjectAccountingCube\_Projects[Total planned cost of completed tasks], Percentage of work completed = ProjectAccountingCube\_Projects[Total actual cost of completed tasks] / (ProjectAccountingCube\_Projects[Total actual cost of completed tasks] + ProjectAccountingCube\_Projects[Total planned cost of project] - ProjectAccountingCube\_Projects[Total planned cost of completed tasks]), ProjectAccountingCube\_Projects[Project total actual billable utilized hours] / (ProjectAccountingCube\_Projects[Project total actual billable utilized hours] + ProjectAccountingCube\_Projects[Project total actual billable burden hours]), ProjectAccountingCube\_Projects[Total planned cost of project] \* ProjectAccountingCube\_Projects[Percentage of work completed] | Calculation of total earned value divided by total actual cost, Calculation of total earned value divided by total planned cost Total percentage of completed work based off total actual cost of completed task and planned cost of the project Total actual billable hours based on utilized + burden, Total planned cost multiply by percentage of completed work | 
| ProjectAccountingCube\_TotalEstimatedCosts   | CompletedActivityPlannedCost | ProjTable  | Sum(TotalCostPrice)  | Total cost price in estimates for all project transaction types with completed tasks   |

## Additional resources

Here are some helpful links that are related to entities and building Power BI content:
-   [Data entities](dynamics365/operations/dev-itpro/data-entities/data-entities)
-   [Creating organizational content packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)
-   [Data modeling using Power BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)
-   [Configure Power BI integration for workspaces](configure-power-bi-integration.md)
