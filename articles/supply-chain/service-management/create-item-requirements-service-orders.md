---
# required metadata

title: Create item requirements for service orders 
description: This topic describes how to create item requirements for service orders.  
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

# Create item requirements for service orders

[!include [banner](../includes/banner.md)]

You can create a service order to track and manage services that you provide to your customers. If you need to reserve specific items for a service order, you can create inventory item requirements for it. An item requirement can be immediately consumed from inventory, or it can initiate a production order for the item.

By using an item requirement instead of an item transaction, you can plan for delivery just before the item is actually used, create a purchase order, include the item in the trade-agreement framework, and include the item requirement in production planning.

Item requirements for service orders are processed through a project. To create an item requirement on a service order, the service order must be assigned to a project. After you create an item requirement for a service order, you can view the item requirement in the **Projects** form for the selected project.

## Create an item requirement for a service order

1. Go to **Service management** \> **Common** \> **Service orders** \> **Service orders**.
1. Select the service order that you want to create an item requirement for.
1. On the **Action Pane**, on the **Dispatch** tab, select **Item requirement**.
1. In the **Item requirements** form, enter information for the required item. For more information about the specific fields, see [Item requirements (form)](https://technet.microsoft.com/library/aa552021\(v=ax.60\)).

## Create an item requirement for a service agreement

1. Go to **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.
1. Open the service agreement for which you want to create an item requirement.
1. On the **Lines** FastTab, select **Add** to create a new line.
1. In the **Transaction type** field, select **Item**.
1. In the **Item setup** field, select **Item requirement**.
1. In the **Item number** field, select the item that is required for the service agreement.
1. On the **Line details** FastTab, on the **Product dimensions** tab, in the **Site** field, select the inventory site for the item.
1. To create a service order from the agreement line, on the **Lines** FastTab, select **Create service orders**, and then enter the relevant information in the **Create service orders** form.

## See also

[Create service orders automatically](create-service-orders-automatically.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
