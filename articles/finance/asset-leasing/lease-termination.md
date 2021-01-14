---
# required metadata

title: Lease termination proposal
description: This topic explains how to propose a lease for termination.
author: moaamer
manager: Ann Beebe
ms.date: 1/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: AssetLease
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

## Propose a lease for termination

This topic explains how to propose a lease for termination. If the lease
is terminated early, Asset leasing can record a termination journal
entry to write off the lease liability, right-of-use asset, accumulated
depreciation, and book a gain or loss. The early termination process
will terminate a lease and its associated lease books. This process will
not terminate individual lease books. This topic describes the
functionality that will propose a lease for termination and to process
the lease termination journal entry.

When a lease is not classified as a deferred rent treatment lease and is
not associated to a fixed asset, Asset leasing will produce the
following termination journal entry:

 | Transaction                            | Debit (Dr.) | Credit (Cr.) |
 |--------------------------------------- |-------------|--------------|
 | Dr. Lease liability                    |X            |              |
 | Dr. Accumulated depreciation           |X            |              |
 | Dr. Gain (loss) on lease modification  |X            |              |
 | Cr. Lease asset                        |             | X            |
 | Cr. Gain (loss) on lease modification  |             | X            |

If the lease book is classified as a deferred rent book, the entry will
write off the balance of the deferred rent prior to the termination to
the gain or loss account:

 | Transaction                            |Debit (Dr.)   | Credit (Cr.) | 
 | ---------------------------------------|------------- |--------------|
 | Dr. Deferred rent                      | X            |              |
 | Cr. Gain (loss) on lease modification  |              | X            |
 | Cr. Deferred rent                      |              | X            |
 | Dr. Gain (loss) on lease modification  | X            |              |

If the lease book is connected to a fixed asset, the right-of-use asset
is accounted for in Fixed assets, including early terminations. Asset
leasing will produce the journal entry to write-off the lease liability:

 | Transaction                            | Debit (Dr.)  | Credit (Cr.)  |
 | ---------------------------------------| -------------| --------------|
 | Dr. Lease liability                    | X            |               |
 | Cr. Gain (loss) on lease modification  |              | X             |

To properly dispose of the right-of-use asset, see
<https://docs.microsoft.com/en-us/dynamics365/finance/fixed-assets/dispose-of-a-fixed-asset-as-scrap>

Propose a lease for termination

1.  Go to the lease to be terminated, and on the Action Pane, select
    **Termination proposal.**

Note: This button will be disabled if there are any unposted journal
entries against any book. Please post or delete any created journal
entries against the lease before terminating the lease.

2.  In the dialog box that appears, enter values for the Effective date
    and Posting date of the termination journal entry.

3.  Select **Termination proposal**, to propose the lease for
    termination. Select **Post lease termination** to automatically post
    the lease termination journal entry.

4.  The **Lease terminations** form will open.

5.  Select the **Lease ID** of the lease proposed for termination to
    view the termination lines. The termination lines will show the
    carrying values of the right-of-use asset, lease liability,
    accumulated depreciation, deferred rent if applicable, and gain or
    loss to be recognized on the termination of the lease.

> The lease is now ready for termination. The Termination status field
> on the lease book has changed to "Ready for termination". When the
> lease is in this status, you cannot post journal entries against the
> lease, adjust or impair the lease.
>
> Process ready for termination leases

1.  To process ready for termination leases and post the termination
    journal entry, select the lease from the **Lease terminations** form
    and click **Terminate**

2.  In the dialog box that appears, click **OK.**

The system will post the termination journal entry. The **Lease status**
field on the lease book will show as "Terminated" and the **Termination
proposal status** will show as "Completed".

Reverse a lease termination

1.  To reverse a lease termination journal entry and open a terminated
    lease, navigate to the **Lease terminations** form.

2.  Select the terminated lease to reverse

3.  Click **Reverse termination**

The system will reverse the termination journal entry. The **Lease
status** field on the lease book will show as "Open". The lease will no
longer appear in the **Lease terminations** form and can be proposed
again for termination.

Example of a lease termination

For this example, the lease is a non-specialized asset that doesn\'t
transfer ownership or grant the lessee the option to purchase.

Setup

The following tables show the values that are set on the General and
Payment schedule lines tabs for the lease that is used in this example.

General tab

 | Field                       | Value
 | ----------------------------| ------------------
 | Fair value of the asset     | 600,000
 | Currency                    | USD
 | Initial direct costs        | 1,000
 | Incremental borrowing rate  | 7%
 | Compounding interval        | Annually
 | Asset useful life (months)  | 600
 | Annuity type                | Ordinary annuity
 | Commencement date           | 1/1/2019

Payment schedule lines tab

 | Field              | Value
 | -------------------| ------------
 | Start date         | 1/1/2019
 | Period interval    | Monthly
 | Periods            | 120
 | End date           | 12/31/2028
 | Payment frequency  | Annually
 | Payment amount     | 10,000

Steps

1.  After you create the lease as described earlier in this topic, go to
    the lease book, and confirm the payment schedule. Then post the
    initial recognition journal entry. The initial right-of-use asset is
    \$71,235.81 and lease liability should be \$70,235.81. For this
    example, the lease was classified as an operating lease under
    ASC 842.

2.  Run the batch journal process three times to simulate the passage of
    three years for the lease payments, interest expenses, and
    depreciation expenses.

3.  After you\'ve finished running all three batch jobs, go back to the
    lease book, and open the liability and asset transactions tables to
    view the current carrying value of the right-of-use asset and lease
    liability. After three years, the value of the liability should be
    approximately \$-53,893.00, and the value of the asset should be
    approximately \$54,593.00.

After three years, the business and lessor mutually agree to terminate
the lease. You must now terminate the lease.

4.  Go to the lease to be terminated, and on the Action Pane, select
    **Termination proposal.**

5.  In the dialog box that appears, enter 1/1/2021 for the Effective
    date and 1/1/2021 for the Posting date.

6.  Select **Termination proposal**, to propose the lease for
    termination.

7.  The Lease Terminations form will open showing the lease to be
    terminated.

8.  Click the Lease ID to view the lease termination lines displaying
    the carrying values of the lease:

 | Field                                                  | Value
 | -------------------------------------------------------| -------------
 | Carrying balance of liability in transaction currency  | \$53,892.89
 | Right-of-use asset in transaction currency             | \$71,235.81
 | Accumulated depreciation in transaction currency       | \$16,642.92
 | Gain (loss) in transaction currency                    | \$-700.00

9.  To post the termination journal entry, select the lease from the
    **Lease terminations** form and click **Terminate**

10. In the dialog box that appears, click **OK.**

11. The termination journal entry has been created and posted. To view
    it, go to the asset's leasing journal in the lease book. The entry
    would appear as shown below:

 | Transaction                            | Debit (Dr.)  | Credit (Cr.)
 | ---------------------------------------| -------------| --------------
 | Dr. Lease liability                    | 53,892.89    | 
 | Dr. Accumulated depreciation           | 16,642.92    | 
 | Dr. Gain (loss) on lease modification  | 700.00       | 
 | Cr. Lease asset                        |              | 71,235.81

12. To view the net effect of the termination, where the right-of-use
    asset and lease liability will be 0, go to the liability and asset
    transactions tables.

The lease status will show as "Terminated". No additional journal
entries will post against this lease unless the termination is reversed.
