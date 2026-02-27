---
title: Extend Business performance analytics in Microsoft Fabric
description: Learn how to extend Business performance analytics by bringing external facts and dimensions into a Business performance analytics data model.
author: yvishwa
ms.author: jyvishwa
ms.topic: how-to
ms.date: 10/30/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Extend Business performance analytics in Microsoft Fabric

You can integrate external facts and dimensions into the Business performance analytics data model to enhance the existing analytical capabilities. However, if there's a strict star schema structure, you need to preserve the integrity of the model while you enable the new data.

This article suggests approaches that you can use to integrate new data into the Business performance analytics model. It focuses on extending existing tables or creating new tables while also maintaining relationships to the Business performance analytics model.

The approach that you use depends on the granularity of the external data, its relevance to existing business processes, and the need for new descriptive context. The key to effective integration of external data is maintaining conformance and clarity while avoiding unnecessary complexity.

## Extend existing dimension tables

This approach involves adding new attributes to existing dimension tables. It's suitable when the external data provides additional descriptive information about entities that the current model already captures.

### External data provides a new description about an existing entity

If the external data provides new descriptive information about an existing entity (for example, new customer demographics or additional product attributes), follow these steps:

1. **Identify the dimension.** Find the relevant dimension where the external data fits (for example, `CustomerDim` or `ProductDim`).
1. **Add new attributes.** Add new columns to the dimension table to hold the external data attributes. For example, add the `CustomerIncomeLevel` column to the `CustomerDim` table or the `ProductCategory` column to the `ProductDim` table.
1. **Ensure grain conformance.** Confirm that the new attributes maintain the existing grain of the dimension table. For example, if the grain is one row per customer, ensure that the new attributes apply to the customer as a whole, not at a lower level of granularity.
1. **No changes to fact tables are required.** Fact tables that reference the dimension automatically inherit the new attributes. Therefore, no changes to the fact table schema are required.

This approach has the following advantages:

- **Simplicity** – By extending dimensions, you avoid the need for extra tables. Therefore, the model is easier to maintain. 
- **Minimal impact on queries** – Because the fact table relationships aren't modified, existing queries remain intact. However, users gain access to the additional context that the new attributes provide.

This approach also has some disadvantages:

- **Granularity limitation** – This approach works only when the external data aligns with the grain of the existing dimension. It doesn't work if the data is at a different level of detail.

## Add new dimensions

When the external data represents a new entity that doesn't fit into any existing dimension, introduce a new dimension table. The external data can then bring new descriptive information that enriches the analysis of fact tables.

### External data creates a new entity

If the external data introduces a new entity that isn't currently represented in the Business performance analytics model (for example, a marketing channel, geographic region, or organizational hierarchy), follow these steps:

1. **Create a new dimension table.** Build a new dimension table (for example, `ChannelDim`, `GeoDim`, or `DepartmentDim`) to hold the attributes that are related to the new entity.
1. **Generate a surrogate key.** Create a surrogate key (for example, `ChannelKey`, `GeoKey`, or `DepartmentKey`) as the primary key of the new dimension table.
1. **Link to existing fact tables.** Modify the relevant fact tables (for example, `SalesFact` or `MarketingFact`) so that they include a foreign key that references the new dimension. In this way, the new dimension can be used in queries.
1. **Ensure conformance.** If the new dimension applies to multiple fact tables, ensure that the foreign key is consistently used across all relevant fact tables and follows conformance rules.

This approach has the following advantages:

- **New context for analysis** – New dimensions add fresh descriptive power to the model. Therefore, they enable additional slicing of fact data.
- **Conformed dimensions** – If the new dimension is used across multiple fact tables, it enhances analytical capabilities by providing a consistent dimension for drill-across reporting.

This approach also has some disadvantages:

- **Model complexity** – The addition of new dimensions increases the complexity of the data model, especially in terms of joins and query performance.
- **ETL complexity** – You need to modify the extraction, transformation, and loading (ETL) process to populate the new dimension table and ensure that it stays in sync with related fact data.

## Extend existing fact tables by adding measures

Use this approach when the external data includes extra metrics that match the grain of existing fact tables. Add the external facts as new columns (measures) to the existing fact table.

If the external data provides new facts or measures that relate to the same business process (for example, extra financial metrics such as discounts, taxes, or extended transaction details), follow these steps:

1. **Identify the fact table.** Find the relevant fact tables (for example, `SalesFact` or `GeneralLedgerFact`) that match the external facts.
1. **Add new measure columns.** For each external fact, add new columns to the fact tables. For example, add the `DiscountAmount`, `TaxAmount`, or `PromotionAmount` column to the `SalesFact` table.
1. **Ensure granularity alignment.** Make sure the new facts have the same grain as the existing fact table. For example, if the fact table records individual transactions, the new measures must be at the transaction level.
1. **Adjust the ETL process.** Modify the ETL process to populate the new measure columns in the fact table during data loads.

This approach has the following advantages:

- **Efficient querying** – By adding new measures to existing fact tables, you keep a streamlined schema that enables efficient queries without extra joins.
- **Minimal changes** – The structure of the model remains largely unchanged. The only change is the addition of new metrics.

This approach also has some disadvantages:

- **Fact table expansion** – Adding too many measures can make fact tables very wide and might affect performance.
- **Granularity limitation** – This approach works only when the external facts match the grain of the existing fact table. If the external data has a different grain, you must consider other approaches.

## Add new fact tables

Create new fact tables when the external data represents a new business process or transactions that the existing fact tables don't capture. This approach keeps the model clean and ensures distinct fact tables for each business process.

If the external data introduces new facts that relate to a different business process (for example, marketing campaigns, inventory transactions, or supplier-related data), follow these steps:

1. **Design a new fact table.** Create a new fact table (for example, `MarketingFact` or `InventoryFact`) that stores the new facts. This fact table should follow the same principles as the existing Business performance analytics fact tables, including a clear grain and surrogate keys for dimensional relationships.
1. **Identify relevant foreign keys.** In the new fact table, add foreign keys that link to the existing dimensions (for example, `CustomerKey`, `ProductKey`, or `TimeKey`).
1. **Add new foreign keys if needed.** If the external data introduces new dimensions (for example, a new `CampaignDim` dimension for marketing campaigns), add a foreign key for the new dimension in the fact table.
1. **Ensure conformance.** If the new fact table shares dimensions with existing fact tables, ensure that the conformed dimensions (for example, `TimeDim` or `CustomerDim`) are used consistently to support drill-across queries.

This approach has the following advantages:

- **Clear separation of business processes** – Different business processes stay isolated, so the data model remains clear.
- **Optimized performance** – Each fact table handles only one business process, so queries stay optimized.
- **Granularity control** – You can set the appropriate grain for the new business process without being limited by existing fact tables.

This approach also has some disadvantages:

- **Model expansion** – The model becomes more complex with more tables to manage.
- **Additional ETL work** – You need to modify the ETL process to handle data loads for the new fact tables, which increases maintenance effort.
