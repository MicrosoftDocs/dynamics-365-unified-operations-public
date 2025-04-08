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

[!include [banner](../includes/banner.md)]

This article explains how to validate the general ledger year-end close process.

The **Year-end close validation** feature helps improve accuracy and performance during the year-end close process. Here are some of the issues that it detects:

- Degenerate dimensions that can slow performance if more than one million unique ledger combinations are identified
- Out-of-balance entries that are caused by settled ledger transactions
- Overflow amounts that exceed 16 digits
- Unrounded amounts that exceed two decimal places

For each issue, the feature provides guidance that can help optimize performance. It might also recommend that you enable specific features or run a consistency check to fix errors.

To run year-end close validation, go to **General ledger** /> **Period close** /> **Year end close**, and select **Validate year-end close**.

## Validate year-end close errors

### Degenerate dimensions

If the year-end close validation logic detects any degenerate dimensions that affect the close process, the following message is shown:

> Over one million unique ledger dimension combinations have been identified and could affect year-end close performance. Refer to official documentation for guidance. To prevent performance issues, avoid using **Close all** for degenerate dimensions. Select **Close single**.

### Out-of-balance entries

The year-end close validation logic detects out-of-balance issues by using the enabled awareness between ledger settlement and the year-end close feature. The opening balance excludes only settled ledger transactions from the fiscal year that is being closed. These excluded transactions can cause debits and credits to be out of balance. If the logic detects any out-of-balance issues, the following message is shown:

> There are out-of-balance vouchers that result in an out-of-balance error during the year-end close process. You can run a consistency check and use the 'Fix error' option to resolve the issue.

### Transaction overflow

If the year-end close validation logic detects any transactions that have overflow amounts, the following error message is shown:

> Transactions have overflow amounts with 16 digits or more including decimal places, which may cause an out-of-balance error during the year-end close process. To address this, enable Optimize year-end close and reverse the original documents causing overflows, or manually adjust the balances.

### Transactions that have unrounded amounts

If the year-end close validation logic detects any transactions that have unrounded amounts, the following error message is shown:

> %1 transactions have unrounded amounts, exceeding two decimal places, which may cause an out-of-balance error during the year-end close process. To resolve this, enable the Optimize year-end close feature, or run a consistency check and use the 'Fix error' option.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
