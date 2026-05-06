--- 
title: Define shift and industry types for books (India)
description: Learn about defining a shift type and industry for a book and then assigning the book to a fixed asset, including a step-by-step process. 
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0 
---

# Define shift and industry types for books (India)

[!include [banner](../../includes/banner.md)]

This procedure shows you how to define a shift type and industry for a book, and then assign the book to a fixed asset. The calculation of depreciation for a fixed asset is for a specific period and is based on the selected type of shift and industry. The calculation of depreciation is also based on the actual number of days in the calendar month when you select **Day based** in the **Calendar** field on the **Books** page for the **Straight line service life depreciation method** or the **Reducing balance depreciation method**. The demo data company used to create this procedure is INMF.

1. Go to **Fixed assets** > **Setup** > **Books**.
1. Select **New**.
1. In the **Book** field, enter a value.
1. Select **Yes** in the **Calculate depreciation** field.
1. In the **Description** field, enter a value.
1. In the **Depreciation profile** field, enter or select a value.
1. In the **Calendar** field, enter or select a value.
1. Select **Yes** in the **Override fixed asset calendar days?** field.
1. In the **Asset working days** field, enter a number.
1. Select **Shift depreciation**.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select **Save**.
1. Close the page.
1. Close the page.
1. Go to **Fixed assets** > **Fixed assets** > **Fixed assets**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Books**.
1. Select **New**.
1. In the **Book** field, enter or select a value.
1. Select **Shift depreciation**.
1. Close the page.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
