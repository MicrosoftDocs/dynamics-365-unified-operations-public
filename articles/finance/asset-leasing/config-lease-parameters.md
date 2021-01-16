---
# required metadata

title: Configure lease parameters (Preview)
description: This topic describes the configuration settings for Asset leasing, such as security information and accounting settings.
author: moaamer
manager: Ann Beebe
ms.date: 10/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14

---

# Configure lease parameters

[!include [banner](../includes/banner.md)]

Several configuration settings affect how Asset leasing behaves. These settings include journal names, general parameters, and posting profile settings.

1. Go to **Asset leasing \> Setup \> Asset leasing parameters**.
2. On the **Leases** tab, select the **General** FastTab.

    The **Allow manual classification override** parameter determines whether the lease classification can be overridden before the payment schedule is confirmed.

    The **Cross-entity batch** parameter determines whether you can post to other legal entities from the current legal entity. If this parameter is turned on, you can create journal entries for the legal entities that you have access to.

3. Set the **Allow delete of confirmed leases** option to **Yes** to allow leases that have confirmed payment schedules to be deleted. Leases can't be deleted if posted or unposted transactions are associated with them, regardless of the setting of this option. You can't restore a lease record after it's deleted. If you upload any records for a deleted lease, either manually or through data entities, the uploaded information is treated as new, not as an update to an existing lease.

    If you set this option to **Yes**, and the transition type of the book is **Cumulative Catchup Option A or B**, the system sets the **Incremental borrowing rate** field to the value of the **Incremental borrowing rate at transition** field on the **Book setup** page. If this option is set to **No**, the rate on the head lease is set to the value of the **Incremental borrowing rate** field on the **Book details** page, regardless of the transition type of the book.

4. Set the **Allow depreciation reversals on closed book version** option to **Yes** to allow depreciation expense transactions to be reversed. Expense transactions can be reversed even when the book version is closed.

    > [!NOTE]
    > We recommend that you keep this option set to **No**. The setting of this option is used as a validation and control to prevent a closed book version from being accidently depreciated. By keeping the option set to **No**, you help keep the net book value and future depreciation calculations accurate.
