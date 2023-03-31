--- 
# required metadata 
 
title: Settle a postdated check for a vendor
description: Settle a postdated check issued to a vendor when the bank has cleared the check transaction after the check has been overdue and cleared by the bank. 
author: kweekley
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendPostDatedChecks, LedgerJournalTable, LedgerJournalTransDaily, LedgerTransVoucher   
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
# Settle a postdated check for a vendor

[!include [banner](../../includes/banner.md)]

Settle a postdated check issued to a vendor when the bank has cleared the check transaction after the check has been overdue and cleared by the bank. 

Complete the following procedures before you start this one.

1) Set up postdated checks

2) Register and post a postdated check for a vendor



The role of this procedure is Treasurer. This procedure uses the USMF demo company.

1. Go to **Accounts payable > Payments > Vendor postdated checks**.
2. Click **Settle**.
3. Click **Settle clearing entries**.
    * Settle the vendor account for the check transaction.  
4. Close the page.
5. Go to **General ledger > Journal entries > General journals**.
6. In the **Show** field, select **All**.
7. Select or clear the **Show user-created only** check box.
8. In the list, mark the selected row.
9. Click **Lines**.
10. Click **Voucher**.
11. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
