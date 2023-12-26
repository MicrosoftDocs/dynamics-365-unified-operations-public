---
# required metadata

title: Inventory object values
description: This article provides information about how the values of an inventory object are calculated. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventCostOnhandItem
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 56a7c8ba-bf4a-4b1d-918d-56bb96926c4f
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Inventory object values

[!include [banner](../includes/banner.md)]

This article provides information about how the values of an inventory object are calculated. 

A new functionality that is named **physical quantity** lets you see the values of a specific inventory object. 

A cost object represents the entity level where inventory accounting is performed. For more information about cost objects, see [Cost objects](cost-object.md). 

To see the values of a specific inventory object, click **Physical quantity** on the **Cost object** page. Here is how the value of an inventory object is calculated: 

Inventory object.Value = Cost object.Average unit cost × Inventory object.Quantity 

The following example shows how the values of an inventory object and a cost object are calculated. Two product receipt events are registered on item A:

-   Product receipt 1: Quantity = 100 pcs., Amount = $1,000.00, Site = 1, Warehouse =11, Batch No. = B1
-   Product receipt 2: Quantity = 50 pcs., Amount = $800.00, Site = 1, Warehouse =11, Batch No. = B2

The following table shows the calculation result for a cost object. You can view the result on the **Cost object** page.

<table>
<colgroup>
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
</colgroup>
<thead>
<tr class="header">
<th>Object type</th>
<th>Item number</th>
<th>Site</th>
<th>Quantity</th>
<th>Inventory unit</th>
<th>Value</th>
<th>Average unit cost</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Cost object</td>
<td>A</td>
<td>1</td>
<td>150</td>
<td>Pcs.</td>
<td><p>$1800.00</p></td>
<td><p>$12.00</p></td>
</tr>
</tbody>
</table>

The following table shows the calculation result for an inventory object. You can view the result by clicking **Physical quantity** on the **Cost object** page.

<table>
<colgroup>
<col width="11%" />
<col width="11%" />
<col width="11%" />
<col width="11%" />
<col width="11%" />
<col width="11%" />
<col width="11%" />
<col width="11%" />
<col width="11%" />
</colgroup>
<thead>
<tr class="header">
<th>Object type</th>
<th>Item number</th>
<th>Site</th>
<th>Warehouse</th>
<th>Batch No.</th>
<th>Quantity</th>
<th>Inventory unit</th>
<th>Value</th>
<th>Average unit cost</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Inventory object</td>
<td>A</td>
<td>1</td>
<td>11</td>
<td>B1</td>
<td>100</td>
<td>Pcs.</td>
<td><p>$1200.00</p></td>
<td><p>$12.00</p></td>
</tr>
<tr class="even">
<td>Inventory object</td>
<td>A</td>
<td>1</td>
<td>11</td>
<td>B2</td>
<td>50</td>
<td>Pcs.</td>
<td><p>$600.00</p></td>
<td><p>$12.00</p></td>
</tr>
</tbody>
</table>



## Additional resources

[Cost objects](cost-object.md)

[Cost entries](cost-entries.md)

[What's new and changed](../../fin-ops-core/fin-ops/get-started/whats-new-changed.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]