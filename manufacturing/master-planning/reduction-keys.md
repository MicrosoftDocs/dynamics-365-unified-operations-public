---
# required metadata

title: Reduction keys
description: This articles provides examples that show how to set up a reduction key. It includes information about the various reduction key settings and the results of each. You can use a reduction key to define how to reduce forecast requirements.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-12-07 09 - 16 - 13
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ReqPlanSched
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 19251
ms.assetid: f1b957f4-3866-4b41-bdec-c62409371133
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Reduction keys

This articles provides examples that show how to set up a reduction key. It includes information about the various reduction key settings and the results of each. You can use a reduction key to define how to reduce forecast requirements.

Example 1: Percent - reduction key forecast reduction principle
---------------------------------------------------------------

This example shows how a reduction key reduces demand forecast requirements according to the percentages and periods that are defined by the reduction key.

1.  On the **Reduction keys** page, set up the following lines.
    | Change | Unit  | Percent |
    |--------|-------|---------|
    | 1      | Month | 100     |
    | 2      | Month | 75      |
    | 3      | Month | 50      |
    | 4      | Month | 25      |

2.  Link the reduction key to the item's coverage group.
3.  On the **Master plans** page, in the **Reduction principle** field, select **Percent - reduction key**.
4.  Create a demand forecast of 1,000 pieces per month.

If you run forecast scheduling on January 1, the demand forecast requirements are consumed according to the percentages that you set up on the **Reduction keys** page. The following requirement quantities are transferred to the master plan.

| Month                | Number of pieces required |
|----------------------|---------------------------|
| January              | 0                         |
| February             | 250                       |
| March                | 500                       |
| April                | 750                       |
| May through December | 1,000                     |

## Example 2: Transactions  reduction key forecast reduction principle
This example shows how actual orders that occur during the periods that are defined by the reduction key reduce demand forecast requirements.

-   On the **Master plans** page, in the **Reduction principle** field, select **Transactions - reduction key**.

The following sales orders exist on January 1.

| Month    | Number of pieces ordered |
|----------|--------------------------|
| January  | 956                      |
| February | 1,176                    |
| March    | 451                      |
| April    | 119                      |

If you use the same demand forecast of 1,000 pieces per month, the following requirement quantities are transferred to the master plan.

| Month                | Number of pieces required |
|----------------------|---------------------------|
| January              | 44                        |
| February             | 0                         |
| March                | 549                       |
| April                | 881                       |
| May through December | 1,000                     |

## Example 3: Transactions  dynamic period forecast reduction principle
In most cases, systems are set up so that transactions reduce demand forecast within specific forecast periods: weeks, months, and so on. These periods are defined in the reduction key. However, the time between two demand forecast lines can also *imply* a period.

1.  Create a demand forecast for the following dates and quantities.
    | Date       | Demand forecast |
    |------------|-----------------|
    | January 1  | 1,000           |
    | January 5  | 500             |
    | January 12 | 1,000           |

    In this forecast, there isn't a clear period between the forecast dates: between the first and second dates there is a four-day span, and between the second and third dates there is a seven-day span. These various spans are the dynamic periods.
2.  Create sales order lines as follows.
    | Date                             | Sales order quantity |
    |----------------------------------|----------------------|
    | December 15 in the previous year | 500                  |
    | January 3                        | 100                  |
    | January 10                       | 200                  |

The forecast will be reduced as follows:

-   The first sales order isn't within any period, so it won't reduce any forecast.
-   The second sales order is between January 1 and January 5, so it will reduce the forecast for January 1 by 100.
-   The third sales order is between January 5 and January 12, so it will reduce the forecast for January 5 by 200.

The following planned order will be created to fulfill the forecast.

| Demand forecast date | Reduced quantity |
|----------------------|------------------|
| January 1            | 900              |
| January 5            | 300              |
| January 12           | 1,000            |

Here is a summary of **Transactions - dynamic period** reduction:

-   Forecast requirements are reduced by the actual order transactions that occur during the dynamic period. The dynamic period covers the current forecast dates and ends at the start of the next forecast.
-   This method doesn't use or require a reduction key.
-   When this option is used, the following behavior occurs:
    -   If the forecast is reduced completely, the forecast requirements for the current forecast become 0 (zero).
    -   If there is no future forecast, forecast requirements from the last forecast that was entered are reduced.
    -   Time fences are included in the forecast reduction calculation.
    -   Positive days are included in the forecast reduction calculation.
    -   If actual order transactions exceed the forecasted requirements, the remaining transactions aren't forwarded to the next forecast period.


See also
--------

[Master plans](master-plans.md)

