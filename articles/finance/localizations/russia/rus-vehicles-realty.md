---
title: Vehicles and realty as fixed assets (Russia)
description: Learn how to set up vehicles and realty as fixed assets for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/12/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
---

# Vehicles and realty as fixed assets (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to set up vehicles and realty as fixed assets for Russia in Microsoft Dynamics 365 Finance.

## Set up the depreciation start date for vehicle and realty assets

Use the **Depreciation groups** page to set up the start date for depreciation of fixed assets of the **Realty** and **Vehicle** types.

You can specify that the calculation of depreciation should be based on the registration date of the asset. If an asset is registered after it's put into operation, depreciation is calculated from the first day of the month of registration. If an asset is registered before it's put into operation, depreciation is calculated from the first day of the month after the asset is put into operation.

To set up the depreciation start date for vehicle and realty assets, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
1. Create a depreciation group, and enter the required details.
1. On the **General** FastTab, in the **Depreciation start date** field, select **Date of the registration** to specify that the registration date of a fixed asset should be used as the depreciation start date.

## Specify the registration date for vehicle and realty assets

To specify the registration date for vehicle and realty assets, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
1. Select **New** to create a fixed asset, and enter the required details.
1. On the **General** FastTab, in the **Type** field, select **Realty**.
1. On the **Technical information** FastTab, in the **Date of the registration** field, select the registration date of the fixed asset.
1. In the **Removal from the register date** field, select the date when the asset should be removed from the tax register.

For more information about asset depreciation, see [Calculate depreciation (Russia)](rus-depreciation-calculation.md).



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
