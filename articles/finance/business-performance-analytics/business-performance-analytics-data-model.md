---
title: Business performance analytics data model
description: Learn about the Business performance analytics data model, including tables assigning facts, grains, and other info to various business processes.
author: jinniew
ms.author: jiwo
ms.topic: article
ms.date: 05/20/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.form: business-performance-analytics
---

# Business performance analytics data model 

## Dimensional data model

A dimensional data model is a framework designed to optimize the performance of complex queries in a data warehouse. It organizes data into fact tables and dimension tables to facilitate easy and intuitive data analysis.

#### Key Components

1. **Fact Table**:
   - **Definition** - The central table in a dimensional model, containing quantitative data for analysis.
   - **Characteristics**:
     - Contains metrics or measures, such as sales revenue, quantity sold, etc.
     - Stores foreign keys that reference dimension tables.
     - Typically has a large number of records.
   - **Example Columns**:
     - `Sales_Amount`
     - `Quantity_Sold`
     - `Date_Key` (Foreign Key)
     - `Product_Key` (Foreign Key)
     - `Customer_Key` (Foreign Key)

2. **Dimension Tables**:
   - **Definition** - Tables that store descriptive attributes related to the facts.
   - **Characteristics**:
     - Contain textual or categorical data, such as product names, dates, and customer information.
     - Provide context for the facts in the fact table.
     - Usually have fewer records compared to fact tables but more columns.
   - **Example Columns for a Product Dimension**:
     - `Product_Key` (Primary Key)
     - `Product_Name`
     - `Category`
     - `Brand`
     - `Price`

#### Why did we use a dimensional model?

- Improved query performance - Designed for fast data retrieval and efficient querying.
- Ease of use - Intuitive structure makes it easy for users to understand and navigate the data.
- Scalability - Can handle large volumes of data and complex queries.

#### How did we model for Business performance analytics?

  1. We modeled by business process (e.g., an invoice entered, or a payment are business processes).
  2. We modeled at the lowest grain (e.g., every line on an invoice is represented in the facts).
  3. We grouped each business process into a value chain for reference (Record to Report, Procure to Pay, etc.).
  4. We created a Bus Matrix to represent the facts and dimensions for your reference. For more information, see the Bus Matrix report in Business Performance Analytics.

