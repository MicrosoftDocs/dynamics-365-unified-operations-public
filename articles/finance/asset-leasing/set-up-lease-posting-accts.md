---
title: Set up lease posting accounts
description: Learn about the posting accounts that are required for Asset leasing transactions and explains how to define posting accounts on the Lease posting parameters page.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeasePostingAccounts
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Set up lease posting accounts

[!include [banner](../includes/banner.md)]

This article lists the posting accounts that are required for Asset leasing transactions and explains how to define posting accounts on the **Lease posting parameters** page.

To comply with Accounting Standards Codification Topic 842 (ASC 842) and International Financial Reporting Standard 16 (IFRS 16), you might have to create accounts in your chart of accounts. However, any accounts that you create to comply with ASC and IFRS standards aren't fixed asset accounts. Under ASC 842, a right-of-use (ROU) asset is recorded for both finance and operating leases. These leases are separate from fixed assets. (You can still maintain an ROU asset by using Fixed assets.)

For information about how to create account structures, see [Create account structures](../general-ledger/tasks/create-account-structures.md). For information about how to create a main account, see [Create a main account](../general-ledger/tasks/create-main-account.md).

The following table shows examples of accounts that you must create for leased asset transactions, if they haven't already been created. Under IFRS 16, the operating lease relationships are still used for low-value and short-term leases.

| Ledger account number | Account type  | Account name                                          |
|-----------------------|---------------|-------------------------------------------------------|
| 180150                | Asset         | Vehicle ROU asset                                     |
| 180160                | Asset         | Building ROU asset                                    |
| 180250                | Asset         | Accumulated depreciation - vehicles                   |
| 180260                | Asset         | Accumulated depreciation - buildings                  |
| 222300                | Liability     | Short-term obligation - finance leases                |
| 222310                | Balance sheet | Short-term obligation - Operating leases              |
| 250200                | Liability     | Notes payable                                         |
| 250601                | Balance sheet | Long-term obligation - finance leases                 |
| 250602                | Balance sheet | Long-term obligation - operating leases               |
| 250606                | Balance sheet | Deferred rent                                         |
| 300160                | Balance sheet | Retained earnings                                     |
| 604500                | Expense       | Lease Expense                                         |
| 604501                | Expense       | Vehicle operating lease expense - interest accretion  |
| 604502                | Expense       | Vehicle operating lease expense - amortization        |
| 605200                | Expense       | Building operating lease expense - interest accretion |
| 605201                | Expense       | Building operating lease expense - amortization       |
| 607101                | Expense       | Vehicle lease amortization expense                    |
| 607102                | Expense       | Building lease amortization expense                   |
| 607103                | Expense       | Impairment expense - finance leases                   |
| 607104                | Expense       | Impairment expense - Operating leases                 |
| 618910                | Expense       | Lease expense - finance leases                        |
| 618920                | Expense       | Variable payments - finance leases                    |
| 618930                | Expense       | Variable payments - operating leases                  |
| 800600                | Expense       | Vehicle lease interest expense                        |
| 800601                | Expense       | Building lease interest expense                       |
| 801201                | Balance sheet | Gain & loss - lease modification                      |

## Configure posting accounts

To assign accounts to the lease books and groups that have been created, you must configure parameters for Asset leasing.

1. Go to **Asset leasing \> Setup \> Lease posting parameters**.
2. On the **Accounts** tab, open the **Lease accounts** FastTab. Determine the main accounts for finance and operation leases to corresponding **Posting type**. The preceding table shows the accounts that are related to operating and finance leases.

    > [!NOTE]
    > This step requires that you set up separate accounts for both operating and finance leases for each posting type except **Lease expense offset** and **Lease increase/decrease**. Companies that adhere to the IFRS 16 accounting framework must add a main account for operating lease. But the system will not use this account even though it's a required field because all leases under IFRS 16 are classified as finance leases.
    >[!NOTE]
    > **Lease increase/decrease** will be used as posting type for additional asset considerations, including **Initial direct cost, Lease incentives, Lease prepayments and Dismantling costs**, but post to the Right-of-use asset main account which defaults to **Lease asset**.        
    
3. To select a specific lease group corresponding to main account, in the **Account Code** field, select **Group**. Then, in the **Account/Group number** field, select the lease group to assign to the main account.
4. To assign account codes to the administrative costs that have been set up in the system, on the **Executory costs** FastTab, in the **Expense type** field, select an expense. Then assign the finance and operating accounts to use for each book.

    > [!NOTE]
    > The selected finance or operating account will be debited when the invoice for the scheduled expense is posted.
    > **Lease expense offset** will be used as posting type for executory costs transactions but post to defined **Offset account** in the **Execuroty costs payment schedule lines** in lease details or lease book form.   


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
