---
title: Vendor invoice entities
description: Learn about vendor invoice entities, which enable cost type codes to be configured for internal costs or externally derived costs.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 05/27/2022
ms.reviewer: kamaybac
ms.search.form:
---

# Vendor invoice entities

[!include [banner](../includes/banner.md)]

The **Landed cost** module enables cost type codes to be configured for internal costs or externally derived costs. If a cost is external to a business, an invoice is expected from the service provider. This invoice is processed as an invoice journal that can be associated with a voyage, and the value of the invoice can be distributed across one or more costs of the voyage.

The vendor invoice entities enable the value of a journal line to be allocated across one or more costs of a voyage that share the same cost type code.

A cost can be allocated only if the invoice journal header and invoice journal lines exist.

## Vendor voyage cost allocations (ITMLedgerJournalCostLinesVoyagesEntity)

The vendor voyage cost allocations data entity enables a vendor invoice line to be allocated across one or more costs that are applied to the voyage cost area. This functionality is supported by the `ITMLedgerJournalCostLinesVoyagesEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | Numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | Numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | Numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | Nvarchar(20) | **Yes** | No |
| Voyage | ITMLedgerJournalCostLines.CostTransRefRecId | Nvarchar(20) | **Yes** | No |

## Vendor shipping container cost allocations (ITMLedgerJournalCostLinesContainersEntity)

The vendor shipping container cost allocations data entity enables a vendor invoice line to be allocated across one or more costs that are applied to the shipping container cost area. This functionality is supported by the `ITMLedgerJournalCostLinesContainersEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | Numeric(32, 6) | No | No |
| Shipping container | ITMLedgerJournalCostLines.CostTransRefRecId | Nvarchar(20) | **Yes** | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | Numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | Numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | Nvarchar(20) | **Yes** | No |
| Voyage | ITMLedgerJournalCostLines.CostTransRefRecId | Nvarchar(20) | **Yes** | No |

## Vendor folio cost allocations (ITMLedgerJournalCostLinesFoliosEntity)

The vendor folio cost allocations data entity enables a vendor invoice line to be allocated across one or more costs that are applied to the folio cost area. This functionality is supported by the `ITMLedgerJournalCostLinesFoliosEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | Numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | Numeric(32, 16) | **Yes** | No |
| Folio | ITMLedgerJournalCostLines.CostTransRefRecId | Nvarchar(20) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | Numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | Nvarchar(20) | **Yes** | No |

## Vendor purchase order cost allocations (ITMLedgerJournalCostLinesPurchTableEntity)

The vendor purchase order cost allocations data entity enables a vendor invoice line to be allocated across one or more costs that are applied to the purchase order cost area. This functionality is supported by the `ITMLedgerJournalCostLinesPurchTableEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | Numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | Numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | Numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | Nvarchar(20) | **Yes** | No |
| Purchase order | ITMLedgerJournalCostLines.CostTransRefRecId | Nvarchar(20) | **Yes** | No |

## Vendor item cost allocations (ITMLedgerJournalCostLinesPurchLineEntity)

The vendor item cost allocations data entity enables a vendor invoice line to be allocated across one or more costs that are applied to the item cost area. The item cost area covers costs on the purchase order line. This functionality is supported by the `ITMLedgerJournalCostLinesPurchLineEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | Numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | Numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | Numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | Nvarchar(20) | **Yes** | No |
| Purchase order | ITMLedgerJournalCostLines.CostTransRefRecId | Nvarchar(20) | **Yes** | No |
| Purchase order line number | ITMLedgerJournalCostLines.CostTransRefRecId | Numeric(32, 16) | **Yes** | No |

## Vendor transfer order line cost allocations (ITMLedgerJournalCostLinesTransferLineEntity)

The vendor transfer order line cost allocations data entity enables a vendor invoice line to be allocated across one or more costs that are applied to the transfer line cost area. This functionality is supported by the `ITMLedgerJournalCostLinesTransferLineEntity` entity. The following table lists the fields and mappings that make up this entity.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Allocated amount | ITMLedgerJournalCostLines.Amount | Numeric(32, 6) | No | No |
| Cost transaction line number | ITMLedgerJournalCostLines.CostTransRefRecId | Numeric(32, 16) | **Yes** | No |
| Journal line number | ITMLedgerJournalCostLines.RefRecId | Numeric(32, 16) | **Yes** | No |
| Journal number | ITMLedgerJournalCostLines.RefRecId | Nvarchar(20) | **Yes** | No |
| Transfer order | ITMLedgerJournalCostLines.CostTransRefRecId | Nvarchar(20) | **Yes** | No |
| Transfer order line number | ITMLedgerJournalCostLines.CostTransRefRecId | Numeric(32, 16) | **Yes** | No |

### Reference table

Voyage cost lines have a direct association with a cost transaction record. This record includes the **Reference table ID** value. This value is unique for each cost area (voyage, shipping container, and so on). When specific table numbers are referenced for data that is created by using data entities, the entities are split based on **Reference table ID** values.

The values for the reference table (`RefTableId`) and the transaction type (`TransType`) are implicit in the selection of either the Landed cost purchase line or the Landed cost transfer line entity.

## Vendor invoice journal lines (VendorInvoiceJournalLineEntity)

Before a journal line value can be allocated to one or more costs in the **Landed cost** module, the journal line must be associated with a cost area. To support this functionality, the **Landed cost** module adds some new fields to the journal lines table (`LedgerJournalTrans`).

### Fields added to the vendor invoice journal line entity

The following table lists the fields that the **Landed cost** module adds to the vendor invoice journal line entity (`VendorInvoiceJournalLineEntity`). These fields enable the system to create journal lines and allocate costs against them.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Cost area | LedgerJournalTrans.ITMCostArea | Int | No | No |
| Cost type code | LedgerJournalTrans.ITMCostTypeId | Nvarchar(20) | No | No |

### Main/offset account

The main/offset account for an invoice journal line that is associated with a Landed cost voyage is determined by the cost type code. When the cost type code is included on the invoice journal line, the clearing account for the code will be used as either the main account or the offset account, depending on the scenario:

- **Single-line journal** – If a main account (in other words, the vendor account) is defined, and a cost type code is provided, the clearing account value for that cost type code will be entered in the offset account.
- **Multiple-line journal** – If a main account isn't defined, but a cost type code is provided, the clearing account value for the that cost type code will be entered in the main account. The journal line that is crediting the vendor won't reference a cost type code.

## Sequencing

Because of dependencies between the journal and journal lines tables, the voyage record must be created first. The voyage lines can be created only after the voyage, shipping container, and folios have been created.

To allocate a voyage invoice, the system must process the entities in the following order:

1. Invoice journal header (`VendInvoiceJournalHeaderEntity`)
1. Invoice journal line (`VendInvoiceJournalLineEntity`)
1. Landed cost allocations (`ITMLedgerJournalEntities`)
