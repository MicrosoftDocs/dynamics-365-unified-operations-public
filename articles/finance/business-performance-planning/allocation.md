---
title: Allocation method
description: Learn how to use the Allocation method in the Business performance planning application, including outlines on how allocation applies at different data levels.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 12/08/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Allocation method

[!include [banner](../includes/banner.md)]

This article describes how to use the **Allocation** method in the Business performance planning application. To fully use this application, you must also install Microsoft Power BI visuals. For information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

An understanding of allocation in the Business performance planning application is fundamental for accurate and informed business planning. The **Allocation** visual works at different levels within dimensions to help you effectively strategize and confidently plan business operations.

## Allocation at different data levels in dimensions

In Dataverse, your data can have different levels beneath it. These levels define hierarchical relationships. For example, a "parent" category might be followed by more specific "child" entities. An example is a product category and its different stockkeeping units (SKUs).

When the Business performance planning application writes values at the parent level, it engages in allocation across all subsidiary child values. The allocation process varies, depending on specific conditions that are described in the following subsections.

### Equal allocation for zero and equal amount child values

By default, if all child values are 0 (zero) or equal amounts, the Business performance planning application does an equal allocation across every child cell. For example, if an allocation of $1,000 is done across 10 child cells, $100 is allocated to each child.

### Respect for preexisting distributions

If child cells contain preexisting values, the Business performance planning application respects this distribution. Allocation is done proportionately, based on existing values. For example, an allocation of $200 is done across two child cells. One cell has an existing value of $5, and the other has an existing value of $15. In this case, $50 is allocated to the first cell, and $150 is allocated to the second cell.

#### Relative increase

To enter a relative increase or decrease, enter the prefix **i** or **d** in front of the number. For example, enter **i10%** to increase by 10 percent or **d10%** to decrease by 10 percent.

Alternatively, select and hold (or right-click), and then select **Relative Increase/Decrease**.

#### Fill right

To write a value to every cell to the right at the same level, enter the prefix **r** in front of the value. For example, if you enter **r1000** in January for a time dimension, **1000** is written from February through December.

Alternatively, select and hold (or right-click), and then select **Fill Right**.

#### Allocation with multi-select

If multi-select mode is turned on, the **s** prefix in the multi-select field lets you spread an entry to the selected cells and use their current distribution.

#### Copy like

This option is available only on the shortcut menu that appears when you select and hold (or right-click). It lets you apply your entry to any distribution in the cube that's used.

## Accurate business planning

When you use the Business performance planning application for high-level business planning, you can be sure that forecasted or budgeted data accurately mirrors historical actuals. The functionality offers the following benefits:

- Confidently plan business strategies at higher levels, and know that the application ensures alignment with historical data.
- Take advantage of the application's allocation mechanism, which adapts to different levels of granularity to ensure accurate planning even when you work with complex hierarchical data structures.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
