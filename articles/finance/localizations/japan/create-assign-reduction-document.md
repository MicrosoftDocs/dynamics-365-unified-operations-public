---
title: Create and assign a reduction entry document for a government grant subsidy
description: Learn how to create and assign a reduction entry document for a government grant subsidy in Japan with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 04/18/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetReductionEntryProfile_JP, AssetTable, AssetBook
ms.custom: 
  - bap-template
---

# Create and assign a reduction entry document for a government grant subsidy

[!include [banner](../../includes/banner.md)]

This article explains how to create and assign a reduction entry document for a government grant subsidy in Japan with Microsoft Dynamics 365 Finance.

For Japan, a reduction entry document is a document that you can attach to a fixed asset that is sponsored using a government subsidy. The reduction entry certificate contains the details about the government subsidy, such as the reduction entry method, depreciation convention, reason, validity, and subsidy threshold. The details of the reduction entry document are used to calculate and post reduction entry amounts.

Before you complete the following procedures, you must first select the **Fixed Asset** configuration key.

The procedures use the JPMF demo company data.

## Create a new reduction entry document

To create a new reduction entry document, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Periodic tasks \> Reduction entries \> Reduction entry documents**.
1. Select **New**.
1. In the **Reduction entry document** field, enter a value.
1. In the **Reduction entry type** field, select a method to journalize the government grant.  
1. In the **Depreciation convention** field, select an option.
    - This field is available only if you select the **Reserve in the Reduction entry type** field.
    - The depreciation convention value should be the same as the one used for the fixed asset.
    - You can choose to record some extra information such as the subsidies reason, the valid from date, the valid to date, and the maximum percentage rate of maximum amount of the government grant subsidy.
    - Under the **Retirement of subsidies** tab, you can enter terms that are required by the government upon the retirement of the fixed asset and its related subsidies. This information is referred to if and when you dispose of the fixed asset.  
1. Select **Save**.

## Assign the reduction entry document to a fixed asset book

To assign the reduction entry document to a fixed asset book, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select **New**. Alternatively, you can choose to edit an existing fixed asset if the sponsored asset is already entered in the system.  
1. In the **Fixed asset group** field, enter a value.
1. Select **Books**.
1. Use the Quick Filter to filter out the desired book.
1. In the **Reduction entry document** field, enter a value.
1. Enter the document date.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
