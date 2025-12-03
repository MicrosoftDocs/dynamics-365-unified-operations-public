---
title: Consolidate inventory transactions FAQ
description: Find answers to frequently asked questions about inventory transaction consolidation in Microsoft Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventTransArchiveProcessForm
ms.topic: how-to
ms.date: 11/12/2025
ms.custom: 
  - bap-template
---

# Consolidate inventory transactions FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about inventory transaction consolidation in Microsoft Dynamics 365 Supply Chain Management.

## What should I consider when choosing a bundle size?

The **Bundle size** setting on the [**Inventory transaction consolidation**](archive-inventory-transactions.md) dialog controls how many unique combinations of item ID and inventory dimension ID values the system can group into a single SQL transaction when consolidating inventory transactions.

Choose the bundle size based on the number of inventory transactions you have per combination. For combinations with a high transaction count, choose a smaller bundle size to avoid performance issues. If the number of transactions per combination is low, a larger bundle size might be more efficient.

> [!NOTE]
> Keep the number of transactions per bundle at or below 100,000. If your environment includes a small number of combinations but a high overall transaction volume, consider narrowing the consolidation timeframe to maintain performance.

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
- The job doesn't support backdate scenarios. If the job doesn't close transactions during the consolidation period, it doesn't consolidate those transactions. You can close these transactions later, but you can't remove them from the `InventTrans` table because the job already created the archive period.

The following examples illustrate these aggregation rules.

### Aggregation rule example 1

#### Before consolidation

| ID | Item number | Inventory dimension ID | Financial date | Reference | Receipt | Issue | Quantity |
|---|---|---|---|---|---|---|---|
| A1 | WHS item A | Dim_1 | January 10, 2020 | Purchase order | Purchased | | 10 |
| A2 | WHS item A | Dim_1 | January 15, 2020 | Counting | | Sold | -3 |
| A3 | WHS item A | Dim_1 | January 20, 2020 | Work | | Sold | -7 |
| A4 | WHS item A | Dim_2 | January 20, 2020 | Work | Purchased | | 7 |
| A5 | WHS item A | Dim_2 | January 20, 2020 | Work | | Sold | -7 |
| A6 | WHS item A | Dim_3 | January 20, 2020 | Work | Purchased | | 7 |
| A7 | WHS item A | Dim_3 | January 25, 2020 | Sales order | | Sold | -7 |

#### After consolidation from January 1, 2020, through January 31, 2020

| ID | Item number | Inventory dimension ID | Financial date | Reference | Receipt | Issue | Quantity |
|---|---|---|---|---|---|---|---|
| B1 | WHS item A | Dim_1 | January 31, 2020 | Archived inventory transaction | Purchased | | 7 |
| A3 | WHS item A | Dim_1 | January 20, 2020 | Work | | Sold | -7 |
| B3 | WHS item A | Dim_2 | January 31, 2020 | Archived warehouse transaction type that affects only location and below | | Sold | 0 |
| A6 | WHS item A | Dim_3 | January 20, 2020 | Work | Purchased | | 7 |
| A7 | WHS item A | Dim_3 | January 25, 2020 | Sales order | | Sold | -7 |

#### Result summary

Note the following results of the consolidation:

- Line B1 consolidates line A1 and line A2, because A1 and A2 both have the same inventory dimension (Dim\_1), and they aren't a warehouse transaction type that affects only location and below.
- Line B3 consolidates line A4 and line A5, because A4 and A5 both have the same inventory dimension (Dim\_2), and they are a warehouse transaction type that affects only location and below. Typically, if the cost amount and quantity are 0, line B3 isn't inserted into the inventory transactions table.
- Line A3 isn't consolidated with line B1, because it's a warehouse transaction type that affects only location and below.

### Aggregation rule example 2

In this example, you complete the following steps:

1. On January 25, 2020, you receive item *A0001*, but you don't financially update the transaction.
1. On February 1, 2020, you run the inventory closing.
1. On February 5, 2020, you run the *Inventory transactions consolidation* job. The archive period is January 1, 2020, through January 31, 2020.
1. After February 5, 2020, you change the session date and time back to January 30, 2020.
1. You financially update the received transaction for item *A0001* to *Purchased*.

As a result, the transaction for item *A0001* is never consolidated, because consolidation is based on the financial date, and overlapping consolidation periods aren't allowed.
