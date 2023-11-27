---
# required metadata

title: Business performance planning overview
description: This article explains business performance planning in Microsoft Dynamics 365 Finance.
author: ShielaSogge
ms.date: 11/28/2023
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
# Business performance planning overview

> [!IMPORTANT]
> The functionality described in this article is available as part of a preview release. The functionality and the content of this article are subject to change.

As businesses grow and evolve, planning becomes a critical part of operationalizing strategic goals. However, planning is often complex and time consuming due to disconnected systems, large volumes of data, and manual processes. These issues result in inaccuracies, delays, and a high total cost of ownership. In a time when businesses are looking to take full advantage of key opportunities, they are lacking visibility into data relationships and any outliers.

To support an efficient and accurate planning process, a solution must provide streamlined aggregation of data, a familiar and collaborative set of tools, and the ability to transform a plan into action.

Business performance planning offers financial and operational planning and analytics that create a connected enterprise experience. Planning utilizes the familiar productivity tools of Power BI and Microsoft Excel which you can use to help plan and create what-if scenarios. With the power of Dataverse, you can use data flows and Power Platform to eliminate manual processes and achieve optimal efficiency for your organization.

The planning feature set consists of two main concepts:

  - Modeling data that's needed for planning
  - Acting on data provided

In the planning application, you can create dimensions and cubes, load fact data into the cubes, and define dimension and cube access. The dimension data can also be modified to create new master data by using the canvas application, Power BI, and Excel.

You can act on the dimensions and cubes within Power BI by leveraging planning specific visuals. Use the visuals to easily copy actuals into a preliminary plan, create multiple versions of plans, write back capability from Power BI to Dataverse to ensure you're looking at the latest data, and provide a collaborative experience by entering comments directly into the plan. Because planning is a native Dataverse solution, Power Automate and other Power Platform capabilities can be leveraged for notifications, workflows, custom fields, and much more.

An Excel add-in provides additional ways to update dimension data and enter in planning related information.\*

\*Available in a later release:

## Key concepts and terms

### Key terms

- **Cube** - A collection of dimension and fact data that's used for modeling and analytical purposes.
- **Dimensions** – Descriptors that define the facts and are typically how you would want to slide and view your fact data. Common dimensions are people, product, place, and time. A dimension consists of one or more columns. For example, a time dimension could contain the date, month, year and other aggregation details or attributes. These columns can then be used in the analysis of the transactions to create a hierarchical structure allows a drill down path from Year to Month to Date.
- **Facts** – Numeric values that can be aggregated and analyzed, which is the fundamental reason to define a cube. Examples of fact data includes sales invoices, production costs, or salaries and wages.

## Cube example

When you create a cube, consider the dimensions to create and include when you assemble the cube. The dimensions provide the mechanism for how you will eventually filter your data in Power BI. When you create your cube, select all the dimensions you want to include in the cube. However, keep in mind that to filter the data by the dimensions in Power BI, the fact data must have a relationship with the dimension.

For example, Contoso Company has the following sales data:

| Sales amount | Product      | Order date | Customer          | Sales territory |
|--------------|--------------|------------|-------------------|-----------------|
| 1000         | Bike         | 3/1/2022   | Oregon trails     | West            |
| 1000         | Bike         | 3/1/2022   | Southern rides    | West            |
| 1000         | Bike         | 3/1/2022   | Longhorn Sales    | West            |
| 10           | Water bottle | 5/1/2022   | Southern rides    | South           |
| 10           | Water bottle | 5/1/2022   | Route 66 Bikes    | South           |
| 1000         | Bike         | 5/2/2022   | Oregon trails     | West            |
| 10           | Water bottle | 6/1/2022   | Dessert Oasis     | South           |
| 10           | Water bottle | 6/1/2022   | Dessert Oasis     | South           |
| 1000         | Bike         | 6/15/2022  | Blue Ox Trails    | North           |
| 50           | Helmet       | 6/15/2022  | Blue Ox Trails    | North           |
| 1000         | Bike         | 7/1/2022   | Dakota bikes      | North           |
| 1000         | Bike         | 7/1/2022   | Oregon trails     | West            |
| 1000         | Bike         | 7/1/2022   | Joe's bikes       | West            |
| 50           | Helmet       | 9/1/2022   | Southern rides    | South           |
| 50           | Helmet       | 9/15/2022  | Palm Street Sales | South           |
| 1000         | Bike         | 9/15/2022  | Southwest Campers | South           |

A sales director at Contoso may want to answer the following basic questions:

- Who is my best customer?
- Which sales territory has the most sales?

The sales director may also want to do a deeper analysis to understand the trends and relationships between the data. For example, they may want to know:

- What are the top selling products within each territory?
- Do any of the products have a seasonal sales pattern?

By creating a cube that contains the dimensions of Product, Time, Customer, Territory, and actual sales, the sales director can filter and group data based on how they want to view it. For example, they may want to group sales by territory so that the top selling products within each territory are identified. This provides insight into when the peak season of sales is. The following table lists out the data the cube would show.

| Territory | Sales amount | Product      | Order date | Customer          |
|-----------|--------------|--------------|------------|-------------------|
| South     |              |              |            |                   |
|           | 10           | Water bottle | 05/01/2022 | Southern rides    |
|           | 10           | Water bottle | 5/01/2022  | Route 66 bikes    |
|           | 10           | Water bottle | 6/01/2022  | Desert Oasis      |
|           | 10           | Water bottle | 6/01/2022  | Desert Oasis      |
|           | 50           | Helmet       | 9/01/22    | Southern rides    |
|           | 50           | Helmet       | 9/15/2022  | Palm Street Sales |
|           | 1000         | Bike         | 9/15/2022  | Southwest Campers |
|           |              |              |            |                   |
| North     |              |              |            |                   |
|           | 50           | Helmet       | 6/15/2022  | Blue Ox Trails    |
|           | 1000         | Bike         | 6/15/2022  | Blue Ox Trails    |
|           | 1000         | Bike         | 7/1/2022   | Dakota Bikes      |
| West      |              |              |            |                   |
|           | 1000         | Bike         | 3/1/2022   | Oregon Trails     |
|           | 1000         | Bike         | 3/1/2022   | Joe’s Bikes       |
|           | 1000         | Bike         | 3/1/2022   | Longhorn Sales    |
|           | 1000         | Bike         | 5/2/2022   | Oregon Trails     |
|           | 1000         | Bike         | 7/1/2022   | Oregon trails     |
|           | 1000         | Bike         | 7/1/2022   | Joe’s bikes       |

The Sales director can utilize the dimensions created during planning to slice their data by territory, product, and date in Power BI. This enables the sales director to understand trends and prepare a plan that takes into account any trends or outliers.

To identify patterns and filter data, a dimension must map to the sales data in table 1the first table in this article. Therefore, the following dimensions defined for the cube: 

- Territory
- Product
- Time
- Customer

The sales data (fact data) must contain the details for Territory, Product, Time, and Customer.

As part of the planning process, the sales director will use the sales fact data to build out a plan of what they think will happen in the upcoming year. During this time, the sales data can be copied into a new scenario called **Sales plan**. This gives the organization a starting point to create a sales plan for the upcoming year. For example, by reviewing their actuals, they can plan for a spike in sales in the summer and a decline in sales in the winter. With the ability to filter and group the data by dimension, they can build a plan based on the insights that the data is giving them.

## The process of configuring and using planning involves the following tasks
The process of configuring and using planning involves the following tasks:

- Create dimensions
- Create cubes
- Load fact data into cubes
- Connect Power BI to data
- Install planning visuals
- Configure visuals
- Secure by dimension or cube (available in a later release)
- Share plans


