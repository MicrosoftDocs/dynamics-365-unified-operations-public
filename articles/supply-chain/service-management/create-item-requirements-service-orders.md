---
title: Create item requirements for service orders 
description: Learn how to create item requirements for service orders, including a step-by-step process for creating item requirements for service orders.  
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable
ms.topic: how-to
ms.date: 01/06/2025
ms.custom: 
  - bap-template
---

# Create item requirements for service orders

[!include [banner](../includes/banner.md)]

You can create a service order to track and manage services that you provide to your customers. If you need to reserve specific items for a service order, you can create inventory item requirements for it. An item requirement can be immediately consumed from inventory, or it can initiate a production order for the item.

By using an item requirement instead of an item transaction, you can plan for delivery just before the item is actually used, create a purchase order, include the item in the trade-agreement framework, and include the item requirement in production planning.

Item requirements for service orders are processed through a project. To create an item requirement on a service order, the service order must be assigned to a project. After you create an item requirement for a service order, you can view the item requirement on the **Projects** page for the selected project.

## Create an item requirement for a service order

1. Go to **Service management** \> **Service orders** \> **Service orders**.
1. Select the service order that you want to create an item requirement for.
1. On the Action Pane, on the **Dispatch** tab, select **Item requirement**.
1. On the **Item requirements** page, enter information for the required item.

## Create an item requirement for a service agreement

1. Go to **Service management** \> **Service agreements** \> **Service agreements**.
1. Open the service agreement for which you want to create an item requirement.
1. On the **Lines** FastTab, select **Add** to create a new line.
1. In the **Transaction type** field, select *Item*.
1. In the **Item setup** field, select *Item requirement*.
1. In the **Item number** field, select the item that is required for the service agreement.
1. On the **Line details** FastTab, on the **Product dimensions** tab, in the **Site** field, select the inventory site for the item.
1. To create a service order from the agreement line, on the **Lines** FastTab, select **Create service orders**, and then enter the relevant information on the **Create service orders** page.

## Related information

- [Create service orders automatically](create-service-orders-automatically.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
