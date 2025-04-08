---
title: Associate fixed assets with leases
description: Learn about how to associate an existing fixed asset with a new lease, including a step-by-step process that outlines how to create a record for fixed assets. 
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeaseDetail
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Associate fixed assets with leases

[!include [banner](../includes/banner.md)]

The article explains how to associate an existing fixed asset with a new lease. When you associate a fixed asset with a lease, the right-of-use (ROU) asset value at initial recognition will be the acquisition cost of the fixed asset.

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

When a lease is associated with a fixed asset, the **Service life** field on the fixed asset book will be updated to align with the smallest value from the following criteria: 

 - The asset’s useful life
 - The lease term from the associated lease book

If the **Transfer of ownership** field is set to **Yes** for the lease book, the value in the **Service life** field will always be the asset’s useful life. 
 
The **Service life** is updated every time the lease is adjusted to ensure that the right-of-use asset is depreciated over the term lease, as if it were depreciated in Asset leasing.

> [!NOTE]
> If you associate a fixed asset with a lease, the **Asset depreciation** and **Lease impairment** buttons are disabled in Asset leasing. You can view asset depreciation and lease impairment transactions from Fixed assets. The **Asset transactions** button, which opens an inquiry form is also disabled. You can also open the **Asset transactions** inquiry form in Fixed assets.  

The **Fixed assets** and **Fixed asset book** pages display the lease ID that is associated with a fixed asset. If a fixed asset is associated with a lease, the lease ID and lease description are displayed on the **Lease information** FastTab on the **Fixed assets** page. For fixed asset books that are associated with lease books, the **Lease ID**, **Lease description**, and **Book type** fields display information for the selected fixed asset book on the **Lease information** FastTab, to indicate that it's associated with a lease book.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
