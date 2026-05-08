---
title: Delete a main account
description: Learn how to delete a main account, when deletion is blocked, and how to retire accounts that can't be deleted.
author: anaborges02
ms.author: aolson
ms.topic: article
ms.date: 05/06/2026
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: MainAccount
---

# Delete a main account

[!include [banner](../includes/banner.md)]

This article describes how to delete a main account, the circumstances that block deletion, and the recommended workaround when you can't delete an account.

## Delete a main account

1. Go to **General ledger** > **Chart of accounts** > **Accounts** > **Main accounts**.
1. Select the main account that you want to delete.
1. Select **Delete**, and confirm the action.

The system runs a reference check against ledger transactions, dimension value combinations, and posting profiles before it commits the deletion. While the check is running, you might see the following message:

> The MainAccount '*account number*' is currently being checked for references before it can be deleted. It can't be deleted until the process is complete.

## When you can't delete a main account

You can't delete a main account if any of the following conditions are true:

- It's used on any posted ledger transaction, or on an unposted journal line.
- It's used in any ledger account on the chart of accounts, even if the transaction that originally used it was reversed or deleted.
- It's set as a default account on a posting profile, the ledger setup, module parameters, or a posting setup such as fixed assets or inventory.
- It's referenced by an account structure, an advanced rule structure, or the Financial Reporting setup.

If the reference check identifies the blocker, remove the reference - for example, clear the posting profile - and retry. If you ever used the account in a ledger account, deletion is permanently blocked, even after you remove every transaction that referenced the combination.

## Autocreated main accounts in a consolidation entity

When you run an online consolidation against an unmapped or partially mapped account, the system automatically creates the missing main account in the consolidation entity's chart of accounts so the transaction can post.

Even if you later reverse or delete the consolidation transactions, the ledger account created during the consolidation remains on file. As a result, you can't delete the autocreated main account from the consolidation entity. This behavior is by design.

To avoid this scenario:

- Validate account mapping on the consolidation account group before running a consolidation.
- Run test consolidations in a sandbox or nonproduction legal entity.

If autocreated accounts already exist in the consolidation entity, retire them rather than delete them:

- Suspend the main account so you can't select it on new transactions, or
- Rename the account to indicate it shouldn't be used (for example, `_DONOTUSE_<oldname>`).

For more information about online consolidations, see [Consolidate online](consolidate-online.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
