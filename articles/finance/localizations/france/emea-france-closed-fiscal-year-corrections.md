---
title: Correct a closed fiscal year in France
description: Learn how to correct the accounting data of a fiscal year that's being closed or that's closed, so that the corrections stay traceable as required in France.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 11/16/2026
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Correct a closed fiscal year in France

[!include [banner](../../includes/banner.md)]

This article explains how a legal entity that has its primary address in France should correct the accounting data of a fiscal year that it's closing or already closed in Microsoft Dynamics 365 Finance. The procedure keeps corrections traceable and preserves the integrity of the opening balances of the next fiscal year.

## Rules that apply in France

- You can't change or delete validated accounting entries. A closing procedure freezes the chronology of the entries no later than the end of the following period. For more information, see the [Plan comptable général](https://www.anc.gouv.fr/plan-comptable-general-0).
- You can't reopen a closed fiscal year. Record corrections as reversing entries and new entries, never by deleting entries, and produce a new archive that matches the corrected return. For more information, see [BOI-BIC-DECLA-30-10-20-40](https://bofip.impots.gouv.fr/bofip/2899-PGP.html/identifiant=BOI-BIC-DECLA-30-10-20-40-20180720).
- If a correction changes a fiscal year that you already declared for tax purposes, you must be able to explain when the restatement took place, which entries you reversed, which new financial statements you produced, and which tax returns you amended. For information about corrected returns, see [Le droit à l'erreur en matière fiscale](https://www.impots.gouv.fr/professionnel/le-droit-lerreur-en-matiere-fiscale).

## Before the final closing: post adjustments in the closing period

Each fiscal year in Finance includes a closing period after the operating periods. Post year-end adjustments in the closing period instead of reopening the operating periods. 

To post adjustments in the closing period, follow these steps:

1. Set the operating periods of the fiscal year to **On hold**. Keep the closing period open, and restrict it to the users who post closing adjustments. For more information, see [Close the general ledger at period end](../../general-ledger/close-general-ledger-at-period-end.md).
1. Post the adjustments in the closing period. Use the **Closing period adjustments** page (**General ledger** \> **Period close** \> **Closing period adjustments**), or a general journal that's posted to the closing period.
1. Run the year-end close again. In **General ledger parameters**, set **Delete existing year-end entries when re-closing the year** to **No**. In this way, the earlier year-end close voucher is kept, and a new voucher is created only for the adjustments. For more information, see [Year-end close](../../general-ledger/year-end-close.md).

## After the final closing: post corrections in the open fiscal year

After the final closing of a fiscal year and the production of its tax archive:

- Don't reopen the fiscal year. Post the correction as reversing and correcting entries in the open fiscal year, and refer to the corrected fiscal year and the date of the original operation in the entry description and in the supporting documents.
- If you must correct a tax return, file the corrected return, and keep it in the tax archive together with the related entries.
- Set the fiscal year to **Permanently closed** so that no transactions can be posted to it.

## Reverse the year-end close

The **Reverse year-end close** function deletes the closing and opening entries of the previous year-end close. For legal entities in France, use this function only as an exception before the final closing, and only if adjustments in the closing period aren't enough. To reverse the year-end close, follow these steps so that the operation stays traceable:

1. Restrict the year-end close functions to a small group of authorized users.
1. Before you reverse the year-end close, generate the FEC and the trial balance of the fiscal year, and store them in the tax archive as the *before* version.
1. Record the reason, the approval, the date, and the user in a restatement note.
1. Reverse the year-end close.
1. Post the corrections, preferably in the closing period.
1. Run the year-end close again.
1. Generate the FEC and the trial balance again, and store them in the tax archive as the *after* version, next to the *before* version and the restatement note.
1. If the corrected fiscal year was already declared, file the corrected tax returns, and keep them in the tax archive.

The **Year-end close** page lists each run and each reversal of the year-end close. The year-end close vouchers are available on the **Voucher transactions** page.

## Additional resources

- [NF203 Computerized Accounting Certification in France](emea-france-nf203.md)
- [Tax archive in France](emea-france-tax-archive.md)
- [Year-end activities FAQ](../../general-ledger/faq-year-end-activities.md)
