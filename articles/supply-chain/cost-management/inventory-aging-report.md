---
# required metadata

title: Inventory aging report examples and logic
description: This topic presents some examples that show how to interpret the results of an Inventory aging report.
author: JennySong-SH
ms.date: 5/29/2020
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventAgingStorage, InventAgingStorageChart, InventAgingStorageDetails
# ROBOTS:
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2020-5-29
ms.dyn365.ops.version: 

---

# Inventory aging report examples and logic

[!include [banner](../includes/banner.md)]

This topic presents some examples that show how to interpret the results of an **Inventory aging** report. This report categorizes on-hand quantity and inventory values for a selected item or item group into several period buckets. This topic also shows the internal logic of the report.

The examples in this topic show results that are presented on a standard **Inventory aging** report. However, in general, we recommend that you use the [Inventory aging report storage](inventory-aging-report-storage.md) version of this report, especially when you have many items and warehouses that must be processed. Inventory aging report storage saves each report that you generate, shows the results as an interactive page and a chart, and lets you export any saved report.

## Sample data that is used in these examples

The examples in this topic are based on the sample inventory transaction data that is described in this section.

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

| Reference      | Site | Warehouse | Receipt   | Issue | Physical date | Financial date | Quantity | Cost amount | Physical cost amount |
|----------------|------|-----------|-----------|-------|---------------|----------------|----------|-------------|----------------------|
| Purchase order | 1    | 11        | Purchased |       | March 15      | March 15       | 10       | 1,000       | 1,000                |
| Purchase order | 2    | 21        | Purchased |       | March 15      | March 15       | 10       | 2,000       | 2,000                |
| Purchase order | 1    | 11        | Received  |       | April 15      |                | 5        |             | 375                  |
| Transfer order | 1    | 11        |           | Sold  | May 2         | May 2          | -5       | -458.33     | -458.33              |
| Transfer order | 1    | 12        | Purchased |       | May 2         | May 2          | 5        | 458.33      | 458.33               |
| Sales order    | 1    | 12        |           | Sold  | May 3         | May 3          | -1       | -91.67      | -91.67               |

## How quantities and amounts in each period bucket are calculated

By using the sample data that is described in the previous sections, you can run an **Inventory aging** report that has the following settings:

- **As of date:** *May 9, 2020*
- **Site:** *View*
- **Warehouse:** *No*
- **Item number:** *Total*
- **Aging period:** Set this field to generate monthly buckets.

In this case, the content of the report that is generated will resemble the following example.

<table>
<thead>
<tr>
    <th rowspan="2">Item number</th>
    <th rowspan="2">Site</th>
    <th rowspan="2">On-hand quantity</th>
    <th rowspan="2">On-hand value</th>
    <th rowspan="2">Inventory value quantity</th>
    <th rowspan="2">Inventory value</th>
    <th rowspan="2">Average unit cost</th>
    <th colspan="2">5/8/2020 - 5/1/2020</th>
    <th colspan="2">4/30/2020 - 4/1/2020</th>
    <th colspan="2">3/31/2020 - 3/1/2020</th>
</tr>
<tr>
    <th>P1:Quantity</th>
    <th>P1:Amount</th>
    <th>P2:Quantity</th>
    <th>P2:Amount</th>
    <th>P3:Quantity</th>
    <th>P3:Amount</th>
</tr>
</thead>
<tbody>
<tr>
    <td>1000</td>
    <td>1</td>
    <td>14</td>
    <td>1,283.33</td>
    <td>14</td>
    <td>1,283.33</td>
    <td>91.67</td>
    <td></td>
    <td></td>
    <td>5.00</td>
    <td>458.33</td>
    <td>9.00</td>
    <td>825.00</td>
</tr>
<tr>
    <td>1000</td>
    <td>2</td>
    <td>10</td>
    <td>2,000.00</td>
    <td>10</td>
    <td>2,000.00</td>
    <td>200.00</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td>10.00</td>
    <td>2,000.00</td>
</tr>
</tbody>
<tfoot>
<tr>
    <td><strong>1000 Totals</strong></td>
    <td></td>
    <td><strong>24.00</strong></td>
    <td><strong>3,283.33</strong></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><strong>5.00</strong></td>
    <td><strong>458.33</strong></td>
    <td><strong>19</strong></td>
    <td><strong>2,825.00</strong></td>
</tr>
</tfoot>
</table>

Note the following details in this example report:

- The **Inventory value quantity**, **Inventory value**, and **Average unit cost** values that are shown on the report are values for the financial inventory dimension (**Site**, in this case).

    For example, for site 1, the report shows the following information:

    - The **Inventory value quantity** value is *14* (= 10 + 5 – 5 + 5 – 1).
    - The **Inventory value** value is *1,283.33* (= 1,000 + 375 – 458.33 + 458.33 – 91.67).
    - The **Average unit cost** value is *91.67*.
    - The **On-hand value** value and the **Amount** value in each period bucket are calculated by using the **Average unit cost** value.

- The report determines the on-hand quantity for each period bucket by summarizing the total received inventory quantity for each period bucket. It then applies the first in, first out (FIFO) principle to deduct the total issued quantity, regardless of the inventory model that the items use.

If you run the same report again, but this time you set both the **Site** and **Warehouse** fields to *View*, the new report will resemble the following example.

<table>
<thead>
<tr>
    <th rowspan="2">Item number</th>
    <th rowspan="2">Site</th>
    <th rowspan="2">Warehouse</th>
    <th rowspan="2">On-hand quantity</th>
    <th rowspan="2">On-hand value</th>
    <th rowspan="2">Inventory value quantity</th>
    <th rowspan="2">Inventory value</th>
    <th rowspan="2">Average unit cost</th>
    <th colspan="2">5/8/2020 - 5/1/2020</th>
    <th colspan="2">4/30/2020 - 4/1/2020</th>
    <th colspan="2">3/31/2020 - 3/1/2020</th>
</tr>
<tr>
    <th>P1:Quantity</th>
    <th>P1:Amount</th>
    <th>P2:Quantity</th>
    <th>P2:Amount</th>
    <th>P3:Quantity</th>
    <th>P3:Amount</th>
</tr>
</thead>
<tbody>
<tr>
    <td>1000</td>
    <td>1</td>
    <td>11</td>
    <td>10</td>
    <td>916.67</td>
    <td>14</td>
    <td>1,283.33</td>
    <td>91.67</td>
    <td></td>
    <td></td>
    <td>5.00</td>
    <td>458.33</td>
    <td>5.00</td>
    <td>458.33</td>
</tr>
<tr>
    <td>1000</td>
    <td>1</td>
    <td>12</td>
    <td>4</td>
    <td>366.67</td>
    <td>14</td>
    <td>1,283.33</td>
    <td>91.67</td>
    <td>4.00</td>
    <td>366.67</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
</tr>
<tr>
    <td>1000</td>
    <td>2</td>
    <td></td>
    <td>10</td>
    <td>2,000.00</td>
    <td>10</td>
    <td>2,000.00</td>
    <td>200.00</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td>10.00</td>
    <td>2,000.00</td>
</tr>
</tbody>
<tfoot>
<tr>
    <td><strong>1000 Totals</strong></td>
    <td></td>
    <td></td>
    <td><strong>24.00</strong></td>
    <td><strong>3,283.33</strong></td>
    <td></td>
    <td></td>
    <td></td>
    <td><strong>4.00</strong></td>
    <td><strong>366.67</strong></td>
    <td><strong>5.00</strong></td>
    <td><strong>458.33</strong></td>
    <td><strong>15</strong></td>
    <td><strong>2,458.33</strong></td>
</tr>
</tfoot>
</table>

This time, site 1 is split into two rows, one for warehouse 11 and one for warehouse 12. However, the **Inventory value quantity**, **Inventory value**, and **Average unit cost** values are the same, because **Warehouse** isn't a financial inventory dimension.

Additionally, notice that the quantity distribution of site 1 is different. In the first report that you ran, the system ignored the transfer order that occurred in the same site and deducted the quantity of the sales invoice from the **3/31/2020 - 3/1/2020** period bucket in site 1. However, in the new report, the system deducts the quantity of the sales invoice from the **5/8/2020 - 5/1/2020** period bucket in warehouse 12.

## Effects of inventory closing

If you run the inventory closing for May and then run the previous report again, but you set the **As of date** field to *May 31, 2020*, you will notice the following results:

- The **Inventory value** and **Average unit cost** values are updated.
- The **On-hand value** value and all the **Amount** values in every period bucket are updated accordingly.

The new report will resemble the following example.

<table>
<thead>
<tr>
    <th rowspan="2">Item number</th>
    <th rowspan="2">Site</th>
    <th rowspan="2">Warehouse</th>
    <th rowspan="2">On-hand quantity</th>
    <th rowspan="2">On-hand value</th>
    <th rowspan="2">Inventory value quantity</th>
    <th rowspan="2">Inventory value</th>
    <th rowspan="2">Average unit cost</th>
    <th colspan="2">5/31/2020 - 5/1/2020</th>
    <th colspan="2">4/30/2020 - 4/1/2020</th>
    <th colspan="2">3/31/2020 - 3/1/2020</th>
</tr>
<tr>
    <th>P1:Quantity</th>
    <th>P1:Amount</th>
    <th>P2:Quantity</th>
    <th>P2:Amount</th>
    <th>P3:Quantity</th>
    <th>P3:Amount</th>
</tr>
</thead>
<tbody>
<tr>
    <td>1000</td>
    <td>1</td>
    <td>11</td>
    <td>10</td>
    <td>910.70</td>
    <td>14</td>
    <td>1,275.00</td>
    <td>91.07</td>
    <td>0.00</td>
    <td></td>
    <td>5.00</td>
    <td>455.36</td>
    <td>5.00</td>
    <td>455.36</td>
</tr>
<tr>
    <td>1000</td>
    <td>1</td>
    <td>12</td>
    <td>4</td>
    <td>364.29</td>
    <td>14</td>
    <td>1,275.00</td>
    <td>91.07</td>
    <td>4.00</td>
    <td>364.29</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
</tr>
<tr>
    <td>1000</td>
    <td>2</td>
    <td></td>
    <td>10</td>
    <td>2,000.00</td>
    <td>10</td>
    <td>2,000.00</td>
    <td>200.00</td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td>10.00</td>
    <td>2,000.00</td>
</tr>
</tbody>
<tfoot>
<tr>
    <td><strong>1000 Totals</strong></td>
    <td></td>
    <td></td>
    <td><strong>24.00</strong></td>
    <td><strong>3,275.00</strong></td>
    <td></td>
    <td></td>
    <td></td>
    <td><strong>4.00</strong></td>
    <td><strong>364.29</strong></td>
    <td><strong>5.00</strong></td>
    <td><strong>455.36</strong></td>
    <td><strong>15</strong></td>
    <td><strong>2,455.36</strong></td>
</tr>
</tfoot>
</table>


[!INCLUDE[footer-include](../../includes/footer-banner.md)]