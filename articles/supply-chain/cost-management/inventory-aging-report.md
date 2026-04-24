---
title: Inventory aging report examples and logic
description: Learn about inventory aging reports and logic, including examples that show how to interpret the results of an Inventory aging report.
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form: InventAgingStorage, InventAgingStorageChart, InventAgingStorageDetails
ms.topic: how-to
ms.date: 4/21/2026
ms.custom: 
  - bap-template
---

# Inventory aging report examples and logic

[!include [banner](../includes/banner.md)]

This article presents some examples that show how to interpret the results of an **Inventory aging** report. This report categorizes on-hand quantity and inventory values for a selected item or item group into several period buckets. This article also shows the internal logic of the report.

The examples in this article show results that are presented on a standard **Inventory aging** report. However, in general, we recommend that you use the [Inventory aging report storage](inventory-aging-report-storage.md) version of this report, especially when you have many items and warehouses that must be processed. Inventory aging report storage saves each report that you generate, shows the results as an interactive page and a chart, and lets you export any saved report.

## Sample data that is used in these examples

The examples in this article are based on the sample inventory transaction data that is described in this section.

### Storage dimension setup

The example system contains the following setup of storage dimensions.

| Name      | Active | Physical inventory | Financial inventory |
|-----------|--------|--------------------|---------------------|
| Site      | Yes    | Yes                | Yes                 |
| Warehouse | Yes    | Yes                | No                  |

### Inventory model

For the example system, the inventory model for the released products is *FIFO*, and the **Cost price** setting for the inventory model is *Include physical value*.

### Inventory transactions

The example system contains the following inventory transactions for a released product that has the item number *1000*.

| Reference | Site | Warehouse | Receipt | Issue | Physical date | Financial date | Quantity | Cost amount | Physical cost amount |
|--|--|--|--|--|--|--|--|--|--|
| Purchase order | 1 | 11 | Purchased |  | March 15 | March 15 | 10 | 1,000 | 1,000 |
| Purchase order | 2 | 21 | Purchased |  | March 15 | March 15 | 10 | 2,000 | 2,000 |
| Purchase order | 1 | 11 | Received |  | April 15 |  | 5 |  | 375 |
| Transfer order | 1 | 11 |  | Sold | May 2 | May 2 | -5 | -458.33 | -458.33 |
| Transfer order | 1 | 12 | Purchased |  | May 2 | May 2 | 5 | 458.33 | 458.33 |
| Sales order | 1 | 12 |  | Sold | May 3 | May 3 | -1 | -91.67 | -91.67 |

## How quantities and amounts in each period bucket are calculated

By using the sample data that is described in the previous sections, you can run an **Inventory aging** report that has the following settings:

- **As of date:** *May 9, 2020*
- **Site:** *View*
- **Warehouse:** *No*
- **Item number:** *Total*
- **Aging period:** Set this field to generate monthly buckets.

In this case, the content of the report that is generated will resemble the following example.

| Item number | Site | On-hand quantity | On-hand value | Inventory value quantity | Inventory value | Average unit cost | P1:Quantity (5/8/2020 - 5/1/2020) | P1:Amount (5/8/2020 - 5/1/2020) | P2:Quantity (4/30/2020 - 4/1/2020) | P2:Amount (4/30/2020 - 4/1/2020) | P3:Quantity (3/31/2020 - 3/1/2020) | P3:Amount (3/31/2020 - 3/1/2020) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1000 | 1 | 14 | 1,283.33 | 14 | 1,283.33 | 91.67 |  |  | 5.00 | 458.33 | 9.00 | 825.00 |
| 1000 | 2 | 10 | 2,000.00 | 10 | 2,000.00 | 200.00 |  |  |  |  | 10.00 | 2,000.00 |
| **1000 Totals** |  | **24.00** | **3,283.33** |  |  |  |  |  | **5.00** | **458.33** | **19** | **2,825.00** |

Note the following details in this example report:

- The **Inventory value quantity**, **Inventory value**, and **Average unit cost** values that are shown on the report are values for the financial inventory dimension (**Site**, in this case).

    For example, for site 1, the report shows the following information:

    - The **Inventory value quantity** value is *14* (= 10 + 5 – 5 + 5 – 1).
    - The **Inventory value** value is *1,283.33* (= 1,000 + 375 – 458.33 + 458.33 – 91.67).
    - The **Average unit cost** value is *91.67*.
    - The **On-hand value** value and the **Amount** value in each period bucket are calculated by using the **Average unit cost** value.

- The report determines the on-hand quantity for each period bucket by summarizing the total received inventory quantity for each period bucket. It then applies the first in, first out (FIFO) principle to deduct the total issued quantity, regardless of the inventory model that the items use.

If you run the same report again, but this time you set both the **Site** and **Warehouse** fields to *View*, the new report will resemble the following example.

| Item number | Site | Warehouse | On-hand quantity | On-hand value | Inventory value quantity | Inventory value | Average unit cost | P1:Quantity (5/8/2020 - 5/1/2020) | P1:Amount (5/8/2020 - 5/1/2020) | P2:Quantity (4/30/2020 - 4/1/2020) | P2:Amount (4/30/2020 - 4/1/2020) | P3:Quantity (3/31/2020 - 3/1/2020) | P3:Amount (3/31/2020 - 3/1/2020) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1000 | 1 | 11 | 10 | 916.67 | 14 | 1,283.33 | 91.67 |  |  | 5.00 | 458.33 | 5.00 | 458.33 |
| 1000 | 1 | 12 | 4 | 366.67 | 14 | 1,283.33 | 91.67 | 4.00 | 366.67 |  |  |  |  |
| 1000 | 2 |  | 10 | 2,000.00 | 10 | 2,000.00 | 200.00 |  |  |  |  | 10.00 | 2,000.00 |
| **1000 Totals** |  |  | **24.00** | **3,283.33** |  |  |  | **4.00** | **366.67** | **5.00** | **458.33** | **15** | **2,458.33** |

This time, site 1 is split into two rows, one for warehouse 11 and one for warehouse 12. However, the **Inventory value quantity**, **Inventory value**, and **Average unit cost** values are the same, because **Warehouse** isn't a financial inventory dimension.

Additionally, notice that the quantity distribution of site 1 is different. In the first report that you ran, the system ignored the transfer order that occurred in the same site and deducted the quantity of the sales invoice from the **3/31/2020 - 3/1/2020** period bucket in site 1. However, in the new report, the system deducts the quantity of the sales invoice from the **5/8/2020 - 5/1/2020** period bucket in warehouse 12.

## Effects of inventory closing

If you run the inventory closing for May and then run the previous report again, but you set the **As of date** field to *May 31, 2020*, you will notice the following results:

- The **Inventory value** and **Average unit cost** values are updated.
- The **On-hand value** value and all the **Amount** values in every period bucket are updated accordingly.

The new report will resemble the following example.

| Item number | Site | Warehouse | On-hand quantity | On-hand value | Inventory value quantity | Inventory value | Average unit cost | P1:Quantity (5/31/2020 - 5/1/2020) | P1:Amount (5/31/2020 - 5/1/2020) | P2:Quantity (4/30/2020 - 4/1/2020) | P2:Amount (4/30/2020 - 4/1/2020) | P3:Quantity (3/31/2020 - 3/1/2020) | P3:Amount (3/31/2020 - 3/1/2020) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1000 | 1 | 11 | 10 | 910.70 | 14 | 1,275.00 | 91.07 | 0.00 |  | 5.00 | 455.36 | 5.00 | 455.36 |
| 1000 | 1 | 12 | 4 | 364.29 | 14 | 1,275.00 | 91.07 | 4.00 | 364.29 |  |  |  |  |
| 1000 | 2 |  | 10 | 2,000.00 | 10 | 2,000.00 | 200.00 |  |  |  |  | 10.00 | 2,000.00 |
| **1000 Totals** |  |  | **24.00** | **3,275.00** |  |  |  | **4.00** | **364.29** | **5.00** | **455.36** | **15** | **2,455.36** |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
