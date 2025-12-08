---
title: Enter depreciation rate schedule and associate to depreciation profile
description: Learn how to enter the Japan depreciation rate schedule and associate it with a depreciation profile in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetDepRate_JP, AssetDepreciationProfile
ms.custom: 
  - bap-template
---

# Enter depreciation rate schedule and associate to depreciation profile

[!include [banner](../../includes/banner.md)]

This article explains how to enter the Japan depreciation rate schedule and associate it with a depreciation profile in Microsoft Dynamics 365 Finance.

In Japan, a government agency releases the fixed asset depreciation rate. You can enter the depreciation rate schedule into the system. The system implements the depreciation rate schedule as a data entity so that you can import it from a file.

Use the following procedures to learn how to modify the depreciation rate schedule and associate it to a depreciation profile. The procedures use the JPMF demo company data.

Before you complete the procedures, select the **Fixed Asset** configuration key.

## Modify a depreciation rate schedule

To modify a depreciation rate schedule, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Depreciation rate schedules \> Depreciation rate schedules**.
1. Select **Edit**.
1. In the **Service life** field, enter a number.
1. In the **Depreciation rate** field, enter a number.
1. In the **Revised depreciation rate** field, enter a number.
1. In the **Guaranteed depreciation rate** field, enter a number.

## Associate a depreciation rate schedule to a depreciation profile

To associate a depreciation rate schedule to a depreciation profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Depreciation profiles**.
1. Select **Edit**.
1. In the **Depreciation rate schedule** field, select the drop-down button to open the lookup.
1. In the list, select the depreciation schedule that you modified in the earlier task.  
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
