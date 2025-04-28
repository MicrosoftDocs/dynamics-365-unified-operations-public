---
title: Change the depreciation method during the asset life for book
description: Learn how to change the depreciation method for fixed assets under a fixed asset group and book in Japan with Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - AssetBookTable, AssetGroupBookSetup, AssetDepProfileChangeApply_JP
  - AssetUndepreciatedBalancedSchedule_JP
---

# Change the depreciation method during the asset life for book

[!include [banner](../../includes/banner.md)]

This article explains how to change the depreciation method for fixed assets under a fixed asset group and book in Japan with Microsoft Dynamics 365 Finance.

In Japan, you can change the depreciation method during the service life of a fixed asset.

The following procedures walk you through how to change a depreciation profile for the fixed assets under a fixed asset group and book. This procedure was created using the demo data company JPMF.

Before you complete the following procedures, you must select the **Fixed Asset** configuration key and configure **Undepreciated balance schedule** or **Years passed schedule**.

## Change a depreciation profile

To change a depreciation profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Books**.
1. Use the Quick Filter to find records. For example, filter on the **Book** field with a value of "250NDB_CUR".
1. Select **Fixed asset groups**.
1. Use the Quick Filter to find records. For example, filter on the **Fixed asset group** field with a value of "STRU-A".
1. Select **Change depreciation profile**.
1. In the **To depreciation profile** field, enter a value.
1. In the **Start date** field, enter the start date of a fiscal year in the current fiscal calendar.  
1. Select **Yes** in the **Update service life** field. You can add an idle period if needed.  
1. Select **Apply**.
1. Select **Yes**.

## View the years passed schedule

To view the years passed schedule, go to **Fixed assets \> Setup \> Depreciation rate schedules \> Years passed schedules**. The corresponding data must exist for the depreciation profile update.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
