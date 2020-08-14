---
# required metadata

title: Record right-of-use asset depreciation
description: This topic lists the steps for creating that journal entry for the amortization, which is necessary for leases that recognized on an organization's balance sheet. 
author: moaamer
manager: Ann Beebe
ms.date: 07/28/2020
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
ms.search.validFrom: 2020-07-28
ms.dyn365.ops.version: 10.0.14

---

# Record right-of-use asset depreciation (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

For leases that are recognized on the organization's balance sheet, the right-of-use (ROU) asset is amortized on a monthly basis. This topic lists the steps for creating that journal entry for the amortization. The amortization will debit the expense ledger account and credit the accumulated depreciation ledger account according to your posting profile setup and lease type. These entries can be created for each lease, or for multiple leases using the batch journal functionality.

## Asset depreciation schedule
1. Open the **Lease summary** page and select a lease. Open the **Asset depreciation schedule** page (**Books > Asset depreciation schedule**).

The right-of-use asset depreciation expense journal entry is based on the amount in the **Depreciation Expense** column. Refer to the Calculation of ROU Asset Amortization Expense for Finance Leases section in this topic for an illustration of the accounting standard compliance guidance.

2. Select the period of depreciation and click **Create journal**. The user will receive a prompt that the journal to record depreciation was created.

3. Open the **Asset leasing journal** page to (**Journals > Asset leasing journals**) to view the depreciation expense journal entry that was created.

4. Select the journal entry and click **Post** to record the depreciation entry to General ledger.

## Calculation of ROU asset amortization expense for operating leases

The depreciation expense of an operating lease is calculated as the difference between the monthly straight-line lease expense and the monthly interest expense on the lease liability, in accordance with US GAAP ASC 842. The straight-line lease expense is calculated as the sum of all lease payments, including any prepayments, initial direct costs, dismantling costs, and lease incentives, divided by the lease term in month. The following table shows an example of the amortization expense for an operating lease. 

### Example of ROU asset amortization expense for operating leases

|     Field                                             	|     Value          	|
|-------------------------------------------------------	|--------------------	|
|     Payment amount                                    	|     1,000          	|
|     Payment frequency                                 	|     Monthly        	|
|     Lease term (months)                               	|     24             	|
|     Total lease payments                              	|     24,000         	|
|     Incremental borrowing rate                        	|     5%             	|
|     Annuity type                                      	|     Annuity due    	|
|     Compounding Interval                              	|     Monthly        	|
|     Present value of future minimum lease payments    	|     22,888.87      	|

The straight-line lease expense is calculated as the sum of all payments divided by the lease term. The system automatically calculates the monthly interest expense on the liability amortization schedule. The interest expense is calculated using the effective interest rate method. The system will subtract the interest expense for each month by the straight-line lease cost. The value is used to reduce the right-of-use asset.

|     Month    	|     Straight-line lease cost    	|     Interest expense                       	|     Calculation of right-of-use asset amortization expense    	|
|--------------	|---------------------------------	|--------------------------------------------	|---------------------------------------------------------------	|
|     1        	|     (24,000/24) = 1,000.00      	|     (22,888.87 – 1,000)*(5%/12) = 91.20    	|     (1,000 – 91.20) = 908.80                                  	|
|     2        	|     (24,000/24) = 1,000.00      	|     (21,980.08 – 1,000)*(5%/12) = 87.42    	|     (1,000 – 87.42) = 912.58                                  	|
|     3        	|     (24,000/24) = 1,000.00      	|     (21,067.49 – 1,000)*(5%/12) = 83.62    	|     (1,000 – 83.62) = 916.39                                  	|


> [!Note] 
> According to US GAAP ASC 842, the depreciation of the right-of-use asset for an operating lease is classified as lease expense in the income statement. For purposes of visibility, the Asset leasing module describes the entry as the depreciation of the right-of-use asset, but the debit should be assigned to an operating lease expense account, and the credit directly to the operating lease right-of-use asset. However, the company can specify in the lease parameters to credit to an accumulated depreciation account for operating right-of-use asset if desired.

## Calculation of ROU Asset Amortization Expense for Finance Leases

For leases with a finance classification, the application calculates the ROU asset amortization on a straight-line basis. Therefore, the depreciation expense will be the same for each month.

In accordance with IFRS 16 and ASC 842, the asset will be amortized over the lesser of the lease term or asset's useful life. Additionally, if the **Transfer of Ownership** parameter is enabled for the lease, the lease will automatically be depreciated over the asset's useful life.

### Example of finance lease amortization expense:

|     Field                                   	|     Value                                      	|
|---------------------------------------------	|------------------------------------------------	|
|     Beginning right-of-use asset balance    	|     22,889.87                                  	|
|     Lease term (months)                     	|     24                                         	|
|     Asset useful life (months)              	|     36                                         	|
|     Month                                   	|     Right-of-use asset amortization expense    	|
|     1                                       	|     (22,889.87/24) = 953.74                    	|
|     2                                       	|     (22,889.87/24) = 953.74                    	|
|     3                                       	|     (22,889.87/24) = 953.74                    	|
