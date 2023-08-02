---
# required metadata

title: Fixed assets in the public sector
description: This article describes the fixed assets functionality that is available for entities in the public sector. 
author: v-kiarnd
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetTransfer
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 552c7969-f044-4774-82ec-080aeae8cf3f
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fixed assets in the public sector

[!include [banner](../includes/banner.md)]

This article describes the fixed assets functionality that is available for entities in the public sector. 

## What do I need to know about disposing of fixed assets?

Public sector organizations can use scrap and sales proposals to dispose of more than one fixed asset at a time.

## Why do I have to enter transfer-from and transfer-to accounts when I transfer fixed assets between funds?
Public sector organizations typically require balanced entries for the financial dimension used to designate funds. When you transfer fixed assets between funds, if the fund dimension requires balanced entries, the transfer-from and transfer-to account fields on the asset transfer page are required. 

> [!NOTE] 
> This is not a property of fixed assets or of funds. Rather, it’s a property of the financial dimension. When you transfer a fixed asset, if any financial dimension associated with the asset requires balanced entries, the transfer-from and transfer-to accounts are required. 

The transfer-from and transfer-to accounts are not the accounts in which the fixed asset’s net book value is held. Rather, the transfer-from and transfer-to accounts are the main accounts used to balance entries in financial dimensions. They are used only when a financial dimension for the fixed asset requires balancing. The transfer-from account will have a debit entry, and the transfer-to account will have a credit entry.

For details, see [Funds in the public sector](funds-public-sector.md).







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
