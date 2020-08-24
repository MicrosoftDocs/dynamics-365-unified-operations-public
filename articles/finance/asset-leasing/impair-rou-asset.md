---
# required metadata

title: Impair a right-of-use asset
description: This topic describes the process of recording the impairment and adjusts the asset depreciation schedule for an ASC 842 operating lease.
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

# Impair a right-of-use asset

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

If a right-of-use (ROU) asset's carrying amount isn't recoverable, you might need to test whether the asset is impaired. If you determine the asset is impaired, Asset leasing can record the impairment and adjust the depreciation schedule accordingly. This topic describes the functionality that records the impairment and adjusts the depreciation schedule of an ASC 842 operating lease. (The same method applies to IFRS 16 leases, as well.)

The remaining ROU asset balance will be amortized on a straight-line basis for the number of periods remaining regardless of whether the lease was classified as finance under IFRS 16 or as an operating lease in accordance with ASC 842.

## To impair a ROU asset

1. Navigate to the impaired lease and select **Books**.
2. Select **Impairment** on the top ribbon.
3. A window will appear, enter the amount of the asset impairment in the **Impairment amount** field. This value should be entered as a positive value to decrease the ROU asset.
4. In the **Transaction date** field, enter the date that the impairment entry will be posted on.
5. In the **Periods remaining** field, enter the number of months remaining to amortize.
6. Enable the **Post** field for the system to automatically post the impairment expense journal entry. If left disabled, the system will create the entry. You can post the entry from the **Asset lease journals** page. 
7. Set the **Preview before posting** field to **Yes** to view the proposed entry before creating or posting.
8. Set the **Close book** field to **Yes** to close the lease book. You can't undo this action. Entries can't be posted against closed leases, nor can a closed lease be adjusted.
9. Click **OK** to create or post the impairment entry.
10. To view the impaired asset depreciation schedule, navigate to the **Asset depreciation schedule** for that lease book. As noted, the asset will now be depreciated on a straight-line basis over the number of months entered in the **Periods remaining** field.
11. To view the impairment expense journal entry, select **Asset leasing journal** on the top ribbon for the impaired lease book. The system will create a journal entry that debits the impairment expense posting account, and that credits the lease asset posting account.
12. To view the new carrying value of the ROU asset, go to the **Asset transactions** page on the top ribbon of the lease book.

### ROU asset impairment example

   The following example assumes that the lease is not a specialized asset that doesn't transfer ownership or grant the lessee the option to purchase.

### General Tab inputs

   |     Field                         	|     Value               	|
   |--------------------------------------|-------------------------	|
   |     Fair value of the asset       	|     600,000             	|
   |     Incremental borrowing rate    	|     7%                  	|
   |     Compounding interval          	|     Annually            	|
   |     Asset useful life (months)    	|     600                 	|
   |     Annuity type                  	|     Ordinary annuity    	|
   |     Commencement date             	|     01/01/2019          	|


### Payment schedule lines tab inputs

   |     Field                	|     Value         	|
   |--------------------------	|-------------------	|
   |     Start date           	|     1/1/2019      	|
   |     Period interval      	|     Monthly       	|
   |     Periods              	|     120           	|
   |     End date             	|     12/31/2028    	|
   |     Payment frequency    	|     Annually      	|
   |     Payment amount       	|     10,000        	|


1. After creating this lease, go to the lease book and confirm the payment schedule. Then, post the initial recognition journal entry. The initial ROU asset and lease liability should be $70,235.81. Assume this lease was classified as an operating lease under ASC 842.
2. Run the batch journal process to simulate the passing of 3 years for the lease payments, interest expense, and depreciation expense.
3. After running all three batch jobs, go back to the lease book and open the liability and asset transactions tables to see the current carrying value of the ROU asset and lease liability. After three years, the value of the liability and the asset are approximately $-53,893.00 and $53,893.00 respectively.  
   
4. After 3 years, impairment tests are performed by the business, and it is determined that the ROU asset has an impairment of $35,000. To record this impairment, navigate to the lease book, and click **Impairment** in the top ribbon.
5. The **Impairment parameter** page will open. Enter the following details:

   |     Field                     	|     Value       	|
   |-------------------------------	|-----------------	|
   |     Impairment amount         	|     35,000      	|
   |     Transaction date          	|     1/1/2022    	|
   |     Periods remaining         	|     84          	|
   |     Post                      	|     Yes         	|
   |     Preview before posting    	|     No          	|
   |     Close book                	|     No          	|

1. An impairment expense journal entry will have been created and posted. To view the journal entry, go to the asset's leasing journal in the lease book. The amount of the impairment was debited to the Impairment expense posting account and the ROU asset posting account was credited.
2. To view the net effect of the impairment, go to the liability and asset transactions tables. The impairment expense has decreased the ROU asset, but the carrying amount of the lease liability remains the same.

There is one final effect of the impairment to consider. Because the ROU asset amount now is much less than the lease liability, the amount must be depreciated differently than before. Specifically, the asset is now depreciated in a straight-line manner throughout the remaining 84 months of the lease beginning on the transaction date.
