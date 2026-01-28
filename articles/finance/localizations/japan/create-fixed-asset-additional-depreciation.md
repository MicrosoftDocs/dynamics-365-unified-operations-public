---
title: Create a fixed asset with additional depreciation
description: Learn how to create a fixed asset with additional depreciation for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetBook
ms.custom: 
  - bap-template
---

# Create a fixed asset with additional depreciation

[!include [banner](../../includes/banner.md)]

This article explains how to create a fixed asset with additional depreciation for Japan in Microsoft Dynamics 365 Finance.

In Japan, a fixed asset can post an additional depreciation amount under certain conditions.

The following procedure shows how to create a fixed asset with an additional depreciation profile. The procedure uses the demo data company JPMF.

Before you complete the procedures, select the **Fixed Asset** configuration key.

## Create a fixed asset and assign an additional depreciation profile to it

To create a fixed asset and assign an additional depreciation profile to it, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select **New**.
1. In the **Fixed asset group** field, select a value.
1. In the **Name** field, enter a value.
1. Select **Books**.
1. Expand the **Depreciation** section.
1. In the **Extraordinary depreciation profile** field, enter or select a value.
1. Under the **Extraordinary depreciation** field group, enter a date. The additional depreciation starts from this date.  
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
