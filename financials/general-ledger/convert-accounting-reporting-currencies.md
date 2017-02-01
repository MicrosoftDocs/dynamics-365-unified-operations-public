---
# required metadata

title: Convert accounting or reporting currencies | Microsoft Docs
description: 
author: RobinARH
manager: AnnBe
ms.date: 2016-04-05 14:45:05
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 78223
ms.assetid: a619d9e4-8f41-4452-a81c-f1f134215856
ms.region: Global
# ms.industry: 
ms.author: aolson

---

# Convert accounting or reporting currencies



A company that must change its accounting currency or reporting currency has two options. The first option is to create a new company and start fresh. The second option is to run the accounting and reporting currency conversion process. This is a very long-running process that changes every transaction in the system. Some setup is also required before the process can be run.

## Preparing the legal entity for currency conversion
Before you can convert the legal entity’s currency, you must revert any foreign currency revaluation amounts for customer and vendor accounts, and close the previous fiscal years. You must also prepare the database for the conversion, and then make the required changes to the legal entity’s account that is undergoing the currency conversion. After you have completed a currency conversion, you must complete some additional procedures. You must reconcile rounding differences in converted amounts, recalculate business statistics, journalize the ledger transactions, limit access to the conversion tool, and revalue foreign currency amounts for customer and vendor accounts.

## Setting up accounts for automatic transactions
During the currency conversion process, gains or losses, or penny differences, are posted to the accounts that are defined on the **Accounts for automatic transactions** page. Main accounts must be assigned to the following types of transaction before the conversion process is run:

-   Accounting currency conversion gain
-   Accounting currency conversion loss
-   Penny difference in accounting currency
-   Penny difference in reporting currency
-   Year-end result

## Posting rounding differences and sum recalculations
The following information explains where differences in rounding might occur:

-   If product prices have been converted to 0 (zero), a report is generated that shows the product number, module type, price before the conversion, and unit.
-   Rounding differences between sales tax and the general ledger are posted to the general journal.
-   Foreign currency revaluation amounts are recalculated, and customer and vendor transaction amounts are recalculated.
-   Customer and vendor settlement records are created for rounding differences for each customer and vendor transaction.
-   Rounding differences for customers and vendors are posted to the general journal.
-   Settled cost amounts and cost adjustment amounts in closed inventory transactions are recalculated.
-   Rounding differences in Inventory management are posted to the general journal.
-   On-hand inventory is recalculated.
-   Total amounts in ledger journals are recalculated.
-   Ledger closing sheets are recalculated.
-   Ledger balances are recalculated.
-   Rounding differences in General ledger are posted to the general journal.
-   Opening ledger transactions are recalculated.
-   The final amount in the ledger balances is calculated.

If you're converting to a new ledger accounting currency, and an error occurs during the recalculation of total amounts or the posting of rounding differences, you must close the **Ledger accounting currency conversion** page. The total amounts are then recalculated, and the rounding differences are posted.

## Processing the currency conversion
When you start the currency conversion process, all users must be signed out of the system. You must define the new ledger or reporting currency, and the exchange rates. When you click **OK**, the process runs and updates every transaction in the system. Currency conversion is a very long process. When it's completed, you will see that the accounting or reporting currency is updated on the **Ledger** page.

## Completing the currency conversion
After the currency conversion, you must generate all reconciliation reports again to make sure that all converted amounts are correct.

-   If the conversion of the ledger accounting currency causes rounding differences, these differences aren't posted by using the voucher where the rounding difference occurred. Instead, the differences are posted by using the voucher that was entered for the conversion postings. After the conversion, all reports that check by voucher and date include these rounding differences. This behavior is correct and can be ignored.
-   If the customer and vendor reconciliation reports display a difference amount on the total line, and no difference amount existed before the conversion, this difference amount must be posted. The account is the summary account for customers and vendors. The offset account is the ledger account for conversion loss or conversion profit.

When all ledger transaction journals have been deleted, you can journalize the ledger transactions. Click **General ledger** &gt; **Periodic** &gt; **Journals** &gt; **Journalizing**. You can revalue foreign currency amounts after the currency conversion, if revaluation is required. You revalue foreign currency amounts by selecting **Standard** in the **Method** field for the revaluation.

