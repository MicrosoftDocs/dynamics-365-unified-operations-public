--- 
# required metadata 
 
title: Settle transactions between ledger accounts
description: This procedure shows how to settle transactions between ledger accounts and cancel a ledger settlement. 
author: aprilolson
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
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Settle transactions between ledger accounts

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to settle transactions between ledger accounts and cancel a ledger settlement. This procedure uses the USMF demo data company.


## Settle transaction between ledger accounts
1. Go to General ledger > Periodic tasks > Ledger settlements.
2. In the list, find the transaction that you want to settle.
    * The amount balance must be zero.  
3. Click Include.
4. Click Accept.

## Cancel a ledger settlement
1. Close the page.
2. Go to General ledger > Inquiries and reports > Trial balance.
3. Click Parameters to open the drop dialog.
4. Click Update.
5. In the list, find the account that has the settled transaction.
6. Click All transactions.
7. Use a filter to easily find the transaction in the list.
8. Click Ledger settlements.
9. In the list, mark the selected row.

