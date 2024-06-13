---
title: Create a fixed asset with special depreciation profile
description: In Japan, you can post a special depreciation amount to a fixed asset, under certain conditions. Learn how to create fixed assets with special depreciation profile.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 08/29/2018
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetBook
ms.dyn365.ops.version: Version 7.0.0
---

# Create a fixed asset with special depreciation profile

[!include [banner](../../includes/banner.md)]

In Japan, you can post a special depreciation amount to a fixed asset, under certain conditions.

Use this procedure to learn how to create a fixed asset with special depreciation profile.

To complete this procedure, the Fixed Assets configuration key must be selected.

This procedure uses the JPMF demo company data.

1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Click New.
3. In the Fixed asset group field, type a value.
4. In the Name field, type a value.
5. Click Save.
6. Click Value models.
7. Expand or collapse the Depreciation section.
    * Select a Special depreciation profile as Extraordinary depreciation profile.  
    * Note that the EQUP-M and 200NDB_CSR already has the SpeRE-1M as default configuration in the demo data.  
    * Allocation start convention, Allocation unit, and Allocation periods fill with default values. You can change them if needed. These are specific to the Reserve method for special depreciation.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
