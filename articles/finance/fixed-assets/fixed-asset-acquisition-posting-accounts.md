---
# required metadata

title: Fixed asset acquisition posting accounts
description: This article explains how to set up General ledger posting accounts for acquiring assets.
author: moaamer
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetPosting
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: d7e86f72-95db-4423-9b04-761e9536a959
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fixed asset acquisition posting accounts

[!include [banner](../includes/banner.md)]

This article explains how to set up General ledger posting accounts for acquiring assets.

Accounts used for posting fixed asset acquisitions may vary depending upon the method used to acquire the asset. On the Fixed asset posting profiles page, on the Ledger accounts tab, select Acquisition and Acquisition adjustment to set up fixed asset accounts to post to the ledger. 

In journals and on purchase orders, Ledger account is typically the balance sheet account, where the acquisition value of the new fixed asset is debited. This account is not displayed in the journal and cannot be replaced in transactions. 

Offset account is also a balance sheet account. In the general journal and in the fixed assets journal, this account often will be the bank account that is used to pay for the acquisition of the asset. The offset account is a default account, which is suggested in the journals. It can be changed in the journal to any other account from the chart of accounts or to a vendor account, if the fixed asset was purchase from a vendor. 

When Invoice journal or Purchase orders in Accounts payable are used for fixed asset acquisitions, the offset account for the fixed asset transaction is replaced by the vendor account that is selected for the transaction.

For acquisitions posted using the Inventory to fixed assets journal in General ledger, the fixed asset is not bought from external sources, but transferred from the company's own inventory. Therefore, the offset account is an inventory issue account for the inventory item in Inventory management.

For more information, see [Acquire assets through procurement](acquire-assets-procurement.md).





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
