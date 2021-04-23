---
title: Purchase accrual posted with amount zero for zero-value product receipt
description: The system creates a posting to purchase accrual with amount zero when a product receipt with zero value is posted
author: niwang
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

# Purchase accrual posted with amount zero for zero-value product receipt

KB Number: 4612588

## Symptoms

The system creates a posting to purchase accrual with amount zero when a product receipt with zero value is posted.

## Resolution

For ledger postings of type *Purchase, accrual*, the field `IsTransferredIndetail` is always set to a value of *Summary* by default in subledger transactions. Therefore, the system creates a related voucher entry regardless of whether the amount is zero or not.

If you would like to skip this posting type when the amount is zero, extend the `subledgerJournalizer.markDoNotTransferEntries` method to include `ledgerPostingType = PurchPckSlpPurchaseOffsetAccount`, as illustrated in the following example:

```xpp
update_recordset existingSubledgerJournalAccountEntry
setting
    IsTransferredInDetail = TransferPolicy::DoNotTransfer
where existingSubledgerJournalAccountEntry.SubledgerJournalEntry == _subledgerJournalEntryRecId
    && (existingSubledgerJournalAccountEntry.AccountingCurrencyAmount == 0 && existingSubledgerJournalAccountEntry.ReportingCurrencyAmount == 0)
    && existingSubledgerJournalAccountEntry.PostingType == LedgerPostingType::PurchPckSlpPurchaseOffsetAccount;
```
