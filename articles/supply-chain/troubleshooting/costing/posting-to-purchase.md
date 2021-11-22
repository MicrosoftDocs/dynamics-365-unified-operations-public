---
title: Purchase accrual that has a zero amount is posted for a zero-value product receipt
description: When a product receipt that has zero value is posted, the system creates a posting to purchase accrual where the amount is 0 (zero).
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

# Purchase accrual that has a zero amount is posted for a zero-value product receipt

KB number: 4612588

## Symptoms

When a product receipt that has zero value is posted, the system creates a posting to purchase accrual where the amount is 0 (zero).

## Resolution

By default, for ledger postings of the *Purchase, accrual* type, the `IsTransferredIndetail` field is always set to *Summary* in subledger transactions. Therefore, the system creates a related voucher entry even if the amount is 0 (zero).

To skip this posting type when the amount is 0 (zero), extend the `subledgerJournalizer.markDoNotTransferEntries` method so that it includes `ledgerPostingType = PurchPckSlpPurchaseOffsetAccount`, as shown in the following example.

```xpp
update_recordset existingSubledgerJournalAccountEntry
setting
    IsTransferredInDetail = TransferPolicy::DoNotTransfer
where existingSubledgerJournalAccountEntry.SubledgerJournalEntry == _subledgerJournalEntryRecId
    && (existingSubledgerJournalAccountEntry.AccountingCurrencyAmount == 0 && existingSubledgerJournalAccountEntry.ReportingCurrencyAmount == 0)
    && existingSubledgerJournalAccountEntry.PostingType == LedgerPostingType::PurchPckSlpPurchaseOffsetAccount;
```
