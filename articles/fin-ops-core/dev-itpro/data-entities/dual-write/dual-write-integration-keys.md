---
title: Managing dual-write integration keys
description: This article describes managing integration keys for dual-write
author: jaredha
ms.date: 03/29/2024
ms.topic: how-to
ms.collection:
  - bap-ai-copilot
audience: Developer
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: jaredha
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Managing dual-write integration keys

[!include [banner](../../includes/banner.md)]

Integration keys for dual-write are the natural key for an entity that uniquely identifies a row of a Dataverse table. The key is used to find the correct record in the Dataverse table on which to perform the dual-write operation that originated in finance and operations apps. For example, for a dual-write map that associates a finance and operations entity to the Global Product table in Dataverse, the integration key must be defined for the Global Product table to ensure the map processes correctly. An update or delete of the product record in finance and operations apps is then able to find the unique related record in the Global Product table to perform the operation.

> [!NOTE]
> Integration keys must only be defined for Dataverse tables. They are not required for finance and operations entities.

The integration key is based on an alternate key of the Dataverse table. A purpose of the alternate keys on the table is to faciliate simplified programming and integration with external systems. These are essential in cases where an external system doesn't store the globally unique identifiers (GUIDs) that uniquely identify rows in Dataverse. See [Define alternate keys to reference rows](https://learn.microsoft.com/power-apps/maker/data-platform/define-alternate-keys-reference-records) for more information on alternate keys in Dataverse.

> [!IMPORTANT]
> The alternate key used for the integration key should only include columns for which application users are not allowed to change the value. The integration key defines the relationship between the record in finance and operations apps and Dataverse. If a value in a column that is part of the alternate key changes for a record, it is essentially changing the identity of the record and breaks the relationship between the record in finance and operations apps and Dataverse. It's important that keys be matched between the finance and operations apps and Dataverse.

## Generating dual-write integration keys

Dual-write integration keys are automatically generated based on the alternate keys defined for the Dataverse table. If you find that any integration keys are missing or incorrect (for example, if you receive an error message from [Dual-write error code](dual-write-error-codes.md) related to integration keys), you can refresh the keys with the following steps:

1. Open the [Power Apps maker portal](https://make.powerapps.com) and select your Dataverse environment.
2. Open the table that defined in the dual-write table map.
3. Ensure at least one [alternate key](https://learn.microsoft.com/power-apps/maker/data-platform/define-alternate-keys-reference-records) has been defined for the Dataverse table.
4. Open the **Dual-write administration workspace** in finance and operations apps.
5. Select the related table map.
6. Select the **Refresh tables** action on the action ribbon.

When the table is refreshed, integration keys are automatically generated for the table.

You can also manually modify an integration key. In the **Dual-write administration workspace** in finance and operations apps, select the **Integration key** tab on the **Environment details** page. This page lists the integration keys that have been generated. If you need to modify the integration key (for example, if the integration key was automatically generated from an alternate key other than the one desired), you can add, remove, or update the key properties for the table and save the changes.

## Configuring dual-write maps with integration key fields
For dual-write to correctly link unique record, the dual-write maps with tables using the integration keys must follow the below requirements:
- All fields of the integration key for a table must be included in the dual-write table maps for that table. Before initializing a map, ensure that all integration key fields are mapped to a field in the finance and operations entity so the correct records can be found during the dual-write synchronization.
- Lookup fields, the expanded key fields of a referenced entity, must also be mapped. If a lookup field is used as part of the altnernate key in Dataverse, the expaned field must also be mapped to a field in finance and operations apps in the dual-write map.
- If a dual-write table map is bidirectionally mapped (that is, if any of the field mappings are bidirectional between finance and operations apps and Dataverse), then all integration key fields must also be bidirectionally mapped.

These requirements ensure that dual-write live synchronization can find a given record in either finance and operations apps or the Dataverse environment.

