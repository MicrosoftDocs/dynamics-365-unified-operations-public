--- 
# required metadata 
 
title: Post online sales and payments
description: This procedure walks through configuring and running a recurrent batch job to create sales orders and payments for online store transactions. 
author: jashanno
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Post online sales and payments

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure walks through configuring and running a recurrent batch job to create sales orders and payments for online store transactions. This procedure uses the USRT company in demo data.

1. Go to All workspaces > Retail store financials.
2. Click Synchronize orders.
3. In the Organization hierarchy field, select 'Retail Stores by Region'.
    * Select either a specific online store, or select a node if you want to create the batch job for a group of stores.  
    * Click the arrow to add your selection.  
4. Click the Run in the background tab.
5. Check or uncheck the Batch processing checkbox.
6. Click Recurrence.
7. Select the No end date option.
8. In the Count field, enter a number.
9. Click OK.
10. Click OK.

