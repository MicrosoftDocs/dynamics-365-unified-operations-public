---
title: Cost transaction entities
description: Cost transaction entities allow the value of a cost to be split among the contents of a cost area (voyage, shipping container, and so on) though the selection of an apportionment method. 
author: yufeihuang
ms.date: 12/16/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-12-16
ms.dyn365.ops.version: 10.0.25
---

# Cost transaction entities

[!include [banner](../includes/banner.md)]

## Apportionment

Landed cost allows for the value of a cost to be split among the contents of a cost area (voyage, shipping container, and so on) through the selection of an apportionment method. The apportionment method is set as a part of the configuration of automatic costs based on business rules. This is pulled through as a part of the cost on the creation of a voyage line.

### Configure apportionment mapping for use with data entities

Where a cost is created from an external source such as a freight forwarder, the forwarder will not be able to provide the preferred method for apportioning the cost value. The apportionment mapping defines the default apportionment method for each cost type code. The apportionment mapping table is accessed from Supply Chain Management, within the Landed cost module (**Landed Cost \> Costing setup \> Apportionment mapping**).

If a mapping combination has been defined and a cost matching the cost type code is created through use of a cost transaction entity, the mapped apportionment method will be used in place of any value submitted to the entity.

When no value is present in the mapping table, but a value has been provided to the entity, then the provided value will be used.

In the case where no value exists in either the mapping table nor the record submitted to the entity, the creation will fail.

### Apportionment mapping (ITMApportionmentMapping)

The apportionment mapping entity (`ITMApportionmentMapping`) creates apportionment mapping relationships and enables users can create or update records.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Apportionment method | ITMApportionmentMapping.ApportionmentMethod | int | No | No |
| Cost type code | ITMApportionmentMapping.ShipCostTypeId | nvarchar(20) | **Yes** | No |

## Voyage costs (ITMCostTransVoyageEntity)

The voyage cost entity (`ITMCostTransVoyageEntity`) creates voyage cost transactions that are applied at the voyage level. During the import process, the system uses the **Category** and **Apportionment method** values included in the entity to determine how the **Value** of the cost is apportioned across the contents of the voyage.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Apportionment method | ITMCostTrans.ApportionmentMethod | int | No | No |
| Cost value | ITMCostTrans.CostValue | numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | numeric(32, 6) | No | No |
| Category | ITMCostTrans.ShipCostCategory | int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | nvarchar(4) | No | **Yes** |
| Voyage | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Item sales tax group | ITMCostTrans.TaxItemGroup | nvarchar(10) | No | No |

## Shipping container costs (ITMCostTransShippingContainerEntity)

The shipping container cost entity (`ITMCostTransShippingContainerEntity`) creates shipping container costs that are applied at the shipping container level. During the import process, the system uses the *category* and *apportionment method* values included in the entity to determine how the *value* of the cost is apportioned across the contents of the shipping container.

The fields **Aggregate**, **Leg** and **Linked leg** are specific to records where the **Cost area** is *shipping container* and so are not present in data entities for other cost areas.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Aggregate | ITMCostTrans.AggregatedCost | int | No | No |
| Apportionment method | ITMCostTrans.ApportionmentMethod | int | No | No |
| Cost value | ITMCostTrans.CostValue | numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | nvarchar(20) | No | No |
| Linked leg | ITMCostTrans.LinkLegId | nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | numeric(32, 6) | No | No |
| Shipping Container | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Category | ITMCostTrans.ShipCostCategory | int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | nvarchar(4) | No | **Yes** |
| Voyage | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Leg | ITMCostTrans.ShipLegId | nvarchar(20) | No | No |
| Item sales tax group | ITMCostTrans.TaxItemGroup | nvarchar(10) | No | No |

## Folio costs (ITMCostTransFolioEntity)

The folio cost entity (`ITMCostTransFolioEntity`) creates cost transaction records that apply to the folio level. During the import process, the system uses the **Category** and **Apportionment method** values included in the entity to determine how the **Value** of the cost is apportioned across the contents of each folio.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Apportionment method | ITMCostTrans.ApportionmentMethod | int | No | No |
| Cost value | ITMCostTrans.CostValue | numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | numeric(32, 6) | No | No |
| Category | ITMCostTrans.ShipCostCategory | int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | nvarchar(4) | No | **Yes** |
| Folio | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Item sales tax group | ITMCostTrans.TaxItemGroup | nvarchar(10) | No | No |

## Purchase order costs (ITMCostTransPurchaseEntity)

The purchase order cost entity (`ITMCostTransPurchaseEntity`) creates cost transactions that apply to the purchaser order header. During the import process, the system uses the **Category** and **Apportionment method** values included in the entity to determine how the **Value** of the cost is apportioned across the contents of each folio.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Apportionment method | ITMCostTrans.ApportionmentMethod | int | No | No |
| Cost value | ITMCostTrans.CostValue | numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | numeric(32, 6) | No | No |
| Purchase order | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Category | ITMCostTrans.ShipCostCategory | int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | nvarchar(4) | No | **Yes** |
| Item sales tax group | ITMCostTrans.TaxItemGroup | nvarchar(10) | No | No |

## Item costs (ITMCostTransItemEntity)

The item cost entity (`ITMCostTransItemEntity`) creates cost transactions that apply to the item level, this is specific to items on purchase order lines. The **Value** of the cost is applied in full to the line.

The fields **Adjustment amount** and **Value adjustment** are specific to the line level cost areas and so are not present in data entity for other cost areas.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Adjustment amount | ITMCostTrans.AdjustmentAmount | numeric(32, 6) | No | No |
| Cost value | ITMCostTrans.CostValue | numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | numeric(32, 6) | No | No |
| Purchase order | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Purchase order line number | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Category | ITMCostTrans.ShipCostCategory | int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | nvarchar(4) | No | **Yes** |
| Item sales tax group | ITMCostTrans.TaxItemGroup | nvarchar(10) | No | No |
| Value adjustment | ITMCostTrans.ValueAdjustmentMethod | int | No | No |

## Transfer line costs (ITMCostTransTransferLineEntity)

The transfer line cost entity (`ITMCostTransTransferLineEntity`) creates cost transactions that apply to the transfer order line level. The **Value** of these costs will be applied in full to the transfer order line.

The fields **Adjustment amount** and **Value adjustment** are specific to the line level cost areas and so are not present in data entity for other cost areas.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Adjustment amount | ITMCostTrans.AdjustmentAmount | numeric(32, 6) | No | No |
| Cost value | ITMCostTrans.CostValue | numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | numeric(32, 6) | No | No |
| Category | ITMCostTrans.ShipCostCategory | int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | nvarchar(4) | No | **Yes** |
| Transfer order | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Transfer order line number | ITMCostTrans.TransRecId | nvarchar(20) | **Yes** | No |
| Item sales tax group | ITMCostTrans.TaxItemGroup | nvarchar(10) | No | No |
| Value adjustment | ITMCostTrans.ValueAdjustmentMethod | int | No | No |

### Transaction table

A cost transaction record is associated with a cost area through the assignment of a transaction table number (`TransTableId`). Where specific table identification numbers are required, the entities are split based on these values so that an entity exists for each Cost area.

The value for the transaction table (`TransTableId`) is implicit in the selection of the cost transaction entity.

### Calculated fields

The following fields are not available for insert or update when using a cost transaction entity, as these fields are populated only when certain actions are taken against the voyage record.

- **Estimated cost** – Populated on invoice posting for the voyage (purchase order) or transfer receiving.
- **Estimated cost currency** – Populated on invoice posting for the voyage (purchase order) or transfer receiving.
- **Actual cost** – Populated on vendor invoice posting associates with the cost.

### Find auto costs

A **Find auto costs** button is located on each cost areas (voyage, shipping container, and so on) and exists as a method for refreshing the cost transactions for that cost area from the information held in the configuration tables. When you select this button, the system achieves this by clearing existing costs for the selected cost area and creating new records based on the current configuration of the Auto Cost setup tables.

Cost transaction records created using a data entity are flagged as having been imported. These records will not be deleted when the **Find auto costs** process is run, as these will not be reinstated from the auto cost setup table. A cost transaction flagged as imported can still be deleted.

### Linked fields

Each cost transaction can be associated with another record within the same cost area. This allows for a cost value to be calculated as a percentage of another cost. This relationship is established through the **Linked cost type** field.

For the **Linked cost type** field to validate, the record being referenced must be processed first, or already exist in the table. The same requirement is in place for the **Linked leg** field, which is only used for costs on the shipping container cost area.
