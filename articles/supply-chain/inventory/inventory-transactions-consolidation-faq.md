---
title: Consolidate inventory transactions FAQ (preview)
description: Find answers to frequently asked questions about inventory transaction consolidation in Microsoft Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventTransArchiveProcessForm
ms.topic: how-to
ms.date: 08/24/2026
ms.custom: 
  - bap-template
---

# Consolidate inventory transactions FAQ (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article provides answers to frequently asked questions about inventory transaction consolidation in Microsoft Dynamics 365 Supply Chain Management.

## Why are there more rows in the InventTransOrigin table after consolidation?

This result is expected. The *Inventory transactions consolidation* job creates new inventory transaction (`InventTrans`) and inventory transactions originator (`InventTransOrigin`) records.

For transactions that aren't warehouse management process (WMS) transactions, the job creates a new record with reference category `InventTransArchive` in the `InventTransOrigin` table. This new record links to the new consolidating inventory transaction.

For WMS transactions, the job creates a new record with reference category `WHSInventTransArchiveOnlyAffectsLocationAndBelow` in the `InventTransOrigin` table. This type of record affects only location and below in the inventory reservation hierarchy. In other words, it's used only for transactions that affect specific locations in the warehouse. Here are some examples:

- `WHSWork` – Transactions related to warehouse work orders.
- `WHSContainer` – Transactions that involve containers in the warehouse.
- `WHSOrderCommittedReservation` – Transactions for orders that have committed reservations.
- `WHSWarehouseInventoryBlocking` – Transactions that block inventory in the warehouse.

Reduce the consolidation frequency to help minimize the increase in the `InventTransOrigin` table.

<!-- (KFM: Replace this when the feature is available)
You can further optimize storage by using the *Archive with Dataverse long term retention* feature to remove and archive old records from the `InventTransOrigin` table. Learn more in [Archive Dynamics 365 Supply Chain Management Inventory transactions data](../../fin-ops-core/dev-itpro/sysadmin/archive-inventory.md). -->

## Why aren't some transactions moved to the InventTransArchive table during consolidation?

This result is expected. In the following scenarios, the system keeps transactions in the `InventTrans` table after inventory transaction consolidation:

- When the *Inventory transactions consolidation* job creates new inventory transactions that consolidate the archived inventory transactions, the job keeps these new transactions in the `InventTrans` table. Learn more in the previous section.
- If an `ItemId` and `InventDimId` combination contains only one receipt or issue transaction in the archive period, the job doesn't consolidate that transaction. Instead, it keeps the transaction in the `InventTrans` table.
- Inventory transactions are only included in the consolidation if all transactions for a given document can be consolidated. If, for example, not all inventory transactions for a sales order can be consolidated, no transactions for the sales order are consolidated. These transactions are automatically included in future consolidations when the prerequisites are met.

The following examples illustrate these aggregation rules.

### Aggregation rule example 1

#### Before consolidation

| ID | Item number | Inventory dimension ID | Financial date | Reference | Receipt | Issue | Quantity |
|---|---|---|---|---|---|---|---|
| A1 | WMS item A | Dim_1 | January 10, 2020 | Purchase order | Purchased | | 10 |
| A2 | WMS item A | Dim_1 | January 15, 2020 | Counting | | Sold | -3 |
| A3 | WMS item A | Dim_1 | January 20, 2020 | Work | | Sold | -7 |
| A4 | WMS item A | Dim_2 | January 20, 2020 | Work | Purchased | | 7 |
| A5 | WMS item A | Dim_2 | January 20, 2020 | Work | | Sold | -7 |
| A6 | WMS item A | Dim_3 | January 20, 2020 | Work | Purchased | | 7 |
| A7 | WMS item A | Dim_3 | January 25, 2020 | Sales order | | Sold | -7 |

#### After consolidation until January 31, 2020

| ID | Item number | Inventory dimension ID | Financial date | Reference | Receipt | Issue | Quantity |
|---|---|---|---|---|---|---|---|
| B1 | WMS item A | Dim_1 | January 31, 2020 | Archived inventory transaction | Purchased | | 7 |
| A3 | WMS item A | Dim_1 | January 20, 2020 | Work | | Sold | -7 |
| B3 | WMS item A | Dim_2 | January 31, 2020 | Archived warehouse transaction type that affects only location and below | | Sold | 0 |
| A6 | WMS item A | Dim_3 | January 20, 2020 | Work | Purchased | | 7 |
| A7 | WMS item A | Dim_3 | January 25, 2020 | Sales order | | Sold | -7 |

#### Result summary

Note the following results of the consolidation:

- Line B1 consolidates line A1 and line A2, because A1 and A2 both have the same inventory dimension (Dim\_1), and they aren't a warehouse transaction type that affects only location and below.
- Line B3 consolidates line A4 and line A5, because A4 and A5 both have the same inventory dimension (Dim\_2), and they are a warehouse transaction type that affects only location and below. Typically, if the cost amount and quantity are 0, line B3 isn't inserted into the inventory transactions table.
- Line A3 isn't consolidated with line B1, because it's a warehouse transaction type that affects only location and below.
