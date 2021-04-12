---
# required metadata

title: Posting to Purchase accrual with amount zero is created when product receipt is posted with zero value
description: Posting to Purchase accrual with amount zero is created when product receipt is posted with zero value
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerTransVoucher
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: smnatara@microsoft.com

---

# Posting to Purchase accrual with amount zero is created when product receipt is posted with zero value

KB Number: 4612588

Posting to Purchase accrual with amount zero is created when product receipt is posted with zero value


## Resolution
For ledger posting type = Purchase, accrual, the IsTransferredIndetail field is always marked with Summary by default in subledger transactions.  Therefore, the related voucher entry will be created no matter the amount is zero or not.

If one would like to skip this posting type when amount is zero, one can extend this method subledgerJournalizer.markDoNotTransferEntries to include ledgerPostingType = PurchPckSlpPurchaseOffsetAccount like below

        update_recordset existingSubledgerJournalAccountEntry
        setting
            IsTransferredInDetail = TransferPolicy::DoNotTransfer
        where existingSubledgerJournalAccountEntry.SubledgerJournalEntry == _subledgerJournalEntryRecId
            && (existingSubledgerJournalAccountEntry.AccountingCurrencyAmount == 0 && existingSubledgerJournalAccountEntry.ReportingCurrencyAmount == 0)
            && existingSubledgerJournalAccountEntry.PostingType == LedgerPostingType::PurchPckSlpPurchaseOffsetAccount;




