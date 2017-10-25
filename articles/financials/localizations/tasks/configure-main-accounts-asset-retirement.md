--- 
# required metadata 
 
title: Configure main accounts for asset retirement obligation posting and market discount rates (Japan)
description: For Japan, asset retirement obligation needs to be assessed and posted when acquiring a fixed asset with legal obligations at retirement. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/22/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure main accounts for asset retirement obligation posting and market discount rates (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

For Japan, asset retirement obligation needs to be assessed and posted when acquiring a fixed asset with legal obligations at retirement. 



The user needs to configure all the main accounts before any transaction of asset retirement obligation can be posted.



Use this task to learn how to configure the main accounts for asset retirement obligation posting.



In order to complete this task, the Fixed Assets configuration key must be selected.



This task uses the JPMF demo company data.


## Configure ledger accounts for asset retirement obligation posting
1. Go to Fixed assets > Setup > Fixed asset posting profiles.
2. Expand the Asset retirement obligation section.
3. Click Add.
4. In the Book field, type a value.
5. In the Groupings field, select an option.
6. In the Fixed asset number field, type a value.
    * Optional: when you select 'Groupings' as Group or Table, you will need to specify a fixed asset group or a fixed asset.  
7. In the Main account field, specify the desired values.
8. In the Offset account field, specify the desired values.
9. In the Select field, select an option.
10. Expand the Disposal parameters by document type section.
11. In the Sale or scrap field, select an option.
    * You must set up both the Sales and Scrap type of disposal accounts before you can post transactions of those types.  
12. Click New.
13. In the Book field, type a value.
14. In the Valid for field, select an option.
15. In the Fixed asset relation field, type a value.
    * Optional: when you select 'Valid for' as Group or Table, you will need to specify a fixed asset group or a fixed asset.  
16. In the Main account field, specify the desired values.
17. In the Offset account field, specify the desired values.
    * Repeat these steps to configure main accounts for other combinations of transactions.  
    * Each line of configuration is needed for one type of Post value.  

## Configure market discount rates
1. Go to Fixed assets > Setup > Cashflow discount rates.
2. Click New.
3. In the Start date field, enter a date.
4. In the Market discount rate percentage field, enter a number.

