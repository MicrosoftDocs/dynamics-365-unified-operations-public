---
title: Business performance planning cubes
description: Learn about cubes in the Business performance planning application, including outlines on key terms, creating and using cubes, and loading fact data.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 12/08/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: Human Resources
---

# Business performance planning cubes

[!include [banner](../includes/banner.md)]

## Key terms

A cube is a collection of dimensions and fact data. It's made up of fact data that's used for modeling and analytical purposes. The dimensions in a cube are descriptors that define the facts. They're typically how you want to slice and view fact data. Common dimensions are people, product, place, and time. A dimension consists of one or more columns. For example, a time dimension might contain the date, month, year, and other aggregation details or attributes. These columns can be used to analyze the transactions. They can also be used to create a hierarchical structure that lets you drill down from Year to Month to Date.

The fact data in a cube is made up of numeric values that can be aggregated and analyzed. Facts are the fundamental reason for defining a cube. Examples of fact data include sales invoices, production costs, or salaries and wages.

For more information about cubes, see [Business performance planning overview](business-performance-planning-overview.md).

## Create and use cubes

To use a cube in Microsoft Power BI for planning purposes, follow these steps.

1. Assemble the cube.

    1. Give the cube a name.
    2. Select the dimensions for the cube.

2. Load fact data into the cube.

    1. Select the location of the fact data.
    2. Map the selected dimensions to columns that contain fact data.

3. Schedule a refresh (available in a later release).

### Create a cube

1. On the navigation pane, select **Cube** \> **New**.
2. In the **Create cube** wizard, name the cube. You can use numbers and special characters for the cube name. Make a note of the cube name, because you'll use it to load your data into Power BI.

    If you're using dataflows, the cube name is used to load fact data. It's shown as **msdyn\_xpna\_CUBENAME**.

### Select dimensions

When you create a cube, consider which dimensions you should include. You must select a minimum of two dimensions to create a cube. The dimensions that you select are then available in Power BI and can be used to filter your data.

You can select as many dimensions as you want to include in the cube. However, for the data to be filtered by the dimensions in Power BI, the fact data must have a relationship with the dimension. For more information, see [Business performance planning overview](business-performance-planning-overview.md).

> [!IMPORTANT]
> After the dimensions are defined, and the cube structure is finalized, you can't add or remove dimensions. If you want to use different dimensions, you must create a new cube and load the fact data into it. 

## Load fact data

To load fact data, go to the **Cube** list, and select **Load fact data**.

There are then two ways to load fact data in the Business performance planning application:

- Load data from an Excel workbook.
- Create a dataflow, and link it to an existing cube.

If you're loading production data, we recommend that you use dataflows. Dataflows provide better support for typical production volume and complexity. They also provide a transformation experience, detailed status results when data is loaded, and the option to schedule refreshes of the data. For more information about how to use dataflows, see [Load data into Business performance planning using dataflows](load-data-dataflows.md).

### Load fact data from Excel

To begin to load fact data from Excel, on the **Cube details** page, select **Load fact data**.

> [!NOTE]
> The amount of data that can be loaded from Excel at one time is limited. Excel is best used with demo data or sample data for testing purposes.

#### Select a data source

To load data from Excel, navigate to and select the workbook that contains the fact data.

#### Column mapping

After you select the data source, select the **Amount** column for your fact data. The values in the **Amount** column must be numeric. They can't contain non-numeric values. Fact data is typically general ledger (GL) account balances, product prices, sales amounts, or employee wages.

Below the **Amount** column is a list of the dimensions that were selected when the cube was created. Each dimension has a **Map type** value of either **Link to** or **Fixed value**.

- When **Link to** is selected, the dimension must be mapped to its corresponding data column in the fact data.
- When **Fixed value** is selected, a value must be entered in the **Table column** field. This value is used as the dimension value for all records in the cube.

For example, if **Department** is selected as a dimension, and the **Map type** field is set to **Link to**, the fact data must have a **Department** column. If the **Map type** field is set to **Fixed value**, and the value is set to **Human Resources**, the **Department** value is set to **Human Resources** for all rows in the cube. In this case, **Human Resources** will be the only available department when you filter and group in Power BI.

> [!NOTE]
> All the dimension values in a column of fact data must exist in the corresponding dimension. For example, the fact data for the Contoso company contains the **Human Resources**, **Finance**, **IT**, and **Marketing** departments. The dimension values in the **Department** dimension contain **Human Resources**, **Finance**, **IT**, and **Sales/Marketing**. Because the dimension value **Marketing** in the fact data and the dimension value **Sales/Marketing** don't match, you receive an error when you try to create the cube.

All dimensions that were selected when the cube was created must be mapped to a column in the fact data before the data is loaded into the cube.

After all the values are mapped, select **Next**. Make a note of the cube name, because you'll need it when you connect to Power BI to load the data for the visuals.

### Load data by using dataflows

For more information about how to load data by using dataflows, see [Load data into Business performance planning using dataflows](load-data-dataflows.md).
