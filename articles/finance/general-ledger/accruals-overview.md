---
title: Accruals overview
description: Learn about accruals and how to set them up and create transactions, including overviews on accrual schemes and ledger accruals.
author: jchrist
ms.author: jchrist
ms.topic: overview
ms.date: 06/04/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerAccuralTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0489b59a-37a7-4a78-87bf-4b597e9efad9
---

# Accruals overview

[!include [banner](../includes/banner.md)]

This article describes accruals, and provides information about how to set them up and create transactions.

Use accruals in accrual accounting to track revenue that you recognize in the period that it's earned, not when payment is received. Use accruals to track expenses (costs) that you recognize when they occur, not when payment is made.

## Accrual schemes

Use accrual schemes to set up the deferred revenue and costs. You can use the same accrual scheme for both revenue and costs. Ledger accruals redistribute the costs or revenue of a journal line so that the costs and revenues are recognized in the appropriate periods. On the **Accrual scheme** page, specify the debit and the credit accounts that are used when you apply the accrual scheme.

- **Debit** – The main account that you define replaces the debit main account on the journal voucher line. This account is also used for the reversal of the deferral, based on the ledger accrual transactions.
- **Credit** – The main account that you define replaces the credit main account on the journal voucher line. This account is also used for the reversal of the deferral, based on the ledger accrual transactions.

After you determine which accounts to use, specify how the voucher number is created when you create accrual transactions. You can also specify how often the transactions occur, the number of times that the transactions are created, and when the transactions are posted. After you create the accrual scheme, use it in some of the journals by using the **Ledger accruals** function.

## Ledger accruals

When you enter a journal, you can select **Ledger accruals** on the **Functions** menu. Then, when you select the accrual scheme, you see the base amount from the journal that spreads over the period, as determined by the accrual scheme.

For example, if you pay an employee's insurance for the whole year in January, and the amount is 12,000, you must recognize that expense each month. You can select the start date. You can also specify whether the amount that is accrued is based on the account or the offset account. After you make your selections, select **Transactions** to view all the transactions that are created based on the accrual scheme. For example, if you spread the 12,000 in insurance expenses over the year, you see 1,000 for each month. After you post the journal, you can view the transactions by using the **Voucher transactions** inquiry page. If an accrual scheme can't be applied (for example, when a sales order invoice or purchase order invoice is involved), you can credit the prepaid amount and debit the expense amount. You can then select **Offset** when you apply the accrual scheme.

For more information, see [Create accrual schemes](tasks/create-accrual-schemes.md) and [Create ledger accrual transactions](tasks/create-ledger-accrual-transactions.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
