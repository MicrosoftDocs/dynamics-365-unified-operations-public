---
# required metadata

title: Payment amount type
description: This topic describes how to set up the payment amount types in Asset leasing.
author: moaamer
ms.date: 01/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeaseIndexRevaluation
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14
---

# Add payment amount types

[!include [banner](../includes/banner.md)]

This topic describes how to set up the **Payment amount types** in Asset leasing. This will help itemize the lease payment amount rather than add the lump sum amount 
in the **Payment schedule lines**.

Add payment amount types
1. Go to **Asset leasing > Setup > Payment amount types**
2. Select **New**.
3. In the appropriate fields, enter the new payment type and description.

> [!NOTE]
> For IFRS 16 index revaluation you'll need to create one payment amount type and marked as **Used** for IRFS 16 index revaluation. This **payment amount type** will be used 
> when the index revaluation process is ran against IFRS 16 book and consider the changes occurred due to index revaluation process. 
> When the **Payment breakdown** in the lease is set to **Yes** and index revaluation for IFRS 16 is ran and there's not a **Payment type** for IFRS 16 the process will 
> not be completed. 

Only one record can be marked as **Used** for IFRS 16 index revaluation.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]


