---
title: Assign price groups (preview)
description: Lear now to assign price groups for trade agreements, adjustments, and discounts 
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: XXXX
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---


# Assign price groups (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [pricing-management-deprecation-banner](../includes/pricing-management-deprecation-banner.md)]

<!-- KFM: Preview until further notice -->

## For trade agreements

1. Go to **Price management** \> **During sales pricing** \> **Sales trade agreement price** \> **Trade agreements journals**.
1. Select a trade agreement journal with status **Not posted**.
1. Select the drop-down list of **Price group** to specify a price group which will be inherited to all lines of the journal.

    ![A screenshot of a computer Description automatically generated](media/image3.png)

1. Select **Lines** button on top of the Trade agreement journal.
1. By selecting **New** button to create lines, the defaulted value of price group is inherited from the Price group value specified in the head of the journals.
1. Modify the value of price group for each line if required.

    ![A screenshot of a computer Description automatically generated](media/image4.png)

## For adjustments

1. Go to **Price management** \> **During sales pricing** \> **Price adjustments** \> **Margin component price adjustments**.
1. Select a specific discount record with status **Disabled**.
1. Select **Price group** button on top and there displays a price group form.

    ![A screenshot of a computer Description automatically generated](media/image5.png)

1. Select **New** button on top to add new records
1. Select drop-down list of price group and choose the name.

    The inherited information displays as follows.

    The value of **pricing priority** will default in the field **Pricing priority** on the current discount record.

    It is non-editable when override priority field is set to be **No**.

    ![A screenshot of a computer Description automatically generated](media/image6.png)

1. Select **New** button on top to select price group for the current adjustment record.
1. Select the drop-down list of Price group to specify a price group.
1. Select **Save** button.

    - **Pricing priority** of the selected pricing group displays accordingly.
    - **Price attribute group** value is visible.

1. Predefined fields names and values for the **Price attribute group** are visible.
1. Multiple price groups can be created for the current adjustment record by selecting **New** button.

## For discounts

1. Go to **Price management** \> **During sales pricing** \> **Discounts** \> **All discounts**.
1. Select a specific discount record with status **Disabled**.
1. Select **Price group** button on top and there displays a price group form.

    ![A screenshot of a computer Description automatically generated](media/image7.png)

1. Select **New** button on top to add new records
1. Select drop-down list of price group and choose the name.

    The inherited information displays as follows.

    The value of **pricing priority** will default in the field **Pricing priority** on the current discount record.

    It is non-editable when override priority field is set to be **No**.

    ![A screenshot of a computer Description automatically generated](media/image8.png)

1. Select **New** button on top to select price group for the current adjustment record.
1. Select the drop-down list of Price group to specify a price group.
1. Select **Save** button.

    - **Pricing priority** of the selected pricing group displays accordingly.
    - **Price attribute group** value is visible.

1. Predefined fields names and values for the **Price attribute group** are visible.
1. Multiple price groups can be created for the current adjustment record by selecting **New** button.
