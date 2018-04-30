---
title: Create an item replacement order
TOCTitle: Create an item replacement order
ms:assetid: 38c243d9-9d42-49e3-b4ff-5197d46ebcae
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg231129(v=AX.60)
ms:contentKeyID: 49684848
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg230920(v=ax.60)/toc.json
---

# Create an item replacement order 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

Item replacement orders are usually created after a product is returned and inspected. However, when an item must be replaced before it has been returned, or when the original item will not be returned, you can create an item replacement order immediately after you create a return order.

## Create a replacement order after you receive an item that is returned

1.  Click **Sales and marketing** \> **Common** \> **Return orders** \> **All return orders**.

2.  Create a new return order, or select a returned order from the list to open the **Return order - RMA number: %1, %2** form.

3.  Click **Return line**, and then select **Replacement item**.

4.  Select the item to replace the returned item with. Enter the item specifications, and then click **Apply**.

5.  Click **Packing slip** to generate the packing slip for the return order. A sales order is generated for the replacement item that you selected.
    
    In Microsoft Dynamics AX 2012 R2, after the sales order is created for the replacement item, sales agreements are automatically searched and if there is an applicable sales agreement, it is applied to the sales order.

## Create a replacement order before you receive an item that will be returned

1.  Click **Sales and marketing** \> **Common** \> **Return orders** \> **All return orders**.

2.  Create a new return order, or select a return order from the list to open the **Return order - RMA number: %1, %2** form.

3.  Click **Find sales order** if you want to identify the sales order for the returned item. Complete the **Find sales order** form and then click **OK** to close the form and return to the **Return order - RMA number: %1, %2** form. The sales order line for the returned item is copied to the return order.

4.  Click **Replacement order** to open the **Create sales order** form.

5.  Select the **Copy return order lines** check box to transfer details from the return order you selected on the **Return order - RMA number: %1, %2** form to this sales order.

6.  Enter or modify details, as required.
    
    In Microsoft Dynamics AX 2012 R2, if you identified the sales order in step 3, and if the sales order line for the returned item is linked to a sales agreement, the identifier of the applicable sales agreement for the item replacement order will be automatically displayed in the **Sales agreement ID** field.

7.  Click **OK** to close the **Create sales order** form and open the **Sales order** form, where you can continue to enter information for the new sales order. Any applicable return order lines will be copied to the new sales order. For more information, see [Sales orders (form)](https://technet.microsoft.com/en-us/library/aa585863\(v=ax.60\)).
    
    In Microsoft Dynamics AX 2012 R2, if the identifier of the sales agreement is automatically displayed in the **Sales agreement ID** field, then the sales agreement has been linked to the sales order header for the item replacement order. If there is an applicable commitment in the sales agreement that has not been fulfilled yet, and the sales order is created before the sales agreement expires, a link is established between the sales agreement line and the sales order line. Therefore, information from the sales agreement, such as item price, is copied to the new sales order line. For more information, see [About sales agreements](about-sales-agreements.md).

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

