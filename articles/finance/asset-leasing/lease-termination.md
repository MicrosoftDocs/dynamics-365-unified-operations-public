---
# required metadata

title: Lease termination proposal
description: This topic explains how to propose a lease for termination.
author: moaamer
ms.date: 07/16/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeaseTerminateLeaseListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations, Finance

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2021-1-28
ms.dyn365.ops.version: 10.0.17

---

# Propose a lease for termination

[!include [banner](../includes/banner.md)]

If a lease is terminated early, Asset leasing can record a termination journal entry to write off the lease liability, right-of-use (ROU) asset, and accumulated depreciation, and book a gain or loss. The early termination process terminates a lease and its associated lease books. It doesn't terminate individual lease books. This topic describes the functionality that lets you propose a lease for termination and process the lease termination journal entry.

If a lease isn't classified as a deferred rent treatment lease and isn't associated with a fixed asset, Asset leasing produces the following termination journal entry.

| Transaction                           | Debit (Dr.) | Credit (Cr.) |
|---------------------------------------|-------------|--------------|
| Dr. Lease liability                   | X           |              |
| Dr. Accumulated depreciation          | X           |              |
| Dr. Gain (loss) on lease modification | X           |              |
| Cr. Lease asset                       |             | X            |
| Cr. Gain (loss) on lease modification |             | X            |

If the lease book is classified as a deferred rent book, the entry writes off the balance of the deferred rent before the termination to the gain or loss account, as shown here.

| Transaction                           | Debit (Dr.) | Credit (Cr.) | 
|---------------------------------------|-------------|--------------|
| Dr. Deferred rent                     | X           |              |
| Cr. Gain (loss) on lease modification |             | X            |
| Cr. Deferred rent                     |             | X            |
| Dr. Gain (loss) on lease modification | X           |              |

If the lease book is connected to a fixed asset, the ROU asset is accounted for in Fixed assets. This accounting includes the accounting for early terminations. Asset leasing produces the following journal entry to write off the lease liability.

| Transaction                           | Debit (Dr.) | Credit (Cr.) |
|---------------------------------------|-------------|--------------|
| Dr. Lease liability                   | X           |              |
| Cr. Gain (loss) on lease modification |             | X            |

For information about the correct way to dispose of an ROU asset, see [Dispose of a fixed asset as scrap](../fixed-assets/dispose-of-a-fixed-asset-as-scrap.md).

## Propose a lease for termination

1. Go to the lease that must be terminated, and then, on the Action Pane, select **Termination proposal**.

    > [!NOTE]
    > The **Termination proposal** button is unavailable if there are any unposted journal entries against any book. Before you can terminate the lease, you must post or delete any journal entries that have been created against the lease.

2. In the dialog box that appears, set the **Effective date** and **Posting date** fields for the termination journal entry.
3. Select **Termination proposal** to propose the lease for termination.
4. Select **Post lease termination** to automatically post the lease termination journal entry.
5. On the **Lease terminations** page, select the lease ID of the lease that you proposed for termination to view the termination lines. The termination lines show the carrying values of the ROU asset, lease liability, accumulated depreciation, deferred rent (if applicable), and gain or loss that must be recognized on the termination of the lease.

The lease is now ready for termination. The value of the **Termination status** field for the lease book is changed to **Ready for termination**. At this point, you can no longer post journal entries against the lease, or adjust or impair it. 

## Process leases that are ready for termination

To process leases that are ready for termination and post the termination journal entry, follow these steps.

1. On the **Lease terminations** page, select the lease to process, and then select **Terminate**.
2. In the dialog box that appears, select **OK**.

The system posts the termination journal entry. The **Lease status** field for the lease book is set to **Terminated**, and the **Termination proposal status** field is set to **Completed**.

## Reverse a lease termination

To reverse a lease termination journal entry and open a terminated lease, follow this step.

- On the **Lease terminations** page, select the terminated lease to reverse, and then select **Reverse termination**.

The system reverses the termination journal entry. The **Lease status** field for the lease book is set to **Open**. The lease no longer appears on the **Lease terminations** page and can be proposed again for termination.

## Example of a lease termination

For this example, the lease is associated with a non-specialized asset, and it doesn't transfer ownership of the asset or grant the lessee the option to purchase the asset.

### Setup

The following tables show the values that are set on the **General** and **Payment schedule lines** tabs for the lease that is used in this example.

**General tab**

| Field                      | Value            |
|----------------------------|------------------|
| Fair value of the asset    | 600,000          |
| Currency                   | USD              |
| Initial direct costs       | 1,000            |
| Incremental borrowing rate | 7%               |
| Compounding interval       | Annually         |
| Asset useful life (months) | 600              |
| Annuity type               | Ordinary annuity |
| Commencement date          | 1/1/2019         |

**Payment schedule lines tab**

| Field             | Value      |
|-------------------|------------|
| Start date        | 1/1/2019   |
| Period interval   | Monthly    |
| Periods           | 120        |
| End date          | 12/31/2028 |
| Payment frequency | Annually   |
| Payment amount    | 10,000     |

### Steps for terminating the lease

1. After you create the lease as described earlier in this topic, go to the lease book, and confirm the payment schedule. Then post the initial recognition journal entry. The initial ROU asset is $71,235.81, and lease liability should be $70,235.81. For this example, the lease was classified as an operating lease under Accounting Standards Codification Topic 842 (ASC 842).
2. Run the batch journal process three times to simulate the passage of three years for the lease payments, interest expenses, and depreciation expenses.
3. After you've finished running all three batch jobs, go back to the lease book, and open the Liability and Asset transactions tables to view the current carrying value of the ROU asset and lease liability. After three years, the value of the liability should be approximately $-53,893.00, and the value of the asset should be approximately $54,593.00.

    After the three years have passed, the business and lessor mutually agree to terminate the lease. Therefore, you must now terminate the lease.

4. Go to the lease that must be terminated, and then, on the Action Pane, select **Termination proposal**. 
5. In the dialog box that appears, in the **Effective date** and **Posting date** field, enter **1/1/2021**.
6. Select **Termination proposal** to propose the lease for termination.

    The **Lease terminations** page appears and shows the lease that will be terminated.

7. To view the termination lines, select the lease ID of the lease that you proposed for termination. The termination lines show the carrying values of the lease. The following table shows what these values should be for this example. 

    | Field                                                 | Value      |
    |-------------------------------------------------------|------------|
    | Carrying balance of liability in transaction currency | $53,892.89 |
    | Right-of-use asset in transaction currency            | $71,235.81 |
    | Accumulated depreciation in transaction currency      | $16,642.92 |
    | Gain (loss) in transaction currency                   | $-700.00   |

8. To post the termination journal entry, select the lease on the **Lease terminations** page, and then select **Terminate**.
9. In the dialog box that appears, select **OK**.
10. To view the termination journal entry that has been created and posted, go to the asset's leasing journal in the lease book. The following table shows what this entry should look like for this example.

    | Transaction                           | Debit (Dr.) | Credit (Cr.) |
    |---------------------------------------|-------------|--------------|
    | Dr. Lease liability                   | 53,892.89   |              |
    | Dr. Accumulated depreciation          | 16,642.92   |              |
    | Dr. Gain (loss) on lease modification | 700.00      |              |
    | Cr. Lease asset                       |             | 71,235.81    |

11. To view the net effect of the termination, where the ROU asset and lease liability will be 0 (zero), open the Liability and Asset transactions tables.

The lease status should now be **Terminated**. No additional journal entries will be posted against this lease unless the termination is reversed.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
