---
title: Asset leasing conventions
description: Learn about the conventions for leased assets, including a table that defines various conventions for leasing assets and steps for viewing and assigning assets.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-1-28
ms.search.form: AssetLease
ms.dyn365.ops.version: 10.0.17
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Asset leasing conventions

[!include [banner](../includes/banner.md)]


This article describes conventions for leased assets. Leasing conventions are used to determine the commencement date of a lease book. If the leasing convention is set to **None**, the commencement date is the same as the start date for the lease (that is, the value of the **Lease start date** field). If the leasing convention is set to **Full month**, the commencement date is the first day of the month that the lease's start date falls in.

The commencement date determines the start date of the period for the liability amortization and asset depreciation schedules. Interest expenses and depreciation expenses are posted on the period end date of the corresponding schedules. The initial recognition and adjustment journal entry are posted on the commencement date.


Leasing conventions are assigned to the setup for a lease asset book.

To view or assign the leasing convention, follow these steps.

1. Go to **Asset leasing \> Setup \> Lease books**.
2. In the **Leasing convention** field, select one of the following values.

    | Leasing convention | Description |
    |--------------------|-------------|
    | None               | The liability amortization and asset depreciation schedules start on the lease's start date, because the commencement date equals the lease's start date. The end date is one month later. This leasing convention doesn't guarantee that the interest will be posted on the last day of each month. |
    | Full month         | For leases that have a start date that occurs at any time during the month, the liability amortization and asset depreciation schedules start to accrue expenses on the first day of that month. This leasing convention ensures that interest is accrued on the last day of each month for the whole month. |

3. Select **Save**.

When a lease is created, the commencement date of each book is automatically entered based on the start date that is entered for the lease and the leasing convention that is specified for the book.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
