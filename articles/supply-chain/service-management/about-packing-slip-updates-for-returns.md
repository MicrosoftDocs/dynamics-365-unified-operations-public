---
# required metadata

title: Packing slip updates for returns  
description: Before returned items can be received into inventory, the packing slip for the order to which they belong must be updated.
author: YuyuScheller
manager: AnnBe
ms.date: 04/30/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: YuyuScheller
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Packing slip updates for returns  

[!INCLUDE [banner](../includes/banner.md)]


Before returned items can be received into inventory, the packing slip for the order to which they belong must be updated. Just as the invoice update process is the update to the financial transaction, the packing slip update process is the physical update of the inventory record, which means that it commits the changes to inventory. In the case of returns, the steps that are assigned to the disposition action are implemented during the packing slip update.

The packing slip update can be processed in either the item arrival journal or the return order.

As part of the process for posting packing slips, the packing slip reference number from the customer’s shipping documents can be associated with the order lines. This association is optional and for reference only. It does not create any transactional updates.

If not all of the expected return items have arrived, you should include only the quantity that has been received in the packing slip update. Leave the remaining items on the order until the rest of the return shipment has arrived.

If an item is sent back from quarantine to the Shipping and Receiving department, such as when the quarantine inspector does not know where to store the item in inventory, the corresponding packing slip must be updated to correctly register and act on the disposition code that is specified as a result of the quarantine.

## New or changed for Microsoft Dynamics AX 2012 R2

In Microsoft Dynamics AX 2012 R2, when you update a packing slip for a returned item that is from a sales agreement, the sales agreement commitment for that item is automatically updated to reflect the change in the quantity or the amount. For more information about returning an item that is from a sales agreement, see [Return an item ordered from a sales agreement](return-an-item-ordered-from-a-sales-agreement.md). For more information about sales agreements, see [About sales agreements](about-sales-agreements.md).

## See also

[Perform invoice updates for returns](perform-invoice-updates-for-returns.md)

  


