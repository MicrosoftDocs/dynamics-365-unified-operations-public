---
# required metadata

title: Allocation visual
description: This article describes how to use the Allocation visual in the Business performance planning application.
author: ShielaSogge
ms.date: 12/08/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2023-12-03
ms.dyn365.ops.version: 

---
# Allocation visual

[!include [banner](../includes/banner.md)]

This article describes how to use the **Allocation** visual in the Business performance planning application. To fully use the planning application, you must also install Power BI visuals. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

Understanding allocation in the planning application is fundamental for accurate and informed business planning. The **Allocation** visual operates at different levels within dimensions, so you can effectively strategize and plan business operations with confidence.

## Understanding data levels in dimensions

In Dataverse, your data can have various levels underneath it. These levels depict hierarchical relationships. For example, a "parent" category may be followed by more specific "child" entities, such as a product category and its respective SKUs.

## Allocation at different levels

When the planning application writes values at the "parent" level, it engages in allocation across all subsidiary "child" values. The allocation process varies based on certain conditions as described below.

### Equal allocation for zero and equal amount child values

If all child values are \$0 or equal amounts, the planning application defaults to an equal allocation across each child cell. For instance, allocating \$1,000 across 10 child cells results in \$100 allocated to each child.

### Respect for preexisting distributions

When child cells contain preexisting values, the planning application respects this distribution. Allocation occurs proportionately based on existing values. For instance, allocating \$200 across two child cells with existing values \$5 and \$15 respectively results in \$50 and \$150 respectively.

**Relative increase**
To enter a relative increase or decrease, enter **i** or **d** in front of the number. For example, **i10%** or **d10%** to increase or decrease by 10%, or use the **Relative Increase/Decrease** option in the right-click context menu.

**Fill right**
Using **r**, write the entered value to every cell on the same level to the right. For example, **r1000** entered in January for a time dimension will write 1000 from February to December, or use the **Fill Right** option in the right-click context menu.

**Allocation with multi-select**
If the multi-select mode is turned on, the **s** prefix in the multi-select value dialog field allows you to spread an entry to the selected cells and use their current distribution.

**Copy Like**
This option is available only with the right-click context menu and it enables you to apply any distribution in the used cube with your entry.

## Accurate business planning

USe the planning application for high-level business planning with an assurance that forecasted or budgeted data accurately mirrors historical actuals. With this functionality, you can:

- Plan business strategies confidently at higher levels, knowing that the planning application ensures alignment with historical data.
- Leverage the planning application's allocation mechanism, which adapts to various levels of granularity, ensuring accurate planning even when working with complex hierarchical data structures.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
