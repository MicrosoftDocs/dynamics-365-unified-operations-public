---
# required metadata

title: Set up lease posting accounts
description: This topic walks through steps for setting up posting accounts that will be used for asset leases.  
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

This topic walks through steps for setting up posting accounts that will be used for asset leases. 

Follow the steps below to set up the lease parameters used in the asset leasing module. The user may have to create new accounts in the chart of accounts to comply with ASC 842 standards and IFRS 16 standards.
To learn how to create a general ledger account, please refer to the Microsoft Dynamics training manual. Note, these are not fixed asset accounts, under ASC 842 the right-of-use (ROU) asset is recorded for both Finance and Operating leases separately from Fixed Assets. However, the user can manage the ROU asset using the fixed asset module, which we will discuss later.
Below is an example of necessary accounts that may need to be created if they do not already exist. The operating lease relationships are still used under IFRS 16 for low-value and short-term leases.

*Table placeholder*

|     Ledger account number    	|     Account type     	|     Account name                                             	|
|------------------------------	|----------------------	|--------------------------------------------------------------	|
|     180150                   	|     Asset            	|     Vehicle ROU asset                                        	|
|     180160                   	|     Asset            	|     Building ROU asset                                       	|
|     180250                   	|     Asset            	|     Accumulated Depreciation - Vehicles                      	|
|     180260                   	|     Asset            	|     Accumulated Depreciation - Buildings                     	|
|     222300                   	|     Liability        	|     Short Term Obligation - Finance Leases                   	|
|     222310                   	|     Balance Sheet    	|     Short Term Obligation - Operating Leases                 	|
|     250200                   	|     Liability        	|     Notes Payable                                            	|
|     250601                   	|     Balance Sheet    	|     Long Term Obligation - Finance Leases                    	|
|     250602                   	|     Balance Sheet    	|     Long Term Obligation - Operating Leases                  	|
|     250606                   	|     Balance Sheet    	|     Deferred Rent                                            	|
|     300160                   	|     Balance Sheet    	|     Retained Earnings                                        	|
|     604500                   	|     Expense          	|     Lease Expense                                            	|
|     604501                   	|     Expense          	|     Vehicle Operating Lease Expense - Interest accretion     	|
|     604502                   	|     Expense          	|     Vehicle Operating Lease Expense - Amortization           	|
|     605200                   	|     Expense          	|     Building Operating Lease Expense - Interest accretion    	|
|     605201                   	|     Expense          	|     Building Operating Lease Expense - Amortization          	|
|     607101                   	|     Expense          	|     Vehicle Lease Amortization Expense                       	|
|     607102                   	|     Expense          	|     Building Lease Amortization Expense                      	|
|     607103                   	|     Expense          	|     Impairment Expense - Finance Leases                      	|
|     607104                   	|     Expense          	|     Impairment Expense - Operating Leases                    	|
|     618910                   	|     Expense          	|     Lease Expense - Finance Leases                           	|
|     618920                   	|     Expense          	|     Variable Payments - Finance Leases                       	|
|     618930                   	|     Expense          	|     Variable Payments - Operating Leases                     	|
|     800600                   	|     Expense          	|     Vehicle Lease Interest Expense                           	|
|     800601                   	|     Expense          	|     Building Lease Interest Expense                          	|
|     801201                   	|     Balance Sheet    	|     Gain & Loss - Lease Modification                         	|

1. To assign accounts to the lease books and groups that have been created, open the Lease posting parameters page (**Asset leasing > Setup > Lease posting parameters**).

2. Click **Accounts** in the side bar. Open the **Lease accounts** drop-down. Click the **Lease asset** from the **Posting types** for the lease drop-down. The preceding table shows the accounts related to operating and finance leases.

>[!Note]
> This requires for both Operating and Finance leases to have their own separate accounts. After the "Lease Asset" selection is complete, move to lease liability and the other necessary posting types.

Companies with the IFRS 16 accounting framework will not need to set up the operating account relationships as all leases under IFRS 16 are classified as Finance leases.

3. To select the main account for a specific lease group, click the drop-down menu under Account Code and select "Group". Next, select the drop-down of the Account/Group number and select the lease group to be assigned to the main accounts.
4. Open the Executory costs subtab to assign account codes to the various executory costs that have been set up in the system. Select an expense from the Expense type dropdown and assign the finance and operating accounts to be used for each book.

> [!Note]
> The finance or operating account chosen will be debited when the expense's scheduled invoice is posted.


