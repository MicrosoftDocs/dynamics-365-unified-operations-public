---
title: View liability, asset, and expense transactions
description: Learn about how to view transactions for a leased asset. These transactions include lease liability transactions and executory expense transactions that are posted.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: SysQueryForm
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# View liability, asset, and expense transactions

[!include [banner](../includes/banner.md)]

This article explains how to view transactions for a leased asset. These transactions include lease liability transactions and executory expense transactions that have been posted. The carrying values of the liability and right-of-use (ROU) asset are used on several reports. They are also used to calculate adjustment values.

## Liability transactions

To view the lease liability transactions, select a lease on the **Lease summary** page, and then select **Books** to open the books that are attached to the lease record. After an initial recognition, an invoice, or an interest journal has been posted, select **Liability transactions**.

The **Liability transactions** page shows the transactions that either increase or decrease the lease liability. Negative amounts on this page represent credit transactions in the standard application. Any interest accruals are shown as negative values and increase the total lease liability. Any lease adjustments are shown as positive or negative values, depending on the nature and impact of the lease book. The current net total balance of the lease liability for the selected lease is shown at the bottom left of the page.

## Asset transactions

To view the lease asset transactions, select a lease on the **Lease summary** page, and then select **Books** to open the lease books that are attached to the lease record. Then select **Asset transactions**.

The **Asset transaction** page shows the transactions that either increase or decrease the lease asset and accumulated depreciation accounts. Debits are shown as positive values, and credits are shown as negative values, as on the **Liability transactions** page. The posted initial recognition and the next of accumulated depreciation are shown at the bottom left of the page as the asset balance. 

## Expenses transactions

To view the lease expense transactions, select a lease on the **Lease summary** page, and then select **Books** to open the lease books that are attached to the lease record. Then select **Expense transactions**.

The **Expense transactions** page shows all the expenses that have been posted against the lease, such as interest expenses, depreciation expenses, and any executory costs.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
