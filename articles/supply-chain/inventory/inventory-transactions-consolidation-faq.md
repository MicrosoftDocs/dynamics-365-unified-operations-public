---
title: Inventory transactions consolidation FAQ
description: Find answers to frequently asked questions about inventory transactions consolidation in Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventTransArchiveProcessForm
ms.topic: how-to
ms.date: 08/19/2024
ms.custom: 
  - bap-template
---

# Inventory transactions consolidation FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about inventory transactions consolidation in Dynamics 365 Supply Chain Management.

## Why are there more rows in the InventTransOrigin table after consolidation?

This is expected. The *Inventory transactions consolidation* job creates new inventory transaction (`InventTrans`) and inventory transactions originator (`InventTransOrigin`) records, which consolidates the archived inventory transactions.

For transactions that aren't warehouse management processes (WMS) transactions, a new record with reference category `InventTransArchive` is created in table `InventTransOrigin`. The new record is linked to the new consolidating inventory transaction.

For WMS transactions, a new record with reference category `WHSInventTransArchiveOnlyAffectsLocationAndBelow` is created in `InventTransOrigin`. This type of record only affects the location and below in the inventory reservation hierarchy. This means it is used for transactions that impact specific locations within the warehouse, such as:

- `WHSWork` – Transactions related to warehouse work orders.
- `WHSContainer` – Transactions involving containers within the warehouse.
- `WHSOrderCommittedReservation` – Transactions for orders that have committed reservations.
- `WHSWarehouseInventoryBlocking` – Transactions that block inventory within the warehouse.

We suggest that you lower the consolidation frequency to minimize the increase in the `InventTransOrigin` table.

You can further optimize storage using the *Archive with Dataverse long term retention* feature to remove and archive old records from the `InventTransOrigin` table (learn more in [Archive Dynamics 365 Supply Chain Management Inventory transactions data](../../fin-ops-core/dev-itpro/sysadmin/archive-inventory.md)). This will be released later. <!-- KFM: I strongly recommend against making promises regarding unreleased features. Please consider removing or hiding this for now... -->

## Why are some transactions not moved to the InventTransArchive table during consolidation?

This is expected. The system keeps transaction in the `InventTrans` table after inventory transaction consolidation in the following scenarios:

- When the *Inventory transactions consolidation* job creates new inventory transactions that consolidate the archived inventory transactions, these new transactions are kept in the `InventTrans` table. Learn more in the previous section.
- If an `ItemId` and `InventDimId` combination contains only one receipt or issue transaction in the archive period, that transaction won't be consolidated and is instead kept in the `InventTrans` table.
- Backdate scenarios aren't supported. Transactions that aren't closed during the consolidation period won't be consolidated. Those transactions can be closed later, but they can't be removed from `InventTrans` table because the archive period has already been created by the job.

The following examples illustrate these aggregation rules.

### Aggregation rule example 1

#### Before consolidation

| ID | Item number | Inventory dimension ID | Financial date | Reference | Receipt | Issue | Quantity |
|--|--|--|--|--|--|--|--|
| A1 | WHS item A | Dim_1 | 1/10/2020 | Purchase order | Purchased |  | 10 |
| A2 | WHS item A | Dim_1 | 1/15/2020 | Counting |  | Sold | -3 |
| A3 | WHS item A | Dim_1 | 1/20/2020 | Work |  | Sold | -7 |
| A4 | WHS item A | Dim_2 | 1/20/2020 | Work | Purchased |  | 7 |
| A5 | WHS item A | Dim_2 | 1/20/2020 | Work |  | Sold | -7 |
| A6 | WHS item A | Dim_3 | 1/20/2020 | Work | Purchased |  | 7 |
| A7 | WHS item A | Dim_3 | 1/25/2020 | Sales order |  | Sold | -7 |

#### After consolidation from 1/1/2020 to 1/31/2020

| ID | Item number | Inventory dimension ID | Financial date | Reference | Receipt | Issue | Quantity |
|--|--|--|--|--|--|--|--|
| B1 | WHS item A | Dim_1 | 1/31/2020 | Archived inventory transaction | Purchased |  | 7 |
| A3 | WHS item A | Dim_1 | 1/20/2020 | Work |  | Sold | -7 |
| B3 | WHS item A | Dim_2 | 1/31/2020 | Archived warehouse transaction type only affects location and below |  | Sold | 0 |
| A6 | WHS item A | Dim_3 | 1/20/2020 | Work | Purchased |  | 7 |
| A7 | WHS item A | Dim_3 | 1/25/2020 | Sales order |  | Sold | -7 |

#### Result summary

Note the following results of the consolidation:

- Line B1 consolidates line A1 &plus; A2 because they both have the same inventory dimension (Dim\_1) and aren't a warehouse transaction type that only affects location and below.
- Line B3 consolidates line A4 &plus; A5 because they both have the same inventory dimension (Dim\_2), and are a warehouse transaction type that only affects location and below. (Typically, if the cost amount and quantity are all zero, Line B3 won't be insert into the inventory transactions table.)
- Line A3 isn't consolidated with line B1 because it is a warehouse transaction type that only affects location and below.

### Aggregation rule example 2

Suppose you take the following steps:

1. You receive item *A0001* on 1/25/2020 and the transaction isn't financially updated
1. You run the inventory closing on 2/1/2020.
1. On 2/5/2020, you run the *Inventory transactions consolidation* job with archive period 1/1/2020 – 1/31/2020.
1. Sometime after 2/5/2020, you change the session date and time back to 1/30/2020.
1. You financially update the received transaction of item *A0001* to *Purchased*.

As a result, this transaction for item *A0001* will never be consolidated because consolidation is based on the financial date, and overlapping consolidation periods aren't allowed.
