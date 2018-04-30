---
title: Service status and progress field interaction
TOCTitle: Service status and progress field interaction
ms:assetid: 1a0773eb-d703-43fa-810c-7b2b7232607b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa499092(v=AX.60)
ms:contentKeyID: 36056117
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg231005(v=ax.60)/toc.json
---

# Service status and progress field interaction 




In the **Service orders** form, the **Progress** field on the service order header reflects the status of the whole service order, and the **Status** reports the status of individual service order lines.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Progress</p></th>
<th><p>Line 1 Status</p></th>
<th><p>Line 2 Status</p></th>
<th><p>Line 3 Status</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>In process</strong></p></td>
<td><p><strong>Created</strong></p></td>
<td><p><strong>Created</strong></p></td>
<td><p><strong>Created</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>In process</strong></p></td>
<td><p><strong>Canceled</strong></p></td>
<td><p><strong>Created</strong></p></td>
<td><p><strong>Created</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>In process</strong></p></td>
<td><p><strong>Created</strong></p></td>
<td><p><strong>Canceled</strong></p></td>
<td><p><strong>Posted</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Canceled</strong></p></td>
<td><p><strong>Canceled</strong></p></td>
<td><p><strong>Canceled</strong></p></td>
<td><p><strong>Canceled</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Posted</strong></p></td>
<td><p><strong>Posted</strong></p></td>
<td><p><strong>Posted</strong></p></td>
<td><p><strong>Posted</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Posted</strong></p></td>
<td><p><strong>Posted</strong></p></td>
<td><p><strong>Canceled</strong></p></td>
<td><p><strong>Canceled</strong></p></td>
</tr>
</tbody>
</table>


The progress of a service order is in process if all lines have the status **Created**; it is still in process if some of the lines have a status of **Canceled** or **Posted**.

If all lines in a service order are marked as **Posted**, the progress of the status order is **Posted**. If some lines are **Posted** and some are **Canceled**, the progress is still **Posted**.

  


