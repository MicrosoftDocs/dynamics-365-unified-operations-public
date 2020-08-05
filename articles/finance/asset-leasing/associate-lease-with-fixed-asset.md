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

The topic lists the steps for associating an existing fixed asset with a new lease. when you associate a lease with a fixed asset, the right-of-use (ROU) asset value at initial recognition will be its acquisition cost as a fixed asset.

1. Add a lease as described in the [Add or copy a lease](add-lease.md) topic. Select the asset that hasn't been acquired yet from the **Fixed asset number dropdown** in the **Add lease** page.
2. Select **Books** and confirm the payment schedule
3. Select **Initial recognition**.
4. Select **General journals**.
5. The initial recognition journal entry for the lease will debit the fixed asset for the amount normally debited to the ROU asset account.
6. To view and edit the transaction type and value model for this asset, click **Journal details**.
7. Select **Lines** to see the individual lines on the journal entry.
8. Select the journal line containing the asset and open the **Fixed Assets** tab.
9. From the **Fixed assets** tab, you can view the transaction type and the value model. The entry in the **Transaction type** field will default to **Acquisition**, and the entry in the **Value model** field will default to the current value model for that fixed asset.

   > [!Note]
   > If values in the **Transaction type** and **Book** fields aren't entered by default, go to **Fixed assets > Setup > Fixed asset parameters** to set up the book and transaction type for the fixed asset records you create.

After posting the initial recognition journal entry, the transaction will appear as an acquisition transaction for the fixed asset. To view the transaction table, navigate to **Fixed Assets > Fixed Assets > Fixed Assets**. Select the appropriate asset, and click **Valuations**. The initial recognition journal entry has created an acquisition transaction for the specified fixed asset.

The fixed asset can now be depreciated using the standard depreciation functionality in Fixed assets. See [Depreciation methods and conventions](../fixed-assets/depreciation-methods-conventions.md) for more information about depreciation.
