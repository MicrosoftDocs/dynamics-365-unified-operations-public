--- 
title: Reservations cannot be removed when canceling an order 
description: You can't cancel a sales order until the work associated with that order is canceled and reversed. To do so, follow these three steps.
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
# Reservations cannot be removed when canceling an order

## Symptoms

If work is associated with a sales order and you try to cancel that order, you receive the following error message:

> Reservations cannot be removed because there is work created which relies on the reservations.

You can't cancel the sales order until the work is canceled and reversed. This requirement applies even if the work that is associated with the sales order is closed.

## Resolution

To fix this issue, follow these steps:

1. Cancel the work and put inventory back into the desired location. Go to the relevant load of the sales order, and select either **Reduce picked quantity** on the load line or **Reverse work** on the Action Pane.

    The work now has a status of *Canceled*, and new inventory movement work is automatically created and processed to put inventory back into the location that was described at the time of reversal.

2. Delete the load. The shipment is also deleted.

3. You should now be able to go to the sales order and cancel it.
