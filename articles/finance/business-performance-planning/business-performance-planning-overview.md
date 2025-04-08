---
title: Business performance planning overview
description: Learn about business performance planning in Microsoft Dynamics 365 Finance, including overviews on key concepts, terms, and an example.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 11/20/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: Human Resources
---

# Business performance planning overview

As businesses grow and evolve, planning becomes a critical part of putting strategic goals into operation. However, planning is often complex and time consuming because of disconnected systems, large volumes of data, and manual processes. These issues lead to inaccuracies, delays, and a high total cost of ownership (TCO). At a time when businesses are looking to take full advantage of key opportunities, they lack visibility into data relationships and any outliers.

To support an efficient and accurate planning process, a solution must provide streamlined aggregation of data, a familiar and collaborative set of tools, and the ability to transform a plan into action.

Business performance planning offers financial and operational planning and analytics that create a connected enterprise experience. It uses the familiar productivity tools of Microsoft Power BI and Excel. By using these tools, you can help plan and create what-if scenarios. Through the power of Dataverse, you can use data flows and Microsoft Power Platform to eliminate manual processes and achieve optimal efficiency for your organization.

The business performance planning feature set consists of two main concepts:

- Modeling data that's required for planning
- Acting on the data that's provided

In the business performance planning app, you can create dimensions and cubes, load fact data into the cubes, and define dimension and cube access. In addition, by using the canvas application, Power BI, and Excel, you can modify the dimension data to create new master data.

You can act on the dimensions and cubes in Power BI by applying planning-specific visuals. Use the visuals to easily copy actuals into a preliminary plan, create multiple versions of plans, use write-back capability from Power BI to Dataverse to ensure that you're looking at the latest data, and provide a collaborative experience by entering comments directly in the plan. Because business performance planning is a native Dataverse solution, Power Automate and other Microsoft Power Platform capabilities can be used for notifications, workflows, custom fields, and much more.

An Excel add-in (available in a later release) provides more ways to update dimension data and enter planning-related information.

## Key concepts and terms

- **Cube** – A collection of dimension and fact data that's used for modeling and analytical purposes.
- **Dimensions** – Descriptors that define the facts. They're typically what you want to use to slice and view your fact data. Common dimensions are people, product, place, and time. A dimension consists of one or more columns. For example, a time dimension might contain the date, month, year, and other aggregation details or attributes. These columns can then be used in the analysis of transactions to create a hierarchical structure that provides a drill-down path from the year to the month to the date.
- **Facts** – Numeric values that can be aggregated and analyzed. (Aggregation and analysis are the fundamental reasons for defining a cube.) Examples of fact data include sales invoices, production costs, or salaries and wages.

## Cube example

Consider the dimensions that you want to create and include when you assemble a cube. The dimensions provide the mechanism for filtering your data in Power BI. When you create the cube, select all the dimensions that you want to include in it. However, keep in mind that you can filter data by those dimensions in Power BI only if the fact data has a relationship with them.

For example, Contoso Company has the following sales data.

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

A sales director at Contoso might want answers to the following basic questions:

- Who is my best customer?
- Which sales territory has the most sales?

The sales director might also want to do a deeper analysis to understand the trends and relationships between the data. For example, they might want answers to the following questions:

- What are the top-selling products in each territory?
- Do any of the products have a seasonal sales pattern?

By creating a cube that contains Product, Time, Customer, Territory, and actual sales as dimensions, the sales director can filter and group data based on how they want to view it. For example, they might want to group sales by territory so that they can identify the top-selling products in each territory. This grouping can give them insight into when the peak season for sales is. The following table lists the data that the cube shows in this example.

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
| North     |              |              |            |                   |
|           | 50           | Helmet       | 6/15/2022  | Blue Ox Trails    |
|           | 1000         | Bike         | 6/15/2022  | Blue Ox Trails    |
|           | 1000         | Bike         | 7/1/2022   | Dakota Bikes      |
| West      |              |              |            |                   |
|           | 1000         | Bike         | 3/1/2022   | Oregon Trails     |
|           | 1000         | Bike         | 3/1/2022   | Joe's Bikes       |
|           | 1000         | Bike         | 3/1/2022   | Longhorn Sales    |
|           | 1000         | Bike         | 5/2/2022   | Oregon Trails     |
|           | 1000         | Bike         | 7/1/2022   | Oregon trails     |
|           | 1000         | Bike         | 7/1/2022   | Joe's bikes       |

The sales director can use the dimensions that were created during planning to slice their data by territory, product, and date in Power BI. In this way, the sales director can understand trends and prepare a plan that takes into account any trends or outliers.

To identify patterns and filter data, a dimension must map to the sales data in the first table in this article. Therefore, the following dimensions are defined for the cube:

- Territory
- Product
- Time
- Customer

The sales data (fact data) must contain the details for Territory, Product, Time, and Customer.

As part of the planning process, the sales director uses the sales fact data to create a plan for what they think will happen in the upcoming year. During this time, the sales data can be copied into a new scenario that's named **Sales plan**. The organization then has a starting point for creating a sales plan for the upcoming year. For example, by reviewing their actuals, they can plan for a spike in sales during the summer and a decline in sales during the winter. By taking advantage of the ability to filter and group the data by dimension, they can build a plan based on the insights that they gain from the data.

## Configuring and using business performance planning

The process of configuring and using business performance planning involves the following tasks:

1. Create dimensions
1. Create cubes
1. Load fact data into cubes
1. Connect Power BI to data
1. Install planning visuals
1. Configure visuals
1. Secure by dimension or cube (available in a later release)
1. Share plans
