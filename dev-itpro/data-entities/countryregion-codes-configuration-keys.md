---
# required metadata

title: Country/region codes and configuration keys | Microsoft Docs
description: This article provides scenarios that are applicable from an implementation perspective for both configuration keys and country/region. 
author: RobinARH
manager: AnnBe
ms.date: 2015-09-14 07:32:07
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 4644
ms.assetid: 535adb2a-f1d0-4be7-b7ea-d297e9afc75c
ms.region: Global
# ms.industry: 
ms.author: kuntalme

---

# Country/region codes and configuration keys

This article provides scenarios that are applicable from an implementation perspective for both configuration keys and country/region. 

### Customer table schema

| Field name     | Field label     | Country context |
|----------------|-----------------|-----------------|
| CustNum        | Customer number |                 |
| CustName       | Customer name   |                 |
| EinvoiceEANNum | EAN             | DK              |
| FiscalCode     | Fiscal code     | IT              |

### Sample data

| CustNum | CustName        | EinvoiceEANNum{DK} | FiscalCode{IT} | DataAreaId |
|---------|-----------------|--------------------|----------------|------------|
| 1       | Contoso Denmark | AA                 | {Empty}        | DK         |
| 2       | Contoso Italy   | {Empty}            | DD             | IT         |

### Sample entity

| Field name     | Country context |
|----------------|-----------------|
| CustomerNumber |                 |
| CustomerName   |                 |
| EAN            | DK              |
| FiscalCode     | IT              |

### Scenario – Field level only

Isaac, a developer, builds a customer entity that has fields that contain regional settings. The entity is consumed through OData. **For read operations:** The consumer of the entity uses this information to complete an effective regional mapping. The consumer ignores the fields that aren't required for that region. For example, consumers in Denmark (DK) are concerned with reading the values of the **EAN** field and core fields only. **For write operations:** The consumer of the entity uses this information to identify only the fields that are required to populate data. The consumer expects validation to occur for regional fields and associated core fields.

### Behaviors – Fields only

| Scenario                        | Description                                                                                                                                                                     |
|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Design                          | Entities automatically inherit localization properties from underlying fields.                                                                                                  |
| Design                          | Developers can’t override or set localization properties on entity fields. These properties should be inherited only from tables. Only override on unmapped fields.             |
| Read behavior (OData metadata)  | The consumer of an entity from OData will have metadata or annotations to specify which fields are localized.                                                                   |
| Read behavior (Data management) | In import/export fields, metadata displays country/region values, so that this information is obvious to the end user.                                                          |
| Read behavior                   | During cross-company read operations, data from localized fields is displayed only if the context matches. Note that this should already be implemented through the table/view. |
| Read behavior (Performance)     | During company-specific read operations, localized fields are dropped from the query when the context doesn't match.                                                            |
| Write                           | During write operations to localized fields, hard errors occur if the fields don't match the context.                                                                           |
| (Shared table)                  | If the data source or fields contain a country/region that is a shared (global) table, all operations are ignored, just as if no keys are applied.                              |

### Behavior – Data source

The behavior of configuration keys and a country/region that are applied at the data source resembles the behavior of fields. These values are inferred from the data source, just as if they are applied to the field level. Here's an example.

    Entity E1

         |_ Data Source 1 (DS1)

              Field1

              Field2

         |_Data Source 2 (DS2) UK

              Field3

              Field4

#### Evaluation at the entity E1 level

    Entity E1

    |_F1

    |_F2

    |_F3 (UK inferred)

    |_F4 (UK inferred)

