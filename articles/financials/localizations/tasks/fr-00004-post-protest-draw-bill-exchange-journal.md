--- 
# required metadata 
 
title: Post protest draw bill of exchange journal (France)
description: This procedure walks you through the steps of protesting bill of exchange. 
author: EvgenyPopovMBS
manager: AnnBe 
ms.date: 03/02/2016
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
ms.search.region: France
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Post protest draw bill of exchange journal (France)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through the steps of protesting bill of exchange.

This procedure was created using the demo data company FRSI. 

This functionality is available for legal entities whose primary address is in France.

You should have a role of Accounts receivables clerk to complete this procedure.



1. Go to Accounts receivable > Payments > Bill of exchange > Protest bill of exchange journal.
2. Click New.
3. In the list, mark the selected row.
4. In the Name field, enter or select a value.
5. In the list, click the link in the selected row.
    * Select "LitigeEAR"  
6. Click Lines.
7. In the list, mark the selected row.
8. In the Account field, specify the values 'FR_SI_0001'.
9. Click Settle transactions.
10. In the list, mark the selected row.
    * Mark the most recently posted draw bill of exchange journal  
11. Select the Mark check box.
12. Click OK.
13. Click Post.
14. Go to Accounts receivable > Inquiries and reports > Payments > Bill of exchange journal.
    * Verify that Status for the newly posted journal should be Protested. If yes, the process is complete  

