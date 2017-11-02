--- 
# required metadata 
 
title: Calculate fixed asset depreciation across legal entities
description: This procedure shows you to how set up and run the depreciation process for multiple legal entities.
author: saraschi2
manager: AnnBe 
ms.date: 11/02/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Calculate fixed asset depreciation across legal entities

[!include[task guide banner](../../includes/task-guide-banner.md)]

Fixed asset depreciation can be run across legal entities in a single step. This procedure shows you to how set up and run the process for multiple legal entities. It uses the accountant role.  

This recording uses the USMF demo company.


Steps (16)
Sub-task: Set up cross company depreciation run journals. 

1. First, you must set up the journals to be used in the cross company depreciation run in each legal entity. 
Go to Fixed assets > Setup > Fixed assets parameters. 
2. Expand the Fixed asset proposals section. 
3. Create a record with the journal name to be used for each posting layer in the legal entity. If books do not post to the general ledger, then the None posting layer should be selected with the associated journal. 
Click Add. 
4. In the Posting layer field, enter or select a value. 
5. In the Journal name field, enter or select a value. 
6. Repeat the journal setup on the Fixed asset parameters page in each legal entity. 

Sub-task: Calculate depreciation

1. Use the Create depreciation proposal page to start your depreciation run across legal entities. 
Go to Fixed assets > Journal entries > Create depreciation proposal. 
2. In the Posting layer field, enter or select a value. 
3. The journal name will default from the Fixed asset parameters. It can be changed here for the current legal entity. 
4. In the To date field, enter a date. 
5. Select the legal entities to be included in the depreciation run. 
Only legal entities with journals set up for Fixed asset proposals on the Fixed asset parameters page will be shown in the list. 
6. When enabled, the Post journals option will automatically post the depreciation journals when they are created. When not selected, the journals will be created, but not posted, so you can review the details before posting. 
Select Yes in the Post journals field. 
7. Filtering fields include all fixed assets, groups, and books for the legal entities selected for this depreciation run. 
8. The Batch processing option is enabled by default. When this option is enabled, the depreciation journal creation and posting will run in the background. 
9. Click Create journal. 
10. You must view the depreciation journals created in the respective legal entities. 
Go to Fixed assets > Journal entries > Fixed assets journal.
