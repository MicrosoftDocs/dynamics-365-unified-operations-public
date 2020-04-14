---
# required metadata

title: Service order item requirements   
description: If you need to reserve specific items for a service order, you can create inventory item requirements for it.
author: ShylaThompson
manager: tfehr
ms.date: 05/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProjSalesItemReq
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

# Service order item requirements   

[!include [banner](../includes/banner.md)]


You can create a service order to track and manage services that you provide to your customers. If you need to reserve specific items for a service order, you can create inventory item requirements for it. An item requirement can be immediately consumed from inventory, or it can initiate a production order for the item.

By using an item requirement instead of an item transaction, you can plan for delivery just before the item is actually used, create a purchase order, include the item in the trade-agreement framework, and include the item requirement in production planning.

Item requirements for service orders are processed through a project. To create an item requirement on a service order, the service order must be attached to a project.

As soon as an item requirement is created for a service order, it can be viewed from **Project** in the individual service order or through the **Sales order** form.

## View an item requirement from a service order

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Click **Dispatch**, and then click **Item requirement** to open the **Item requirements** form.

3.  Click the **Project** tab, and check the **Service order** field to see the service orders of the item requirement.

## Delete service orders with item requirements

If an item requirement is created on a service order, you cannot delete the service order. You must delete the item requirement before you can delete the service order.

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Click **Dispatch**, and then click **Item requirement** to open the **Item requirements** form. This form lists the item requirements that are created on the service order.

3.  Select the item requirement to delete, and then click **Delete**.

–or–

1.  Click **Project management and accounting** \> **Common** \> **Projects** \> **All projects**.

2.  Open the project that has the service order in which an item requirement is created.

3.  In the **Projects** form, in the right pane, click **Item requirements**. The **Item requirements** form lists the item requirements that are associated with the selected project.

4.  Select the item requirement to delete, and then click **Delete**.

## See also

[Item requirements (form)](https://technet.microsoft.com/library/aa552021\(v=ax.60\))

