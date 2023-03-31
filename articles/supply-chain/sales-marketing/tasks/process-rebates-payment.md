--- 
# required metadata 
 
title: Process rebates for payment
description: This procedure demonstrates how to convert approved and processed customer rebates to credit notes. 
author: Henrikan
ms.date: 11/10/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Process rebates for payment

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to convert approved and processed customer rebates to credit notes. You can use this guide in the USMF demo company. The precondition for this guide is to have one or more rebate claims which have a status of Mark. If you're using USMF you should run the "Generate and process customer rebates" guide before you start this guide.


## Convert rebate claims to credit note
1. Go to All customers.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. On the Action Pane, click Collect.
5. Click Settle transactions.
6. Click Functions.
7. Click Rebate program.
    * The Rebate page lists the rebate claims that you have processed in the customer rebate workbench and that are in status Mark.    
8. Click Edit.
    * Set checkmarks in the Mark field for the claims that you want to include into credit note.   
9. Click Functions.
10. Click Create credit note.
    * A message appears to inform you that a journal has been posted (This is the Accounts receivable consumption journal, as specified in the Accounts receivable parameters page). This causes the real liability (credit) amount to be moved to the customer balance. This means that the customer's account has been credited, and the Rebate accrual account has been debited.  
11. Close the page.
12. Click Cancel.
    * This refreshes the page so that you can see the updates.  
13. On the Action Pane, click Collect.
14. Click Settle transactions.
    * Note that a transaction for negative amount, representing the total rebate amount, without invoice reference has been added to the customer balance.   
15. Click Cancel.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]