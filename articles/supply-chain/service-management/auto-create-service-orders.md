---
# required metadata

title: Automatically create service orders  
description: You can generate service orders that are based on a service agreement for the valid period of the service agreement.
author: ShylaThompson
manager: tfehr
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable
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

# Automatically create service orders 

[!include [banner](../includes/banner.md)]


You can generate service orders that are based on a service agreement for the valid period of the service agreement.

The service orders that you generate from a service agreement are all attached to the service agreement.

Service orders are generated automatically from the following settings:

  - The service agreement interval that is set up in the service agreement lines. The service agreement interval indicates the frequency that service-order lines are created. For more information, see [Service intervals](service-intervals.md).

  - The period that you specify to define the service period in the **From date** and **To date** fields in the **Create service orders** form. For more information, see [Create service orders automatically](create-service-orders-automatically.md).

  - The **Combine service orders** option on the service agreement header. This option defines whether service order lines generated from a service agreement, combines service orders according to employee, service task, service object, or service agreement. For more information, see [Combine service orders](combine-service-orders.md).

  - The **Time window** option on the service agreement line. The time window defines how far a service order line can move with regard to its calculated date. For more information, see [Time windows](time-windows.md).


> [!NOTE]
> <P>If the day that is specified for a service order is not open in the calendar that you have selected in the <STRONG>Service management parameters</STRONG> form, a message will indicate that there is a calendar conflict. You can safely ignore the message; the service order will be created, even though the day is closed on the calendar.</P>

## Example 1

The service agreement lasts from January 1, 2012 until December 31, 2012. If the service period that you specify in the **Create service orders** form is from November 1, 2012 until February 1, 2013, service orders are created from November 1, 2012 until December 31, 2012.

## Example 2

The service agreement lasts from January 1, 2012 until December 31, 2012. Two service agreement lines are attached to the service agreement. The first service agreement line has a starting date on January 2, 2012 and an ending date on March 1, 2012. The second service agreement line has a starting date on April 1, 2012 and an ending date on December 31, 2012. You specify a period in the **Create service orders** form that is from October 1, 2012 until December 31, 2012. Therefore, service orders are generated only for the second agreement line, because the starting date and ending date of the first agreement line are before the period that you specified for the service order.

  


