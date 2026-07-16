---
title: Record right-of-use asset depreciation 
description: Learn about how to create the journal entry for the amortization that is required for leases that are recognized on an organization's balance sheet.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeaseAssetSchedule
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Record right-of-use asset depreciation

[!include [banner](../includes/banner.md)]

For leases that are recognized on an organization's balance sheet, the right-of-use (ROU) asset is amortized on a monthly basis. This article explains how to create the journal entry for the amortization. The amortization debits the expense ledger account and credits the accumulated depreciation ledger account, based on the setup of your posting profile and the lease type. These entries can be created for each lease, or they can be created for multiple leases by using the batch journal functionality.

## Asset depreciation schedule

1. On the **Lease summary** page, select a lease. Then select **Books \> Asset depreciation schedule** to open the **Asset depreciation schedule** page.

    The ROU asset depreciation expense journal entry is based on the amount in the **Depreciation Expense** column. For an example of the guidance for accounting standard compliance, see the [Calculation of ROU asset amortization expense for finance leases](#calculation-of-rou-asset-amortization-expense-for-finance-leases) section later in this article.

1. Select the period of depreciation, and then select **Create journal**. You receive a message that states that the journal to record depreciation was created.
1. Select **Journals \> Asset leasing journals** to open the **Asset leasing journal** page, where you can view the depreciation expense journal entry that was created.

   The system locks certain financial fields from being edited to prevent any variances between the transactions and the schedules. Some locked fields include: **Account**, **Amounts**, **Financial dimensions**, **Currency**, and **Transaction type**. Additionally, you can't add or delete journal entry lines in any Asset leasing journal entries, as this action might cause variances between the schedules and the transactions.

1. Select the journal entry, and then select **Post** to record the depreciation entry to General ledger.

## Calculation of ROU asset amortization expense for operating leases

The depreciation expense of an operating lease is calculated as the difference between the monthly straight-line lease expense and the monthly interest expense on the lease liability, in accordance with Accounting Standards Codification Topic 842 (ASC 842), which is the standard in Generally Accepted Accounting Principles in the US (US GAAP). The straight-line lease expense is calculated as the sum of all lease payments divided by the lease term in months. (The sum of lease payments includes any prepayments, initial direct costs, dismantling costs, and lease incentives.) The following table shows an example of the amortization expense for an operating lease.

### Example of ROU asset amortization expense for operating leases

| Field                                          | Value       |
|------------------------------------------------|-------------|
| Payment amount                                 | 1,000       |
| Payment frequency                              | Monthly     |
| Lease term (months)                            | 24          |
| Total lease payments                           | 24,000      |
| Incremental borrowing rate                     | 5%          |
| Annuity type                                   | Annuity due |
| Compounding Interval                           | Monthly     |
| Present value of future minimum lease payments | 22,888.87   |

As mentioned earlier, you calculate the straight-line lease expense by dividing the sum of all payments by the lease term. The monthly interest expense is automatically calculated on the liability amortization schedule. You calculate the interest expense by using the effective interest rate method. Use the straight-line lease cost to subtract the interest expense for each month. Use this value to reduce the ROU asset.

| Month | Straight-line lease cost | Interest expense                        | Calculation of ROU asset amortization expense |
|-------|--------------------------|-----------------------------------------|-----------------------------------------------|
| 1     | (24,000 ÷ 24) = 1,000.00 | (22,888.87 – 1,000) × (5% ÷ 12) = 91.20 | 1,000 – 91.20 = 908.80                        |
| 2     | (24,000 ÷ 24) = 1,000.00 | (21,980.08 – 1,000) × (5% ÷ 12) = 87.42 | 1,000 – 87.42 = 912.58                        |
| 3     | (24,000 ÷ 24) = 1,000.00 | (21,067.49 – 1,000) × (5% ÷ 12) = 83.62 | 1,000 – 83.62 = 916.39                        |

> [!NOTE]
> According to ASC 842, the depreciation of the ROU asset for an operating lease is classified as a lease expense on the income statement. For visibility, Asset leasing describes the entry as the depreciation of the ROU asset. However, assign the debit entry to an operating lease expense account, and assign the credit entry directly to the ROU asset for the operating lease. Nevertheless, in the lease parameters, you can specify that credit entries should be made to an accumulated depreciation account for operating ROU assets.

If the lease is classified as an operating lease, the monthly depreciation after impairment is calculated using straight-line depreciation.

## Calculation of ROU asset amortization expense for finance leases

For leases that have a finance classification, the system calculates the ROU asset amortization on a straight-line basis. Therefore, the depreciation expense is the same for each month.

In accordance with International Financial Reporting Standard 16 (IFRS 16) and ASC 842, the asset amortizes over either the lease term or the asset's useful life, whichever is less. If you turn on the **Transfer of ownership** parameter for the lease, the lease automatically depreciates over the asset's useful life.

### Example of ROU asset amortization expense for finance leases

| Field                                | Value                                   |
|--------------------------------------|-----------------------------------------|
| Beginning right-of-use asset balance | 22,889.87                               |
| Lease term (months)                  | 24                                      |
| Asset useful life (months)           | 36                                      |
| Month                                | Right-of-use asset amortization expense |
| 1                                    | 22,889.87 ÷ 24 = 953.74                 |
| 2                                    | 22,889.87 ÷ 24 = 953.74                 |
| 3                                    | 22,889.87 ÷ 24 = 953.74                 |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
