---
# required metadata

title: Inventory aging report examples and logic
description: This topic presents some examples that illustrate how to interpret the results of an inventory aging report.
author: RichardLuan
manager: AnnBe
ms.date: 5/29/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: CostAdminWorkspace, CostAnalysisWorkspace
# ROBOTS:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: riluan
ms.search.validFrom: 2020-5-29
ms.dyn365.ops.version: 

---

# Inventory aging report examples and logic

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)] <!-- KFM: Is this really preview functionality? -->

This topic presents some examples that illustrate how to interpret the results of an **Inventory aging** report, which categorizes on-hand quantity and inventory values for a selected item or item group into several period buckets. This topic also illustrates the internal logic of the report.

This topic presents an example that illustrates results as they would be presented by a standard inventory aging report. However, we recommend that you normally use the [Inventory aging report storage](inventory-aging-report-storage.md) version of this report, especially when you have a large number of items and warehouses to process. Inventory aging report storage saves each report that you generate, displays results as an interactive page and a chart, and lets you export any saved report.

## Sample data used in these examples

To illustrate how this report works, we will present examples based on the example inventory transaction data described in this section.

### Storage dimension setup

The example system contains the following **Storage dimension** setup .

| Name      | Active | Physical inventory | Financial inventory |
|-----------|--------|--------------------|---------------------|
| Site      | Yes    | Yes                | Yes                 |
| Warehouse | Yes    | Yes                | No                  |

### Inventory model

For this example system, the **Inventory model** for the released products is *FIFO*, and  the **Cost price** setting for the inventory model is *Include physical value*.

### Inventory transactions

The example system contains the following inventory transactions for a released product with **Item number** *1000*. <!-- KFM: I assumed this item number. Please confirm.  -->

| Reference      | Site | Warehouse | Receipt   | Issue | Physical date | Financial date | Quantity | Cost amount | Physical cost amount |
|----------------|------|-----------|-----------|-------|---------------|----------------|----------|-------------|----------------------|
| Purchase order | 1    | 11        | Purchased |       | 15-Mar        | 15-Mar         | 10       | 1,000     | 1,000              |
| Purchase order | 2    | 21        | Purchased |       | 15-Mar        | 15-Mar         | 10       | 2,000     | 2,000              |
| Purchase order | 1    | 11        | Received  |       | 15-Apr        |                | 5        |             | 375                |
| Transfer order | 1    | 11        |           | Sold  | 2-May         | 2-May          | -5       |  -458.33  | -458.33            |
| Transfer order | 1    | 12        | Purchased |       | 2-May         | 2-May          | 5        |  458.33   |  458.33            |
| Sales order    | 1    | 12        |           | Sold  | 3-May         | 3-May          | -1       |  -91.67   |  -91.67            |

## How quantities and amounts in each bucket are calculated

Using the sample data presented previously, you could create an inventory aging report using the following settings:

- **As of date** - *9 May*
- **Site** - *View*
- **Warehouse** to *No*
- **Item number** - *Total*
- **Aging period** - Is set to generate monthly buckets.

The content of this report could appear as shown in the following example.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-1wig{font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-7btt{border-color:inherit;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-amwm{font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-fymr{border-color:inherit;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-7btt" rowspan="2">Item number</th>
    <th class="tg-7btt" rowspan="2">Site</th>
    <th class="tg-7btt" rowspan="2">On-hand quantity</th>
    <th class="tg-7btt" rowspan="2">On-hand value</th>
    <th class="tg-7btt" rowspan="2">Inventory value quantity</th>
    <th class="tg-7btt" rowspan="2">Inventory value</th>
    <th class="tg-7btt" rowspan="2">Average unit cost</th>
    <th class="tg-7btt" colspan="2">5/8/2020 - 5/1/2020</th>
    <th class="tg-7btt" colspan="2"><span style="font-style:normal">4/30/2020 - 4/1/2020 </span><br></th>
    <th class="tg-amwm" colspan="2">3/31/2020 - 3/1/2020</th>
  </tr>
  <tr>
    <td class="tg-fymr">P1:Quantity</td>
    <td class="tg-fymr">P1:Amount</td>
    <td class="tg-fymr">P2:Quantity</td>
    <td class="tg-1wig">P2:Amount</td>
    <td class="tg-1wig">P3:Quantity</td>
    <td class="tg-1wig">P3:Amount</td>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">1000</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">14</td>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal">1,283.33</span></td>
    <td class="tg-0pky">14</td>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal">1,283.33</span><br></td>
    <td class="tg-0pky">91.67</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">5.00</td>
    <td class="tg-0lax">458.33</td>
    <td class="tg-0lax">9.00</td>
    <td class="tg-0lax">825.00</td>
  </tr>
  <tr>
    <td class="tg-0pky">1000</td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">10</td>
    <td class="tg-0pky">2,000.00</td>
    <td class="tg-0pky">10</td>
    <td class="tg-0pky">2,000.00</td>
    <td class="tg-0pky">200.00</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax">10.00</td>
    <td class="tg-0lax">2,000.00</td>
  </tr>
  <tr>
    <td class="tg-1wig"><span style="font-weight:bold">1000 Totals</span></td>
    <td class="tg-1wig"></td>
    <td class="tg-1wig">24.00</td>
    <td class="tg-1wig">3,283.33</td>
    <td class="tg-1wig"></td>
    <td class="tg-1wig"></td>
    <td class="tg-1wig"></td>
    <td class="tg-1wig"></td>
    <td class="tg-1wig"></td>
    <td class="tg-1wig">5.00</td>
    <td class="tg-1wig">458.33</td>
    <td class="tg-1wig">19</td>
    <td class="tg-1wig">2,825.00</td>
  </tr>
</tbody>
</table>

Note the following in the example report:

- The **Inventory value quantity**, **Inventory value** and **Average unit cost** shown in the report are values for the financial inventory dimension (which is **Site** in this case).
- Taking **Site 1** as an example:
  - The **Inventory value quantity** is 14 (10 + 5 - 5 + 5 - 1)
  - The **Inventory value** is 1,283.33 (1,000 + 375 - 458.33 + 458.33 - 91.67)
  - The **Average unit cost** is 91.67.
  - The **On-hand value** and the **Amount** in each period bucket are calculated by **Average unit cost**.
- The report determines the on-hand quantity for each period bucket by summarizing the total received inventory quantity for each period buckets, then applies the FIFO (First In First Out) principle to deduct the total issued quantity regardless of which inventory model the items use.

If you were to run the same report again, but this time with both **Site** and **Warehouse** to *View*, the new report could appear as shown in the following example.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-7btt{border-color:inherit;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-fymr{border-color:inherit;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-7btt" rowspan="2">Item number</th>
    <th class="tg-7btt" rowspan="2">Site</th>
    <th class="tg-fymr" rowspan="2">Warehouse</th>
    <th class="tg-7btt" rowspan="2">On-hand quantity</th>
    <th class="tg-7btt" rowspan="2">On-hand value</th>
    <th class="tg-7btt" rowspan="2">Inventory value quantity</th>
    <th class="tg-7btt" rowspan="2">Inventory value</th>
    <th class="tg-7btt" rowspan="2">Average unit cost</th>
    <th class="tg-7btt" colspan="2">5/8/2020 - 5/1/2020</th>
    <th class="tg-7btt" colspan="2"><span style="font-style:normal">4/30/2020 - 4/1/2020 </span><br></th>
    <th class="tg-7btt" colspan="2">3/31/2020 - 3/1/2020</th>
  </tr>
  <tr>
    <td class="tg-fymr">P1:Quantity</td>
    <td class="tg-fymr">P1:Amount</td>
    <td class="tg-fymr">P2:Quantity</td>
    <td class="tg-fymr">P2:Amount</td>
    <td class="tg-fymr">P3:Quantity</td>
    <td class="tg-fymr">P3:Amount</td>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">1000</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">11</td>
    <td class="tg-0pky">10</td>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal">916.67</span></td>
    <td class="tg-0pky">14</td>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal">1,283.33</span><br></td>
    <td class="tg-0pky">91.67</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">5.00</td>
    <td class="tg-0pky">458.33</td>
    <td class="tg-0pky">5.00</td>
    <td class="tg-0pky">458.33</td>
  </tr>
  <tr>
    <td class="tg-0pky">1000</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">12</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">366.67</td>
    <td class="tg-0pky">14</td>
    <td class="tg-0pky">1,283.33</td>
    <td class="tg-0pky">91.67</td>
    <td class="tg-0pky">4.00</td>
    <td class="tg-0pky">366.67</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">1000</td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">10</td>
    <td class="tg-0pky">2,000.00</td>
    <td class="tg-0pky">10</td>
    <td class="tg-0pky">2,000.00</td>
    <td class="tg-0pky">200.00</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">10.00</td>
    <td class="tg-0pky">2,000.00</td>
  </tr>
  <tr>
    <td class="tg-fymr"><span style="font-weight:bold">1000 Totals</span></td>
    <td class="tg-fymr"></td>
    <td class="tg-0pky"></td>
    <td class="tg-fymr">24.00</td>
    <td class="tg-fymr">3,283.33</td>
    <td class="tg-fymr"></td>
    <td class="tg-fymr"></td>
    <td class="tg-fymr"></td>
    <td class="tg-fymr">4.00</td>
    <td class="tg-fymr">366.67</td>
    <td class="tg-fymr">5.00</td>
    <td class="tg-fymr">458.33</td>
    <td class="tg-fymr">15</td>
    <td class="tg-fymr">2,458.33</td>
  </tr>
</tbody>
</table>

This time, **Site 1** is split into two rows (one each for warehouse **11** and **12**). However **Inventory value quantity**, **Inventory value** and **Average unit cost** are the same, because warehouse isn't a financial inventory dimension. Note that the quantity distribution of **Site 1** is also different. In the first report run, the system ignores the transfer order that happens within the same site, and deducts the quantity of the sales invoice from the bucket **3/31/2020 - 3/1/2020** in **Site 1**. In the second report run, the system deducts the quantity in the sales invoice from the bucket **5/8/2020 - 5/1/2020** in **Warehouse 12**.

## Effects of inventory closing

If you were to run the inventory closing for May and then run the previous report again with **As of date** set to *5/31/2020*, you would notice the following results:

- **Inventory value** and **Average unit cost** will be updated
- **On-hand value** and all the other **Amount** values in each bucket will also updated accordingly.

The new report could appear as shown in the following example.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-7btt{border-color:inherit;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-fymr{border-color:inherit;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-7btt" rowspan="2">Item number</th>
    <th class="tg-7btt" rowspan="2">Site</th>
    <th class="tg-fymr" rowspan="2">Warehouse</th>
    <th class="tg-7btt" rowspan="2">On-hand quantity</th>
    <th class="tg-7btt" rowspan="2">On-hand value</th>
    <th class="tg-7btt" rowspan="2">Inventory value quantity</th>
    <th class="tg-7btt" rowspan="2">Inventory value</th>
    <th class="tg-7btt" rowspan="2">Average unit cost</th>
    <th class="tg-7btt" colspan="2">5/31/2020 - 5/1/2020</th>
    <th class="tg-7btt" colspan="2"><span style="font-style:normal">4/30/2020 - 4/1/2020 </span><br></th>
    <th class="tg-7btt" colspan="2">3/31/2020 - 3/1/2020</th>
  </tr>
  <tr>
    <td class="tg-fymr">P1:Quantity</td>
    <td class="tg-fymr">P1:Amount</td>
    <td class="tg-fymr">P2:Quantity</td>
    <td class="tg-fymr">P2:Amount</td>
    <td class="tg-fymr">P3:Quantity</td>
    <td class="tg-fymr">P3:Amount</td>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">1000</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">11</td>
    <td class="tg-0pky">10</td>
    <td class="tg-0pky">910.70</td>
    <td class="tg-0pky">14</td>
    <td class="tg-0pky">1,275.00</td>
    <td class="tg-0pky">91.07</td>
    <td class="tg-0pky">0.00</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">5.00</td>
    <td class="tg-0pky">455.36</td>
    <td class="tg-0pky">5.00</td>
    <td class="tg-0pky">455.36</td>
  </tr>
  <tr>
    <td class="tg-0pky">1000</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">12</td>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">364.29</td>
    <td class="tg-0pky">14</td>
    <td class="tg-0pky">1,275.00</td>
    <td class="tg-0pky">91.07</td>
    <td class="tg-0pky">4.00</td>
    <td class="tg-0pky">364.29</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">1000</td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">10</td>
    <td class="tg-0pky">2,000.00</td>
    <td class="tg-0pky">10</td>
    <td class="tg-0pky">2,000.00</td>
    <td class="tg-0pky">200.00</td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">10.00</td>
    <td class="tg-0pky">2,000.00</td>
  </tr>
  <tr>
    <td class="tg-fymr">1000 Totals</td>
    <td class="tg-fymr"></td>
    <td class="tg-0pky"></td>
    <td class="tg-fymr">24.00</td>
    <td class="tg-fymr">3,275.00</td>
    <td class="tg-fymr"></td>
    <td class="tg-fymr"></td>
    <td class="tg-fymr"></td>
    <td class="tg-fymr">4.00</td>
    <td class="tg-fymr">364.29</td>
    <td class="tg-fymr">5.00</td>
    <td class="tg-fymr">455.36</td>
    <td class="tg-fymr">15</td>
    <td class="tg-fymr">2,455.36</td>
  </tr>
</tbody>
</table>