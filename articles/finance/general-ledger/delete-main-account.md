---
title: Delete a main account
description: Learn how to delete a main account, when deletion is blocked, and how to retire accounts that can't be deleted.
author: anaborges02
ms.author: aolson
ms.topic: article
ms.date: 05/06/2026
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: MainAccount
---

# Delete a main account

[!include [banner](../includes/banner.md)]

This article describes how to delete a main account, the circumstances under which deletion is blocked, and the recommended workaround when an account can't be deleted.

## Delete a main account

1. Go to **General ledger** > **Chart of accounts** > **Accounts** > **Main accounts**.
2. Select the main account that you want to delete.
3. Select **Delete**, and confirm the action.

The system runs a reference check against ledger transactions, dimension value combinations, and posting profiles before the deletion is committed. While the check is running, you might see the following message:

> The MainAccount '*account number*' is currently being checked for references before it can be deleted. It cannot be deleted until the process is complete.

## When a main account can't be deleted

A main account can't be deleted if any of the following are true:

- It's used on any posted ledger transaction, or on an unposted journal line.
- It's been used in any ledger account on the chart of accounts, even if the transaction that originally used it was reversed or deleted.
- It's set as a default account on a posting profile, the ledger setup, module parameters, or a posting setup such as fixed assets or inventory.
- It's referenced by an account structure, an advanced rule structure, or the Financial Reporting setup.

If the reference check identifies the blocker, remove the reference — for example, clear the posting profile — and retry. If the account has ever been used in an ledger account, deletion is permanently blocked, even after every transaction that referenced the combination has been removed.

## Auto-created main accounts in a consolidation entity

When you run an online consolidation against an unmapped or partially mapped account, the system automatically creates the missing main account in the consolidation entity's chart of accounts so the transaction can post.

Even if you later reverse or delete the consolidation transactions, the ledger account created during the consolidation remain on file. As a result, the auto-created main account can't be deleted from the consolidation entity. This is by design.

To avoid this scenario:

- Validate account mapping on the consolidation account group before running a consolidation.
- Run test consolidations in a sandbox or non-production legal entity.

If auto-created accounts already exist in the consolidation entity, the supported approach is to retire them rather than delete them:

- Suspend the main account so it can't be selected on new transactions, or
- Rename the account to indicate it shouldn't be used (for example, `_DONOTUSE_<oldname>`).

For more information about online consolidations, see [Consolidate online](consolidate-online.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
