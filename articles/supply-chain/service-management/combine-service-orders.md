---
# required metadata

title: Combine service orders  
description: You can combine service orders.
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

# Combine service orders   

[!include [banner](../includes/banner.md)]


When you create service order lines automatically in the **Service agreements** form, you can choose one of the following options to specify how you want to group them:

  - **By service agreement**

  - **By service task**

  - **By employee**

  - **By service object**

## Example

You create a service agreement that has a start date on 03-31-2007. In the **Combine service orders** field, you specify **By service object**. You then create the following service agreement lines:

<table>
<colgroup>
<col />
<col />
<col />
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Agreement line number</p></th>
<th><p>Transaction type</p></th>
<th><p>Description</p></th>
<th><p>Interval</p></th>
<th><p>Service object</p></th>
<th><p>Start date</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p><strong>Hour</strong></p></td>
<td><p>SAL1</p></td>
<td><p>Weekly</p></td>
<td><p>X-1</p></td>
<td><p>04-01-2007</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p><strong>Hour</strong></p></td>
<td><p>SAL2</p></td>
<td><p>Biweekly</p></td>
<td><p>X-2</p></td>
<td><p>04-01-2007</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p><strong>Hour</strong></p></td>
<td><p>SAL3</p></td>
<td><p>Weekly</p></td>
<td><p>X-2</p></td>
<td><p>04-01-2007</p></td>
</tr>
</tbody>
</table>


You do not specify time windows for any of the service agreement lines. Therefore, the service order lines will not move from the calculated day on which they fall.

Next, you generate service order lines from the **Create service orders** form from 04-01-2007 until 04-30-2007.

In total, 10 service orders are created. Because the combined setting that you selected was **By service object**, all service orders that are created have only service order lines with one specific service object. Service order lines that are generated from the service agreement and have the same service date and object are combined on the same service order.


> [!NOTE]
> <P>In this example, the calendar that is specified in the <STRONG>Service management parameters</STRONG> form has no closed days.</P>



Additional grouping of service order lines into service orders occurs according to any time window that you specify on the service agreement lines.

## See also

[Create service orders automatically](create-service-orders-automatically.md)

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]