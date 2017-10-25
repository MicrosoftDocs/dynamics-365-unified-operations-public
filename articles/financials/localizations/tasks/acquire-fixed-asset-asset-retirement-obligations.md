--- 
# required metadata 
 
title: Acquire a fixed asset with asset retirement obligations (Japan)
description: For Japan, the asset retirement obligation (ARO) is discounted to present value, and added to the acquisition cost of the fixed asset. 
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
# Acquire a fixed asset with asset retirement obligations (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

For Japan, the asset retirement obligation (ARO) is discounted to present value, and added to the acquisition cost of the fixed asset. 



Use this task to learn how to acquire a fixed asset with ARO. 



In order to complete this task, the Fixed Assets configuration key must be selected.



This task uses the JPMF demo company data.

1. Go to Fixed assets > Asset retirement obligations > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. In the Date field, enter a date.
7. In the Account field, specify the desired values.
8. In the Book field, type a value.
9. In the Debit field, enter a number.
10. Click Functions.
11. Click Generate asset retirement obligation transactions.
    * The menu at Functions > Generate asset retirement obligation transactions is used when the fixed asset is in the same journal.     You can also use the menu at Proposals > Capitalized asset retirement obligation for already acquired fixed assets.  
    * Confirm that a new record with Document type of Asset retirement obligation is created.  
12. In the list, mark the selected row.
    * The proposed amount is discounted to present value.  
13. Click Post.

