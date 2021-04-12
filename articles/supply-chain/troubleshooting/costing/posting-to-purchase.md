---
title: Posting to purchase accrual with amount zero is created when product receipt is posted with zero value
description: The system creates a posting to purchase accrual with amount zero when a product receipt with zero value is posted
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: LedgerTransVoucher
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---
<!-- KFM: Title is over 80 characters. Please find a way to reduce -->
# Posting to purchase accrual with amount zero is created when product receipt is posted with zero value

KB Number: 4612588

## Issue description

The system creates a posting to purchase accrual with amount zero when a product receipt with zero value is posted.

## Resolution

For ledger postings of type purchase, accrual <!-- KFM: Is this two types ("purchase" and "accrual") or one type  ("purchase, accrual")? --> , the IsTransferredIndetail <!-- KFM: Please use the field label, not the internal name --> field is always marked with Summary <!-- KFM: Do you mean the field has a value of "Summary"? --> by default in subledger transactions.  Therefore, the system creates a related voucher entry regardless of whether the amount is zero or not.

If you would like to skip this posting type when the amount is zero, extend the `subledgerJournalizer.markDoNotTransferEntries` method to include `ledgerPostingType = PurchPckSlpPurchaseOffsetAccount`, as illustrated in the following example:

```xpp
update_recordset existingSubledgerJournalAccountEntry
setting
    IsTransferredInDetail = TransferPolicy::DoNotTransfer
where existingSubledgerJournalAccountEntry.SubledgerJournalEntry == _subledgerJournalEntryRecId
    && (existingSubledgerJournalAccountEntry.AccountingCurrencyAmount == 0 && existingSubledgerJournalAccountEntry.ReportingCurrencyAmount == 0)
    && existingSubledgerJournalAccountEntry.PostingType == LedgerPostingType::PurchPckSlpPurchaseOffsetAccount;
```
