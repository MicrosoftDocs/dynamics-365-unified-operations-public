---
# required metadata

title: Set up lease posting accounts
description: This topic lists the posting accounts that will be needed for Asset leasing transactions, and walks through the steps for defining posting accounts on the Lease posting parameters page.  
author: moaamer
manager: Ann Beebe
ms.date: 07/22/2020
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
ms.search.validFrom: 2020-07-22
ms.dyn365.ops.version: 10.0.14

---

# Set up lease posting accounts (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists the posting accounts that will be needed for Asset leasing transactions, and walks through the steps for defining posting accounts on the **Lease posting parameters** page. 

You might need to create new accounts in your chart of accounts to comply with ASC 842 and IFRS 16 standards. However, any accounts you create to comply with ASC and IFRS standards are not Fixed asset accounts. Under ASC 842, the right-of-use (ROU) asset is recorded for both finance and operating leases, which are separate from Fixed assets. (You can still maintain an ROU asset using Fixed assets.) For information about creating account structures, see [Create account structures](../general-ledger/tasks/create-account-structures.md). For information about creating a main account, see [Create a main account](../general-ledger/tasks/create-main-account.md). 

The following table shows examples of accounts that you'll need to create for leased asset transactions, if they haven't been created previously. The operating lease relationships are still used under IFRS 16 for low-value and short-term leases.


|     Ledger account number    	|     Account type     	|     Account name                                             	|
|------------------------------	|----------------------	|--------------------------------------------------------------	|
|     180150                   	|     Asset            	|     Vehicle ROU asset                                        	|
|     180160                   	|     Asset            	|     Building ROU asset                                       	|
|     180250                   	|     Asset            	|     Accumulated depreciation - vehicles                      	|
|     180260                   	|     Asset            	|     Accumulated depreciation - buildings                     	|
|     222300                   	|     Liability        	|     Short-term obligation - finance leases                   	|
|     222310                   	|     Balance sheet    	|     Short-term obligation - Operating leases                 	|
|     250200                   	|     Liability        	|     Notes payable                                            	|
|     250601                   	|     Balance sheet    	|     Long-term obligation - finance leases                    	|
|     250602                   	|     Balance sheet    	|     Long-term obligation - operating leases                  	|
|     250606                   	|     Balance sheet    	|     Deferred rent                                            	|
|     300160                   	|     Balance sheet    	|     Retained earnings                                        	|
|     604500                   	|     Expense          	|     Lease Expense                                            	|
|     604501                   	|     Expense          	|     Vehicle operating lease expense - interest accretion     	|
|     604502                   	|     Expense          	|     Vehicle operating lease expense - amortization           	|
|     605200                   	|     Expense          	|     Building operating lease expense - interest accretion    	|
|     605201                   	|     Expense          	|     Building operating lease expense - amortization          	|
|     607101                   	|     Expense          	|     Vehicle lease amortization expense                       	|
|     607102                   	|     Expense          	|     Building lease amortization expense                      	|
|     607103                   	|     Expense          	|     Impairment expense - finance leases                      	|
|     607104                   	|     Expense          	|     Impairment expense - Operating leases                    	|
|     618910                   	|     Expense          	|     Lease expense - finance leases                           	|
|     618920                   	|     Expense          	|     Variable payments - finance leases                       	|
|     618930                   	|     Expense          	|     Variable payments - operating leases                     	|
|     800600                   	|     Expense          	|     Vehicle lease interest expense                           	|
|     800601                   	|     Expense          	|     Building lease interest expense                          	|
|     801201                   	|     Balance sheet    	|     Gain & loss - lease modification                         	|


## Configure posting accounts

Complete the following steps below to configure parameters for Asset leasing.

1. To assign accounts to the lease books and groups that have been created, open the **Lease posting parameters** page (**Asset leasing > Setup > Lease posting parameters**).

2. Click **Accounts** in the side bar. Open the **Lease accounts** drop-down. Click the **Lease asset** from the **Posting types** for the lease drop-down. The preceding table shows the accounts that are related to operating and finance leases.

> [!Note]
> This requires that you set up separate accounts for both Operating and Finance leases. After the "Lease asset" selection is complete, continue to enter information in for the **Lease liability** and other required posting types. Companies that adhere to the IFRS 16 accounting framework won't need to set up the operating account relationships, as all leases under IFRS 16 are classified as Finance leases.

3. To select the main account for a specific lease group, click the drop-down menu under **Account Code** and select **Group**, then select the drop-down of the **Account/Group number** field, and then select the lease group to assign to the main account.

4. Open the **Executory costs** tab to assign account codes to the administrative costs that have been set up in the system. Select an expense from the **Expense type** dropdown and assign the finance and operating accounts to use for each book.

> [!Note]
> The finance or operating account chosen will be debited when the invoice for the scheduled expense is posted.


