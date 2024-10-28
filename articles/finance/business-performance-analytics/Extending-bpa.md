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
When integrating external facts and dimensions into the Business performance analytics data model with a strict star schema structure. It's essential to preserve the integrity of the model while enabling the new data to enhance the existing analytical capabilities. This article provides suggestions for integrating new data into the Business performance analytics model. It focuses on extending existing tables or creating new tables while maintaining relationships to the Business performance analytics model.

## Extend existing dimension tables
This approach involves adding new attributes to existing dimension tables. It is suitable when the external data provides additional descriptive information about entities already captured in the current model.

### Enternal data provide new description about an existing entity
The external data provides new descriptive information about an existing entity (for example, new customer demographics, additional product attributes).
1. Identify the dimension: Find the relevant dimension (for example, CustomerDim, ProductDim) where the external data fits.`
2. Add new attributes: Add new columns to the dimension table to hold the external data attributes. For example, adding CustomerIncomeLevel to the CustomerDim or ProductCategory to the ProductDim.
3. Ensure grain conformance: Verify that the new attributes maintain the existing grain of the dimension table. For example, if the grain is one row per customer, ensure that the new attributes apply to the customer as a whole and not at a lower level of granularity.
4. No changes to fact tables: Fact tables that reference this dimension automatically inherit the new attributes, no changes are needed to the fact table schema.

Some advantages are:
- Simplicity: Extending dimensions avoids the need for additional tables, making the model easier to maintain.
- Minimal Impact on Queries: Since the fact table relationships are not modified, existing queries remain intact, but users gain access to the additional context provided by the new attributes.

Some disadvantages are:
- Limited by grain: This approach only works when the external data aligns with the grain of the existing dimension. If the data is at a different level of detail, this strategy won't work.

### Add new dimensions
When the external data represents a new entity that doesn't fit into any existing dimension, you should introduce a new dimension table. This allows the external data to bring new descriptive information that enriches the analysis of fact tables.

### Enternal data creates new entity
If the external data introduces a new entity, for example, a marketing channel, geographic region, or new organizational hierarchy that's not currently represented in the Business performance analytics model, follow these steps:
1. Create a new dimension table: Build a new dimension table (for example, ChannelDim, GeoDim, or DepartmentDim) to hold the attributes related to the new entity.
2. Generate a surrogate key: Create a surrogate key (for example, ChannelKey, GeoKey, or DepartmentKey) as the primary key of the new dimension table.
3. Link to existing fact tables: Modify the relevant fact tables (for example, SalesFact, MarketingFact) to include a foreign key that references the new dimension. This allows the new dimension to be used in queries.
4. Ensure conformance: If the new dimension applies to multiple fact tables, ensure the foreign key is consistently used across all relevant fact tables, following conformance rules.

Advantages of creating a new entity:
- New context for analysis: New dimensions add fresh descriptive power to the model, enabling additional slicing of fact data.
- Conformed dimensions: If the new dimension is used across multiple fact tables, it enhances analytical capabilities by providing a consistent dimension for drill-across reporting.

Disadvantages of creating a new entity:
- Model complexity: Adding new dimensions increases the complexity of the data model, especially in terms of joins and query performance.
- ETL complexity: Modify the ETL process to populate the new dimension table and ensure it stays in sync with related fact data.


### Extend existing fact tables by adding measures
This method is used when the external data includes additional metrics that align with the grain of existing fact tables. The external facts are added as new columns (measures) to the existing fact table.

If the external data provides new facts or measures related to the same business process (for example, additional financial metrics such as discounts, taxes, or extended transaction details), follow these steps:
1. Identify the fact table: Identify the relevant fact table(s) (for example., SalesFact, GeneralLedgerFact) that align with the external facts.
2. Add new measure columns: Add new columns to the fact table for each of the external facts. For example, add DiscountAmount, TaxAmount, or PromotionAmount to the SalesFact.
3. Ensure granularity alignment: Confirm the new facts are at the same grain as the existing fact table. For example, if the fact table records individual transactions, the new measures must be at the transaction level.
4. Adjust ETL process: Modify the ETL process to populate the new measure columns in the fact table during data loads.

Advantages of adding measures:
- Efficient querying: By adding new measures to existing fact tables, you maintain a streamlined schema that enables efficient queries without additional joins.
- Minimal changes: The structure of the model remains largely unchanged, with only the addition of new metrics.

Disadvantages of adding mearsures:
- Fact table expansion: Adding too many measures can lead to very wide fact tables, which may impact performance.
- Limited by grain: This approach only works if the external facts align with the grain of the existing fact table. If the external data is at a different grain, you’ll need to consider other approaches.


## New fact tables
When the external data represents a new business process or transactions that aren't captured in the existing fact tables, you should create new fact tables to store this data. This approach ensures the model remains clean, with distinct fact tables for each business process.

If the external data introduces new facts related to a different business process (for example, marketing campaigns, inventory transactions, or supplier-related data), create a new fact table and follow these steps:
1. Design a new fact table: Create a new fact table (for example, MarketingFact, InventoryFact) that stores the new facts. This fact table should follow the same principles as the existing Business performance analytics fact tables, including a clear grain and surrogate keys for dimensional relationships.
2. Identify relevant foreign keys: Add foreign keys to the new fact table that link to the existing dimensions (for example, CustomerKey, ProductKey, TimeKey).
3. Add new foreign keys (if needed): If the external data introduces new dimensions (for example, a new CampaignDim for marketing campaigns), add a foreign key for the new dimension in the fact table.
4. Ensure conformance: If the new fact table shares dimensions with existing fact tables, ensure that the conformed dimensions (for example, TimeDim, CustomerDim) are used consistently to support drill-across queries.

Advantages of creating a new fact table:
- Clear separation of business processes: Creating new fact tables ensures that different business processes are isolated, maintaining clarity in the data model.
- Optimized performance: Queries against the fact tables are optimized since each table handles only one business process.
- Granularity control: You can ensure the new fact table has the appropriate grain for the new business process, without the limitations of existing fact tables.

Disadvantages of creating a new fact table:
- Model expansion: Introducing new fact tables increases the complexity of the model and adds more tables to manage.
- Additional ETL work: The ETL process needs to be modified to handle data loads for the new fact tables, increasing the maintenance effort. The choice of approach depends on the granularity of the external data, its relevance to existing business processes, and the need for new descriptive context. Maintaining conformance and clarity while avoiding unnecessary complexity is key to integrating external data effectively.
