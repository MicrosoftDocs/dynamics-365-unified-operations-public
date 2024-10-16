---
title: Year-end close validation
description: Learn how to validate the general ledger year-end close process. 
author: MOAAMER
ms.author: moaamer 
ms.topic: article
ms.date: 09/25/2024
ms.custom: evergreen 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerClosingSheet
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
---

# Year-end close validation

The **Year-end close validation** functionality introduces key checks to enhance accuracy and performance during the close process. It detects potential issues such as
degenerate dimensions, which can slow performance if over one million unique ledger combinations are identified. Additionally, it flags out-of-balance situations caused by
settled ledger transactions, overflow amounts exceeding, and unrounded amounts exceeding two decimal places. For each issue, the system provides guidance to optimize
performance, including enabling specific features or running a consistency check to resolve errors. To access the **Year-end close validation** function go to **General ledger|
Period close| Year end close**, then select #Validate year-end close#

**Degenerate dimensions**
The year-end close validation logic detects degenerate dimensions that could impact the close process and will trigger the following message: "Over one million unique ledger
dimension combinations have been identified, which could affect year-end close performance. Refer to official documentation for guidance. To prevent performance issues, avoid
using 'Close all' for degenerate dimensions; instead, select 'Close single.

**Out of balance**
The year-end close validation logic identifies an out-of-balance issue due to the enabled awareness between ledger settlement and the year-end close feature. Only settled
ledger transactions from the fiscal year being closed are excluded from the opening balance, which can cause debits and credits to become out of balance. When this occurs, the
following message is triggered: "There are out-of-balance vouchers that result in an out-of-balance error during the year-end close process. You can run a consistency check
and use the 'Fix error' option to resolve the issue.

**Transactions overflow flow**
The year-end close validation throws the following error message when transactions have overflow amounts " transactions have overflow amounts, with 16 digits or more including
decimal places, which may cause an out-of-balance error during the year-end close process. To address this, enable the 'Optimize year-end close' feature, reverse the original
documents causing overflows, or manually adjust the balances.”

**Transactions have unrounded amounts**
The year-end close validation throws the following error message when transactions have unrounded amounts: "%1 transactions have unrounded amounts, exceeding 2 decimal places,
which may cause an out-of-balance error during the year-end close process. To resolve this, enable the 'Optimize year-end close' feature, or run a consistency check and use
the 'Fix error' option."

[!include [banner](../includes/banner.md)]

This article describes how to validate the general ledger year-end close process.
