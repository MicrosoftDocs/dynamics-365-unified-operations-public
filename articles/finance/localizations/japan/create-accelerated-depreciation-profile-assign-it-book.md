---
title: Create accelerated depreciation profile and assign it to book
description: Learn how to create an accelerated depreciation profile and assign it to book for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 04/18/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetDepreciationProfile, AssetBookTable
ms.custom: 
  - bap-template
---

# Create accelerated depreciation profile and assign it to book

[!include [banner](../../includes/banner.md)]

This article explains how to create an accelerated depreciation profile and assign it to book for Japan in Microsoft Dynamics 365 Finance.

For Japan, accelerated depreciation requires configuration of a depreciation profile, just like other depreciation methods. 

Use the following procedures to create a depreciation profile for accelerated depreciation and assign it to a book. The procedures were created using the demo data company JPMF.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Create a depreciation profile

To create a depreciation profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Depreciation profiles**.
1. Select **New**.
1. In the **Depreciation profile** field, enter a value.
1. Note the **Depreciation profile** value to reference later.
1. In the **Name** field, enter a value.
1. In the **Method** field, select "Accelerated".
1. Select **Save**.

## Assign the depreciation profile to a book

To assign the depreciation profile to a book, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Books**.
1. Select the book for which to assign the accelerated depreciation profile.
1. Select **Edit**.
1. Use the value noted previously in the **Accelerated depreciation profile** field.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
