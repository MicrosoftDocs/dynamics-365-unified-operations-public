---
title: Impair right-of-use assets
description: Learn about the functionality that records an impairment and adjusts the asset depreciation schedule of an Accounting Standards Codification Topic 842 operating lease.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: 
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Impair right-of-use assets

[!include [banner](../includes/banner.md)]

If a right-of-use (ROU) asset's carrying amount isn't recoverable, you might need to test whether the asset is impaired. If you determine that the asset is impaired, Asset leasing can record the impairment and adjust the depreciation schedule accordingly. This article describes the functionality that records the impairment and adjusts the depreciation schedule of an Accounting Standards Codification Topic 842 (ASC 842) operating lease. The same method also applies to International Financial Reporting Standard 16 (IFRS 16) leases.

The remaining balance of the ROU asset will be amortized on a straight-line basis for the number of periods that remain, regardless of whether the lease was classified as a finance lease under IFRS 16 or an operating lease under ASC 842.

You must define the impairment number sequence on the **Asset leasing parameters** page.

## Impair an ROU asset

1. Go to a lease, and select **Books**.
1. On the Action Pane, select **Impairment**.
1. In the dialog box that appears, enter the amount of the asset impairment in the **Impairment amount** field. To decrease the ROU asset, enter a positive value.
1. Enter the date when the impairment entry should be posted in the **Transaction date** field.
1. Enter the remaining number of months to amortize in the **Periods remaining** field.
1. Set the **Preview** option to view the proposed asset balance and financial entry before they're created or posted.
1. Set the **Close book** option to **Yes** to close the lease book. You can undo this action by using the **Reopen lease** status. You can't post entries against closed leases, and you can't adjust closed leases.
1. Select **Post** to create or post the impairment entry.

> [!NOTE]
> After the impairment transaction is posted, a new book version is created.
> If the lease is classified as an operating lease, the system calculates the monthly depreciation after impairment by using straight-line depreciation.
>
> If the impairment workflow is configured, the **Post** button isn't visible and you must submit the impairment for approval.

1. To view the impaired asset depreciation schedule, open the asset depreciation schedule for the lease book. The asset is now depreciated on a straight-line basis over the number of months that you entered in the **Periods remaining** field.
1. To view the impairment expense journal entry, select **Asset leasing journal** on the Action pane of the impaired lease book. The system creates a journal entry that debits the impairment expense posting account and credits the lease asset posting account.
1. To view the new carrying value of the ROU asset, select **Asset transactions** on the Action pane of the lease book.

## Example of ROU asset impairment

For this example, the lease is a nonspecialized asset that doesn't transfer ownership or grant the lessee the option to purchase.

### Setup

The following tables show the values that you set on the **General** and **Payment schedule lines** tabs for the lease that you use in this example.

**General** tab

| Field                      | Value            |
|----------------------------|------------------|
| Fair value of the asset    | 600,000          |
| Incremental borrowing rate | 7%               |
| Compounding interval       | Annually         |
| Asset useful life (months) | 600              |
| Annuity type               | Ordinary annuity |
| Commencement date          | 01/01/2025       |

**Payment schedule lines** tab

| Field             | Value      |
|-------------------|------------|
| Start date        | 1/1/2025   |
| Period interval   | Monthly    |
| Periods           | 120        |
| End date          | 12/31/2034 |
| Payment frequency | Annually   |
| Payment amount    | 10,000     |

### Steps

1. After you create the lease as described earlier in this article, go to the lease book, and confirm the payment schedule. Then post the initial recognition journal entry. The initial ROU asset and lease liability should be $70,235.81. For this example, the lease was classified as an operating lease under ASC 842.
1. Run the batch journal process three times to simulate the passage of three years for the lease payments, interest expenses, and depreciation expenses.
1. After you finish running all three batch jobs, go back to the lease book, and open the liability and asset transactions tables to view the current carrying value of the ROU asset and lease liability. After three years, the value of the liability is approximately $-53,893.00, and the value of the asset is approximately $53,893.00.

    After three years, the business does impairment tests and determines that the ROU asset has an impairment of $35,000. You must now record this impairment.

1. Go to the lease book, and then, on the Action Pane, select **Impairment**.
1. On the **Impairment parameter** page, enter the following details.

    | Field                  | Value    |
    |------------------------|----------|
    | Impairment amount      | 35,000   |
    | Transaction date       | 1/1/2028 |
    | Periods remaining      | 84       |
    | Post                   | Yes      |
    | Close book             | No       |

1. An impairment expense journal entry is created and posted. To view it, go to the asset's leasing journal in the lease book. Notice that the amount of the impairment is debited to the Impairment expense posting account, and the ROU asset posting account is credited.

1. To view the net effect of the impairment, go to the liability and asset transactions tables. Notice that the impairment expense decreases the ROU asset, but the carrying amount of the lease liability doesn't change.

The impairment has one other effect that you should consider. Because the ROU asset amount is now much less than the lease liability, you must depreciate the amount differently than before. Specifically, the asset is now depreciated in a straight-line manner throughout the remaining 84 months of the lease, beginning on the transaction date.

## Lease impairment workflow

Use the lease **Impairment workflow** to ensure a consistent impairment process. The workflow guides each lease impairment through predefined approval steps and assigns tasks to specific users. After you approve a lease impairment, it finalizes on the **Lease impairment** list page.
To approve a lease impairment, go to the **Lease book** and open the **Lease impairment** dialog. Select **Submit** to workflow. You manage the approval directly from the **Lease impairment** page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
