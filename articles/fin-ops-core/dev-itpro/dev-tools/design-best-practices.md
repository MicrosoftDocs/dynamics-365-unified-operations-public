---
title: Design principles and best practices for data entities
description: This article describes design principles for data entities.
author: peakerbl
ms.date: 06/20/2017
ms.topic: article
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b41f6fc4-7883-4987-8160-374576b11d16
---

# Design principles and best practices for data entities

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article describes design principles for data entities. It also includes guidelines for the names of data entities, fields, relation roles, roles, and OData EntityTypes and EntitySets.

## Entity design principles

A data entity should provide a holistic object that encapsulates the relevant business logic in a single consumable contract. The contract is then exposed through application interfaces (APIs), such as OData, import and export, integration, and the programming model. Each data entity should be designed to meet the following goals.

### Encapsulation

-   Each entity should provide an abstraction between the physical data model and the consumer of the entity. The entity should encapsulate the underlying tables that, together, can define an object that has a specific purpose in the business. Consumers of the entity might be form clients, services, and integration.
-   Each entity should encapsulate multiple related tables to represent the domain object. In some situations, single table entities are acceptable.

### A single public contract

-   The public contract for an entity should be the same across all integration end points. For example, the customer entity must expose the same fields or API to both OData and import/export. This principle guarantees that the published schema for an entity is consistent, regardless of the mechanism for consumer interaction.
-   When an entity is consumed, the business logic that is executed within the entity during CRUD operations must not vary based on the type of consumer.

### Simplicity

-   The consumer of an entity should be able to interact with the entity based on the accepted industry or domain definitions of the entity. The behavior details of the entity should be kept hidden and should be prevented from distorting the interaction.
-   The consumer of an entity must be able to interact with the entity by using the natural key of the entity. The consumer must not be required to use any keys that are implementation-specific, such as any surrogate key that it generates.

## Naming guidelines
### Data entity names

| Do                                                                                                                                                                                                                                                                                                | Don’t                                        |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|
| Prefix the name with standard prefixes, because of the lack of namespaces.                                                                                                                                                                                                                        | Don't include underscores in names.          |
| Add the postfix "Entity" to the name to prevent conflicts with tables and classes that have the same prefix.                                                                                                                                                                                      | Don't use abbreviations in conceptual names. |
| Give the entity a conceptual name that is aligned with the name in the en-us UI. For example, the conceptual name of the entity that exposes records from the InventTable table should be named **ReleasedProduct**, so that the full name of the entity will be **EcoResReleasedProductEntity**. |                                              |

**Result:** &lt;prefix&gt;&lt;ConceptualName&gt;Entity

### Data entity field names

| Do                                                                                                                                                                                                                                                                                                         | Don’t                                                                                                                                |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| Give the field name a conceptual name that is aligned with the name in the en-us UI. For example, use **ItemNumber** instead of **ItemID** as the field name to align with the UI, where the label is **Item number**.                                                                                     | Don't include prefixes in field names. For example, a field should not be named **InventLocationId**.                                |
| Add the postfix "ID," "Number," and so on, to the name of a field that is part of foreign keys to prevent collision with the navigation properties. For example, use **WarehouseID** instead of **Warehouse** as a field name, because **Warehouse** is the navigation method to the **Warehouse** entity. | Don't include country/region-specific postfixes in field names. For example, a field should not be named **InventoryProfileID\_RU**. |
|                                                                                                                                                                                                                                                                                                            | Don't include underscores in field names.                                                                                            |
|                                                                                                                                                                                                                                                                                                            | Don't use abbreviations in field names.                                                                                              |

### Data entity relation role names

| Do                                                                                                                                                                                                                                        | Don’t                                                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Use the plural form when you name roles that have a cardinality that is higher than 1. For example, the foreign key on Customer to Party should have the role name of Customers, because the cardinality from Party to Customer is 0...N. | Don't include prefixes in relation role names. For example, don’t use the name **WMSWarehouseLocation**, even though the referenced entity includes the prefix "WMS."                                                                 |
| Use the singular form when you name roles that have a cardinality of 0 (zero) or 1. For example, the foreign key on Worker to Person should have the role name of Worker, because the cardinality from Person to Worker is 0..1.          | Don't add the postfix "Entity" to relation role names. For example, don’t use the role name **WarehouseEntity** in a relationship, even though the referenced entity includes the name "Entity." Instead, use the name **Warehouse**. |
| Consider adding the role of the relationship as a prefix. For example, to clearly describe the role of the relationship, name a relationship **BuyingLegalEntity** instead of **LegalEntity**.                                            | Don't add country/region-specific postfixes to relation role names. For example, don’t use the role name **InventoryProfile\_RU**, even though the relationship applies only in an RU country/region format.                          |
|                                                                                                                                                                                                                                           | Don't include underscores in relation role names.                                                                                                                                                                                     |

### Data entity relation names

**Do**

-   Give the relation name the same name as the related role name, in singular form. For example, the relation that describes the foreign key from Customer to Party should be named **Party**.

### OData EntityType names

**Do**

-   Give the EntityType a conceptual name. The name should be the same as the conceptual name of the data entity, but without the prefix and without the "Entity" postfix. For example, **EcoResReleasedProductEntity** becomes **ReleasedProduct**.
-   Name the EntityType in singular form.

### OData EntitySet (Entity Collection) names

**Do**

-   Name the EntitySet in plural form. For example, the EntitySet for the **ReleasedProduct** EntityType is **ReleasedProducts**.

### Number of columns in a data entity
Note that Microsoft Excel based import/export supports a maximum of 255 columns. If it is expected for an entity to be able to export/import more than 255 columns, then a non-Excel format must be planned or the entity should have less than or equal to 255 columns.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
