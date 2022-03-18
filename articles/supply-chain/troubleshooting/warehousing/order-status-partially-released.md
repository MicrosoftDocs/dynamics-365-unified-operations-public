--- 
title: Order status remains Partially released after it's invoiced 
description: In some cases, the status of a sales order remains Partially released, even after the order has been invoiced. This page explains why and a possible workaround. 
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Order status remains Partially released even after the sales order is invoiced

## Symptoms

A sales order is a delivery order, but one or more items on it have a different mode of delivery. After the order is invoiced, it still has a release status of *Partially released*.

For example, a sales order has two items: one for delivery and one for pickup. Both the delivery and the pickup have been done. Therefore, both lines have been invoiced. However, the release status is still shown as *Partially released*, which is misleading.

## Workaround

The release status applies only to order lines where the items are enabled for warehouse management. Therefore, the release status remains *Partially released* in this scenario. Microsoft has evaluated this issue and has determined that it's a feature limitation. An extension could be added as part of the packing slip and invoicing process to update the release status.
