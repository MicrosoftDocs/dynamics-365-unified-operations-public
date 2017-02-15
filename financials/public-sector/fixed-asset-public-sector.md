---
# required metadata

title: Fixed assets in the public sector
description: This article describes the fixed assets functionality that is available for public sector. 
author: rschloma
manager: AnnBe
ms.date: 2015-12-08 18 - 55 - 24
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetTransfer
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 20891
ms.assetid: fcfbe8bb-561c-438d-969a-51eb5a9716a2
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Fixed assets in the public sector

This article describes the fixed assets functionality that is available for public sector. 

What do I need to know about disposing of fixed assets?
-------------------------------------------------------

Public sector organizations can use scrap and sales proposals to dispose of more than one fixed asset at a time.

## Why do I have to enter transferfrom and transferto accounts when I transfer fixed assets between funds?
Public sector organizations typically require balanced entries for the financial dimension used to designate funds. When you transfer fixed assets between funds, if the fund dimension requires balanced entries, the transfer-from and transfer-to account fields on the asset transfer page are required. **Note**: This is not a property of fixed assets or of funds. Rather, it’s a property of the financial dimension. When you transfer a fixed asset, if any financial dimension associated with the asset requires balanced entries, the transfer-from and transfer-to accounts are required. The transfer-from and transfer-to accounts are not the accounts in which the fixed asset’s net book value is held. Rather, the transfer-from and transfer-to accounts are the main accounts used to balance entries in financial dimensions. They are used only when a financial dimension for the fixed asset requires balancing. The transfer-from account will have a debit entry, and the transfer-to account will have a credit entry. For details, see [Funds in the public sector](funds-public-sector.md).

See also
--------

[Fixed assets](https://ax.help.dynamics.com/en/?post_type=incsub_wiki&p=197821)

