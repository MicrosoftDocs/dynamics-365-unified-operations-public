--- 
# required metadata 
 
title: Configure and run a job to post statements
description: This procedure walks through configuring and running a recurrent batch job to post statements for a selected store or group of stores. 
author: josaw1
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-365-retail 
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
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure and run a job to post statements

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure walks through configuring and running a recurrent batch job to post statements for a selected store or group of stores. This procedure uses the USRT company in demo data.

1. Go to All workspaces > .. > Retail store financials.
2. Click Post statements.
    * Select an organizational hierarchy and then in the organization nodes tree, select either an individual store or a node. Select a node if you want to create the batch job for a group of stores.  
    * Click the arrow to add your selection.  
3. Click the Run in the background tab.
4. Check or uncheck the Batch processing checkbox.
5. Click Recurrence.
6. In the Start date field, enter a date.
7. In the Start time field, enter a time.
    * Choose whether you want to end the recurrence after a specific number of runs, at a specific date, or never. Then choose the various options to define how frequently you want the job to run.  
8. Click OK.
9. Click OK.

