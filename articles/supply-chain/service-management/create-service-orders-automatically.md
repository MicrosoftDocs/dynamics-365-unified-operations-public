---
# required metadata

title: Create service orders automatically   
description: You can create service orders for one service agreement or for several service agreements.
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

# Create service orders automatically    

[!include [banner](../includes/banner.md)]


You can create service orders for one service agreement or for several service agreements. When they are created, you can view your service orders in the **Service orders** form.

Service orders are created only for the valid period of the service agreement. If the interval that you specify in the **Create service orders** form is before the starting date or after the ending date of the service agreement, service orders are created only for the part of the interval that is within the service agreement dates.

When you create service orders manually or automatically from the service agreement line, the service order must be in the time interval that is defined by the starting and ending dates for the line, unless you do not specify an ending date on the line.

## Create service orders automatically for a service agreement

1.  Click **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.

2.  Select a service agreement.

3.  Click the **Deliver** tab, and then click **Planned service orders**.

4.  Specify dates in the **From date** and **To date** fields to define the service period.

5.  Select the **Show Infolog** check box to display a list of the service orders that are created.

6.  Select transaction types in the **Include transaction types** field group. The transaction types represent the lines that are created in the service agreement, and each transaction type that you select generates several service orders, depending on the service interval that is specified on the service agreement line.

7.  To create any service orders that are missing from continuous series of service orders, select the **Continuous** check box.

8.  Click **OK**.

## Create service orders automatically for several service agreements

1.  Click **Service management** \> **Periodic** \> **Service orders** \> **Create service orders**.

2.  Click **Select** to make selections to add or remove criteria to use to create service orders.

3.  Click **OK**.

## See also

[Service orders](service-orders.md)

[Automatically create service orders](auto-create-service-orders.md)

  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]