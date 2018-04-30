---
title: Create item requirements for service orders
TOCTitle: Create item requirements for service orders
ms:assetid: 5baf239e-d3f2-47b9-aea8-e3d5aa96040e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa549087(v=AX.60)
ms:contentKeyID: 54273729
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg231005(v=ax.60)/toc.json
---

# Create item requirements for service orders 




In Microsoft Dynamics AX 2012, you can create a service order to track and manage services that you provide to your customers. If you need to reserve specific items for a service order, you can create inventory item requirements for it. An item requirement can be immediately consumed from inventory, or it can initiate a production order for the item.

By using an item requirement instead of an item transaction, you can plan for delivery just before the item is actually used, create a purchase order, include the item in the trade-agreement framework, and include the item requirement in production planning.

Item requirements for service orders are processed through a project. To create an item requirement on a service order, the service order must be assigned to a project. After you create an item requirement for a service order, you can view the item requirement in the **Projects** form for the selected project.

## Create an item requirement for a service order

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Select the service order that you want to create an item requirement for.

3.  On the **Action Pane**, on the **Dispatch** tab, click **Item requirement**.

4.  In the **Item requirements** form, enter information for the required item. For more information about the specific fields, see [Item requirements (form)](https://technet.microsoft.com/en-us/library/aa552021\(v=ax.60\)).

## Create an item requirement for a service agreement

1.  Click **Service management** \> **Common** \> **Service agreements** \> **Service agreements**.

2.  Open the service agreement for which you want to create an item requirement.

3.  On the **Lines** FastTab, click **Add** to create a new line.

4.  In the **Transaction type** field, select **Item**.

5.  In the **Item setup** field, select **Item requirement**.

6.  In the **Item number** field, select the item that is required for the service agreement.

7.  On the **Line details** FastTab, on the **Product dimensions** tab, in the **Site** field, select the inventory site for the item.

8.  To create a service order from the agreement line, on the **Lines** FastTab, click **Create service orders**, and then enter the relevant information in the **Create service orders** form. For more information about automatically creating service orders from a service agreement, see [Create service orders automatically](create-service-orders-automatically.md).

## See also

[About service order item requirements](about-service-order-item-requirements.md)

  


