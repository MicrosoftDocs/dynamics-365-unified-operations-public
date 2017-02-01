---
# required metadata

title: Fixed assets in the public sector | Microsoft Docs
description: This article describes the fixed assets functionality that is available for public sector. 
author: rschloma
manager: AnnBe
ms.date: 2015-12-08 18:55:24
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: AssetTransfer
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 20891
ms.assetid: 97c65418-d932-4d7a-8c4b-77428f03454e
ms.region: Global
ms.industry: Public sector
ms.author: brpotter

---

# Fixed assets in the public sector

This article describes the fixed assets functionality that is available for public sector. 

What do I need to know about disposing of fixed assets?
-------------------------------------------------------

Public sector organizations can use scrap and sales proposals to dispose of more than one fixed asset at a time.

## Why do I have to enter transferfrom and transferto accounts when I transfer fixed assets between funds?
Public sector organizations typically require balanced entries for the financial dimension used to designate funds. When you transfer fixed assets between funds, if the fund dimension requires balanced entries, the transfer-from and transfer-to account fields on the asset transfer page are required. **Note**: This is not a property of fixed assets or of funds. Rather, it’s a property of the financial dimension. When you transfer a fixed asset, if any financial dimension associated with the asset requires balanced entries, the transfer-from and transfer-to accounts are required. The transfer-from and transfer-to accounts are not the accounts in which the fixed asset’s net book value is held. Rather, the transfer-from and transfer-to accounts are the main accounts used to balance entries in financial dimensions. They are used only when a financial dimension for the fixed asset requires balancing. The transfer-from account will have a debit entry, and the transfer-to account will have a credit entry. For details, see [Funds in the public sector](https://docs.microsoft.com/en-us/dynamics365/operations/financials/public-sector/funds-in-the-public-sector).

See also
--------

[Fixed assets](https://ax.help.dynamics.com/en/?post_type=incsub_wiki&p=197821)

