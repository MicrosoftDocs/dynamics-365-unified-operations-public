---
title: Calculated columns in Dynamics 365 Finance business performance planning
description: Learn how to create calculated columns by using formulas in Microsoft Dynamics 365 Finance business performance planning.
author: ShielaSogge
ms.author: romainpham
ms.topic: how-to
ms.date: 11/11/2025
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Calculated columns in Dynamics 365 Finance Business performance planning

> [!NOTE]
> This article describes the cube creation process that's available in Business performance planning versions 1.13 and earlier. Starting in version 1.14, a new cube creation process is available. For more information, see [Cubes (preview)](bpp-create-cubes.md). 

Business performance planning in Microsoft Dynamics 365 Finance supports calculated columns that are known as computed columns. You can use them to define formula-based logic directly in your planning cube. These columns use the Dataverse formula column engine to drive financial modeling, workforce planning, revenue calculations, and more.

This article explains how to create computed columns inside a cube by using expressions that are powered by Dataverse formula columns. In this way, you enable dynamic and context-aware calculations. 

## Prerequisites
- Access to business performance planning in Dynamics 365 Finance.
- An existing cube where dimensions and drivers are defined.
- A security role that has permissions to edit cubes and add computed columns.
- An understanding of the syntax for Dataverse formula columns. Learn more in [Work with formula columns](/power-apps/maker/data-platform/formula-columns).

### Create a calculated column

To create a calculated column, follow these steps:
1. In business performance planning, select **Cubes**.
1. Open the cube that you want to add a computed column to.
1. In **Computed columns**, select **Add**.
1. In the **Name** field, enter a name.
1. In the **Description** field, enter a short explanation of the formula.
1. In the **Formula** field, enter the Dataverse formula syntax.
1. Select **Submit** to save the column.

### Formula syntax guidelines

You can reference the following elements:

- Other computed columns in the same cube
- Columns from dimensions that were used to build the cube

You can't reference the following elements:
- Rows other than the current row (In other words, lookup/aggregation across rows can't be done.)
- Reference dimensions that aren't included in the cube

### Revenue planning: Price &times; Quantity
Use this formula for revenue forecast modeling by stock-keeping unit (SKU), region, or channel.
*Price* \* *Quantity*

### Gross Margin and Margin %
Use this formula for profitability modeling by product line.
*GrossMargin* = *Revenue* - *COGS*
*MarginPercent* = (*Revenue* - *COGS*) / *Revenue*


### Operating expense allocation (Headcount-Based)
Use this formula for shared cost allocation.
(*DepartmentHeadcount* / *TotalHeadcount*) \* *ITCost*

> [!NOTE]
> Total headcount must be stored or precalculated in your dataset.

### CapEx depreciation (Straight-Line)
Use this formula for fixed asset and depreciation forecasting.
*CapExAmount* / *UsefulLifeYears*

### Workforce planning: Fully Loaded full-time employee (FTE) cost

In Human Resources planning scenarios, you can use calculated columns to model fully loaded full-time employee (FTE) cost based on the following information:

- Base salary
- Bonus
- Benefits
- Tax

*FTETotalCost* = *BaseSalary* + *Bonus* + *Benefits* + *Taxes*

## Power BI integration and performance considerations

If you use DirectQuery mode with Dataverse to enable write-back and bring real-time access to planning data in Power BI and Excel, there are some performance limitations when calculations are handled entirely through Data Analysis Expressions (DAX).

Use computed columns instead of DAX in the following situations:

- The same key performance indicator (KPI) is repeatedly calculated (for example, margin, bonus, or adjusted cost).
- You want to centralize business rules and avoid duplication.
- You want consistent logic across multiple reports.

### Example

Instead of defining margin in DAX, create a computed column. Here is an example:

*Revenue* \* *COGS*

In this case, Power BI fetches only a precomputed column. Therefore, this approach improves performance, reduces the DAX load, and ensures reusability.

### Best practices

- Use computed columns for all common KPIs.
- Format the results (for example, a percentage or currency) in Power BI visuals.
- Use dimension security and OAuth 2.0 in Power BI for row-level filtering.

### Use composite models to blend planning and analytics

A *composite model* combines the following elements:

- DirectQuery connections to the business performance planning cube (for planning and write-back)
- Imported data (for example, previous year actuals, external KPIs, or warehouse data)

This hybrid architecture provides the following benefits.

| Benefit | DirectQuery (business performance planning) | Import (external)|
|---|---|---|
| Real-time planning and write-back |Yes | No |
| High-performance analytics | Slower for large sets | Yes |
| Complex DAX modeling | Limited | Fully supported |
| Combination of data sources|  Limited | Through the composite model |

Here are some common scenarios for composite models:

- Optimize performance for reporting that requires many years of actuals.
- Compare budget (in business performance planning) with actuals (in the data warehouse).
- Add benchmarks or ratios that aren't available in Dataverse.

> [!NOTE]
> The planning cube must remain in DirectQuery mode to support write-back. Imported tables can enhance reporting logic without breaking this behavior.
