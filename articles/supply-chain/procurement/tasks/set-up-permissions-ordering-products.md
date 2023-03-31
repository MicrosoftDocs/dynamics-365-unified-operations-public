--- 
# required metadata 
 
title: Set up permissions for ordering products on behalf of someone else
description: This article explains how to grant workers permission to prepare purchase requisitions on behalf of other workers. 
author: GalynaFedorova
ms.date: 08/20/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchReqAuthorization, HcmWorkerLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up permissions for ordering products on behalf of someone else

[!include [banner](../../includes/banner.md)]

This article explains how to grant workers permission to prepare purchase requisitions on behalf of other workers. In other words, a purchase requisition "preparer" can create a requisition for another "requester." The procedure also shows how to grant a worker permission to order items and services in different legal entities or operating units. Typically, these tasks are performed by a purchasing manager. You can use this procedure either on data for the USMF demo company or on your own data.


## Grant permission to enter purchase requisitions on behalf of another worker
1. Go to **Procurement and sourcing > Setup > Policies > Purchase requisition permissions**. Make sure that the **Current view** field is set to **By preparer**. The list in the left pane shows the people who can be granted permission to prepare requisitions on behalf of other people.  
2. Select the person to grant permission to (the preparer).
3. Select **Add**.
4. Find and select the person to add as a requester.
    - The requester is the person that the preparer can create requisitions on behalf of.  
    - In the **Authorization** field, select **Specific** if the preparer should be able to create purchase requisitions on behalf of the selected worker. Select **Reporting** if the preparer should also be able to create purchase requisitions on behalf of all workers who report to that worker.  
5. In the **Effective** field, enter a date.
6. In the **Expiration** field, enter a date.

## View preparers who have permission to create purchase requisitions for a selected worker
1. In the **Current view** field, select **By requester**. This view shows a list of preparers who have been granted permission to create purchase requisitions on behalf of a selected worker.  
2. Use the Quick Filter to find the worker that you just added as the requester.
3. Select the requester. The Preparer list shows the people who have permission to order items on behalf of the requester who is selected in the left pane.  You can add additional preparers here. This view also lets you grant the requester permission to create requisitions in legal entities and operating units that aren't that person's primary legal entity or operating unit.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]