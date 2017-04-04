---
# required metadata

title: CODA bank statement
description: This topic includes information about CODA, which is a report format used in the Belgian electronic banking system. 
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: BankAccountTable, BankCodaAccountStatement, BankCodaAccountStatementLines, BankCodaParameters, BankCodaTrans, BankCodaTransCategory, BankCodaTransDefTable, BankCodaTransFamily
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 262534
ms.assetid: 38a1f540-1488-4b63-b850-04e270622296
ms.search.region: Belgium
# ms.search.industry: 
ms.author: v-lenest
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# CODA bank statement

This topic includes information about CODA, which is a report format used in the Belgian electronic banking system. 

For Belgian bank statement imports, you'll use the CODA file format. This feature lets you verify company bank account opening and ending balances, and reconcile imported transactions based on reconciliation rules.

## Import transactions from a bank statement
To import a bank statement file for a bank account, complete the following steps. **Note**: Before you import a bank statement file, you must have already completed the following:

-   Import the CODA configurations from Lifecycle Services (LCS). For more information, see [Download Electronic reporting configurations from Lifecycle Services](/dynamics365/operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).
-   Select the imported CODA configuration on the **CODA parameters** page.

1.  Go to the **Bank accounts** page.
2.  Click **Reconcile** &gt; **CODA**.
3.  Click **CODA** &gt; **Import from file**, and then select the path to the bank statement file.

After you import transactions, you can do the following on the **Bank statement** page.

-   Verify the opening and ending balances.
-   View the imported transactions as a bank statement report that you can print.
-   View imported transactions with additional lines, such as lines with an Account type of "None". Click **CODA &gt; Details**.

## Process imported bank statement transactions
Complete the following steps to process the bank statement transactions.

1.  Process details lines (**CODA** &gt; **Process detail lines**). Start automatic matching based on **CODA definitions**. These rules determine which ledger, customer, or vendor account should be used for this transaction. Comparison is based on which Transaction group code, Transaction code, and Transaction category code are specified in CODA file for each transaction.
2.  Transactions with a customer and vendor account type can be matched with the invoices. If necessary, imported transactions can be manually changed at any time after processing, before transferring to the ledger.
3.  If there are any transactions with errors (generally, if there are no rules set up), these can be referred to the special ledger account, specified on the **CODA parameters **page (**CODA** &gt; **Clear errors**).
4.  After all transactions in the bank statement are settled, they are ready to be transferred to the general ledger journal (**CODA** &gt;**Transfer to ledger**). Journal settings should be specified for the bank account. Journals can be opened on the **Bank accounts **page for the selected record by clicking **Set up** &gt; **CODA journal**.

After processing bank statement transactions is complete, a new general ledger journal is created and ready for posting.

