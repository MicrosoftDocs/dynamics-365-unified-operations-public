---
title: Add payment amount types
description: Learn about how to set up payment amount types in Asset leasing, including a step-by-step process for adding payment amount types.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 01/11/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeaseIndexRevaluation
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Add payment amount types

[!include [banner](../includes/banner.md)]

This article describes how to set up payment amount types in Asset leasing. In this way, you can itemize the lease payment amount instead of adding the lump sum amount on the payment schedule lines.

To add payment amount types, follow these steps.

1. Go to **Asset leasing \> Setup \> Payment amount types**.
2. Select **New**.
3. Enter the new payment type and a description.

> [!NOTE]
> For IFRS 16 index revaluation, you must create one payment amount type and mark it as **Used for IRFS 16 index revaluation**. This payment amount type will be used when the index revaluation process is run against IFRS 16 book, and it will consider the changes that occurred because of the index revaluation process.
>
> When the **Payment breakdown** option in the lease is set to **Yes**, if the index revaluation for IFRS 16 is run, but there is no payment type for IFRS 16, the process won't be completed.

Only one record can be marked as **Used for IFRS 16 index revaluation**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
