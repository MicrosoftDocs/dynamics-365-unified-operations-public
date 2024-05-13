---
title: Fixed asset disposal posting accounts
description: Learn how to set up General ledger posting accounts for disposing of assets. The ledger account is credited for the disposal value of the fixed assets.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AssetPosting
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: dfdc0730-e030-48cc-8d93-15bdc7b23776
---

# Fixed asset disposal posting accounts

[!include [banner](../includes/banner.md)]

This article explains how to set up General ledger posting accounts when you're disposing assets.

To set up General ledger posting accounts to use when you're disposing of an asset, select **Disposal - sale** and **Disposal - scrap** in the **Ledger accounts** FastTab on the **Fixed assets posting profiles** page.

For both transaction types (disposing of an asset by sale or scrap), the ledger account is credited for the disposal value of the fixed asset. The debit is posted to an offset account, which might be a bank account (as an example). If a fixed asset is sold to a customer, the customer account is used instead of the offset account. For more information, see [Dispose of a fixed asset as scrap](dispose-of-a-fixed-asset-as-scrap.md).

Click **Disposal** and then click **Sale** or **Scrap**, and then set up detailed accounts to reverse the net book value of the fixed asset. You can also enter information in the **Post value** and **Sales value type** fields on the **Disposal parameters** page. 

The disposal transaction for an asset in a low-value pool reduces the net book value of the low-value pool by the disposed amount only. However, when the sale of an asset exceeds the net book value of the low-value pool, the net book value is reduced to zero.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
