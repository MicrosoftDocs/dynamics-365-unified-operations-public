---
title: Manage dual-write integration keys
description: This article describes how to manage integration keys for dual-write.
author: jaredha
ms.date: 03/29/2024
ms.topic: how-to
ms.custom: 
  - bap-template
audience: Developer
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: jaredha
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Manage dual-write integration keys

[!include [banner](../../includes/banner.md)]

Integration keys for dual-write are the natural key for an entity that uniquely identifies a row of a Dataverse table. When a dual-write operation originates in finance and operations apps, the key is used to find the correct record to perform that operation on in the Dataverse table. For example, for a dual-write map that associates a finance and operations entity with the Global Product table in Dataverse, the integration key must be defined for the Global Product table to ensure that the map is processed correctly. An update or deletion of the product record in finance and operations apps can then find the unique related record to perform the operation on in the Global Product table.

> [!NOTE]
> Integration keys must be defined only for Dataverse tables. They aren't required for finance and operations entities.

The integration key is based on an alternate key of the Dataverse table. The alternate keys on the table facilitate simplified programming and integration with external systems. These keys are essential in cases where an external system doesn't store the globally unique identifiers (GUIDs) that uniquely identify rows in Dataverse. For more information about alternate keys in Dataverse, see [Define alternate keys to reference rows](/power-apps/maker/data-platform/define-alternate-keys-reference-records).

> [!IMPORTANT]
> The alternate key on the Dataverse table that's used for the integration key should include only columns that application users aren't allowed to change the value of. The integration key defines the relationship between the record in finance and operations apps and Dataverse. If the value of a column that's part of the alternate key is changed for a record, that change essentially changes the identity of the record and breaks the relationship between the record in finance and operations apps and Dataverse. It's important that keys are matched between the finance and operations apps and Dataverse.

## Generating dual-write integration keys

### Automated key generation

Dual-write integration keys are automatically generated based on the alternate keys that are defined for the Dataverse table. You can refresh the integration keys if you find that any are missing or incorrect. (For example, you might learn that keys are missing or incorrect because you receive an [error code](dual-write-error-codes.md) that's related to integration keys.)

To refresh integration keys, follow these steps.

1. Verify that an alternate key was created for the Dataverse table.

    1. Open the [Power Apps maker portal](https://make.powerapps.com), and select your Dataverse environment.
    2. Open the Dataverse table that's selected in the dual-write table map.
    3. Ensure that at least one [alternate key](/power-apps/maker/data-platform/define-alternate-keys-reference-records) is defined for the Dataverse table.

1. In finance and operations apps, open the **Dual-write administration** workspace.
1. Select the related table map.
1. On the Action Pane, select **Refresh tables**.

When the table is refreshed, the integration keys are automatically generated for it.

### Manual key updates

You can manually modify an integration key. The **Integration key** page lists the integration keys that were automatically generated. In the list, there's a key for each Dataverse table that's included in a dual-write map in the environment. You might have to modify an integration key if, for example, it was automatically generated from an alternate key other than the one that you want.

To modify an integration key, follow these steps.

1. In finance and operations apps, open the **Dual-write administration** workspace.
1. On the Action Pane, select **Environment details**.
1. On the **Integration key** tab, add, remove, or update the key properties for the integration key of the selected Dataverse table.
1. On the Action Pane, select **Save**.

## Configuring dual-write maps with integration key fields

For dual-write to correctly link unique records, the dual-write maps for tables that use the integration keys must meet the following requirements:

- All fields of the integration key for a table must be included in the dual-write table maps for that table. Before you initialize a map, make sure that all integration key fields are mapped to a field in the finance and operations entity. In this way, you ensure that the correct records can be found during dual-write synchronization.
- Lookup fields, the expanded key fields of a referenced entity, must also be mapped. If a lookup field is used as part of the alternate key in Dataverse, the expanded field must also be mapped to a field in finance and operations apps in the dual-write map.
- If a dual-write table map is bidirectionally mapped (that is, if any of the field mappings are bidirectional between finance and operations apps and Dataverse), all integration key fields must also be bidirectionally mapped.

These requirements ensure that dual-write live synchronization can find a given record in either finance and operations apps or the Dataverse environment.
