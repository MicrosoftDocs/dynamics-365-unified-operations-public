---
# required metadata

title: Fixed asset disposal posting accounts | Microsoft Docs
description: This article explains how to set up general ledger posting accounts for disposing of assets.
author: twheeloc
manager: AnnBe
ms.date: 2015-09-10 21:04:08
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: AssetPosting
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 3461
ms.assetid: 4e68c9d3-d90b-403b-b9e5-4fa259dce6fc
ms.region: Global
# ms.industry: 
ms.author: saraschi

---

# Fixed asset disposal posting accounts

This article explains how to set up general ledger posting accounts for disposing of assets.

In the Fixed asset posting profiles page, on the Ledger accounts FastTab, select Disposal - sale and Disposal - scrap to set up postings to the ledger.
For both transaction types, the ledger account is credited for the disposal value of the fixed asset. The debit is posted to an offset account, which might be, for example, a bank account. If a fixed asset is sold to a customer, the customer account is used instead of the offset account. Click Disposal and then click Sale or Scrap, and then set up detailed accounts to reverse the net book value of the fixed asset. You can also enter information in the Post value and Sales value type fields in the Disposal parameters page. The disposal transaction for an asset in a low-value pool reduces the net book value of the low-value pool by the disposed amount only. However, when the sale of an asset is exceeds the net book value of the low-value pool, the net book value is reduced to zero.



