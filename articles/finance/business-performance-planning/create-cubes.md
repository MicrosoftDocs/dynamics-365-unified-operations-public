---
# required metadata

title: Business performance planning cubes
description: This article describes cubes in the Business performance planning application.
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
ms.dyn365.ops.version: Human Resources

---
# Business performance planning cubes

[!include [banner](../includes/banner.md)]


## Key terms

A cube is a dimension made up of fact data that's used for modeling and analytical purposes. The dimensions in a cube are descriptors that define the facts and are typically how you want to slide and view fact data. Common dimensions are people, product, place, and time. A dimension consists of one or more columns. For example, a time dimension could contain the date, month, year, and other aggregation details or attributes. These columns can be used to analyze the transactions and create a hierarchical structure that allows you to drill down from Year to Month to Date.
The fact data in a cube is made up of numeric values that can be aggregated and analyzed. Facts are the fundamental reason for defining a cube. Examples of fact data might be sales invoices, production costs, or salaries and wages.


To learn more about cubes, see [Business performance planning overview](business-performance-planning-overview.md). 

## Create and use cubes

To use a cube in Power BI for planning purposes, complete the following steps.

1. Assemble the cube.
    1. Give the cube a name.
    2. Select the dimensions for the cube.
2. Load fact data into the cube.
    1. Select the location of the fact data.
    2. Map the selected dimensions to columns with fact data.
3. Schedule a refresh (available in a later release).

### Create the cube

In the navigation pane, select **Cube** > **New**. In the **Create cube** wizard, name the cube. You can use numbers and special characters for the cube name. Make a note of the cube name, as this will be used to load your data into Power BI. If you are using Dataflow, the cube name is used to load fact data and is displayed as msdyn\_xpna\_CUBENAME.

### Select dimensions

When you create a cube, consider which dimensions to include. You must select a minimum of tow dimensions to create the cude. The dimensions you select are then available in Power BI to filter your data. You can select as many dimensions as you want to include in the cube. However, for the data to be filtered by the dimensions in Power BI, the fact data must have a relationship with the dimension. For more information, see, [Business performance planning overview](business-performance-planning-overview.md).

> [!IMPORTANT]
> After the dimensions have been defined and the cube structure is finalized, you can't add or remove dimensions. If you want to use different dimensions, create a new cube and load the fact data into the new cube. 

## Load fact data

Load the fact data by navigating to the **Cube** list and selecting **Load fact data**.

There are two ways to load fact data in the planning application. You can upload data from a Microsoft Excel spreadsheet or you can create a dataflow and link it to an existing cube.

If you're loading production data, we recommend you use dataflows. Dataflows better support typical production volume and complexity. They also provide a transforming experience, detailed status results when data loads, and the option to schedule refreshes of the data. To learn more about using data flows, see [Load data into Business performance planning using dataflows](load-data-dataflows.md).

### Load fact data from Excel

To begin loading fact data from Excel, on the **Cube details** page, select **Load fact data**.

> [!NOTE]
> Excel is limited with the amount of data that can be loaded at one time. Excel is best used with demo data or sample data for testing purposes.

### Select a data source

To load data from Excel, navigate to and select the spreadsheet that contains the fact data. 

### Column mapping

After you select the data source, select the **Amount** column for your fact data. The values in the **Amount** field must be numeric and can't contain non-numeric values. Fact data is typically GL account balances, product prices, sales amounts, or employee wages.

Listed below the **Amount** column are the dimensions that were selected when the cube was created. Each dimension has a **Map type** of **Link to** or **Fixed value**. When **Link to** is selected, the dimension must map to it’s corresponding data column in the fact data. When **Fixed value** is selected, the **Table column** field must be populated with a value. The value entered is used as the dimension value for all records in the cube. For example, if **Department** is selected as a dimension, and the **Map type** is **Link to**, the fact data must have a **Department** column. If the **Map type** is set to **Fixed value**, and the value is set to **Human Resources**, all rows in the cube will have the **Department** value set to **Human Resources**. When you filter and group in Power BI, only Human Resources will be available as a Department for filtering and grouping.

> [!TIP]
> All the  dimension values in a column of fact data must exist in the corresponding dimension. For example, the fact data for the Contoso company contains the departments of Human Resources, Finance, IT, and Marketing. The dimension values in the **Department** dimension contain **Human Resources**, **Finance**, **IT**, and **Sales/Marketing**. The dimension value **Marketing** in the fact data and the dimension value **Sales/Marketing** don't match. An error would occur when you attempt to create the cube.

All dimensions that were selected when the cube was created must be mapped to a column in the fact data before the data is loaded in the cube.

After all the values are mapped, select **Next**. Make a note of the cube name because you will need it when you connect to PowerBI to load the data for the visuals.

## Loading data using dataflows

To learn more about how to load data using dataflows, see [Loading data via data flows](load-data-dataflows.md).
