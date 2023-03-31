--- 
# required metadata 
 
title: Settle transactions between ledger accounts
description: This procedure shows how to settle transactions between ledger accounts and cancel a ledger settlement. 
author: aprilolson
ms.date: 10/03/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerTransSettlement, LedgerTrialBalanceListPage, LedgerTrialBalanceListPageBalanceParms, LedgerTransAccount, LedgerTransSettled   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Settle transactions between ledger accounts

[!include [banner](../../includes/banner.md)]

This procedure shows how to settle transactions between ledger accounts and cancel a ledger settlement. This procedure uses the USMF demo data company.


## Settle transaction between ledger accounts
1. Go to **General ledger > Periodic tasks > Ledger settlements**.
2. In the list, find the transaction that you want to settle.
   > [!NOTE]
   > The amount balance must be zero.  
3. Click **Include**.
4. Click **Accept**.

## Cancel a ledger settlement

1. Go to **General ledger > Inquiries and reports > Trial balance**.
2. Click **Parameters** to open the drop dialog.
3. Click **Update**.
4. In the list, find the account that has the settled transaction.
5. Click **All transactions**.
6. Use a filter to easily find the transaction in the list.
7. Click **Ledger settlements**.
8. In the list, mark the selected row.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
