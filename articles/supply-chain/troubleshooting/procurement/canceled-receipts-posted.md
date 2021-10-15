---
title: Transactions can be posted to a suspended ledger account
description: If a product receipt is canceled, the system allows transactions to be posted to suspended ledger accounts, even though the main accounts are suspended
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# Transactions can be posted to a suspended ledger account

## Symptoms

If a product receipt is canceled, the system allows transactions to be posted to suspended ledger accounts, even though the main accounts are suspended.

## Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. On the **Accounts payable parameters** page, on the **General** tab, make sure that the **Post product receipt in ledger** option is set to *Yes*.
1. Create a purchase order, and add an order line that has a quantity of *1,000* for a product.
1. Confirm the purchase order.
1. Post the product receipt, and check the vouchers.
1. Suspend the relevant main accounts, *200140* and *140200*.
1. Cancel the posted product receipt.
1. Notice that transactions can be posted to the suspended leger accounts.

## Resolution

Transactions can be posted to the suspended leger accounts when product receipts are canceled, because this behavior allows for correct postings.
