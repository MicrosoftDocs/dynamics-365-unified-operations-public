---
title: Consolidate inventory transactions FAQ
description: Find answers to frequently asked questions about inventory transaction consolidation in Microsoft Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventTransArchiveProcessForm
ms.topic: how-to
ms.date: 08/19/2024
ms.custom: 
  - bap-template
---

# Consolidate inventory transactions FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about inventory transaction consolidation in Microsoft Dynamics 365 Supply Chain Management.

## Why are there more rows in the InventTransOrigin table after consolidation?

This result is expected. The *Inventory transactions consolidation* job works by creating new inventory transaction (`InventTrans`) and inventory transactions originator (`InventTransOrigin`) records.

For transactions that aren't warehouse management process (WMS) transactions, a new record that has reference category `InventTransArchive` is created in the `InventTransOrigin` table. This new record is linked to the new consolidating inventory transaction.

For WMS transactions, a new record that has reference category `WHSInventTransArchiveOnlyAffectsLocationAndBelow` is created in the `InventTransOrigin` table. This type of record affects only location and below in the inventory reservation hierarchy. In other words, it's used only for transactions that affect specific locations in the warehouse. Here are some examples:

- `WHSWork` – Transactions that are related to warehouse work orders.
- `WHSContainer` – Transactions that involve containers in the warehouse.
- `WHSOrderCommittedReservation` – Transactions for orders that have committed reservations.
- `WHSWarehouseInventoryBlocking` – Transactions that block inventory in the warehouse.

We recommend that you reduce the consolidation frequency to help minimize the increase in the `InventTransOrigin` table.

<!-- (KFM: Replace this when the feature is available)
You can further optimize storage using the *Archive with Dataverse long term retention* feature to remove and archive old records from the `InventTransOrigin` table. Learn more in [Archive Dynamics 365 Supply Chain Management Inventory transactions data](../../fin-ops-core/dev-itpro/sysadmin/archive-inventory.md). -->

## Why aren't some transactions moved to the InventTransArchive table during consolidation?

This result is expected. In the following scenarios, the system keeps transactions in the `InventTrans` table after inventory transaction consolidation:

- When the *Inventory transactions consolidation* job creates new inventory transactions that consolidate the archived inventory transactions, these new transactions are kept in the `InventTrans` table. Learn more in the previous section.
- If an `ItemId` and `InventDimId` combination contains only one receipt or issue transaction in the archive period, that transaction isn't consolidated. Instead, it's kept in the `InventTrans` table.
- Backdate scenarios aren't supported. Transactions that aren't closed during the consolidation period aren't consolidated. Those transactions can be closed later, but they can't be removed from the `InventTrans` table, because the job already created the archive period.

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

- Line B1 consolidates line A1 &plus; line A2, because A1 and A2 both have the same inventory dimension (Dim\_1), and they aren't a warehouse transaction type that affects only location and below.
- Line B3 consolidates line A4 &plus; line A5, because A4 and A5 both have the same inventory dimension (Dim\_2), and they are a warehouse transaction type that affects only location and below. (Typically, if the cost amount and quantity are 0 \[zero\], line B3 isn't inserted into the inventory transactions table.)
- Line A3 isn't consolidated with line B1, because it's a warehouse transaction type that affects only location and below.

### Aggregation rule example 2

For this example, you complete the following steps:

1. On January 25, 2020, you receive item *A0001*, and the transaction isn't financially updated.
1. On February 1, 2020, you run the inventory closing.
1. On February 5, 2020, you run the *Inventory transactions consolidation* job. The archive period is January 1, 2020, through January 31, 2020.
1. Sometime after February 5, 2020, you change the session date and time back to January 30, 2020.
1. You financially update the received transaction of item *A0001* to *Purchased*.

As a result, the transaction for item *A0001* is never consolidated, because consolidation is based on the financial date, and overlapping consolidation periods aren't allowed.
