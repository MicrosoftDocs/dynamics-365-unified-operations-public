--- 
# required metadata 
 
title: Settle a postdated check from a customer
description: You can settle a postdated check after the check has been cleared by the bank. 
author: kweekley
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustPostDatedChecks, SystemDate, LedgerJournalTable, LedgerJournalTransDaily, LedgerTransVoucher   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Settle a postdated check from a customer

[!include [banner](../../includes/banner.md)]

You can settle a postdated check after the check has been cleared by the bank. This financial transaction also clears the bridge account transaction for the postdated check. 

The following tasks must be complete before you start this one.

1) Set up postdated checks

2) Register and post a postdated check for a customer 



The role of this task guides is Treasurer.



This procedure uses the USMF demo company.

1. Go to **Credit and collections > Inquiries and reports > Payments > Customer postdated checks**.
2. Click **Settle**.
3. Click **Settle clearing entries**.
    * Settle the customer account for the check transaction.  
4. Close the page.
5. Go to **General ledger > Journal entries > General journals**.
6. In the **Show** field, select an option.
7. Select or clear the **Show user-created only** check box.
8. In the list, find and select the desired record.
9. Click **Lines**.
10. Click **Voucher**.
11. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
