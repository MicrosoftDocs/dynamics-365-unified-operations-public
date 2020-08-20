---
# required metadata

title: Configure lease parameters
description: This topic walks through configuration settings for Asset leasing, such as security information and accounting settings.
author: moaamer
manager: Ann Beebe
ms.date: 07/28/2020
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
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-07-28
ms.dyn365.ops.version: 10.0.14

---

# Configure lease parameters (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

There are several parameters that affect how Asset leasing behaves, including journal names, general parameters, and posting profile settings.

1.	Open the **Asset leasing parameters** page (**Asset leasing > Setup > Asset leasing parameters**).

2.	Open the **Leases** tab and expand **General** FastTab. 

   The **Allow manual classification override** determines whether or not the lease classification can be overridden before the payment schedule is confirmed.

   The **Cross-entity batch** parameter determines whether you can post into other legal entities from the current legal entity. If this parameter is enabled, you'll be able to create journal entries for the legal entities that you have access to.

3.	Set the **Allow delete of confirmed leases** field to **Yes** to allow leases with confirmed payment schedules to be deleted. Leases with associated posted or unposted transactions can't be deleted, regadless of the field is set. You can't retore the lease record after it's been deleted. If you upload any records for a deleted lease, either manually or through data entities, the uploaded information is treated as new, rather than updates to an existing lease.

   If the transition type of the book is Cumulative Catchup Option A or B, the system will insert the value in the **Incremental borrowing rate at transition** from the **Book setup** page into the **Incremental borrowing rate** field, if this parameter is enabled. If this field is set to **No**, the value in the **Incremental borrowing rate** field on the **Book details** page will be the rate entered on the head lease regardless of the transition type.

4.	Set the **Allow depreciation reversals on closed book version** field to **Yes** to allow depreciation expense transactions to be reversed. Expense transactions can be reversed, even when the book version is closed.
 	
 >  [!Note]
 >  We recommend that you keep this field disabled. The field is used as a validation and control to prevent depreciating a closed book version accidently. Keeping the field disabled helps to keep net book value and future depreciation calculations accurate.


