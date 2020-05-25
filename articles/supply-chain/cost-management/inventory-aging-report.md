---
# required metadata

title: Inventory aging report
description: This topic describes the functionality that lets you run an Inventory aging report.
author: RichardLuan
manager: AnnBe
ms.date: 5/9/2020
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
ms.search.validFrom: 2020-5-9
ms.dyn365.ops.version: 

---

# Inventory aging report

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)] <!-- KFM: Is this really preview functionality? -->


You can run an **Inventory aging** report to categorize the on-hand quantity and inventory value for a selected item or item group into several period buckets. This topic describes the internal logic of the report. <!-- KFM: I think we need to set the scene a bit more here. It looks like we are illustrating the logic by setting up a specific example and then discussing the result. Are we using demo data, such as USMF? -->

> [!NOTE]
> We recommend that you use the [Inventory aging report storage](inventory-aging-report-storage.md), which displays the result as a form and a chart, rather than use SSRS. Especially when you have a large number of items and warehouses to process. <!-- KFM: Spell out SSRS. Also, when we try to generate teh report described here, we get a warning that it has been deprecated. Can we instead provide an example based on the new report? -->

## Inventory transactions

Create a new item with following Storage dimension setup. <!-- KFM: Give a short description of why we are doing this. -->

| Name      | Active | Physical inventory | Financial inventory |
|-----------|--------|--------------------|---------------------|
| Site      | Yes    | Yes                | Yes                 |
| Warehouse | Yes    | Yes                | No                  |

The **Inventory model** is *FIFO*, it *Include physical value* into the **COST PRICE**. <!-- KFM: I am not sure what this mens. Are these settings? -->

Create following inventory transactions on the item. <!-- KFM: Give a short description of why we are doing this. -->

| Reference      | Site | Warehouse | Receipt   | Issue | Physical date | Financial date | Quantity | Cost amount | Physical cost amount |
|----------------|------|-----------|-----------|-------|---------------|----------------|----------|-------------|----------------------|
| Purchase order | 1    | 11        | Purchased |       | 15-Mar        | 15-Mar         | 10       | $ 1,000     | $ 1,000              |
| Purchase order | 2    | 21        | Purchased |       | 15-Mar        | 15-Mar         | 10       | $ 2,000     | $ 2,000              |
| Purchase order | 1    | 11        | Received  |       | 15-Apr        |                | 5        |             | $ 375                |
| Transfer order | 1    | 11        |           | Sold  | 2-May         | 2-May          | -5       |  $ -458.33  | $ -458.33            |
| Transfer order | 1    | 12        | Purchased |       | 2-May         | 2-May          | 5        |  $ 458.33   |  $ 458.33            |
| Sales order    | 1    | 12        |           | Sold  | 3-May         | 3-May          | -1       |  $ -91.67   |  $ -91.67            |

## Run an Inventory aging report

1. Go to **Cost management \> Inquiries and reports \> Inventory accounting \- analysis reports \> Inventory aging**.

1. The **Inventory aging** pane opens. Make the following settings here: <!-- KFM:Leave all other settings at default? -->

    - **As of date** - *9 May*
    - **Site** - *View*
    - **Item number** - *Total*
    - **Aging period** - <!-- KFM: what should we specify? -->

1. Select **OK** to generate the report.

<!-- KFM: We should introduce this table. Is it what we should expect to see based on demo data and our specific settings? Or just a typical example? -->

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

The *Inventory value quantity*, *Inventory value* and *Average unit cost* shown in the report are values for the financial inventory dimension (which is *Site* in this case). Taking Site 1 as an example, note the following:

- The *Inventory value quantity* is 14 (10 + 5 - 5 + 5 - 1)
- The *Inventory value* is 1,283.33 (1,000 + 375 - 458.33 + 458.33 - 91.67)
- The *Average unit cost* is 91.67.
- The *On-hand value* and the *Amount* in each period bucket are calculated by *Average unit cost*.

> [!NOTE]
> The report determines the on-hand quantity for each period buckets by summarizing the total received inventory quantity for each period buckets, then applies the FIFO (First In First Out) principle to deduct the total issued quantity regardless of which inventory model the items use.

Run the report again, this time with both **Site** and **Warehouse** set to *View*.

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

This time, *Site 1* is split into two rows for warehouse *11* and *12*. However *Inventory value quantity*, *Inventory value* and *Average unit cost* are the same, because warehouse isn't a financial inventory dimension. Note that the quantity distribution of *Site 1* is also different. In the first report run, the system ignores the transfer order that happens within the same site, and deducts the quantity of the sales invoice from the bucket *3/31/2020 - 3/1/2020* in *Site 1*. In the second report run, the system deducts the quantity in the sales invoice from the bucket *5/8/2020 - 5/1/2020* in *Warehouse 12*. 

After run the inventory closing for May, and run the report again with *As of date: 5/31/2020*, *Inventory value* and *Average unit cost* will be updated, *On-hand value* and all the other *Amount* in each buckets are also updated accordingly. <!-- KFM: I think we may need to be a bit more explicit here. I am not sure what to do. -->

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