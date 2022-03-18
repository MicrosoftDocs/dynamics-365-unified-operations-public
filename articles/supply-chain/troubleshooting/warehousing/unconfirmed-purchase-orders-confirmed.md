--- 
title: Update product receipts task confirms unconfirmed orders 
description: After running Update product receipts, the system confirms unconfirmed orders that have a status of Registered. Learn about the feature that fixes this issue. 
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

# Unconfirmed purchase orders are confirmed after running Update product receipts

## Symptoms

After you run the *Update product receipts* periodic task, the system automatically confirms unconfirmed purchase orders that have an inventory transaction status of *Registered*.

## Resolution

A new inbound load handling feature, *Over receipt of load quantities*, fixes this issue. To turn on this feature, go to the [Feature management](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) workspace and turn on the following features in the order that they're listed:

1. Associate purchase order inventory transactions with load
2. Over receipt of load quantities

For more information, see [Post registered product quantities against purchase orders](/dynamics365/supply-chain/warehousing/inbound-load-handling).
