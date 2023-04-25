--- 
# required metadata 
 
title: View journal entries or transactions
description: This procedure shows how to use the Voucher transactions inquiry to search for journal entries or transactions. 
author: aprilolson
ms.date: 03/01/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysQueryForm, LedgerTransVoucher, LedgerTransBase, Originaldocuments   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2023-02-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# View journal entries or transactions

[!include [banner](../../includes/banner.md)]

This procedure shows how to use the Voucher transactions inquiry to search for journal entries or transactions.

1. Go to **General ledger > Inquiries and reports > Voucher transactions**.
2. Select the field for which you want to define a filter criteria.
3. Enter your filter critieria for the selected field. You could filter on a single value or a range. When defining a range, make sure the correct syntax is used. The values should be separated by a double period (..).  
4. Click the **Joins** tab to add additional tables from which to filter.
5. In the tree, select **Tables/General journal entry**.
6. Click **Add table join**.
7. Click **Cancel** if you decide not to add an additional table.
8. Click the **Range** tab.
9. Click **OK** to run the query.
10. On the Action pane, click **Transaction origin**. Various buttons about the grid can be used to research additional information about the selected record of the voucher. Some buttons may not be available, depending on the type of transaction.
11. On the Action pane, click **Original document**.
12. Close the page.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
