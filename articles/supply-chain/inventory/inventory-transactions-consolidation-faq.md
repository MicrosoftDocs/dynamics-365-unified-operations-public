---
title: Inventory transactions consolidation FAQ
description: Find answers to frequently asked questions about inventory transactions consolidation in Dynamics 365 Supply Chain Management.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventTransArchiveProcessForm
ms.topic: how-to
ms.date: 08/12/2024
ms.custom: 
  - bap-template
---

# Inventory transactions consolidation FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about inventory transactions consolidation in Dynamics 365 Supply Chain Management.

## Why are there more rows in the InventTransOrigin table after consolidation?

This is expected. The Inventory transactions consolidation job creates new inventory transactions (`InventTrans`) and inventory transactions originator (`InventTransOrigin`) which consolidates the archived inventory transactions.

For transactions that are not warehouse management processes (WMS) transactions, a new record with reference category `InventTransArchive` is created in table `InventTransOrigin`, which is linked to the new consolidating inventory transaction.

For WMS transactions, a new record with reference category `WHSInventTransArchiveOnlyAffectsLocationAndBelow` is created in `InventTransOrigin`. The key point is that this type of record only affects the location and below in the inventory reservation hierarchy. This means it is used for transactions that impact specific locations within the warehouse, such as:

- `WHSWork` – Transactions related to warehouse work orders.
- `WHSContainer` – Transactions involving containers within the warehouse.
- `WHSOrderCommittedReservation` – Transactions for orders that have committed reservations.
- `WHSWarehouseInventoryBlocking` – Transactions that block inventory within the warehouse.

We suggest customers lower the consolidation frequency to minimize the increase in table `InventTransOrigin`. Please kindly note, you can further optimize storage using the *Archive with Dataverse long term retention* feature for table `InventTransOrigin`. This will be released later.

## Why are some transactions not moved to the InventTransArchive table during consolidation?

This is expected. There are three scenarios in which transactions are kept in the `InventTrans` table after inventory transaction consolidation.

1. Inventory transactions consolidation job creates new inventory transactions which consolidate the archived inventory transactions. These new consolidating inventory transactions are kept in table `InventTrans`. Please see more details in the above question.
1. If an `ItemId` and `InventDimId` combination contains only one receipt or issue transaction in the archive period, that transaction won't be consolidated and will be kept in the `InventTrans` table.
1. There is no backdate scenario supported. Suppose this scenario, when doing inventory transaction consolidation, those transactions not closed during the consolidation period will not be consolidated. Those transactions can be closed later, but they cannot be removed from `InventTrans` table as the archive period has been created the job already.

Finally, there is no backdate scenario support. If transactions are not closed by the time a consolidation.

Refer to below example about the aggregation rule explanation.

### Aggregation rule example 1

![A screenshot of a computer Description automatically generated](media/image1.png)

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

#### After consolidation

| ID | Item number | Inventory dimension ID | Financial date | Reference | Receipt | Issue | Quantity |
|--|--|--|--|--|--|--|--|
| B1 | WHS item A | Dim_1 | 1/31/2020 | Archived inventory transaction | Purchased |  | 7 |
| A3 | WHS item A | Dim_1 | 1/20/2020 | Work |  | Sold | -7 |
| B3 | WHS item A | Dim_2 | 1/31/2020 | Archived warehouse transaction type only affects location and below |  | Sold | 0 |
| A6 | WHS item A | Dim_3 | 1/20/2020 | Work | Purchased |  | 7 |
| A7 | WHS item A | Dim_3 | 1/25/2020 | Sales order |  | Sold | -7 |

#### Result summary

Line B1 is consolidated by line A1 &plus; A2, as they are with the same Dim\_1, and are not warehouse transaction type only affects location and below

Line B3 is consolidated by line A4 &plus; A5, as they are with the same Dim\_2, and are all warehouse transaction type only affects location and below

(Typically, if cost amount and quantity are all zero, Line B3 will not be insert into Inventory transactions table)

Line A3 is not consolidated with line B1, as it is warehouse transaction type only affects location and below

### Aggregation rule example 2

Given Item A0001 is received on 1/25/2020, not financially updated.

1. Run the inventory closing on 2/1/2020.
1. Run the Inventory transactions consolidation with archive period (1/1/2020 – 1/31/2020) on 2/5/2020.
1. Someday after 2/5/2020, change the session date and time back to 1/30/2020. Financially update the received transaction of Item A0001 to Purchased.

As a result, this transaction for Item A0001 will never be consolidated, since consolidation is based on the financial date, and overlapping consolidation periods are not allowed.
