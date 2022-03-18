--- 
title: On-hand inventory not considered for batch-above items
description: Some slotting templates don't consider current on-hand inventory for batch-above items. The batch or serial number must be specified on the demand order. 
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

# Slotting templates don't consider on-hand inventory for batch-above items

## Symptoms

Slotting templates that have the *Consider on-hand* slot criterion don't consider current on-hand inventory for *batch-above* items. They consider it only if the batch number is specified on the sales order line.

However, when you use *batch-below* items, the current on-hand inventory is considered as expected.

For more information, see [Warehouse slotting](/dynamics365/supply-chain/warehousing/warehouse-slotting).

## Resolution

The slotting template header can be defined for the *Ordered,* *Reserved*, or *Released* demand strategy. For the *Ordered* demand strategy, the same reservation hierarchy requirements apply that apply to reservation or release to warehouse processes. Therefore, for items that have *batch-above* and *serial-below* reservation hierarchies, the batch or serial number must be specified on the demand order (sales or transfer).

Alternatively, the *Reserved* demand strategy can be used to select the batch or serial number before the warehouse slotting demand is generated.
