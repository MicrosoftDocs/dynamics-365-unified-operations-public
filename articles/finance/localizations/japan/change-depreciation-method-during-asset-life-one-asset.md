---
title: Change the depreciation method during the asset life for one asset
description: Learn how to change the depreciation method during the asset life for one asset in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - AssetTable, AssetBook, AssetDepProfileChange_JP
  - AssetUndepreciatedBalancedSchedule_JP
ms.custom: 
  - bap-template
---
# Change the depreciation method during the asset life for one asset

[!include [banner](../../includes/banner.md)]

This article explains how to change the depreciation method during the asset life for one asset in Japan with Microsoft Dynamics 365 Finance.

In Japan, you can change the depreciation method during the service life of a fixed asset.

The following procedures walk you through how to change the depreciation profile for a fixed asset. The procedures use the demo data company JPMF.

Before you complete the following procedures, select the **Fixed Asset** configuration key and configure **Undepreciated balance schedule** or **Years passed schedule**.

## Change the depreciation profile for a fixed asset

To change the depreciation profile for a fixed asset, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Use the Quick Filter to find records. For example, filter on the **Fixed asset number** field with a value of "STRUM-000001".
1. Select **Books**.
1. Select **Functions**.
1. Select **Change depreciation profile**.
1. Select **New**.
1. In the **Start date** field, enter the start date of a fiscal year, in the current fiscal calendar.  
1. In the **Depreciation profile** field, enter a value.
1. Select **Update service life**. Confirm that **Service life** and **Depreciation periods remaining** are updated.  

## View the undepreciated balance schedule for fixed assets

To view the undepreciated balance schedule for fixed assets, go to **Fixed assets \> Setup \> Depreciation rate schedules \> Undepreciated balance schedules**.

- The system requires corresponding data for the depreciation profile update.  
- The **From method**, **To method**, **Service life**, and **Years passed** values determine which record to apply to the asset change.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
