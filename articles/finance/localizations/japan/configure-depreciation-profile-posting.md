---
title: Configure depreciation profile and posting profile for additional depreciation
description: Learn how to configure a depreciation profile and a posting profile for special depreciation in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - AssetDepreciationProfile
  - AssetPosting
ms.custom: 
  - bap-template
---

# Configure depreciation profile and posting profile for additional depreciation

[!include [banner](../../includes/banner.md)]

This article explains how to configure a depreciation profile and a posting profile for special depreciation in Japan with Microsoft Dynamics 365 Finance.

In Japan, special depreciation is permitted under certain conditions. It is treated as extraordinary depreciation. 

The following procedures were created using the demo data company JPMF.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Configure a depreciation profile

To configure a depreciation profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Depreciation profiles**.
1. Select **New**.
1. In the **Depreciation profile** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Method** field, select **Special depreciation**.
1. In the **Accounting method** field, select an option. Select **Reserve** for the reserve method, or select **Direct-off** for the direct-off method for journalization. Reserve method is usually the preferred representation on a financial statement.  
1. In the **Apply number of periods** field, enter a number.
1. In the **Base ratio** field, enter "1" for 100%. The actual value can vary depending on the fixed asset.  
1. In the **Special depreciation rate** field, enter "0.3" for 30%. The actual value can vary depending on the fixed asset. The special depreciation amount is calculated as the product of acquisition cost, base ratio, and special depreciation rate.  
1. Select **Save**.

## Configure a posting profile

To configure a posting profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed asset posting profiles**.
1. Select **Edit**.
1. In the **Transaction type** field, select **Extraordinary depreciation**.
    - You must select **Edit** before you can modify the account fields.
    - Special depreciation is posted as extraordinary depreciation.  
    - Optionally, you can configure **Main account** and **Offset account**.  
  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
