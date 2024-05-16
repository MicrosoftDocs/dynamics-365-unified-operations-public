---
title: Revalue lease payments that are linked to an index rate
description: Learn about the adjustment that is made to lease the liability for a right-of-use (ROU) asset when variable lease payments change because of a change in the index rate.
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

# Revalue lease payments that are linked to an index rate

[!include [banner](../includes/banner.md)]

This article describes the adjustment that is made to the lease liability for a right-of-use (ROU) asset when variable lease payments change because of a change in the index rate. The lease liability and ROU asset will be adjusted to account for the new payment amounts. Under Accounting Standards Codification Topic 842 (ASC 842), which is the standard in Generally Accepted Accounting Principles in the US (US GAAP), only the variable payments change when payments increase or decrease because of a change in the index rate, unless there are additional changes to cash flows. These additional changes might include a change in lease terms that is related to interest rates. For more information, see ASC 842-10-55-225 and paragraph 42(b) of International Financial Reporting Standard 16 (IFRS 16).

## Adjust lease payments

Follow these steps to revalue lease payments that are linked to an index rate.

1. To run the lease index revaluation process, go to **Asset leasing \> Periodic \> Index rate revaluation**.

    The **Index rate revaluation** page appears and shows all previous lease index revaluation processes that have been run. The information on this page includes the process ID that was generated from the number sequence setup, the legal entity, the number of lease books that were adjusted, the total liability adjustment for IFRS 16 leases, and the total variable payments that were adjusted for ASC 842 leases.

2. To run the revaluation, on the Action Pane, select **Lease index revaluation**.

    The **Index revaluation parameters** dialog box appears. Here, you can filter and select which leases, lease groups, or other criteria should be used when you select the leases to revalue. Additionally, on the **Run in the background** tab, you can set up the index revaluation process so that it runs in a batch.

4. Select the filters for selecting leases that should be included in the background processing, and then select **OK**.

    The **Index Rate revaluation preview** dialog box appears and shows the leases that will be revalued. It also shows the asset and liability adjustments or the variable payment adjustments.

5. To prevent leases from being revalued, select the leases that **should** be revalued. If you don't select any leases, all leases will be revalued. When you've finished, select **OK** to revalue the lease payments.
6. To view the transactions that were created for a specific index revaluation process, select the process ID, and then select **Transactions**.

    A dialog box appears and shows the details of the transactions that were created during processing.

> [!NOTE]
> Only leases that have a revaluation date that is on or before the system date can be revalued. The system automatically ignores all leases that have a revaluation date that is later than the system date.

## ASC 842 leases – Index revaluation

To view the effects of the lease revaluation process on ASC 842 leases, open the payment schedule for a lease. The page shows only the variable payments that have been made on or after the revaluation date was changed because of the index revaluation. The amortization and depreciation schedules remain unchanged. When you create an invoice that has a variable payment, the variable payment is debited to the Variable payment posting account. Also, the variable payment amount is added to the credit entry that's posted directly to the vendor, or posted to Notes payable account, depending on the lease book setup.

The payment schedule lines on the lease details page are automatically updated with a new line that indicates the new index rate. Additionally, a column shows whether the line was created manually or through the index revaluation process.

## IFRS 16 leases – Index revaluation

To view the effects of the lease revaluation process on IFRS 16 leases, open the lease details for an adjusted lease. The **Lease term** and **Asset useful life** fields have been updated to reflect the passage of time from the commencement date or modification date to the revaluation date. Additionally, the payment schedule lines have updated to reflect the new payments on the lease, the new index rate, and how the line was created.

You can view the newly generated payment schedule that starts on the revaluation date and show the total updated payment amount. A new lease liability amortization schedule and an asset depreciation schedule have also been created to reflect the adjusted payment schedule.

The journal entry has automatically posted the adjustment journal entry to the account for the change in lease payments that are related to the index revaluation.

> [!NOTE]
> If the **Breakdown payment amount** option is enabled on the **General** FastTab of the **Lease details** page, and the associated book is IFRS 16, the index revaluation process will automatically add a record in the **Payment amount break down** dialog box. The amount will reflect the change that was made to the payment because of index revaluation. The record will be marked as **Used for IRFS 16 index revaluation**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
