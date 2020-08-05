---
# required metadata

title: Associate a lease with a fixed asset
description: The topic lists the steps for associating an existing fixed asset with a new lease. 
author: moaamer
manager: Ann Beebe
ms.date: 08/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
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
ms.search.validFrom: 2020-08-05
ms.dyn365.ops.version: 10.0.14
---

# Associate a lease with a fixed asset

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The topic lists the steps for associating an existing fixed asset with a new lease. To associate a lease to a fixed asset, the right-of-use (ROU) asset value at initial recognition will be the acquisition cost of that fixed asset.

1. Add a lease as described in the Input and Record Leases section of the user guide. Select the not-yet-acquired fixed asset from the Fixed asset number dropdown in the Add Lease form.
2. Select books and confirm the payment schedule
3. Select Initial recognition
4. Select General Journals
5. The initial recognition journal entry for the lease will debit the fixed asset for the amount normally debited to the ROU asset account.
6. To view and edit the Transaction Type and Value Model for the fixed asset, click Journal details.
7. Select Lines to see the individual lines of the journal entry.
8. Select the journal line containing the asset and select the Fixed Assets tab.
9. Here the user can view the Transaction Type and the Value Model. The Transaction Type will auto-populate to "Acquisition" and the Value Model will default to the current value model for that fixed asset.

Note: If the transaction type and book do not auto-populate, please go to Fixed assets > Setup > Fixed asset parameters to set up the book and transaction type for the created fixed assets.

1.	After posting the initial recognition journal entry, the transaction will appear as an acquisition transaction of the fixed asset. To view the transaction table, navigate to **Fixed Assets > Fixed Assets > Fixed Assets**. Select the appropriate fixed asset and click **Valuations** in the top ribbon. The initial recognition journal entry has created an acquisition transaction for the specified fixed asset.

The fixed asset can now be depreciated using the standard depreciation functionality in Fixed assets. Please refer to the Microsoft Dynamics 365 Finance training manual for help depreciating the asset.
