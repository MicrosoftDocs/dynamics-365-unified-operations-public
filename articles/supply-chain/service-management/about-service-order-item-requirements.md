---
title: About service order item requirements
TOCTitle: About service order item requirements
ms:assetid: b7aab3fd-b3df-4bc2-b796-749cddf0a339
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa572246(v=AX.60)
ms:contentKeyID: 36059106
ms.date: 05/02/2014
mtps_version: v=AX.60
_tocRel: gg231005(v=ax.60)/toc.json
f1_keywords:
- project
- service order
- service management
- reserve item
---

# About service order item requirements 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

In Microsoft Dynamics AX 2012, you can create a service order to track and manage services that you provide to your customers. If you need to reserve specific items for a service order, you can create inventory item requirements for it. An item requirement can be immediately consumed from inventory, or it can initiate a production order for the item.

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

[Item requirements (form)](https://technet.microsoft.com/en-us/library/aa552021\(v=ax.60\))

[Consume item requirements in a project](consume-item-requirements-in-a-project.md)

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

