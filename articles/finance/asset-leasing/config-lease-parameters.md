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

There are several parameters that determine the behavior of Asset leasing capability, such as jouenal names, general parameters and posting profile settings.

1.	Open the Asset leasing parameters page (**Asset leasing > Setup > Asset leasing parameters**).

2.	Open the **Leases** tab and expand **General** fasttab. 

3.	The **Allow manual classification override** determines whether or not the lease classification can be overidden before the payment schedule is confirmed.

4.	The **Cross-entity batch** parameter determines whether you can post into other legal entities from the current legal entity. If this parameter is enabled, you'll be able to create journal entries for the legal entities that you have access to.

5. Enable the **Short term on index** to classify leases as shor-term after an index revaluation, if the new lease term is less than or equal to the short-term threshold in the book setup.

6.	Enable the **Allow delete of confirmed leases** field to allow leases with confirmed payment schedules to be deleted. Once the lease record is deleted, it can't be restored. Any records for the same that are uploaded manually or through data entities are treated as fresh records.

7. The **Incremental borrowing rate on books** if the transition type of the book is Cumulative Catchup Option A or B, the system will use the Incremental Borrowing Rate at Transition from the Book Setup to populate the Incremental Borrowing Rate field if this parameter is enabled. If this field is set to "No", the Incremental Borrowing Rate on the Book details will be the rate entered on the head lease regardless of the transition type.

8. Enable the **Short term on adjustment** field to classify leases as short-term after the lease has been adjusted and the new lease term is less than or equal to the short-term threshold in the book setup. If this parameter is disabled, leases won't be classified as short-term after a lease adjustment, regardless of the lease term.	

9.	Enable the **Allow depreciation reversals on closed book version** to allow depreciation expense transactions to be reversed, even when the book is closed.
 	
 >  [!Note]
 >  We recommend that you keep this field disabled as this serves as a validation and control for not allowing to reverse out a deprecation on a closed book accidently and thus maintain the correct Net book value and future depreciation calculations.


