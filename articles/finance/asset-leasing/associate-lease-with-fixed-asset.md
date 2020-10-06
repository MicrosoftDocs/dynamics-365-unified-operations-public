---
# required metadata

title: Associate fixed assets with leases
description: The topic explains how to associate an existing fixed asset with a new lease. 
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

# Associate fixed assets with leases

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The topic explains how to associate an existing fixed asset with a new lease. When you associate a fixed asset with a lease, the right-of-use (ROU) asset value at initial recognition will be the acquisition cost of the fixed asset.

Before you can associate a fixed asset with a lease, you must create a record for the fixed asset in Fixed assets. Then, on the **Lease summary** page, you must create a lease and link the asset to that lease.

1. Add a lease by following the steps in [Add or copy leases](add-lease.md). On the **Add lease** page, in the **Fixed asset number** field, select the asset that hasn't yet been acquired.
2. Select **Books**, and confirm the payment schedule.
3. Select **Initial recognition**.
4. Select **Asset leasing journal**.

    The initial recognition journal entry for the lease debits the fixed asset for the amount that is usually debited to the ROU asset account.

    You can now view the transaction type and book for the fixed asset.

5. Select **Journal details**.
6. Select **Lines** to view the individual lines for the journal entry.
7. Select the journal line that contains the asset, and then select the **Fixed Assets** tab.

    The **Fixed assets** tab shows the transaction type and the book. By default, the **Transaction type** field is set to **Acquisition**, and the **Book** field is set to the current book for the fixed asset.

After you post the initial recognition journal entry, the transaction appears as an acquisition transaction for the fixed asset. To view the transaction table, go to **Fixed assets \> Fixed assets \> Fixed assets**, select the appropriate asset, and then select **Valuations**. You should see that the initial recognition journal entry has created an acquisition transaction for the specified fixed asset.

The fixed asset can now be depreciated by using the standard depreciation functionality in Fixed assets. For more information about depreciation, see [Depreciation methods and conventions](../fixed-assets/depreciation-methods-conventions.md).

> [!NOTE]
> If you associate a fixed asset with a lease, the following transactions and inquiry should occur on the **Asset depreciation**, **Lease impairment**, and **Asset transactions** pages in Fixed assets. The corresponding functions in Asset leasing will automatically be disabled.
