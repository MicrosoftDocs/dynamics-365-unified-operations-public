---
title: About packing slip updates for returns
TOCTitle: About packing slip updates for returns
ms:assetid: 2fe7c589-4bbf-41eb-a4d4-dcb1f89d046b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg231026(v=AX.60)
ms:contentKeyID: 36056302
ms.date: 04/18/2014
mtps_version: v=AX.60
_tocRel: gg230920(v=ax.60)/toc.json
---

# About packing slip updates for returns 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2, Microsoft Dynamics AX 2012 Feature Pack, Microsoft Dynamics AX 2012_

Before returned items can be received into inventory, the packing slip for the order to which they belong must be updated. Just as the invoice update process is the update to the financial transaction, the packing slip update process is the physical update of the inventory record, which means that it commits the changes to inventory. In the case of returns, the steps that are assigned to the disposition action are implemented during the packing slip update.

The packing slip update can be processed in either the item arrival journal or the return order.

As part of the process for posting packing slips, the packing slip reference number from the customer’s shipping documents can be associated with the order lines. This association is optional and for reference only. It does not create any transactional updates.

If not all of the expected return items have arrived, you should include only the quantity that has been received in the packing slip update. Leave the remaining items on the order until the rest of the return shipment has arrived.

If an item is sent back from quarantine to the Shipping and Receiving department, such as when the quarantine inspector does not know where to store the item in inventory, the corresponding packing slip must be updated to correctly register and act on the disposition code that is specified as a result of the quarantine.

## New or changed for Microsoft Dynamics AX 2012 R2

In Microsoft Dynamics AX 2012 R2, when you update a packing slip for a returned item that is from a sales agreement, the sales agreement commitment for that item is automatically updated to reflect the change in the quantity or the amount. For more information about returning an item that is from a sales agreement, see [Return an item ordered from a sales agreement](return-an-item-ordered-from-a-sales-agreement.md). For more information about sales agreements, see [About sales agreements](about-sales-agreements.md).

## See also

[Perform invoice updates for returns](perform-invoice-updates-for-returns.md)

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

