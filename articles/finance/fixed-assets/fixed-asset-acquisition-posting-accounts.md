---
title: Fixed asset acquisition posting accounts
description: Learn about how to set up General ledger posting accounts for acquiring assets, with an outline on offset accounts and balance sheet accounts.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 06/24/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AssetPosting
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: d7e86f72-95db-4423-9b04-761e9536a959
---

# Fixed asset acquisition posting accounts

[!include [banner](../includes/banner.md)]

This article explains how to set up General ledger posting accounts for acquiring assets.


Accounts for posting fixed asset acquisitions vary depending on the method used to acquire the asset. On the **Fixed asset posting profiles** page, on the **Ledger accounts** tab, select **Acquisition** and **Acquisition adjustment** to set up fixed asset accounts to post to the ledger.

Offset account is also a balance sheet account. In the general journal and in the fixed assets journal, this account is often the bank account that is used to pay for the acquisition of the asset. The offset account is a default account, which is suggested in the journals. It can be changed in the journal to any other account from the chart of accounts or to a vendor account, if the fixed asset was purchase from a vendor.

In journals and on purchase orders, the **Ledger account** is typically the balance sheet account where you debit the acquisition value of the new fixed asset. This account doesn't display in the journal and you can't replace it in transactions.

For acquisitions posted using the Inventory to fixed assets journal in General ledger, the fixed asset isn't bought from external sources, but transferred from the company's own inventory. Therefore, the offset account is an inventory issue account for the inventory item in Inventory management.

For more information, see [Acquire assets through procurement](acquire-assets-procurement.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
