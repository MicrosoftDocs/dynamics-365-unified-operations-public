---
title: Extend Business performance analytics
description: Learn how to extend Business performance analytics.
author: lizmota
ms.author: jiwo
ms.topic: conceptual
ms.date: 10/30/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Bringing external facts and dimensions into a Business performance analytics data model
When integrating external facts and dimensions into the Business performance analytics data model with a strict star schema structure, it's essential to preserve the integrity of the model while enabling the new data to enhance the existing analytical capabilities. Below are several suggestions for integrating new data into the Business performance analytics model, focusing on extending existing tables or creating new tables while maintaining relationships to the Business performance analytics model.

## Extend existing dimension tables
This approach involves adding new attributes to existing dimension tables. It is suitable when the external data provides additional descriptive information about entities already captured in the current model.

### Scenario:
The external data provides new descriptive information about an existing entity (e.g., new customer demographics, additional product attributes).
Steps
- Step 1: Identify the dimension: Find the relevant dimension (e.g., CustomerDim, ProductDim) where the external data fits.`
- Step 2: Add new attributes: Add new columns to the dimension table to hold the external data attributes. For example, adding CustomerIncomeLevel to the CustomerDim or ProductCategory to the ProductDim.
- Step 3: Ensure grain conformance: Verify that the new attributes maintain the existing grain of the dimension table (e.g., if the grain is one row per customer, ensure that the new attributes apply to the customer as a whole and not at a lower level of granularity).
- Step 4: No changes to fact tables: Fact tables that reference this dimension will automatically inherit the new attributes, so no changes are needed to the fact table schema.

### Pros
- Simplicity: Extending dimensions avoids the need for additional tables, making the model easier to maintain.
- Minimal Impact on Queries: Since the fact table relationships are not modified, existing queries remain intact, but users gain access to the additional context provided by the new attributes.

### Cons
- Limited by grain: This approach only works when the external data aligns with the grain of the existing dimension. If the data is at a different level of detail, this strategy won't work.

## Add new dimensions
When the external data represents a new entity that does not fit into any existing dimension, you should introduce a new dimension table. This allows the external data to bring new descriptive information that enriches the analysis of fact tables.

### Scenario
The external data introduces a new entity (e.g., a marketing channel, geographic region, or new organizational hierarchy) not currently represented in the BPA model.
Steps
- Step 1: Create a New Dimension Table: Build a new dimension table (e.g., ChannelDim, GeoDim, or DepartmentDim) to hold the attributes related to the new entity.
- Step 2: Generate a Surrogate Key: Create a surrogate key (e.g., ChannelKey, GeoKey, or DepartmentKey) as the primary key of the new dimension table.
- Step 3: Link to Existing Fact Tables: Modify the relevant fact tables (e.g., SalesFact, MarketingFact) to include a foreign key that references the new dimension. This will allow the new dimension to be used in queries.
- Step 4: Ensure Conformance: If the new dimension applies to multiple fact tables, ensure the foreign key is consistently used across all relevant fact tables, following conformance rules.

### Pros
- New Context for Analysis: New dimensions add fresh descriptive power to the model, enabling additional slicing and dicing of fact data.
- Conformed Dimensions: If the new dimension is used across multiple fact tables, it enhances analytical capabilities by providing a consistent dimension for drill-across reporting.

### Cons
- Model Complexity: Adding new dimensions increases the complexity of the data model, especially in terms of joins and query performance.
- ETL Complexity: You will need to modify the ETL process to populate the new dimension table and ensure it stays in sync with related fact data.


## Extend existing fact tables by adding measures
This method is used when the external data includes additional metrics that align with the grain of existing fact tables. The external facts are added as new columns (measures) to the existing fact table.

### Scenario:
The external data provides new facts or measures related to the same business process (e.g., additional financial metrics such as discounts, taxes, or extended transaction details).
Steps:
- Step 1: Identify the Fact Table: Identify the relevant fact table(s) (e.g., SalesFact, GeneralLedgerFact) that align with the external facts.
- Step 2: Add New Measure Columns: Add new columns to the fact table for each of the external facts. For example, add DiscountAmount, TaxAmount, or PromotionAmount to the SalesFact.
- Step 3: Ensure Granularity Alignment: Ensure that the new facts are at the same grain as the existing fact table. For example, if the fact table records individual transactions, the new measures must also be at the transaction level.
- Step 4: Adjust ETL Process: Modify the ETL process to populate the new measure columns in the fact table during data loads.

### Pros
- Efficient querying: By adding new measures to existing fact tables, you maintain a streamlined schema that enables efficient queries without additional joins.
- Minimal changes: The structure of the model remains largely unchanged, with only the addition of new metrics.

### Cons
- Fact table expansion: Adding too many measures can lead to very wide fact tables, which may impact performance.
- Limited by grain: This approach only works if the external facts align with the grain of the existing fact table. If the external data is at a different grain, you’ll need to consider other approaches.


## New fact tables
When the external data represents a new business process or transactions that are not captured in the existing fact tables, you should create new fact tables to store this data. This approach ensures the model remains clean, with distinct fact tables for each business process.

### Scenario
The external data introduces new facts related to a different business process (e.g., marketing campaigns, inventory transactions, or supplier-related data).
To create a new fact table, follow these steps:
1. Design a new fact table: Create a new fact table (e.g., MarketingFact, InventoryFact) that stores the new facts. This fact table should follow the same principles as the existing BPA fact tables, including a clear grain and surrogate keys for dimensional relationships.
2. Identify relevant foreign keys: Add foreign keys to the new fact table that link to the existing dimensions (e.g., CustomerKey, ProductKey, TimeKey).
3. Add new foreign keys (if needed): If the external data introduces new dimensions (e.g., a new CampaignDim for marketing campaigns), add a foreign key for the new dimension in the fact table.
4. Ensure conformance: If the new fact table shares dimensions with existing fact tables, ensure that the conformed dimensions (e.g., TimeDim, CustomerDim) are used consistently to support drill-across queries.

### Pros
- Clear separation of business processes: Creating new fact tables ensures that different business processes are isolated, maintaining clarity in the data model.
- Optimized performance: Queries against the fact tables are optimized since each table handles only one business process.
- Granularity control: You can ensure the new fact table has the appropriate grain for the new business process, without the limitations of existing fact tables.

### Cons
- Model expansion: Introducing new fact tables increases the complexity of the model and adds more tables to manage.
- Additional ETL work: The ETL process needs to be modified to handle data loads for the new fact tables, increasing the maintenance effort. The choice of approach depends on the granularity of the external data, its relevance to existing business processes, and the need for new descriptive context. Maintaining conformance and clarity while avoiding unnecessary complexity is key to integrating external data effectively.
