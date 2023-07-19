---
# required metadata

title: Country/region codes and configuration keys
description: This article provides scenarios that are applicable from an implementation perspective for both configuration keys and country/region.
author: peakerbl
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 4644
ms.assetid: 86eda511-b1a6-46d2-bd0f-f9991b727f1a
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Country/region codes and configuration keys

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

This article provides scenarios that are applicable from an implementation perspective for both configuration keys and country/region.

### Customer table schema

| Field name     | Field label     | Country/region context |
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

| Field name     | Country/region context |
|----------------|-----------------|
| CustomerNumber |                 |
| CustomerName   |                 |
| EAN            | DK              |
| FiscalCode     | IT              |

### Scenario – Field level only

Isaac, a developer, builds a customer entity that has fields that contain regional settings. The entity is consumed through OData.

**For read operations:** The consumer of the entity uses this information to complete an effective regional mapping. The consumer ignores the fields that aren't required for that region. For example, consumers in Denmark (DK) are concerned with reading the values of the **EAN** field and core fields only.

**For write operations:** The consumer of the entity uses this information to identify only the fields that are required to populate data. The consumer expects validation to occur for regional fields and associated core fields.

### Behaviors – Fields only

| Scenario                        | Description |
|---------------------------------|-------------|
| Design                          | Entities automatically inherit localization properties from underlying fields. |
| Design                          | Developers can’t override or set localization properties on entity fields. These properties should be inherited only from tables. Only override on unmapped fields. |
| Read behavior (OData metadata)  | The consumer of an entity from OData will have metadata or annotations to specify which fields are localized. |
| Read behavior (Data management) | In import/export fields, metadata displays country/region values, so that this information is obvious to the end user. |
| Read behavior                   | During cross-company read operations, data from localized fields is displayed only if the context matches. Note that this should already be implemented through the table/view. |
| Read behavior (Performance)     | During company-specific read operations, localized fields are dropped from the query when the context doesn't match. |
| Write                           | During write operations to localized fields, hard errors occur if the fields don't match the context. |
| (Shared table)                  | If the data source or fields contain a country/region that is a shared (global) table, all operations are ignored, just as if no keys are applied. |

### Behavior – Data source

The behavior of configuration keys and a country/region that are applied at the data source resembles the behavior of fields. These values are inferred from the data source, just as if they are applied to the field level. Here's an example.

```Text
Entity E1

    |_ Data Source 1 (DS1)

        Field1

        Field2

    |_Data Source 2 (DS2) UK

        Field3

            Field4
```

#### Evaluation at the entity E1 level

```Text
Entity E1

|_F1

|_F2

|_F3 (UK inferred)

|_F4 (UK inferred)
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
