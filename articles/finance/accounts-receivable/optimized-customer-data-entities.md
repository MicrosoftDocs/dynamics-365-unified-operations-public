---
title: Optimized Customer Entities 
description: Optimized customer data entities in Dynamics 365 Finance replace bulky Customers V3 integrations. Learn how to import, export, and sync focused customer data.
ms.date: 10/07/2026
ms.topic: concept-article
ai-usage: ai-assisted
author: twheeloc
ms.author: twheeloc
---

# Optimized customer data entities overview

The optimized customer data entities are focused alternatives to the Customers V3 entity for importing, exporting, and integrating customer data in Finance and operations for Dynamics 365. Each entity targets a specific category of customer information, such as core customer attributes, addresses, electronic contact information, or invoice and payment settings.

This separation reduces the amount of unrelated data that must be processed when an integration updates only one category of customer information. The entities support Data management for import and export scenarios and OData integration scenarios.

> [!IMPORTANT]
> The optimized customer entities were available as a private preview starting in Dynamics 365 Finance version 10.0.44. The feature isn't backported to earlier versions. The same is available for Public preview 10.0.50 onwards.

## Prerequisites

- Your environment runs Dynamics 365 Finance version 10.0.44 or later.
- The **Enable this feature to migrate data from timestate table to current table (preview)** and **Enable optimized entities to support data management of customer (preview)** features available in Feature management.
- You can review Feature management and Data maintenance job status.

**Enable optimized entities to support data management of customer (preview)** depends on **Enable this feature to migrate data from timestate table to current table (preview)**. Enable the directory-related feature first.

> [!NOTE]
> The new entity schemas exist independently of Feature management because features or flights can't control schema changes. However, except for OData read operations, using the optimized entities returns an error until you enable **Enable optimized entities to support data management of customer (preview)**.

### Entity summary

The following table summarizes the entities, integration patterns, and behaviors.

| **Type** | **Name / behavior** |
| --- | --- |
| **Data management entities** | Customers foundation; Customers foundation extended; Customer electronic addresses; Customer postal addresses V2; Customer associations |
| **OData public collections** | CustomersFoundation; CustomersFoundationExtended; CustomerElectronicAddresses; CustomerPostalAddressesV2; CustomerAssociations |
| **Supported integration patterns** | Data management import and export; OData |
| **Application Object Tree (AOT) name** | CustFoundationEntity; CustFoundationExtendedEntity; CustElectronicAddressEntity; CustPostalAddressV2Entity; CustToCustAssociationEntity |
| **Extensibility** | The entities are designed to be extensible. |
| **Performance pattern** | Multiple threads supported – Recommendation is to set Import threshold record count to 2500 and set Import task count to 8. For more information, see [Parallel imports](/fin-ops-core/dev-itpro/data-entities/data-import-export-job.md#parallel-imports). |

### When to use these entities

Use the customer data entities when you want to create, update, import, export, or integrate a focused set of customer information without processing the broader Customers V3 entity.

- Use *Customers foundation* when the integration needs core customer data.
- Use *Customers foundation extended* when the integration also requires financial dimensions, localization data, or warehouse-related customer data.
- Use *Customer electronic addresses* for customer email, phone, fax, URL, and other electronic contact information.
- Use *Customer postal addresses V2* for postal addresses that are associated with customers.
- Use *Customer associations* to update invoice account and payment-term information.

> [!NOTE]
> Use only the entities that are required for the business scenario. Complete customer integration can require more than one entity.

### Feature enablement

When you enable **Enable this feature to migrate data from timestate table to current table (preview)**, you automatically start the first migration job that populates the current-record tables.

1. In Feature management, enable **Enable this feature to migrate data from timestate table to current table (preview)**.
1. Enable **Enable optimized entities to support data management of customer (preview)**.
1. Open the Data maintenance job named **Migrate active record from date effective tables to current tables**.
1. Verify that both tasks in the job have a status of **Complete**.
1. Use the optimized customer entities only after both tasks are complete.

If an optimized customer entity returns a feature-dependency or initialization error, check the following items:

1. Confirm that the environment runs version 10.0.44 or later.
1. In Feature management, confirm that **Enable this feature to migrate data from timestate table to current table (preview)** is enabled.
1. Confirm that **Enable optimized entities to support data management of customer (preview)** is enabled. This feature depends on the directory-related feature.
1. Open the Data maintenance job **Migrate active record from date effective tables to current tables**.
1. Confirm that both tasks under the Data maintenance job have a status of **Complete**. If either task isn't complete, don't use the optimized entities until migration finishes.

An OData read can be available because the entity schema exists outside feature control. Other operations return an error until you enable **Enable optimized entities to support data management of customer (preview)** and migration is complete.

### Customer creation and update pattern

For OData scenarios, use Customers foundation or Customers foundation extended for the base customer record. Then use the applicable supporting entities for electronic addresses, postal addresses, and invoice or payment information.

| **Sequence** | **Entity** | **Purpose** |
| ---- | ---- | ---- |
| 1 | Customers foundation or Customers foundation extended | Create or maintain the base customer record. |
| 2 | Customer electronic addresses | Create or maintain electronic contact details, when required. |
| 3 | Customer postal addresses V2 | Create or maintain postal addresses, when required. |
| 4 | Customer associations | Apply invoice account and payment-term values, when required. |

> [!IMPORTANT]
> The source design identifies the preceding endpoint groups, but it doesn't provide a field-level dependency matrix. Validate required fields, keys, and sequencing for each integration before publication or deployment.

#### Security

The design adds or updates entity access through existing customer maintenance and inquiry duties. It also introduces maintain and view access for the customer electronic address entity. Security administrators should grant access through the applicable duties and privileges rather than assigning entry points directly.

| **Area** | **Design references** |
| ---- | ---- |
| Foundation and extended entities | Customer maintenance and customer inquiry privileges are extended for the new foundation of entities. |
| Customer associations | Customer maintenance and customer inquiry privileges are extended for the invoice and payment terms of entity. |
| Postal addresses | Postal address maintain and view privileges are extended for Customer postal addresses V2. |
| Electronic addresses (new) | New maintain and view privileges are introduced and linked to customer and data-management duties. |

#### Issues and considerations

- The optimized entities are available in Dynamics 365 Finance version 10.0.50 as a public preview.
- These entities cover Data management import and export and OData integration scenarios.
- The source design lists no entities supporting row-level change tracking. Validate the final released support before using these entities in scenarios that depend on row-version change tracking.
- Existing customizations and integrations that are built on Customers V3 must be assessed and remapped to the applicable focused entities.
- Validation errors are returned through the entity framework in the same general manner as Customers V3.

#### Example

An integration creates a customer and maintains its invoice account, postal address, and primary electronic contact information. Instead of sending all values through Customers V3, the integration can use the following focused sequence:

1. Create the customer through Customers foundation or Customers foundation extended.
1. Create the customer postal address through Customer postal addresses V2.
1. Create the email address or phone number through Customer electronic addresses.
1. After the referenced invoice-account customer exists, update invoice account and payment terms through Customer associations.

Only supply the fields that each entity and scenario require. Validate entity keys and mandatory fields in the target environment.

#### Substitute existing Customers V3 with new entities

Before replacing an existing Customers V3 integration, inventory the fields that the integration reads or writes. Map each field to the focused entity that owns the corresponding customer data category, and identify records that require multiple entity calls.

| **Migration activity** | **Expected outcome** |
| ---- | ---- |
| Prerequisite validation | The environment runs version 10.0.44 or later, both Feature management features are enabled in dependency order, and both tasks in **Migrate active record from date effective tables to current tables** show **Complete**. |
| Inventory | A list of Customers V3 fields, operations, integration endpoints, and data-management projects currently in use. |
| Field mapping | Each used field is mapped to a focused entity, with unresolved fields documented for internal review. |
| Dependency review | Customer, address, contact, invoice-account, and payment-term dependencies are sequenced explicitly. |
| Functional validation | Import, export, POST, PATCH, GET, and DELETE behavior is tested where applicable. Tests confirm that non-read operations are blocked when **Enable optimized entities to support data management of customer (preview)** isn't enabled. |
| Current-record validation | Current names and addresses resolve correctly after initial migration, and future-dated or expired records are synchronized by background process automation. By default, it runs in 6 hours, which can be modified. |
| Performance validation | The replacement flow is tested with representative data volume and parallelism in the customer environment. No performance percentage is assumed. |
| Fallback plan | The existing Customers V3 integration remains available until the replacement meets acceptance criteria. |
