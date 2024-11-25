--- 
title: Set up bonus depreciation
description: Learn how to create a special depreciation allowance and associate it with a fixed asset book, including a process for creating special depreciations.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 03/28/2023
ms.custom:
ms.reviewer: twheeloc   
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: AssetBonus, AssetGroup, AssetGroupBookSetup, AssetGroupSetupBonus
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up bonus depreciation

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a special depreciation allowance and associate it with a fixed asset book. It uses the accountant role and demo data for the USMF legal entity.


## Create a special depreciation allowance
1. Go to **Fixed assets > Setup > Special depreciation allowance**.
2. Click **New**.
3. In the **Special depreciation allowance** field, type a value.
4. In the **Description** field, type a value.
5. In the **Percentage** field, enter a number.
    * If a percentage was not indicated, set an amount.  

## Associate a special depreciation allowance with a fixed asset group book
1. Go to **Fixed assets > Setup > Fixed asset groups**.
2. In the list, select the fixed asset group associated with the special depreciation allowance.
3. Click **Books**.
4. In the list, select the book that is associated with the special depreciation allowance.
5. Click **Special depreciation allowance**.
6. Click **New**.
7. In the **Special depreciation allowance** field, enter or select a value.
    * The default for **Percentage** or **Amount** comes from the special depreciation allowance setup.  
8. In the **Priority** field, enter a number.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
