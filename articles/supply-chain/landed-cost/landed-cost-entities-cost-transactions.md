---
title: Cost transaction entities
description: Learn about cost transaction entities, which enable the value of a cost split among the contents of a cost area through the selection of an apportionment method.
author: lisascholz
ms.author: lisascholz
ms.topic: article
ms.date: 05/27/2022
ms.reviewer: kamaybac
ms.search.form:
---

# Cost transaction entities

[!include [banner](../includes/banner.md)]

## Apportionment

Landed cost enables the value of a cost to be split among the contents of a cost area (voyage, shipping container, and so on) through the selection of an apportionment method. The apportionment method is set as part of the configuration of automatic costs that is based on business rules. It's pulled through as a part of the cost when a voyage line is created.

### Configure the apportionment mapping for use with data entities

When a cost is created from an external source such as a freight forwarder, that external source can't specify the preferred method for apportioning the cost value. The apportionment mapping defines the default apportionment method for each cost type code. The apportionment mapping table is accessed from the **Apportionment mapping** page in Microsoft Dynamics 365 Supply Chain Management (**Landed Cost \> Costing setup \> Apportionment mapping**).

If a mapping combination has been defined, and a cost that matches the cost type code is created by using a cost transaction entity, the mapped apportionment method will be used instead of any value that has been provided to the entity.

If no value is present in the mapping table, but a value has been provided to the entity, the provided value will be used.

If no value exists in either the mapping table or the record that has been submitted to the entity, creation will fail.

### Apportionment mapping (ITMApportionmentMapping)

The apportionment mapping entity (`ITMApportionmentMapping`) creates apportionment mapping relationships and enables users to create or update records.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Apportionment method | ITMApportionmentMapping.ApportionmentMethod | Int | No | No |
| Cost type code | ITMApportionmentMapping.ShipCostTypeId | Nvarchar(20) | **Yes** | No |

## Voyage costs (ITMCostTransVoyageEntity)

The voyage cost entity (`ITMCostTransVoyageEntity`) creates voyage cost transactions that are applied at the voyage level. During the import process, the system uses the **Category** and **Apportionment method** values that are included in the entity to determine how the value of the cost is apportioned across the contents of the voyage.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Apportionment method | ITMCostTrans.ApportionmentMethod | Int | No | No |
| Cost value | ITMCostTrans.CostValue | Numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | Nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | Numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | Nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | Numeric(32, 6) | No | No |
| Category | ITMCostTrans.ShipCostCategory | Int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | Nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | Nvarchar(4) | No | **Yes** |
| Voyage | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Item sales tax group | ITMCostTrans.TaxItemGroup | Nvarchar(10) | No | No |

## Shipping container costs (ITMCostTransShippingContainerEntity)

The shipping container cost entity (`ITMCostTransShippingContainerEntity`) creates shipping container costs that are applied at the shipping container level. During the import process, the system uses the **Category** and **Apportionment method** values that are included in the entity to determine how the value of the cost is apportioned across the contents of the shipping container.

The **Aggregate**, **Leg**, and **Linked leg** fields are specific to records where the **Cost area** value is *Shipping container*. Therefore, they aren't present in data entities for other cost areas.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Aggregate | ITMCostTrans.AggregatedCost | Int | No | No |
| Apportionment method | ITMCostTrans.ApportionmentMethod | Int | No | No |
| Cost value | ITMCostTrans.CostValue | Numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | Nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | Numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | Nvarchar(20) | No | No |
| Linked leg | ITMCostTrans.LinkLegId | Nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | Numeric(32, 6) | No | No |
| Shipping Container | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Category | ITMCostTrans.ShipCostCategory | Int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | Nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | Nvarchar(4) | No | **Yes** |
| Voyage | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Leg | ITMCostTrans.ShipLegId | Nvarchar(20) | No | No |
| Item sales tax group | ITMCostTrans.TaxItemGroup | Nvarchar(10) | No | No |

## Folio costs (ITMCostTransFolioEntity)

The folio cost entity (`ITMCostTransFolioEntity`) creates cost transaction records that apply to the folio level. During the import process, the system uses the **Category** and **Apportionment method** values that are included in the entity to determine how the value of the cost is apportioned across the contents of each folio.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Apportionment method | ITMCostTrans.ApportionmentMethod | Int | No | No |
| Cost value | ITMCostTrans.CostValue | Numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | Nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | Numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | Nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | Numeric(32, 6) | No | No |
| Category | ITMCostTrans.ShipCostCategory | Int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | Nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | Nvarchar(4) | No | **Yes** |
| Folio | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Item sales tax group | ITMCostTrans.TaxItemGroup | Nvarchar(10) | No | No |

## Purchase order costs (ITMCostTransPurchaseEntity)

The purchase order cost entity (`ITMCostTransPurchaseEntity`) creates cost transactions that apply to the purchaser order header. During the import process, the system uses the **Category** and **Apportionment method** values that are included in the entity to determine how the value of the cost is apportioned across the contents of each folio.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Apportionment method | ITMCostTrans.ApportionmentMethod | Int | No | No |
| Cost value | ITMCostTrans.CostValue | Numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | Nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | Numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | Nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | Numeric(32, 6) | No | No |
| Purchase order | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Category | ITMCostTrans.ShipCostCategory | Int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | Nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | Nvarchar(4) | No | **Yes** |
| Item sales tax group | ITMCostTrans.TaxItemGroup | Nvarchar(10) | No | No |

## Item costs (ITMCostTransItemEntity)

The item cost entity (`ITMCostTransItemEntity`) creates cost transactions that apply to the item level. This entity is specific to items on purchase order lines. The value of the cost is applied in full to the line.

The **Adjustment amount** and **Value adjustment** fields are specific to the line-level cost areas. Therefore, they aren't present in data entities for other cost areas.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Adjustment amount | ITMCostTrans.AdjustmentAmount | Numeric(32, 6) | No | No |
| Cost value | ITMCostTrans.CostValue | Numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | Nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | Numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | Nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | Numeric(32, 6) | No | No |
| Purchase order | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Purchase order line number | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Category | ITMCostTrans.ShipCostCategory | Int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | Nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | Nvarchar(4) | No | **Yes** |
| Item sales tax group | ITMCostTrans.TaxItemGroup | Nvarchar(10) | No | No |
| Value adjustment | ITMCostTrans.ValueAdjustmentMethod | Int | No | No |

## Transfer line costs (ITMCostTransTransferLineEntity)

The transfer line cost entity (`ITMCostTransTransferLineEntity`) creates cost transactions that apply to the transfer order line level. The value of these costs is applied in full to the transfer order line.

The **Adjustment amount** and **Value adjustment** fields are specific to the line-level cost areas. Therefore, they aren't present in data entities for other cost areas.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Adjustment amount | ITMCostTrans.AdjustmentAmount | Numeric(32, 6) | No | No |
| Cost value | ITMCostTrans.CostValue | Numeric(32, 6) | No | No |
| Currency | ITMCostTrans.CurrencyCode | Nvarchar(3) | No | **Yes** |
| Line number | ITMCostTrans.LineNum | Numeric(32, 16) | **Yes** | No |
| Linked cost type | ITMCostTrans.LinkCostTypeId | Nvarchar(20) | No | No |
| Minimum cost | ITMCostTrans.MinCostAmount | Numeric(32, 6) | No | No |
| Category | ITMCostTrans.ShipCostCategory | Int | No | No |
| Cost type code | ITMCostTrans.ShipCostTypeId | Nvarchar(20) | No | No |
| Company | ITMCostTrans.ShipDataArea | Nvarchar(4) | No | **Yes** |
| Transfer order | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Transfer order line number | ITMCostTrans.TransRecId | Nvarchar(20) | **Yes** | No |
| Item sales tax group | ITMCostTrans.TaxItemGroup | Nvarchar(10) | No | No |
| Value adjustment | ITMCostTrans.ValueAdjustmentMethod | Int | No | No |

### Transaction table

A cost transaction record is associated with a cost area through the assignment of a transaction table number (`TransTableId`). When specific table identification numbers are required, the entities are split based on these values, so that an entity exists for each cost area.

The value for the transaction table (`TransTableId`) is implicit in the selection of the cost transaction entity.

### Calculated fields

The following fields aren't available for insert or update when a cost transaction entity is used, because these fields are set only when specific actions are taken against the voyage record:

- **Estimated cost** – This field is set when an invoice is posted for the voyage (purchase order) or a transfer is received.
- **Estimated cost currency** – This field is set when an invoice is posted for the voyage (purchase order) or a transfer is received.
- **Actual cost** – This field is set when a vendor invoice is posted. It's associated with the cost.

### Find auto costs

A **Find auto costs** button that is available for each cost area (voyage, shipping container, and so on) provides a way to update the cost transactions for that cost area from the information in the configuration tables. When you select the button for a cost area, the system clears existing costs for that cost area and creates new records, based on the current configuration of the auto cost setup tables.

Cost transaction records that are created by using a data entity are flagged as imported. These records aren't deleted when you select **Find auto costs**, because they won't be re-created from the auto cost setup tables. However, a cost transaction record that is flagged as imported can still be deleted.

### Linked fields

Each cost transaction can be associated with another record in the same cost area. This association is established through the **Linked cost type** field. It enables a cost value to be calculated as a percentage of another cost.

The **Linked cost type** field can be validated only if the record that is being referenced is processed first, or if it already exists in the table. The same requirement applies to the **Linked leg** field that is used for costs in the shipping container cost area only.
