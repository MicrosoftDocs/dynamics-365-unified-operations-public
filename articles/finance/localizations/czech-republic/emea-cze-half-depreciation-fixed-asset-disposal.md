---
title: Half year depreciation on fixed asset disposal for the Czech Republic
description: Learn how to set up half-yearly depreciation, so that you can apply half the yearly depreciation for fixed assets that are sold or otherwise disposed of.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic
ms.search.validFrom: 2016-11-30
ms.search.form: AssetDepreciationProfile
ms.custom: 
  - bap-template
---

# Half year depreciation on fixed asset disposal for the Czech Republic

[!include [banner](../../includes/banner.md)]

This article explains how to set up half-yearly depreciation, so that you can apply half the yearly depreciation for fixed assets that you sell or otherwise dispose of.

When you sell or otherwise dispose of a fixed asset, you can apply half the yearly depreciation for the asset, for tax purposes. You can apply this half-yearly depreciation regardless of the disposal date.

## Set up depreciation methods for the depreciation profile

Use the Regular CZ and Accelerated CZ depreciation methods to apply half-yearly depreciation for a fixed asset.

1. Select **Fixed assets** > **Setup** > **Depreciation** > **Depreciation profiles**.
1. Select **New** to create a depreciation profile.
1. In the **Method** field, select **Regular CZ** or **Accelerated CZ**.
1. In the **Depreciation year** field, select **Calendar** as the basis for the calculation of depreciation.
1. In the **Period frequency** field, select **Yearly**.

## Apply the half yearly depreciation method

After you set up the depreciation methods, apply half the yearly depreciation for assets that you dispose of.

1. Select **Fixed assets** > **Journals** > **Fixed assets**.
1. On the **Overview** tab, select **New** to create a journal, and then enter the required details.
1. Select **Lines** to open the **Journal voucher** page.
1. Create a journal line for the fixed asset that you sold or otherwise disposed of.
1. Select **Proposals** > **Depreciation proposal** to open the **Depreciation proposal** page.
1. In the **To date** field, enter the journal date.
1. Select the **Calculate half-year depreciation amount** check box to calculate half-yearly depreciation. When you select this check box, the yearly depreciation amount is divided by two and rounded according to the rounding setup for the depreciation book.
1. (Optional) Select the **Summarize depreciation** check box to summarize the calculated depreciation for each fixed asset or for each value model.
1. Select **OK** to close the **Depreciation proposal** page.
1. Post the journal.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
