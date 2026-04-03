---
title: Manage dual-write integration keys
description: This article describes how to manage integration keys for dual-write.
author: jaredha
ms.date: 04/03/2026
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

Dual-write integration keys are the natural key for an entity that uniquely identifies a row of a Dataverse table. When a dual-write operation starts in finance and operations apps, the key helps find the correct record to perform that operation on in the Dataverse table. For example, for a dual-write map that associates a finance and operations entity with the Global Product table in Dataverse, you must define the integration key for the Global Product table to ensure that the map is processed correctly. An update or deletion of the product record in finance and operations apps can then find the unique related record to perform the operation on in the Global Product table.

> [!NOTE]
> Define integration keys only for Dataverse tables. Finance and operations entities don't require integration keys.

The integration key is based on an alternate key of the Dataverse table. The alternate keys on the table facilitate simplified programming and integration with external systems. These keys are essential in cases where an external system doesn't store the globally unique identifiers (GUIDs) that uniquely identify rows in Dataverse. For more information about alternate keys in Dataverse, see [Define alternate keys to reference rows](/power-apps/maker/data-platform/define-alternate-keys-reference-records).

> [!IMPORTANT]
> The alternate key on the Dataverse table that's used for the integration key should include only columns that application users can't change. The integration key defines the relationship between the record in finance and operations apps and Dataverse. If you change the value of a column that's part of the alternate key for a record, you essentially change the identity of the record and break the relationship between the record in finance and operations apps and Dataverse. It's important that keys match between the finance and operations apps and Dataverse.

## Generating dual-write integration keys

### Automated key generation

Dual-write integration keys are automatically generated based on the alternate keys that you define for the Dataverse table. You can refresh the integration keys if you find that any are missing or incorrect. For example, you might learn that keys are missing or incorrect because you receive an [error code](dual-write-error-codes.md) that's related to integration keys.

To refresh integration keys, follow these steps:

1. Verify that an alternate key exists for the Dataverse table.

    1. Open the [Power Apps maker portal](https://make.powerapps.com), and select your Dataverse environment.
    1. Open the Dataverse table that's selected in the dual-write table map.
    1. Ensure that at least one [alternate key](/power-apps/maker/data-platform/define-alternate-keys-reference-records) is defined for the Dataverse table.

1. In finance and operations apps, open the **Dual-write administration** workspace.
1. Select the related table map.
1. On the Action Pane, select **Refresh tables**.

When you refresh the table, the integration keys are automatically generated for it.

### Manual key updates

You can manually modify an integration key. The **Integration key** page lists the integration keys that were automatically generated. In the list, there's a key for each Dataverse table that's included in a dual-write map in the environment. You might need to modify an integration key if, for example, it was automatically generated from an alternate key other than the one that you want.

To modify an integration key, follow these steps:

1. In finance and operations apps, open the **Dual-write administration** workspace.
1. On the Action Pane, select **Environment details**.
1. On the **Integration key** tab, add, remove, or update the key properties for the integration key of the selected Dataverse table.
1. On the Action Pane, select **Save**.

## Configuring dual-write maps with integration key fields

For dual-write to correctly link unique records, dual-write maps for tables that use integration keys must meet the following requirements:

- Include all fields of the integration key for a table in the dual-write table maps for that table. Before you initialize a map, make sure that you map all integration key fields to a field in the finance and operations entity. This step ensures that dual-write synchronization can find the correct records.
- Map lookup fields, which are the expanded key fields of a referenced entity. If you use a lookup field as part of the alternate key in Dataverse, you must also map the expanded field to a field in finance and operations apps in the dual-write map.
- If you bidirectionally map a dual-write table map (that is, if any of the field mappings are bidirectional between finance and operations apps and Dataverse), you must also bidirectionally map all integration key fields.

These requirements ensure that dual-write live synchronization can find a given record in either finance and operations apps or the Dataverse environment.
