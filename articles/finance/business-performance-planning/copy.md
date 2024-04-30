---
title: Copy visual
description: Learn how to use the Copy visual in the Business performance planning application, including benefits, prerequisites, and an example.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 12/03/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Copy visual

This article describes how to use the **Copy** visual in the Business performance planning application. To fully use this application, you must also install Microsoft Power BI visuals. For information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

The **Copy** visual lets you effortlessly transfer baseline data, including actuals or forecasts, to new planning or forecasting scenarios. The ability to select the level of detail during the copy process allows for precise scenario creation. For example, you can easily copy data from the previous year's actuals and use it as the foundation for a new plan. You can make a complete copy of the data, or you can apply dimensional filters to copy data only for a specific department or product, for example.

## Benefits

- **Time-saving functionality** – The **Copy** visual helps expedite the creation of forecasts and budgets. Because users no longer have to manually build each forecast from scratch, the planning process is faster and more efficient.
- **Consistency and accuracy** – The **Copy** visual ensures consistency between historical data and planned budgets by facilitating the transfer of specific data coordinates. Therefore, it helps ensure an accurate and coherent planning structure.
- **Scenario analysis simplification** – Users can create diverse forecast scenarios by using a base case. Users can build a foundational forecast and then efficiently generate multiple variations by copying it. Therefore, scenario analysis is simplified and doesn't require that users start from scratch for each permutation.

## Prerequisites and installation

For more information about prerequisites and installation, see [Install Power BI visuals](powerBI-visual-install.md).

> [!NOTE]
> The **Format visual** tab is available only when a visual is selected on the report canvas.

## Use the Copy visual

This custom visual enables data to be copied between scenarios and models at any level of detail. For example, you can copy data from the previous quarter's sales actuals and use it as the basis for a new plan (for the upcoming quarter's sales forecast), based on the most recent quarter's "baseline." You can create a complete copy of the plan or apply further dimension details, such as a specific cost center or product.

Therefore, instead of creating forecasts from scratch, users can use document assumptions about business evolution between quarters.

### Example

To define the copy criteria, follow these steps.

1. In the dropdown list at the top of the **Copy** visual, select a cube.
2. Select **Select**.
3. In the upper-right corner of the visual, select the plus sign (**+**) to configure fields for the copy criteria. Focus on two dimensions. This example uses Fiscal quarter and Scenario.
4. Set the following values:

    - **Dimension:** Scenario
    - **Column:** Name
    - **From:** Actual
    - **To:** Forecast

5. Configure the fiscal quarter by setting the following values:

    - **Dimension:** MonthYear
    - **Column:** Fiscal quarter
    - **From:** FY2020 Q4
    - **To:** FY2021 Q4

6. After you've completed the configuration, select **Copy** to start the copy process.
