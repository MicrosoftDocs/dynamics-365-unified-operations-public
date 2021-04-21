---
# required metadata

title: Year-end close missing opening balances 
description: This topic explains why opening balances might be missing when you close a year, and how to rebuild those balances.
author: kweekley
ms.date: 01/25/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2020-12-14
ms.dyn365.ops.version: 10.0.14

---

# Year-end close missing opening balances

[!include [banner](../includes/banner.md)]

This topic explains why opening balances might be missing when you close a year, and how to rebuild those balances.

## Why are there no beginning balances after running the General ledger year-end close? 

## Answer

Here are a few things to check if you have run the General ledger year-end close and no opening balances are shown on the trial balance for the next fiscal year.

### Run close vs Undo close

If the Undo previous close selection is set to Yes, the previous year-end close for the same fiscal year is being reversed. When running an undo, all closing balance and opening balance entries will be deleted, as if the year-end close had never been run. The vouchers are also deleted. The year-end close will not run again automatically. You must start the process again, this time changing Undo previous close to No.


This scenario is covered in the year-end close FAQ topic. For more information, see [Year-end activities FAQ(faq-year-end-activities.md). ](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/faq-year-end-activities).


I ran year-end close with the option Undo previous close set to No, and I still do not have opening balances for my fiscal year.

First check the status of the batch job.  Closing a year comprises a number of separate tasks, but the most critical step is the batch task with the task description “Step 5.0.0”.  Posting the opening, and optionally the closing, transactions to General ledger takes place during this step. 


[![Batch history list](./media/yec-mssng-open-blnces-01.png])(./media/yec-mssng-open-blnces-01.png)

If this step ended successfully but you don’t see opening balances on the Trial balance inquiry page (General ledger > Inquires and reports > Trial balance), review the results of the year-end close batch job to see if the Rebuild balances for [CompanyId] step completed successfully:

[![Results of year-end close batch job](./media/yec-mssng-open-blnces-02.png])(./media/yec-mssng-open-blnces-02.png)

If this step has failed for any reason, the opening (and optionally closing) transactions were likely posted successfully. You can verify the General ledger transactions were posted successfully using the Voucher transactions inquiry by specifying the Voucher number and Date provided on the year-end close dialog for your criteria, (**General Ledger > Inquiries and reports > Voucher transactions**).
[![Voucher transactions inquiry](./media/yec-mssng-open-blnces-03.png])(./media/yec-mssng-open-blnces-03.png)

If the opening (and optionally closing) vouchers are there, you don’t need to run the year-end close again. Instead refer to the next question for information on how to move forward.

The “Rebuild balances” step in the year-end close failed, do I need to re-run the entire year-end close process?

The Rebuild balances step updates the General ledger balances that are consumed by the Trial balance inquiry.  It is the final step in the year-end close process.  If this step is the only step that failed, the general ledger transactions have posted successfully.  You do not need to run the year-end close again. The rebuild of the balances can be executed manually using the Financial dimension sets form.  This can be performed by going to, (**General ledger > Chart of accounts > Dimensions > Financial dimension sets**).

If this step takes more time than you expected to process, we recommend reviewing the best practices for Financial dimension sets as described in the post that covers this process. For more information, see [Best practices for updating Financial dimension sets] (https://community.dynamics.com/365/financeandoperations/b/dynamics-365-finance-blog/posts/best-practices-for-updating-financial-dimension-set-dimension-sets). 

