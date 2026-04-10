--- 
title: DE-00002 Depreciation adjustments for additional acquisitions in the second year
description: Learn how to set up the calculation of depreciation for additional acquisitions in Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/16/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak   
ms.search.region: Germany
ms.search.validFrom: 2016-06-30
ms.search.form: AssetParameters, AssetDepreciationProfile
---

# DE-00002 Depreciation adjustments for additional acquisitions in the second year

[!include [banner](../../includes/banner.md)]

This article explains how to set up the calculation of depreciation for additional acquisitions in Microsoft Dynamics 365 Finance.

This guide demonstrates how to set up the calculation of depreciation for additional acquisitions.

The following procedures were created by using the DEMF demo data company.

## Allow multiple acquisitions

To allow multiple acquisitions, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Fixed assets parameters**.
1. Select the **Allow multiple acquisitions** checkbox.
1. Select **Save**.

## Set up a depreciation profile

To set up a depreciation profile, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Depreciation profiles**.
1. Select **New**.
1. In the **Depreciation profile** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Method** field, select **Straight line life remaining**.
1. In the **Period frequency** field, select **Monthly**.
1. Select the **Full year depreciation on additional acquisitions** checkbox.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
