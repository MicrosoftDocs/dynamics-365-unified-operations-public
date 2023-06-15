--- 
# required metadata 
 
title: Close the fiscal year
description: This procedure steps through the year end close process that transfers balances to a new fiscal year. 
author: aprilolson
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerParameters, LedgerFiscalCloseGroup, LedgerFiscalCloseAddLedger, SysLookupMultiSelectGrid, LedgerFiscalCloseRunGroup   
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
# Close the fiscal year

[!include [banner](../../includes/banner.md)]

This procedure steps through the year end close process that transfers balances to a new fiscal year.


## Validate year-end close parameters
1. Go to **General ledger > Ledger setup > General ledger parameters**.
2. Expand the **Fiscal year close** section.
3. Select **Yes** or **No** for the **Delete close-of-year transactions during transfer** option.
    
If the fiscal year has already been closed and the year-end close is being run again, this setting is important. If set to **Yes**, the voucher for the previous year-end close will be deleted, and a new voucher will be created for all accounts beginning balances. If set to **No**, the previous voucher will remain and a new voucher will only be created for adjusting entries that were posted after the last year-end close.

4. Select **Yes** or **No** for the **Create closing transactions during transfer** option.

If set to **Yes**, two transactions are created. One voucher is created in the fiscal year being closed to bring the balances of all ledger accounts down to zero and a second voucher is created in the next fiscal year for the beginning balances. If set to **No**, a single voucher is created in the next fiscal year for the beginning balances.  

5. Select **Yes** or **No** for the **Set fiscal year status to permanently closed** option.

If set to **Yes**, the fiscal year status will be set to **Permanently closed**. Because a permanently closed year can't be reopened, it would be a best practice to set this option to **No**.  

6. Select **Yes** or **No** for the **Voucher number must be filled in during the year end close** option.

If set to **Yes**, a voucher number must be manually entered during the year end close process. A number sequence is not used to generate this voucher number. It's a best practice to set this to **Yes**.  

7. Close the page.
8. Go to **General ledger > Period close > Year end close**.
9. Click **New** to create a year-end close template.

A template can be created for a group of legal entities for which to run the year-end close. This template can be reused year after year.  

10. In the **Group name** field, enter a year-end close template name.
11. In the **Fiscal calendar** field, select the fiscal year for which the template will be created.

Only legal entities which use the same fiscal year can be grouped together in the year-end close template. This is because the year end close is done by selecting a fiscal year, not a date.  

12. On the **Action pane**, click **Save**.
13. In the **Legal entities** section, click **Add** to select the legal entities for this template.
    
Legal entities can be added by either selecting the legal entities or by selecting an organizational hierarchy. Only legal entities with the organizational hierarchy with the same fiscal calendar selected will be added.  

14. Select either the legal entities or the organizational hierarchy.
15. Click **OK**.
16. Select **Yes** or **No** in the **Transfer balance sheet dimension**.

It's best practice to set this option to **Yes** for Balance sheet accounts. This will maintain the financial dimensions on posted transactions when creating the beginning balances for the balance sheet accounts. For profit and loss accounts, you can select to maintain the financial dimensions (**Close all**) when the balances are moved to Retained earnings or you can select to have the financial dimensions replaced with a different dimension value (**Close single**). If you choose **Close single**, you can define a specific dimension value for each dimension or even choose to leave it blank.  

17. Click **Save**.
18. Start the year-end close by choosing **Run fiscal close** on the **Action Pane**. The year-end close will be run for the selected template.  
19. Select all or a subset of legal entities from the template for which to run the year-end close.

When first running the year-end close, to get beginning balances, most organizations may choose to run the year-end close for all legal entities within the template. If adjusting entries are made after that, you may choose to run the year-end close for only the legal entities that have adjustments.  

20. Click **OK**.
21. Select the fiscal year for which to run the year-end close.
22. In the **Voucher field**, type a value. It's best practice to include the fiscal year in the voucher number, to make it easier to find the year-end close voucher that is created.  
23. The year-end close defaults to run in batch. It's best practice for long-running processes to run in batch mode. This is typically one of those processes, which is why the default is to use batch mode.  
24. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
