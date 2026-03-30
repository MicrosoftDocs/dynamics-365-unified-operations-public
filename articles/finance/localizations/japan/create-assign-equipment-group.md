---
title: Create and assign an equipment group
description: Learn how to create and configure an equipment group for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetAcceleratedDepEquipmentGroup_JP, AssetTable
ms.custom: 
  - bap-template
---

# Create and assign an equipment group

[!include [banner](../../includes/banner.md)]

This article explains how to create and configure an equipment group for Japan in Microsoft Dynamics 365 Finance.

Use the following procedures to learn how to create an equipment group and configure an equipment group on a fixed asset. Equipment groups provide default values when creating an accelerated depreciation document. The procedures use the demo data company JPMF.

Before you complete the procedures, select the **Fixed Asset** configuration key.

## Create an equipment group

To create an equipment group, follow these steps:

1. Create equipment group **Fixed assets \> Setup \> Equipment group**.
1. Select **New**.
1. In the **Fixed asset equipment group** field, enter a value.
1. In the **Description**field, enter a value.
1. In the **Equipment type** field, enter a value.
1. In the **Location** field, enter a value. This value is the default when you create an accelerated depreciation document.  
1. In the **Equipment type division** field, enter a value.
1. In the **Industry average hours per day** field, enter a number. This value is the default when you create an accelerated depreciation document.  
1. In the **Industry annual working days** field, enter a number. This value is the default when you create an accelerated depreciation document.  
1. Select **Save**.

## Configure default equipment group on fixed assets

To configure a default equipment group on fixed assets, follow these steps:

1. Create equipment group **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select the fixed asset to which you want to assign the equipment group.
1. Select **Edit**.
1. In the **Fixed asset equipment group** field, enter a value.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
