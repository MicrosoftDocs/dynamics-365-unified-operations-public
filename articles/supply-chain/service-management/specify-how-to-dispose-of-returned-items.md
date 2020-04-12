---
# required metadata

title: Specify how to dispose of returned items 
description: Specify how to dispose of returned items.
author: ShylaThompson
manager: tfehr
ms.date: 05/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventQuarantineOrder
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ShylaThompson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Specify how to dispose of returned items 

[!include [banner](../includes/banner.md)]


When you handle a return order, you must specify a reason return code to identify why the product is being returned. You must also specify a disposition code and a disposition action to determine what should be done with the returned product itself.

A disposition code can be applied when you create the return order, register item arrival or packing-slip update an item arrival, and end a quarantine order.

You can define any disposition codes that you need in order to support the business processes. The following table provides a set of typically used codes to assign return-item disposition.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Disposition type</p></th>
<th><p>Common code</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Disposal</p></td>
<td><p>SC</p></td>
<td><p>Scrap/Destroy</p></td>
</tr>
<tr class="even">
<td><p>Disposal</p></td>
<td><p>DC</p></td>
<td><p>Donate to Charity</p></td>
</tr>
<tr class="odd">
<td><p>Disposal</p></td>
<td><p>TD</p></td>
<td><p>Third-Party Disposal</p></td>
</tr>
<tr class="even">
<td><p>Disposal</p></td>
<td><p>SL</p></td>
<td><p>Salvage</p></td>
</tr>
<tr class="odd">
<td><p>Disposal</p></td>
<td><p>TS</p></td>
<td><p>Third-Party Sale (Secondary Markets)</p></td>
</tr>
<tr class="even">
<td><p>Repair/Modify</p></td>
<td><p>RW</p></td>
<td><p>Rework</p></td>
</tr>
<tr class="odd">
<td><p>Repair/Modify</p></td>
<td><p>RF</p></td>
<td><p>Remanufacture/Refurbish</p></td>
</tr>
<tr class="even">
<td><p>Repair/Modify</p></td>
<td><p>MD</p></td>
<td><p>Modify</p></td>
</tr>
<tr class="odd">
<td><p>Repair/Modify</p></td>
<td><p>RP</p></td>
<td><p>Repair</p></td>
</tr>
<tr class="even">
<td><p>Repair/Modify</p></td>
<td><p>RV</p></td>
<td><p>Return to Vendor</p></td>
</tr>
<tr class="odd">
<td><p>Other</p></td>
<td><p>AI</p></td>
<td><p>Use as is</p></td>
</tr>
<tr class="even">
<td><p>Other</p></td>
<td><p>RS</p></td>
<td><p>Resale</p></td>
</tr>
<tr class="odd">
<td><p>Other</p></td>
<td><p>EX</p></td>
<td><p>Exchange</p></td>
</tr>
<tr class="even">
<td><p>Other</p></td>
<td><p>MS</p></td>
<td><p>Miscellaneous</p></td>
</tr>
</tbody>
</table>


For each disposition code that you define, you must select a disposition action. The disposition action determines the physical and financial implications of the disposition codes. For example, the disposition action determines the physical handling of the returned item, the financial effect of the returned item, and if a replacement item must be sent to the customer. You can define an unlimited number of disposition codes according to your business needs, but there are only six predefined disposition actions that you can select from. The following table provides the disposition actions and their definitions.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Disposition action</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Credit</strong></p></td>
<td><p>Return the item to inventory and credit the customer.</p></td>
</tr>
<tr class="even">
<td><p><strong>Credit only</strong></p></td>
<td><p>Credit the customer without requiring or expecting the item to be returned.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Scrap</strong></p></td>
<td><p>Scrap the item and credit the customer.</p></td>
</tr>
<tr class="even">
<td><p><strong>Replace and credit</strong></p></td>
<td><p>Return the item to inventory, create a replacement order, and credit the customer.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Replace and scrap</strong></p></td>
<td><p>Scrap the item, create a replacement order, and credit the customer.</p></td>
</tr>
<tr class="even">
<td><p><strong>Return to customer</strong></p></td>
<td><p>Reject the returned item and return it to the customer.</p></td>
</tr>
</tbody>
</table>


## Select a disposition code for a quarantine order

1.  Click **Inventory management** \> **Periodic** \> **Quality management** \> **Quarantine orders**.

2.  For an existing quarantine order, select an action from the **Disposition code** field on the **Overview** tab.



## See also

[Quarantine order (form)](https://technet.microsoft.com/library/aa554073(v=ax.60))

[Disposition codes (form)](https://technet.microsoft.com/library/hh597113\(v=ax.60\))

  


