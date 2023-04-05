--- 
# required metadata 
 
title: Set up mandatory payment references
description: Use this procedure to set up mandatory payment reference for a specific ledger account and post a payment. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: MainAccount, LedgerJournalTable, LedgerJournalTransDaily   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Iceland
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up mandatory payment references

[!include [banner](../../includes/banner.md)]

Use this procedure to set up mandatory payment reference for a specific ledger account and post a payment. When you select the ledger account in the journal you must specify a payment reference for the journal line.

This recording uses the DEMF demo company. This functionality is available for legal entities whose primary address is in Iceland.

This functionality is typically used by accountants, accounting managers, accounting clerks.


## Set up the main account
1. Go to General ledger > Chart of accounts > Accounts > Main accounts.
2. Use the Quick Filter to find records. For example, filter on the Main account field with a value of '170150'.
3. In the list, click the link in the selected row.
4. Click Edit.
5. Select or clear the Require payment reference check box.
6. Click Save.

## Create a payment with a payment reference
1. Go to General ledger > Journal entries > General journals.
2. Click New.
3. In the list, mark the selected row.
4. In the Name field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
6. Click Lines.
7. In the list, mark the selected row.
8. In the Account field, specify the desired values.
9. In the Debit field, enter a number.
10. In the Offset account field, specify the desired values.
11. Click the Payment tab.
12. In the Payment reference field, type a value.
13. Click Save.
14. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]