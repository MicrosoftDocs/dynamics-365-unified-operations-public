--- 
title: Bundle item not supported in an intercompany process  
description: The bundle item isn't available for purchase. The sales order only buys the components of the bundle item, not the bundle item itself.
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
ms.search.form: SalesTable, SalesTableListPage, SalesTableListPage_SalesCancelOrder
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# A bundle item isn't supported in an intercompany process

## Symptoms

The bundle item isn't available for the purchase order because, if you examine the sales order lines for the bundle item, you will notice that the quantity is *0* (zero) and the status is *Canceled*.

## Resolution

This behavior is by design. The sales order buys only the components of the bundle item. It doesn't buy the bundle item itself. If you must buy a bundle, consider whether you have to mark it as bundle item, because this functionality is designed for revenue recognition scenarios. For more information about bundle items, see [Bundles](/dynamics365/finance/accounts-receivable/revenue-recognition-setup).
