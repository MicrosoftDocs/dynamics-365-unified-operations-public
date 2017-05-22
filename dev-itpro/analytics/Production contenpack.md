**Overview**

This content pack was created for Production managers or individuals in the
organization responsible for performing production control.

The reports in this content pack lets you use Microsoft Power BI to monitor the
performance of manufacturing operations with respect to timely execution,
quality, and cost. The reports leverage transactional data from production
orders and batch orders in Microsoft Dynamics 365 for Operations, and provide
both an aggregate view of company-wide production metrics and a breakdown of
metrics by product and resource.

The ability to complete production on time and in full is highlighted, and the
future performance is projected based on the production plans. Comprehensive
reports provide detailed insights into product defects caused by production, as
well as the defect rates for resources and operations.

This content pack also lets you analyze production variances, which are
calculated as the difference between estimated cost and realized cost.
Production variances are calculated when production order or batch order reach
status ended.

The Production performance content pack only include data origin from Production
orders and Batch orders. The reports do not include data related to Kanban
productions.

**Accessing the content pack**

The Production performance Power BI content pack is published as an
implementation asset in Lifecycle Services (LCS) and can be accessed from
Dynamics 365 for Operations. For more information about how to access and launch
Power BI reports, see the blog [Authoring and distributing Power BI reports with
Dynamics](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/23/authoring-and-distributing-power-bi-reports-with-dynamics-ax7/).

**Metrics included in the content pack**

The content pack includes a set of report pages which each consists of a set of
metrics visualized as charts, tiles, and tables.

The following table provides an overview of the visualizations in the content
pack.

| **Report page**                            | **Charts**                                           | **Tiles**             |
|--------------------------------------------|------------------------------------------------------|-----------------------|
| Production performance                     | Number of production by date                         | Total orders          |
|                                            | Number of productions by product and item group      | On-time & in full %   |
|                                            | Number of planned productions by date                | Incomplete %          |
|                                            | Bottom 10 products by on-time & in-full              | Early %               |
|                                            |                                                      | Late %                |
| Defects by product                         | Defective rate (ppm) by date                         | Defective rate (ppm)  |
|                                            | Defective rate (ppm) by product and item group       | Defective quantity    |
|                                            | Quantity produced by date                            | Total quantity        |
|                                            | Top 10 products by effective rate                    |                       |
| Defects trend by product                   | Defect rate (ppm) by quantity produced               | Defect rate (ppm)     |
| Defects by resource                        | Defect rate (ppm) by date                            | Defective quantity    |
|                                            | Defect rate (ppm) by resource and Site               |                       |
|                                            | Defect rate (ppm) by operation                       |                       |
|                                            | Top 10 resources by defect rate                      |                       |
| Defects trend by resource                  | Defect rate (ppm) by quantity processed              |                       |
| Production variances for job order costing | Production variance by date and cost group type      | Realized cost         |
|                                            | Production variance by site and cost group type      | Production variance   |
|                                            | Top 10 products with unfavorable production variance | Production variance % |
|                                            | Top 10 unfavorable production variance by resource   |                       |

**Understanding the data model and entities**

Dynamics 365 for Operations data is used to populate the report pages in the
Production performance content pack. This is represented as aggregate
measurements that are staged in the Entity store, which is a Microsoft SQL
database optimized for analytics. Read more about it in the blog [Power BI
integration with Entity Store in
Dynamics](https://blogs.msdn.microsoft.com/dynamicsaxbi/2016/06/09/power-bi-integration-with-entity-store-in-dynamics-ax-7-may-update/).

The following key aggregate measurements of the entities listed below are used
as the basis of the content pack.

| **Entity**               | **Key aggregate measurements** | **Data source for Dynamics 365 for Operations** | **Field**          |
|--------------------------|--------------------------------|-------------------------------------------------|--------------------|
| CostCalculation          | CostAmount                     | ProdCalcTransExpanded                           | CostAmount         |
| CostCalculation          | CostMarkup                     | ProdCalcTransExpanded                           | CostMarkup         |
| CostCalculation          | ActualCostAmount               | ProdCalcTransExpanded                           | RealCostAmount     |
| CostCalculation          | RealCostAdjustment             | ProdCalcTransExpanded                           | RealCostAdjustment |
| RouteTransactions        | ErrorQuantity                  | ProdRouteTransExpanded                          | QtyError           |
| RouteTransactions        | GoodQuantity                   | ProdRouteTransExpanded                          | QtyGood            |
| ProductionOrder          | DaysDelayed                    | ProdTableExpanded                               | DaysDelayed        |
| ProductionOrder          | LeadTime                       | ProdTableExpanded                               | LeadTime           |
| ProductionOrder          | PlannedLeadTime                | ProdTableExpanded                               | PlannedLeadTime    |
| ProductionOrder          | ProductionOrderCount           | ProdTableExpanded                               |                    |
| CoproductCostCalculation | CoproductCostAmount            | PmfCoByProdCalcTransExpanded                    | CostAmount         |
| CoproductCostCalculation | CoproductCostMarkup            | PmfCoByProdCalcTransExpanded                    | CostMarkup         |
| CoproductCostCalculation | CoproductRealCostAdjustment    | PmfCoByProdCalcTransExpanded                    | RealCostAdjustment |
| CoproductCostCalculation | CoproductActualCostAmount      | PmfCoByProdCalcTransExpanded                    | RealCostAmount     |

The following table shows how the key aggregate measurements are used to create
several calculated measures in the content pack’s dataset.

| **Measure**              | **Calculated as**                                                                                                                                                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Production variance, %   | SUM('Production variance'[Production variance]) / SUM('Production variance'[Estimated cost])                                                                                                                    |
| All planned orders       | COUNTROWS('Planned production order')                                                                                                                                                                           |
| Early                    | COUNTROWS(FILTER('Planned production order', 'Planned production order'[Scheduled end date] \< 'Planned production order'[Requirement date]))                                                                   |
| Late                     | COUNTROWS(FILTER('Planned production order', 'Planned production order'[Scheduled end date] \> 'Planned production order'[Requirement date]))                                                                   |
| On-time                  | COUNTROWS(FILTER('Planned production order', 'Planned production order'[Scheduled end date] = 'Planned production order'[Requirement date]))                                                                    |
| On-time %                | IF ( 'Planned production order'[On-time] \<\> 0, 'Planned production order'[On-time], IF ('Planned production order'[All planned orders] \<\> 0, 0, BLANK()) ) / 'Planned production order'[All planned orders] |
| Completed                | COUNTROWS(FILTER('Production order', 'Production order'[Is RAF'ed] = TRUE))                                                                                                                                     |
| Defective rate (ppm)     | IF( 'Production order'[Total quantity] = 0, BLANK(), (SUM('Production order'[Defective quantity]) / 'Production order'[Total quantity]) \* 1000000)                                                             |
| Delayed production rate  | 'Production order'[Late \#] / 'Production order'[Completed]                                                                                                                                                     |
| Early & in full          | COUNTROWS(FILTER('Production order', 'Production order'[Is in full] = TRUE && 'Production order'[Is early] = TRUE))                                                                                             |
| Early \#                 | COUNTROWS(FILTER('Production order', 'Production order'[Is early] = TRUE))                                                                                                                                      |
| Early %                  | IFERROR( IF('Production order'[Early \#] \<\> 0, 'Production order'[Early \#], IF('Production order'[Total orders] = 0, BLANK(), 0)) / 'Production order'[Total orders], BLANK())                               |
| Incomplete               | COUNTROWS(FILTER('Production order', 'Production order'[Is in full] = FALSE && 'Production order'[Is RAF'ed] = TRUE))                                                                                           |
| Incomplete %             | IFERROR( IF('Production order'[Incomplete] \<\> 0, 'Production order'[Incomplete], IF('Production order'[Total orders] = 0, BLANK(), 0)) / 'Production order'[Total orders], BLANK())                           |
| Is delayed               | 'Production order'[Is RAF'ed] = TRUE && 'Production order'[Delayed value] = 1                                                                                                                                   |
| Is early                 | 'Production order'[Is RAF'ed] = TRUE && 'Production order'[Days delayed] \< 0                                                                                                                                   |
| Is in full               | 'Production order'[Good quantity] \>= 'Production order'[Scheduled quantity]                                                                                                                                    |
| Is RAF'ed                | 'Production order'[Production status value] = 5 \|\| 'Production order'[Production status value] = 7                                                                                                            |
| Late & in full           | COUNTROWS(FILTER('Production order', 'Production order'[Is in full] = TRUE && 'Production order'[Is delayed] = TRUE))                                                                                           |
| Late \#                  | COUNTROWS(FILTER('Production order', 'Production order'[Is delayed] = TRUE))                                                                                                                                    |
| Late %                   | IFERROR( IF('Production order'[Late \#] \<\> 0, 'Production order'[Late \#], IF('Production order'[Total orders] = 0, BLANK(), 0)) / 'Production order'[Total orders], BLANK())                                 |
| On-time & in full        | COUNTROWS(FILTER('Production order', 'Production order'[Is in full] = TRUE && 'Production order'[Is delayed] = FALSE && 'Production order'[Is early] = FALSE))                                                  |
| On-time & in full %      | IFERROR( IF('Production order'[On-time & in full] \<\> 0, 'Production order'[On-time & in full], IF('Production order'[Completed] = 0, BLANK(), 0)) / 'Production order'[Completed], BLANK())                   |
| Total orders             | COUNTROWS('Production order')                                                                                                                                                                                   |
| Total quantity           | SUM('Production order'[Good quantity]) + SUM('Production order'[Defective quantity])                                                                                                                            |
| Defect rate (ppm)        | IF( 'Route transactions'[Processed quantity] = 0, BLANK(), (SUM('Route transactions'[Defective quantity]) / 'Route transactions'[Processed quantity]) \* 1000000)                                               |
| Defect ratio mixed (ppm) | IF( 'Route transactions'[Total mixed quantity] = 0, BLANK(), (SUM('Route transactions'[Defective quantity]) / 'Route transactions'[Total mixed quantity]) \* 1000000)                                           |
| Processed quantity       | SUM('Route transactions'[Good quantity]) + SUM('Route transactions'[Defective quantity])                                                                                                                        |
| Total mixed quantity     | SUM('Production order'[Good quantity]) + SUM('Route transactions'[Defective quantity])                                                                                                                          |

The following key dimensions are used as filters to slice the aggregate
measurements to achieve greater granularity and deeper analytical insights.

| **Entity**                | **Examples of attributes**                                    |
|---------------------------|---------------------------------------------------------------|
| Reported as finished date | Completion (RAF) date, Month and Year offset                  |
| Ended date                | Ended month offset and Month                                  |
| Requirement date          | Requirement date month offset, Requirement date               |
| Route transaction date    | Route transaction month offset, Date                          |
| Sites                     | Sites ID, Site name, State and City ect.                      |
| Entities                  | Id and Name                                                   |
| Resources                 | Resource ID, Resource name, Resource type and Resource group, |
| Products                  | Product number, Product name, Item ID and Item group          |

**Additional resources**

Here are some helpful links that are related to entities and building Power BI
content:

-   [Data entities](https://ax.help.dynamics.com/en/wiki/data-entities/)

-   [Creating organizational content
    packs](https://powerbi.microsoft.com/en-us/documentation/powerbi-service-organizational-content-packs-introduction/)

-   [Data modeling using Power
    BI](https://powerbi.microsoft.com/en-us/guided-learning/powerbi-learning-2-1-intro-modeling-data)

-   [Adding Power BI tiles to
    workspaces](http://ax.help.dynamics.com/en/wiki/configuring-powerbi-integration/)
