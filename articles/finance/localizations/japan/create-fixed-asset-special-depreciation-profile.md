---
title: Create a fixed asset with special depreciation profile
description: Learn how to create a fixed asset with a special depreciation profile for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/18/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetBook
ms.custom: 
  - bap-template
---

# Create a fixed asset with special depreciation profile

[!include [banner](../../includes/banner.md)]

This article explains how to create a fixed asset with a special depreciation profile for Japan in Microsoft Dynamics 365 Finance.

In Japan, you can post a special depreciation amount to a fixed asset, under certain conditions.

The following procedure walks you through how to create a fixed asset with a special depreciation profile. The procedure uses the JPMF demo company data.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

To create a fixed asset with a special depreciation profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select **New**.
3. In the **Fixed asset group** field, type a value.
4. In the **Name** field, type a value.
5. Select **Save**.
6. Select **Value models**.
7. Expand or collapse the **Depreciation** section.
1. Set **Special depreciation profile** to **Extraordinary depreciation profile**.  
    - The EQUP-M and 200NDB_CSR already have the SpeRE-1M as default configuration in the demo data.  
    - The **Allocation start convention**, **Allocation unit**, and **Allocation periods** fields automatically populate with default values that you can change if necessary. The default values are specific to the reserve method for special depreciation.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
