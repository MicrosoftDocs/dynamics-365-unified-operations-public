---
# required metadata

title: Add an address to a service order   
description: This topic describes how to add a customer address to a service order.
author: sorenva
ms.date: 05/02/2018
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

# Add an address to a service order    

[!include [banner](../includes/banner.md)]


This topic describes how to add a customer address to a service order. When you create a service order, the address information is transferred from the project that the service order is attached to. However, you can select an alternative location from addresses that are already entered in Microsoft Dynamics AX for customers, vendors, sites, warehouses, service orders, and projects.

You can also create a new address. By default, the new address is transferred to the project. However, you can specify that the new address is only relevant for this instance of the service. If you do, the new address is not transferred to the project.

## Create a customer address for a service order

To add an address to a service order, follow these steps:

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Open the service order that you want to create an address for.

3.  On the **Action Pane**, click **Edit**, and then click **Header view**.

4.  On the **Address** FastTab, click **Add address**.

5.  In the **New address** form, enter a unique name for the address and complete the remaining fields. 
    

    > [!WARNING]
    > <P>If you enter the same name as an existing address, the information that you enter in the remaining fields will overwrite information for the existing address.</P>


6.  Click **OK** to copy the new address to your service order.

## Specify an alternative address on a service order

To add an alternative address to a service order, follow these steps:

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Open the service order that you want to enter an alternative address for.

3.  On the **Action Pane**, click **Edit**, and then click **Header view**.

4.  On the **Address** FastTab, click **Other address**.

5.  In the **Address selection** form, in the **Record type** field, select **Service orders**.

6.  Select an address, and then click **OK** to copy it to your service order.


  




[!INCLUDE[footer-include](../../includes/footer-banner.md)]