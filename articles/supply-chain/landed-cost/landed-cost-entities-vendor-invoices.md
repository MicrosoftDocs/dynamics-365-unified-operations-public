---
title: Vendor invoice entities
description: Vendor invoice entities allow cost type codes to be configured for internal or externally derived costs.
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

# Vendor invoice entities

[!include [banner](../includes/banner.md)]

The Landed cost module allows for cost type codes to be configured for internal or externally derived costs. Where a cost is external to a business an invoice is expected to be received from the service provider. This invoice is processed as an invoice journal where it can be associated to a Voyage and the value of the invoice distributed across one or more of the costs on the voyage.

The vendor invoice entities provide the ability to allocate the value of a journal line across one or more costs on a Voyage that share the same cost type code.

The invoice journal header and invoice journal lines must exist for a cost to be allocated.

## Vendor voyage cost allocations (ITMLedgerJournalCostLinesVoyagesEntity)

The vendor voyage cost allocations data entity enables the allocation of a vendor invoice line across one or more costs applied at the voyage cost area. This functionality is supported by the entity `ITMLedgerJournalCostLinesVoyagesEntity`. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | nvarchar(20) | **Yes** | No |
| Voyage | ITMLedgerJournalCostLines.CostTransRefRecId | nvarchar(20) | **Yes** | No |

## Vendor shipping container cost allocations (ITMLedgerJournalCostLinesContainersEntity)

The vendor shipping container cost allocations data entity enables the allocation of a vendor invoice line across one or more costs applied at the shipping container cost area. This functionality is supported by the entity `ITMLedgerJournalCostLinesContainersEntity`. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | numeric(32, 6) | No | No |
| Shipping container | ITMLedgerJournalCostLines.CostTransRefRecId | nvarchar(20) | **Yes** | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | nvarchar(20) | **Yes** | No |
| Voyage | ITMLedgerJournalCostLines.CostTransRefRecId | nvarchar(20) | **Yes** | No |

## Vendor folio cost allocations (ITMLedgerJournalCostLinesFoliosEntity)

The vendor folio cost allocations data entity enables the allocation of a vendor invoice line across one or more costs applied at the folio cost area. This functionality is supported by the entity `ITMLedgerJournalCostLinesFoliosEntity`. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | numeric(32, 16) | **Yes** | No |
| Folio | ITMLedgerJournalCostLines.CostTransRefRecId | nvarchar(20) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | nvarchar(20) | **Yes** | No |

## Vendor purchase order cost allocations (ITMLedgerJournalCostLinesPurchTableEntity)

The vendor purchase order cost allocations data entity enables the allocation of a vendor invoice line across one or more costs applied at the purchase order cost area. This functionality is supported by the entity `ITMLedgerJournalCostLinesPurchTableEntity`. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | nvarchar(20) | **Yes** | No |
| Purchase order | ITMLedgerJournalCostLines.CostTransRefRecId | nvarchar(20) | **Yes** | No |

## Vendor item cost allocations (ITMLedgerJournalCostLinesPurchLineEntity)

The vendor item cost allocations data entity enables the allocation of a vendor invoice line across one or more costs applied at the item cost area, which covers costs on the purchase order line. This functionality is supported by the entity `ITMLedgerJournalCostLinesPurchLineEntity`. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | nvarchar(20) | **Yes** | No |
| Purchase order | ITMLedgerJournalCostLines.CostTransRefRecId | nvarchar(20) | **Yes** | No |
| Purchase order line number | ITMLedgerJournalCostLines.CostTransRefRecId | numeric(32, 16) | **Yes** | No |

## Vendor transfer order line cost allocations (ITMLedgerJournalCostLinesTransferLineEntity)

The vendor transfer order line cost allocations data entity enables the allocation of a vendor invoice line across one or more costs applied at the transfer line cost area. This functionality is supported by the entity `ITMLedgerJournalCostLinesTransferLineEntity`. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | nvarchar(20) | **Yes** | No |
| Transfer order | ITMLedgerJournalCostLines.CostTransRefRecId | nvarchar(20) | **Yes** | No |
| Transfer order line number | ITMLedgerJournalCostLines.CostTransRefRecId | numeric(32, 16) | **Yes** | No |

### Reference table

Voyage cost lines have a direct association with a cost transaction record, which includes the **Reference table ID**. This value is unique for each of the cost areas (voyage, shipping container, and so on). Where specific table numbers are referenced for data being created using data entities, the entities are split based on these values.

The values for the reference table (`RefTableId`) and the transaction type (`TransType`) are implicit in the selection of either the Landed cost purchase line or Landed cost transfer line entity.

## Vendor invoice journal lines (VendorInvoiceJournalLineEntity)

For a journal line value to be allocated to one or more costs in the Landed cost module, the journal line must be associated to a cost area. To support his, the Landed cost module adds a few new fields to the journal lines table (`LedgerJournalTrans`).

### Fields added to the vendor invoice journal line entity

The following table lists fields that the Landed cost module adds to the vendor invoice journal line entity (`VendorInvoiceJournalLineEntity`). These fields enable the system to create journal lines and allocate costs against them

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Cost area | LedgerJournalTrans.ITMCostArea | | | |
| Cost type code | LedgerJournalTrans.ITMCostTypeId | | | |

<!-- KFM: I suspect some values are missing in the above table. Following up with author. -->

### Main/offset account

The main/offset account for an invoice journal line associated with a Landed cost voyage is determined by the cost type code. Where the cost type code is included on the invoice journal line the clearing account for the code will be used as either the main or offset account based on the following scenarios

- **Single line journal** – If a main account is defined (in other words, the vendor account) and a cost type code is provided, the offset account will be populated with the clearing account value for the entered cost type code.
- **Multiple line journal** – If a main account is not defined and a cost type code is provided, the main account will be populated with the clearing account value for the entered cost type code. The journal line crediting the vendor will not reference a cost type code.

## Sequencing

Due to dependencies between on the journal and journal lines tables, the voyage record must be created first and voyage lines can only be created once the voyage, shipping container, and folios have been created.

To allocate a voyage invoice, the system must process entities in the following order:

1. Invoice journal header (`VendInvoiceJournalHeaderEntity`)
1. Invoice journal line (`VendInvoiceJournalLineEntity`)
1. Landed cost allocations (`ITMLedgerJournalEntities`)
