---
# required metadata

title: Why can't I reverse this transaction?
description: This topic describes different reasons why transactions can't be reversed. It also lists solutions for this issue.
author: kweekley
ms.date: 07/21/2021
ms.topic: article
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
ms.search.validFrom: 2021-07-21
ms.dyn365.ops.version: 10.0.20

---

# Why can't I reverse this transaction?

[!include [banner](../includes/banner.md)]

This topic describes different reasons why transactions can't be reversed. It also lists solutions for this issue.

## Symptom

Organizations might encounter situations where they must reverse a transaction that they have posted. Occasionally, the system will prevent them from reversing these transactions. This behavior can prompt two questions:

- Why can't I reverse the transaction?
- How does the Mass reversal feature affect this behavior?

## Resolution

Transactions must meet specific criteria before they can be reversed. The remaining sections of this topic provide the validation for each module. Although this topic focuses on transactions in Microsoft Dynamics 365 Finance, some of the concepts and validation can be applied to other apps, such as Dynamics 365 Supply Chain Management.

Additionally, the place where a transaction is reversed might affect whether it can be reversed. For example, a vendor payment that is posted as a check can be reversed only from the **Checks** section on the transaction page for the bank accounts. It can't be reversed from the **Voucher transactions** page in General ledger.

If the **Mass reversal for multiple documents** feature (also known as the Mass reversal feature) is turned on in the **Feature management** workspace, it affects how many transactions can be reversed and where they can be reversed. This feature provides two benefits when it's turned on:

- For some types of transactions, more than one transaction at a time can be selected and reversed from the journal that it was posted from, or from the **Voucher transactions** page. However, the individual transactions must have been reversible before the feature was turned on. Before this feature was introduced, transactions had to be reversed one at a time.
- *Some* subledger transactions can be reversed from the journal (general journal) or the **Voucher transactions** page. They don't have to be reversed from the subledger page. For example, a vendor invoice journal could previously be reversed only from the **Vendor transactions** page. However, it can now be reversed from the General ledger side too, from the journal or the **Voucher transactions** page. Each section of this topic explains the types of transactions that this benefit doesn't apply to.

The Mass reversal feature does **not** enable more types of transactions to be reversed. If a transaction type could not previously be reversed, it still can't be reversed after the feature is turned on. For example, purchase order vendor invoices can't be reversed, regardless of whether the Mass reversal feature is turned on.

For more information about the Mass reversal feature, see [Reverse journal posting](reverse-journal-posting.md).

## General ledger

General ledger adjustments are entered only by using ledger accounts. Therefore, they update only General ledger.

If the Mass reversal feature is turned off, most general ledger adjustments can be reversed individually from the **Transactions for \<main account\>** page for the ledger (**LedgerTransAccount**). (The exact title of the page varies, depending on the selected main account.) The page shows each transaction that has been posted to the main account. It's typically opened from the **Trial balance list** page, or by selecting **Transactions** on the **Voucher transactions** page.

If the Mass reversal feature is turned on, one or more general ledger vouchers can now be reversed from the **Voucher transactions** page, and from the journal that the transaction was posted from. The exceptions are General ledger foreign currency revaluation, consolidation, and year-end close transactions. Those transactions are reversed from the pages that the year-end close was run from.

### Reasons why transactions can't be reversed

Transactions can't be reversed for the following reasons:

- General journal:

    - The fiscal period is on hold or permanently closed:

        - If the reversing date is in a fiscal period that isn't open, the transaction can't be reversed.
        - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.

    - The year-end close process has been run:

        - The transaction's accounting date is in a fiscal year that has been through a year-end close. Although a period in the fiscal year might still be open, the transaction can't be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods in it.
        - The year-end close can be reversed, and then the transaction can be reversed. This approach might not be an option. It might be easier to manually enter a reversing transaction in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close process. If a new transaction is posted to an open period of the fiscal year that has been through the year-end close process, the year-end close must be run again.

    - Transaction reversal is already in process:

        - If the transaction is in the process of being reversed, that process must be completed. A separate reversal process can't be done. 
        - After the reversal is completed, a reversed transaction can be reversed again (that is, the reversal can be reversed).

    - Ledger settlement:

        - If one or more lines of the transaction have been ledger-settled by using the **Ledger settlements** periodic task (**General ledger \> Periodic tasks \> Ledger settlements**), so that the record exists in the LedgerTransSettlement table, the transaction can't be reversed.
        - The ledger settlement can be reversed, and then the voucher can be reversed.

    - Intercompany:

        - If the transaction is an intercompany transaction, it can't be reversed.
        - The transaction is **not** an intercompany transaction, but is posted to a "due to" or "due from" main account that was defined on the **Intercompany setup** page.

    - Accruals:

        - If the accrued general ledger voucher is reversed, the accrued entry and all the corresponding accrual sub-transactions will be reversed.
        - The individual accrual sub-transactions can't be reversed.

- Revenue recognition journal:

    - Revenue recognition transactions can't be reversed.
    - When revenue is recognized through the revenue recognition journal, the voucher is posted only to ledger accounts. Therefore, on pages such as **Voucher transactions**, the transactions appear as if they are only general ledger entries.

- Foreign currency revaluation:

    - Foreign currency revaluation transactions can be reversed, but only from the General ledger **Foreign currency revaluation** page that the revaluation was run from.
    - The reversal can be completed only if it's posted to an open fiscal period.

- Consolidation:

    - Consolidation transactions can be reversed, but only from the **Consolidation transactions** page.
    - The reversal can be completed only if it's posted to an open fiscal period.

- Year-end close:

    - Year-end close transactions (both closing and opening transactions) can be reversed in these ways:

        - If the General ledger year-end close enhancements feature is turned off, select the **Undo previous close** option in the **Year-end close** dialog box.
        - If the General ledger year-end enhancements feature is turned on, select the company and fiscal year records that were created for the year-end close on the **Year-end close** page, and then select **Reverse year-end close**.

    - Note that reversal of the year-end close actually deletes the closing and opening transactions. A reversing voucher is never posted.

## Accounts payable

Multiple transaction types update the Accounts payable subledger. Examples include vendor invoices, vendor invoice journals, and expense reports.

If the Mass reversal feature is turned off, transactions can be reversed individually from either the **Vendor transactions** page for invoices or the **Bank account** page for check payments.

If the Mass reversal feature is turned on, one or more Accounts payable transactions can also be reversed from the **Voucher transactions** page, and from the journal that the transactions were posted from. However, vendor payments can still be reversed only from the bank account. Additionally, vendor transactions can't be reversed from the **Transactions for \<main account\>** page for the ledger. They can be reversed only from the **Voucher transactions** page.

Note that some transactions can't be reversed at all. Examples include purchase order vendor invoices and electronic vendor payments.

### Reasons why vouchers can't be reversed

Vouchers can't be reversed for the following reasons:

- The fiscal period is on hold or closed:

    - If the reversing date is in a fiscal period that isn't open, the transaction can't be reversed.
    - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.

- The General ledger year-end close process has been run:

    - The transaction's accounting date is in a fiscal year that has been closed in General ledger. Although a period in the fiscal year might still be open, the transaction can't be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods in it.
    - The year-end close can be reversed, and then the transaction can be reversed. This approach might not be an option. It might be easier to manually enter a reversing transaction in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close process. If a new transaction is posted to an open period of the fiscal year that has been through the year-end close process, the year-end close must be run again.

- The subledger journal entry hasn't been transferred to General ledger:

    - This reason applies only to non-purchase order vendor invoices.
    - Use the **Subledger journal entries not yet transferred** page to transfer the entry to General ledger. The non-purchase order vendor invoice can then be reversed from the **Vendor transactions** page.

- Settlement:

    - The transaction (such as an invoice or payment) is settled or marked for settlement.

        - You can verify whether a transaction is settled or marked for settlement by selecting **View settlements** or **Settlement \> Settlement history** on the **Vendor transactions** page.
        - You can also reverse a settlement from the **Vendor transactions** page (**Settlement \> Undo settlement**) if one of the transactions must be reversed.

- The voucher contains more than one subledger transaction that was entered by using the same voucher number (One voucher issue).
- The invoice hasn't been approved:

    - If the **Approval** checkbox isn't selected on the invoice, the invoice can't be reversed.

        - In this case, approval doesn't refer to approvals in the workflow process but to the **Approval** option on the invoice. This option is used to prevent an invoice from being paid. It's typically used for vendor invoice register invoices.

- The transaction is in the invoice pool:

    - An invoice in the pool can't be reversed directly from the **Vendor transactions** page. Instead, it must be reversed through the cancellation process on the **Invoice approval journal** page.

- The transaction has a parent invoice that has been corrected (Indian localization).
- The transaction has a promissory status of **Invoice remitted**.
- The transaction is used for a partial tax settlement.
- The transaction contains a vendor account but is being reversed from an incorrect page, such as the **Transactions for \<main account\>** page:

    - As this reason suggests, even when the Mass reversals feature is turned on, some subledger transactions can be reversed only from specific pages.

### Types of transactions that can't be reversed

The following types of transactions can't be reversed:

- Foreign currency revaluation:

    - Unlike General ledger foreign currency revaluation, Accounts receivable and Accounts payable foreign currency revaluation can't be reversed. Instead, the revaluation must be run again by using the invoice date. In this case, the revaluation uses the exchange rate from the invoice's date, and essentially brings the unrealized gain or loss to 0 (zero). Therefore, the result resembles the result of reversing the previous revaluation. However, note that the same amount won't be reversed if the default exchange rate was changed on the invoice.

- Purchase order vendor invoice:

    - A credit note must be created to reverse the vendor invoice. For more information about how to create a reversing transaction, see [Create a purchase return order](../../supply-chain/procurement/tasks/create-purchase-return-order.md).

- Promissory note
- Bank letter of credit export shipment

## Accounts receivable

Several transaction types update Accounts receivable subledgers. Examples include customer invoices from sales orders, customer invoices that are entered through the general journal, free text invoices, customer payments, and write-offs.

If the Mass reversal feature is turned off, transactions can be reversed individually from either the **Customer transactions** page for invoices or the **Bank accounts** page for deposits. For information about how to reverse a payment, see the [Cash and bank management](cant-reverse-transctns.md#cash-and-bank-management) section later in this topic.

If the Mass reversal feature is turned on, one or more Accounts receivable transactions can also be reversed from the **Voucher transactions** page and the journal that it was posted from. However, deposits can still be reversed only from the bank account, and free text invoices can be reversed only from the originating page (if the feature that allows for corrections is turned on). Additionally, customer transactions still can't be reversed from the **Transactions for \<main account\>** page for the ledger. However, they can be reversed from the **Voucher transactions** page.

Note that some transactions can't be reversed. Examples include sales order customer invoices and write-offs.

### Reasons why transactions can't be reversed

Transactions can't be reversed for the following reasons:

- The fiscal period is on hold or permanently closed:

    - If the reversing date is in a fiscal period that isn't open, the transaction can't be reversed.
    - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.

- The General ledger year-end close process has been run:

    - The transaction's accounting date is in a fiscal year that has been through a General ledger year-end close. Although a period in the fiscal year might still be open, the transaction can't be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods in it.
    - The year-end close can be reversed, and then the transaction can be reversed. This approach might not be an option. It might be easier to manually enter a reversing transaction in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close process. If a new transaction is posted to an open period of the fiscal year that has been through the year-end close process, the year-end close must be run again.

- The subledger journal entry hasn't been transferred to General ledger:

    - This reason applies only to free text invoices.
    - Use the **Subledger journal entries not yet transferred** page to transfer the entry to General ledger. The free text invoice can then be reversed or corrected if the corrections functionality is enabled.

- Settlement:

    - The transaction (such as an invoice or payment) is settled or marked for settlement.

        - You can verify whether a transaction is settled or marked for settlement by selecting **View settlements** or **Settlement \> Settlement history** on the **Customer transactions** page.
        - You can also reverse a settlement from the **Customer transactions** page (**Settlement \> Undo settlement**) if one of the transactions must be reversed.

- The transaction contains more than one subledger transaction that was entered by using the same voucher number (One voucher issue).
- The invoice hasn't been approved:

    - If the **Approval** checkbox isn't selected on the invoice, the invoice can't be reversed.

        - In this case, approval doesn't refer to approvals in the workflow process but to the **Approval** option on the voucher lines. This option is used to prevent an invoice from being paid. Although this option is typically used in Accounts payable, it's also available for Accounts receivable invoices that are entered through journals.

- The transaction has a parent invoice that has been corrected (Indian localization).
- The transaction contains a customer account but is being reversed from an incorrect page, such as the **Transactions for \<main account\>** page:

    - As this reason suggests, even when the Mass reversals feature is turned on, some subledger transactions can be reversed only from specific pages.

### Types of transactions that can't be reversed

The following types of transactions can't be reversed:

- Foreign currency revaluation:

    - Unlike General ledger foreign currency revaluation, Accounts receivable and Accounts payable foreign currency revaluation can't be reversed. Instead, the revaluation must be run again by using the invoice date. In this case, the revaluation uses the exchange rate from the invoice's date, and essentially brings the unrealized gain or loss to 0 (zero). Therefore, the result resembles the result of reversing the previous revaluation. However, note that the same amount won't be reversed if the default exchange rate was changed on the invoice.

- A transaction that has adjusted tax withholding
- Sales order customer invoice:

    - A credit note or return must be created to reverse the transaction. For information about how to create the reversing transaction, see [Sales returns](../../supply-chain/warehousing/sales-returns.md).

- Bill of exchange
- Cash register transaction
- Advanced adjustment
- Interest note
- Collections letter
- Bank letter of credit
- Export shipment
- Revenue recognition journal:

    - When you recognize revenue through the revenue recognition journal, the vouchers are posted to ledger accounts. Therefore, they appear as if they are only general ledger entries. These entries can't be reversed, because the revenue schedule won't be reopened to recognize the revenue again.

## Cash and bank management

Several transaction types update the Bank subledger through the general journal. Examples include vendor payments, customer payments, and bank transfers.

If the Mass reversal feature is turned off, transactions can be reversed individually from the **Bank accounts** page for checks and deposits, or from the **Customer transactions** page for customer payments.

If the Mass reversal feature is turned on, one or more payment transactions can also be reversed from the **Voucher transactions** page, and from the journal that the transactions were posted from. However, deposits can still be reversed only from the bank account. Additionally, bank transactions still can't be reversed from the ledger's **Transactions for \<main account\>** page. However, they can be reversed from the **Voucher transactions** page.

Note that some transactions can't be reversed. Examples include electronic vendor payments.

### Reasons why transactions can't be reversed

Transactions can't be reversed for the following reasons:

- The fiscal period is on hold or permanently closed:

    - If the reversing date is in a fiscal period that isn't open, the transaction can't be reversed.
    - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.

- The General ledger year-end close process has been run:

    - The transaction's accounting date is in a fiscal year that has been through a General ledger year-end close. Although a period in the fiscal year might still be open, the transaction can't be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods in it.
    - The year-end close can be reversed, and then the transaction can be reversed. This approach might not be an option. It might be easier to manually enter a reversing transaction in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close process. If a new transaction is posted to an open period of the fiscal year that has been through the year-end close process, the year-end close must be run again.

- Settlement:

    - The transaction (payment) is settled or marked for settlement.

        - You can verify whether a transaction is settled or marked for settlement by selecting **View settlements** or **Settlement \> Settlement history** on the **Vendor transactions** or **Customer transactions** page.
        - You can also reverse a settlement from the **Vendor transactions** or **Customer transactions** page (**Settlement \> Undo settlement**) if one of the transactions must be reversed.

- The transaction contains more than one subledger transaction that was entered by using the same voucher number (One voucher issue).
- Bridged transactions:

    - If the transaction is related to a bridging payment, it can't be reversed.
    - If the bridged payment must be reversed, the payment first has to be cleared from the bridging account to the bank. The payment can then be reversed, provided that it meets the other validation criteria.

- The transaction contains a bank account, but is being reversed from the **Transactions for \<main account\>** page or from an incorrect subledger, such as Accounts receivable or Accounts payable:

    - As this reason suggests, even when the Mass reversals feature is turned on, some subledger transactions can be reversed only from specific pages.

- Bank foreign currency revaluation:

    - Bank foreign currency revaluation can be reversed. However, reversal might be prevented if you complete the reversal steps out of chronological order. For example, if you ran the revaluation in March and April, the March revaluation can't be reversed until the April revaluation is reversed.

### Types of transactions that can't be reversed

The following types of transactions can't be reversed:

- Vendor payments that were made as electronic funds transfers (EFTs)
- Promissory notes
- Bills of exchange

## Fixed assets

Several transaction types update the Fixed assets subledger. Examples include acquisitions and depreciation.

If the Mass reversal feature is turned off, transactions can be reversed individually from the **Vendor transactions** page, from the **Fixed asset transactions** page, or from Asset leasing, depending on the transaction type.

If the Mass reversal feature is turned on, one or more Fixed asset transactions can also be reversed from the **Voucher transactions** page in the journal that the transactions were posted from.

### Reasons why transactions can't be reversed

Transactions can't be reversed for the following reasons:

- The fiscal period is on hold or permanently closed:

    - If the reversing date is in a fiscal period that isn't open, the transaction can't be reversed.
    - If the transaction supports entry of a reversing date, the transaction can still be reversed by changing the reversal date to an open period.

- The General ledger year-end close process has been run:

    - The transaction's accounting date is in a fiscal year that has been closed in General ledger. Although a period in the fiscal year might still be open, the transaction can't be reversed if the year-end close process has been run for the fiscal year. The fiscal year has a different status than the periods in it.
    - The year-end close can be reversed, and then the transaction can be reversed. This approach might not be an option. It might be easier to manually enter a reversing transaction in an open period of either the closed fiscal year or the next fiscal year, depending on the status of the fiscal close process. If a new transaction is posted to an open period of the fiscal year that has been through the year-end close process, the year-end close must be run again.

- Acquisitions:

    - If the acquisition occurred on a purchase order vendor invoice, the reversal must be done by entering a vendor credit note. For information about how to enter the reversal transaction, see [Create a purchase return order](../../supply-chain/procurement/tasks/create-purchase-return-order.md).
    - The acquisition occurred on a project transaction.
    - The acquisition can't be reversed after depreciation is posted for the asset. The depreciation must be reversed before the acquisition can be reversed.
    - If the status of the value model or depreciation book for a fixed asset isn't open, the transaction can't be reversed.

- Disposals:

    - The disposal is done through a free text invoice:

        - The correction of a free text invoice is blocked if it contains a fixed asset. However, if the asset is disposed of through a journal, the free text invoice can be reversed from the fixed asset record.

    - If the status of the value model or depreciation book for a fixed asset isn't open, the transaction can't be reversed.

- Depreciation:

    - The depreciation **can** be reversed if subsequent depreciation is also posted. However, you will receive a warning, because this approach isn't a best practice.
    - If the status of the value model or depreciation book for a fixed asset isn't open, the transaction can't be reversed.

- Transactions (or reverse transactions) for a specific asset and asset book exist for the voucher's transaction date or later.
- The transaction contains an asset account, but is being reversed from the **Transactions for \<main account\>** page or from an incorrect subledger, such as Accounts receivable or Accounts payable:

    - As this reason suggests, even when the Mass reversals feature is turned on, some subledger transactions can be reversed only from specific pages.
    - If an acquisition occurs on a non-purchase order vendor invoice or a vendor invoice journal, it can be reversed only from the **Vendor transactions** page in Accounts payable.
    - If an asset is acquired from Asset leasing, it can be reversed from the **Liability transactions** page in Asset leasing.
