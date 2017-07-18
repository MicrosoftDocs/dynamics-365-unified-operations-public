--- 
# required metadata 
 
title: Configure and run a job to calculate statements
description: This procedure walks through configuring and running recurrent batch jobs to create and calculate statements for a selected store or group of stores. 
author: TonyaFehr 
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
# ms.reviewer: tfehr 
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: RET
ms.author: tfehr 
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

[!include[banner](../includes/banner.md)]

# Configure and run a job to calculate statements

This procedure walks through configuring and running recurrent batch jobs to create and calculate statements for a selected store or group of stores. This procedure uses the USRT company in demo data.

1. Go to All workspaces > Retail store financials.
2. Click Calculate statements.
    * Select either a specific store, or a node if you want to create the batch job for a group of stores.  
    * Click the arrow to add your selection.  
3. Click the Run in the background tab.
4. Under Batch processing, select 'Yes'.
5. Click Recurrence.
6. In the Start date field, enter a date.
7. In the Start time field, enter a time.
8. Select the No end date option.
9. In the PatternUnit field, enter 'Days'.
10. In the Per field, enter a number.
11. Click OK.
12. Click OK.

