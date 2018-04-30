---
title: About automatically creating service orders
TOCTitle: About automatically creating service orders
ms:assetid: fd26f268-b49b-47ee-9172-2e8e6b9444ec
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa500103(v=AX.60)
ms:contentKeyID: 36060100
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg231005(v=ax.60)/toc.json
f1_keywords:
- automatic
- automate
- service orders
---

# About automatically creating service orders 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

You can generate service orders that are based on a service agreement for the valid period of the service agreement.

The service orders that you generate from a service agreement are all attached to the service agreement.

Service orders are generated automatically from the following settings:

  - The service agreement interval that is set up in the service agreement lines. The service agreement interval indicates the frequency that service-order lines are created. For more information, see [About service intervals](about-service-intervals.md).

  - The period that you specify to define the service period in the **From date** and **To date** fields in the **Create service orders** form. For more information, see [Create service orders automatically](create-service-orders-automatically.md).

  - The **Combine service orders** option on the service agreement header. This option defines whether service order lines generated from a service agreement, combines service orders according to employee, service task, service object, or service agreement. For more information, see [Combine service orders](combine-service-orders.md).

  - The **Time window** option on the service agreement line. The time window defines how far a service order line can move with regard to its calculated date. For more information, see [About time windows](about-time-windows.md).


> [!NOTE]
> <P>If the day that is specified for a service order is not open in the calendar that you have selected in the <STRONG>Service management parameters</STRONG> form, a message will indicate that there is a calendar conflict. You can safely ignore the message; the service order will be created, even though the day is closed on the calendar.</P>



## Example 1

The service agreement lasts from January 1, 2012 until December 31, 2012. If the service period that you specify in the **Create service orders** form is from November 1, 2012 until February 1, 2013, service orders are created from November 1, 2012 until December 31, 2012.

## Example 2

The service agreement lasts from January 1, 2012 until December 31, 2012. Two service agreement lines are attached to the service agreement. The first service agreement line has a starting date on January 2, 2012 and an ending date on March 1, 2012. The second service agreement line has a starting date on April 1, 2012 and an ending date on December 31, 2012. You specify a period in the **Create service orders** form that is from October 1, 2012 until December 31, 2012. Therefore, service orders are generated only for the second agreement line, because the starting date and ending date of the first agreement line are before the period that you specified for the service order.

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

