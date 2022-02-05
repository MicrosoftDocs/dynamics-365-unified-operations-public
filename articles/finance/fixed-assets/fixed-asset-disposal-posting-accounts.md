---
# required metadata

title: Fixed asset disposal posting accounts
description: This topic explains how to set up General ledger posting accounts for disposing of assets.
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
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 3461
ms.assetid: dfdc0730-e030-48cc-8d93-15bdc7b23776
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fixed asset disposal posting accounts

[!include [banner](../includes/banner.md)]

This topic explains how to set up General ledger posting accounts when you're disposing assets.

To set up General ledger posting accounts to use when you're disposing of an asset, select **Disposal - sale** and **Disposal - scrap** in the **Ledger accounts** FastTab on the **Fixed assets posting profiles** page.

For both transaction types (disposing of an asset by sale or scrap), the ledger account is credited for the disposal value of the fixed asset. The debit is posted to an offset account, which might be a bank account (as an example). If a fixed asset is sold to a customer, the customer account is used instead of the offset account. For more information, see [Dispose of a fixed asset as scrap](dispose-of-a-fixed-asset-as-scrap.md).

Click **Disposal** and then click **Sale** or **Scrap**, and then set up detailed accounts to reverse the net book value of the fixed asset. You can also enter information in the **Post value** and **Sales value type** fields on the **Disposal parameters** page. 

The disposal transaction for an asset in a low-value pool reduces the net book value of the low-value pool by the disposed amount only. However, when the sale of an asset exceeds the net book value of the low-value pool, the net book value is reduced to zero.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
