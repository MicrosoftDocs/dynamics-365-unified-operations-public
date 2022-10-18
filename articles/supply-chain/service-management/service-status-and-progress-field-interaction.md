---
# required metadata

title: Service status and progress field interaction 
description: In the Service orders form, the Progress field on the header reflects the status of the whole service order, and the Status reports the status of individual service order lines.
author: sorenva
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---


# Service status and progress field interaction

[!include [banner](../includes/banner.md)]

In the **Service orders** form, the **Progress** field on the service order header reflects the status of the whole service order, and the **Status** reports the status of individual service order lines.

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
