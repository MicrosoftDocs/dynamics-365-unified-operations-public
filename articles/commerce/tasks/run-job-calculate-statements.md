--- 
# required metadata 
 
title: Configure and run job to calculate statements
description: This procedure walks through configuring and running recurrent batch jobs to create and calculate statements for a selected store or group of stores. 
author: josaw1
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailChannelOperationsWorkspace, RetailOperatingUnitPicker, SysRecurrence   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Configure and run job to calculate statements

[!include [banner](../includes/banner.md)]

This procedure walks through configuring and running recurrent batch jobs to create and calculate statements for a selected store or group of stores. This procedure uses the USRT company in demo data.

1. Go to All workspaces > Store financials.
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



[!INCLUDE[footer-include](../../includes/footer-banner.md)]