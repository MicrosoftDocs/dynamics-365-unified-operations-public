---
# required metadata

title: Business performance planning cubes
description: This article describes cubes in Business performance planning application.
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

**Cubes**

Key terms:
----------

**Cube** \- A cube consists of dimension and fact data and is used for modeling and analytical purposes.

**Dimensions** – descriptors that define the facts and are typically how you would want to slide and view your fact data. Common dimensions are people, product, place, and time. A dimension consists of one or more columns. For example, a time dimension could contain the date, month, year and other aggregation details or attributes. These columns can then be used in the analysis of the transactions to create a hierarchical structure allows a drill down path from Year to Month to Date.

**Facts** – Numeric values that can be aggregated and analyzed. It is the fundamental reason for defining a cube. Examples of fact data might be sales invoices, production costs, or salaries and wages.

Cube example:
-------------

To learn more about cubes, please review the **About business performance planning topic (link needed).** This will cover a detailed example of the components of a cube, and how cubes are used in the planning process.

Overview of creating and using cubes
------------------------------------

To use a cube within Power BI for planning purposes, the following steps must be taken:

1.  Assemble the cube
    1.  Give the cube a name
    2.  Select the dimensions for the cube
2.  Load fact data into the cube
    1.  Select the location of the fact data
    2.  Map the selected dimensions to columns with fact data
3.  Schedule refresh (available in a later release)

### Create the cube

Navigate to the cube menu option in the left navigation pane and select ‘New’. This will launch the create cube wizard.

Cube name: You can use numbers and special characters for the cube name. Note the cube name, as this will be used for loading your data into Power BI, or if using Dataflow, to load fact data and will be displayed as msdyn\_xpna\_CUBENAME

### Select dimensions

When creating a cube, you should consider which dimensions you would like included. The dimensions selected will be available in Power BI to filter your data on. You can select as many dimensions as you would like to be included in the cube. However, for the data to be filtered by the dimensions in Power BI, the fact data must have a relationship with the dimension. Please see the cube example in **About business performance planning topic (link needed)** for more information.

You must select a minimum of two dimensions to create the cube.

**Important!** Once the cube structure has been finalized ( i.e. the dimensions have been defined)  dimensions can't be added or removed. In the event you would like to use different dimensions, a new cube will need to be created and the fact data loaded into the cube again. 

Load fact data
--------------

Once the cube has been created, you will need to load in the fact data. You will need to navigate to the Cube list and select **load fact data**.

There are two ways to load fact data in planning. Data can be loaded in the planning app by uploading data from an excel spreadsheet. Data can also be loaded by creating a dataflow and linking it to an already created cube.

If loading production data it is recommended to use dataflows, this will better support typical production volume and complexity. Dataflows also provide a transform experience, detailed status results when loading data, and the option to schedule refreshes of the data. Learn more about using data flows here: **Link to dataflows topic needed.**

### Loading fact data from Excel

To begin loading fact data via Excel, select **Load fact data** in the cube details page.

Note: Excel is limited with the amount of data that can be loaded at one time. This is best used when using demo data or sample data for testing purposes.

### Select data source

The first step in loading data from Excel is to navigate to the spreadsheet that contains the fact data. Once the spreadsheet is selected, select the **worksheet** that contains the fact data.

### Column mapping

Once the data source has been selected, you will need to select your amount column for your fact data. The amount field must be numeric and cannot contain non-numeric values. Fact data is typically GL account balances, product prices, sales amount or employee wages for example.

Listed below the amount column are the dimensions that were selected when the cube was created. Each dimension has a **Map type** of **Link to** or **Fixed value**. When choosing Link to, the dimension must map to it’s corresponding data column in the fact data. When choosing Fixed value, the **Table column** field needs to be populated with a value. The value that is entered will be used as the dimension value for all records in the cube. For example, if Department is selected as a dimension, and the **Map type** is **Link to**, then the fact data must have a department column. If the Map type is set to Fixed value, and the value is set to Human Resources, then all rows in the cube will have the department value set to Human Resources and when filtering and group in Power BI, only Human Resources will be available as a department for filtering and grouping.

Tip: All the of the dimension values in a column of fact data must exist in the corresponding dimension. Using in the department example again, the fact data for Contoso company contains the departments of HR, Finance, IT, and Marketing. The dimension values in the department dimension contain HR, Finance, IT and Sales/Marketing. The dimension values of **Marketing** in the fact data and the dimension value **Sales/Marketing** do not match, and an error will be generated when attempting to create the cube.

All dimensions that were selected when the cube was created must be mapped to a column in the fact data before the data will be loaded in the cube.

Once all values are mapped, select **Next**. Note the cube name, as this will be needed when connecting to PowerBI to load the data for the visuals.

Loading data via dataflows
--------------------------

See the topic **Loading data via data flows.**
