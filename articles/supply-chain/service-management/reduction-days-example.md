---
title: Reduction days example
TOCTitle: Reduction days example
ms:assetid: af9ba3d4-f1d1-4763-8d77-68f549474c30
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa498637(v=AX.60)
ms:contentKeyID: 36058957
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg232212(v=ax.60)/toc.json
---

# Reduction days example 




You have created a subscription transaction for a customer's maintenance subscription, as described in the following table.

<table>
<colgroup>
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th><p>From date</p></th>
<th><p>To date</p></th>
<th><p>Subscription</p></th>
<th><p>Subscription type</p></th>
<th><p>Project</p></th>
<th><p>Category</p></th>
<th><p>Sales currency</p></th>
<th><p>Sales price</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>March 01, 2011</p></td>
<td><p>March 31, 2011</p></td>
<td><p>NR-2</p></td>
<td><p><strong>Regular</strong></p></td>
<td><p>9013</p></td>
<td><p>SubCat2</p></td>
<td><p>EUR</p></td>
<td><p>200.00</p></td>
</tr>
</tbody>
</table>


The customer reports that it does not need service coverage for two days (March 10 and March 11). You agree to reduce the subscription by these two days.

You create a new transaction of the **Reduction days** type, as described in the following table.

<table>
<colgroup>
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th><p>From date</p></th>
<th><p>To date</p></th>
<th><p>Subscription</p></th>
<th><p>Subscription type</p></th>
<th><p>Project</p></th>
<th><p>Category</p></th>
<th><p>Sales currency</p></th>
<th><p>Sales price</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>March 10, 2011</p></td>
<td><p>March 11, 2011</p></td>
<td><p>NR-2</p></td>
<td><p><strong>Reduction days</strong></p></td>
<td><p>9013</p></td>
<td><p>SubCat2</p></td>
<td><p>EUR</p></td>
<td><p>-12.90</p></td>
</tr>
</tbody>
</table>


When the transactions for March 2011 are invoiced, the sales price of EUR 200 is reduced by EUR 12.90. The chargeable amount for the subscription transaction is therefore EUR 187.10, and two transactions are invoiced at a total of EUR 187.10.

## See also

[Reduce the days on subscription fees](reduce-the-days-on-subscription-fees.md)

  


