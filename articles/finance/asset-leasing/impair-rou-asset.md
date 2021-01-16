---
# required metadata

title: Impair right-of-use assets
description: This topic describes the functionality that records an impairment and adjusts the asset depreciation schedule of an Accounting Standards Codification Topic 842 (ASC 842) operating lease.
author: moaamer
manager: Ann Beebe
ms.date: 10/28/2020
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

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14
---

# Impair right-of-use assets

[!include [banner](../includes/banner.md)]

If a right-of-use (ROU) asset's carrying amount isn't recoverable, you might have to test whether the asset is impaired. If you determine that the asset is impaired, Asset leasing can record the impairment and adjust the depreciation schedule accordingly. This topic describes the functionality that records the impairment and adjusts the depreciation schedule of an Accounting Standards Codification Topic 842 (ASC 842) operating lease. The same method also applies to International Financial Reporting Standard 16 (IFRS 16) leases.

The remaining balance of the ROU asset will be amortized on a straight-line basis for the number of periods that remain, regardless of whether the lease was classified as a finance lease under IFRS 16 or an operating lease under ASC 842.

## Impair an ROU asset

1. Go to the impaired lease, and select **Books**.
2. On the Action Pane, select **Impairment**.
3. In the dialog box that appears, in the **Impairment amount** field, enter the amount of the asset impairment. To decrease the ROU asset, you should enter a positive value.
4. In the **Transaction date** field, enter the date when the impairment entry should be posted.
5. In the **Periods remaining** field, enter the remaining number of months to amortize.
6. Turn on the **Post** parameter if you want the system to automatically post the impairment expense journal entry. If you leave this parameter turned off, the system creates the entry but doesn't post it. You can then post the entry from the **Asset lease journals** page.
7. Set the **Preview before posting** option to **Yes** to view the proposed entry before it's created or posted.
8. Set the **Close book** option to **Yes** to close the lease book. You can't undo this action. Entries can't be posted against closed leases, and closed leases can't be adjusted.
9. Select **OK** to create or post the impairment entry.
10. To view the impaired asset depreciation schedule, open the asset depreciation schedule for that lease book. The asset will now be depreciated on a straight-line basis over the number of months that you entered in the **Periods remaining** field.
11. To view the impairment expense journal entry, select **Asset leasing journal** on the Action Pane of the impaired lease book. The system creates a journal entry that debits the impairment expense posting account and credits the lease asset posting account.
12. To view the new carrying value of the ROU asset, select **Asset transactions** on the Action Pane of the lease book.

## Example of ROU asset impairment

For this example, the lease is a non-specialized asset that doesn't transfer ownership or grant the lessee the option to purchase.

### Setup

The following tables show the values that are set on the **General** and **Payment schedule lines** tabs for the lease that is used in this example.

**General tab**

| Field                      | Value            |
|----------------------------|------------------|
| Fair value of the asset    | 600,000          |
| Incremental borrowing rate | 7%               |
| Compounding interval       | Annually         |
| Asset useful life (months) | 600              |
| Annuity type               | Ordinary annuity |
| Commencement date          | 01/01/2019       |

**Payment schedule lines tab**

| Field             | Value      |
|-------------------|------------|
| Start date        | 1/1/2019   |
| Period interval   | Monthly    |
| Periods           | 120        |
| End date          | 12/31/2028 |
| Payment frequency | Annually   |
| Payment amount    | 10,000     |

### Steps

1. After you create the lease as described earlier in this topic, go to the lease book, and confirm the payment schedule. Then post the initial recognition journal entry. The initial ROU asset and lease liability should be $70,235.81. For this example, the lease was classified as an operating lease under ASC 842.
2. Run the batch journal process three times to simulate the passage of three years for the lease payments, interest expenses, and depreciation expenses.
3. After you've finished running all three batch jobs, go back to the lease book, and open the liability and asset transactions tables to view the current carrying value of the ROU asset and lease liability. After three years, the value of the liability should be approximately $-53,893.00, and the value of the asset should be approximately $53,893.00. 

    After three years, the business does impairment tests and determines that the ROU asset has an impairment of $35,000. You must now record this impairment.
    
4. Go to the lease book, and then, on the Action Pane, select **Impairment**.
5. On the **Impairment parameter** page, enter the following details.

    | Field                  | Value    |
    |------------------------|----------|
    | Impairment amount      | 35,000   |
    | Transaction date       | 1/1/2022 |
    | Periods remaining      | 84       |
    | Post                   | Yes      |
    | Preview before posting | No       |
    | Close book             | No       |

6. An impairment expense journal entry has been created and posted. To view it, go to the asset's leasing journal in the lease book. Notice that the amount of the impairment was debited to the Impairment expense posting account, and the ROU asset posting account was credited.
7. To view the net effect of the impairment, go to the liability and asset transactions tables. Notice that the impairment expense has decreased the ROU asset, but the carrying amount of the lease liability hasn't changed.

The impairment has one other effect that you should consider. Because the ROU asset amount is now much less than the lease liability, the amount must be depreciated differently than it was before. Specifically, the asset is now depreciated in a straight-line manner throughout the remaining 84 months of the lease, beginning on the transaction date.
