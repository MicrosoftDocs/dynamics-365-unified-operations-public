---
title: Custom drivers in Dynamics 365 Finance business performance planning
description: Learn how to define and use custom drivers in business performance planning.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 06/11/2025
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Custom drivers in Dynamics 365 Finance business performance planning

This article explains how to extend a planning cube by adding drivers such as **Price**, **Quantity**, or **Discount** to the default **Amount** driver. In this way, you can support more granular or driver-based planning logic.

Planners can use business performance planning to do driver-based modeling directly within planning cubes. In addition to the default **Amount** driver, you can define drivers such as **Quantity**, **Price**, or **Discount**, or other user-defined inputs, during the cube creation stage. These drivers support flexible allocation. They also support downstream calculations that use the calculated column and Data Analysis Expressions (DAX) measures.

## Prerequisites

- You must have access to business performance planning in Microsoft Dynamics 365 Finance.
- You must have appropriate security roles to create cubes and upload data.

## Add drivers

To add drivers, follow these steps.

1. In business performance planning, go to **Cubes**.
1. Select **New cube**.
1. Select relevant dimensions. For example, select **Product**, **Region**, or **Channel**.
1. In the driver section, add drivers.
1. Enter driver names separated by commas. For example, enter **Profit**, **Loss**, or **Margin**.

    If you leave the field blank, the **Amount** driver is added by default.

1. Select **Add driver** to add other drivers:

    - Quantity
    - Price
    - Discount
    - Headcount

Each driver appears as a separate editable column in the cube and is available for formulas.

> [!TIP]
> Each driver must be defined before you upload data into the cube. After data is loaded, the driver structure is locked.

## Write-back from Power BI and Excel

All drivers that are created in a cube, including the default **Amount** driver and custom drivers such as **Price**, **Quantity**, or **Discount**, can be edited directly in supported write-back experiences:

- The Power BI **Table edit**, **Matrix planning**, **Graphical planning**, and **Variance** visuals
- Excel, by using the BPP Excel Add-in

Planners can then complete the following tasks:

- Enter values directly into the driver fields.
- Interactively update planning scenarios.
- Trigger allocation when values are entered at an aggregated level.
- Trigger real-time recalculations through computed columns.

Unlike computed columns, driver fields are fully editable and user-controlled through these write-back experiences.

## Limitations

- You can't add or remove drivers after data is uploaded into the cube.
- After the cube is created, you can't reference any defined driver in the same cube in a computed column.

## Example

If you want to calculate revenue as *Price* &times; *Quantity*, follow these steps.

1. Add the **Price** and **Quantity** drivers.
1. Create the following computed column: **Revenue = Price \* Quantity**.

Learn more in [Create calculated columns](calculated-columns.md).
