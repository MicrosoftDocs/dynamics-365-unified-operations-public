---
title: Service status and progress field interaction 
description: On the Service orders page, the Progress field on the header reflects the status of the whole service order. Learn about service status.
author: Henrikan
ms.author: henrikan
ms.topic: article
ms.date: 05/01/2018
ms.custom:
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable
---


# Service status and progress field interaction

[!include [banner](../includes/banner.md)]

On the **Service orders** page, the **Progress** field on the service order header reflects the status of the whole service order, and the **Status** reports the status of individual service order lines.

<table>
<colgroup>
<col />
<col />
<col />
<col />
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

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
