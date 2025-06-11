---
title: Calculated columns in Dynamics 365 Finance business performance planning
description: This article describes how to create calculated columns using formulas in Dynamics 365 Finance business performance planning.
author: ShielaSogge
ms.author: romainpham
ms.topic: how-to
ms.date: 06/11/2025
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Calculated columns in Dynamics 365 Finance business performance planning

This articles describes how to create computed columns inside a cube using expressions powered by Dataverse formula columns, enabling dynamic and context-aware calculations.

## Overview
Business performance planning in Dynamics 365 Finance supports calculated columns (also known as computed columns) that allows you to define formula-based logic directly within your planning cube. These columns
use the Dataverse formula column engine to drive financial modelling, workforce planning, revenue calculations, and more. 

This article describes how to create computed columns and showcases typical FP&A use cases, plus best practices on how to use computed column to optimize performance for Direct Query data model in Power BI and 
Excel.

For more information, see [Dataverse formula columns](power-apps/maker/data-platform/formula-columns).

### Prerequisites
•	Access to Business performance planning in Dynamics 365 Finance.
•	An existing cube with dimensions and drivers defined.
•	Security role with permissions to edit cubes and add computed columns.
•	Understanding of the Dataverse formula column syntax. For more information, see [Formula columns](/power-apps/maker/data-platform/formula-columns).

### Create a calculated column

To create a calculated column, follow these steps:
1.	Go to Business performance planning, select **Cubes**.
2.	Open the cube to add the computed column.
3.	In **Computed columns**, select **+ Add**.
4.	In the **Name** field, enter a name.
5.	In the **Description** field, enter a short explanation of the formula.
6.	In the **Formula** field, enter the Dataverse formula syntax.
7.	Click **Submit** to save your column.

#### Formula syntax guidelines

You can reference:
 - Other computed columns in the same cube
 - Columns from dimensions used to build the cube

You can't reference:
 - Rows other than the current one (no lookup/aggregation across rows)
 - Reference dimensions that aren't included in the cube
o	Be edited or overwritten by users using Excel or Power BI write-back visuals.

### Example formulas

Example: Revenue planning: Price × Quantity
Price * Quantity
Use: Revenue forecast modelling by SKU, region, or channel.

Example: Gross Margin and Margin %
GrossMargin = Revenue - COGS
MarginPercent = (Revenue - COGS) / Revenue Example 3: Total Compensation
Use: Profitability modelling by product line.

Example: Operating expense allocation (Headcount-Based)
(DepartmentHeadcount / TotalHeadcount) * ITCost
Note: TotalHeadcount must be stored or pre-calculated in your dataset.
Use: Shared cost allocation.

Example: CapEx depreciation (Straight-Line)
CapExAmount / UsefulLifeYears
Use: Fixed asset and depreciation forecasting.

Example: Workforce planning: Fully Loaded fulltime employee (FTE) cost
In Human resources planning scenarios, calculated columns allow modelling fully loaded FTE cost based on:
•	Base salary
•	Bonus 
•	Benefits
•	Tax
FTETotalCost = BaseSalary + Bonus + Benefits + Taxes

### Power BI integration and performance considerations

Using DirectQuery mode with Dataverse in order to enable write back and bring realtime access to planning data in Power BI and Excel comes with some performance limitations when calculations are handled entirely
via DAX. 

Use computed columns instead of DAX when:
 - The same KPI is repeatedly calculated (e.g., margin, bonus, adjusted cost)
 - You want to centralize business rules and avoid duplication
 - You want consistent logic across multiple reports


### Example

Instead of defining margin in DAX, create a computed column.
Revenue - COGS
Power BI only fetches a precomputed column — improving performance, reducing DAX load, and ensuring reusability.

#### Best practices
 - Computed columns for all common KPIs
 - Format results (e.g., % or currency) in Power BI visuals
 - Use dimension security and OAuth2 in Power BI for row-level filtering

#### Use Composite models to blend planning and analytics

A composite model combines:
 - DirectQuery connections to the Business performance planning cube (for planning and write-back)
 - Imported data (e.g., previous years actuals, external KPIs, warehouse data)

This hybrid architecture proved these benefits: 

|Benefit|	DirectQuery (Business performance planning)	|Import (External)|
|---|---|---| 
|Real-time planning and write-back|	X	| |
|High performance analytics|	Slower for large sets|	X|
|Complex DAX modeling|	Limited	|Fully supported|
|Combining data sources|	Limited	| using composite model|

Common scenarios for composite models:
 - Optimize performance for reporting requiring many years of actuals
 - Compare budget (Business performance planning) with actuals (Data warehouse)
 - Add benchmarks or ratios not available in Dataverse

>[!Note]
> The planning cube must remain in DirectQuery mode to support write-back. Imported tables can enhance reporting logic without breaking this behavior.





