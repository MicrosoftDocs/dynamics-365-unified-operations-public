---
# required metadata

title: Dual reporting
description:   
author: moaamer
manager: Ann Beebe
ms.date: 08/10/2020
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
ms.search.validFrom: 2020-08-10
ms.dyn365.ops.version: 10.0.14
---

# Dual reporting

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic walks through an example of the dual reporting capabilities in Asset leasing for both IFRS and statutory reporting. For purposes of this example, familiarity with posting layers in Dynamics is required.

## Fact Pattern

The following example accounts for a lease under Italian statutory reporting under a cash-basis method and IRF reporting methods. The company must establish three books to account for both the Italian statutory requirements and the IRS 16 requirements. The books that are needed include one for IFRS 16, a book for statutory requirements, and a book to automatically reverse statutory postings. The books are set up as shown in the following tables. 

This first book is set up to comply with the IFRS 16 accounting standard. All entries posted in this book will post to a custom layer.

|     Name                                       	|     Description     	|
|------------------------------------------------	|---------------------	|
|     Book type                                  	|     IFRS 16         	|
|     Book description                           	|     IFRS 16         	|
|     Posting Layer                              	|     Custom layer    	|
|     Lease Type                                 	|     Finance         	|
|     Automatic                                  	|     No              	|
|     Accounting Framework                       	|     IFRS 16         	|
|     Lease Term / Useful life Set Up            	|     0.00            	|
|     Present Value / Asset Fair Value Set Up    	|     0.00            	|
|     Short term threshold                       	|     12              	|
|     Low Value Threshold                        	|     5,000.00        	|
|     Pay to Vendor                              	|     No              	|

The statutory book is a cash-basis book where the company will account for the lease expense as the amount of cash paid each month for rent. This book will not produce a right-of-use asset or lease liability.

|     Name                                       	|     Description    	|
|------------------------------------------------	|--------------------	|
|     Book type                                  	|     Statutory      	|
|     Book description                           	|     Local GAAP     	|
|     Posting Layer                              	|     Current        	|
|     Lease Type                                 	|     None           	|
|     Automatic                                  	|     Yes            	|
|     Accounting Framework                       	|     Cash basis     	|
|     Lease Term / Useful life Set Up            	|     0.00           	|
|     Present Value / Asset Fair Value Set Up    	|     0.00           	|
|     Short term threshold                       	|     0              	|
|     Low Value Threshold                        	|     0              	|
|     Pay to Vendor                              	|     No             	|

The statutory reversal book will be setup identically to the statutory book.

|     Name                                       	|     Description                       	|
|------------------------------------------------	|---------------------------------------	|
|     Book type                                  	|     Statutory - Reversal              	|
|     Book description                           	|     Book to reverse statutory book    	|
|     Posting Layer                              	|     Custom layer                      	|
|     Lease Type                                 	|     None                              	|
|     Automatic                                  	|     Yes                               	|
|     Accounting Framework                       	|     Cash basis                        	|
|     Lease Term / Useful life Set Up            	|     0.00                              	|
|     Present Value / Asset Fair Value Set Up    	|     0.00                              	|
|     Short term threshold                       	|     0                                 	|
|     Low Value Threshold                        	|     0                                 	|
|     Pay to Vendor                              	|     No                                	|

Assume a lease with the following entries in the **General** tab.

|     Field                         	|     Value               	|
|-----------------------------------	|-------------------------	|
|     Incremental borrowing rate    	|     5%                  	|
|     Commencement date             	|     1/1/2020            	|
|     Lease group                   	|     Buildings           	|
|     Vendor                        	|     1001                	|
|     Fair value of the asset       	|     245,000             	|
|     Asset useful life             	|     120                 	|
|     Annuity type                  	|     Ordinary annuity    	|
|     Compounding interval          	|     Monthly             	|

Payment schedule lines inputs:

|     Field                	|     Value         	|
|--------------------------	|-------------------	|
|     Start date           	|     1/1/2020      	|
|     Period interval      	|     Months        	|
|     Periods              	|     24            	|
|     End date             	|     12/31/2020    	|
|     Payment frequency    	|     Monthly       	|
|     Payment amount       	|     1,000         	|

In order to account for this lease under 2 different frameworks, we will use a current posting layer and a custom posting layer. The figure below is an example of each journal entry required to fairly represent the financials under each reporting standard. We will be walking through each journal entry in detail for the 1st month of the lease.

*There seems to be a table here, but I'm not sure what the columns and rows are intended to be.*

You will see that there are 3 books required in order to report under both statutory reporting and IFRS. The statutory book will record the lease payment under cash basis under the current layer, the reversal book will reverse the statutory journal entries, and the IFRS 16 book will book journal entries required under IFRS 16. The user will only need to enter a lease once and navigate to books, in order to see all the books associated to a lease. When entering the books, you will note all three books are associated to one lease record.

The first journal entry will record the lease expense under the statutory book. The user will be able to either create these payments in batch, or by selecting the payment schedule in the statutory book.

Assume the following journal entry is produced for the Statutory book from the Payment schedule:

### Lease payment -- 1/31/2020 -- JE 100

|     Account type    	|     Account No    	|     Layer      	|     Account Description    	|     Debit    	|     Credit    	|
|---------------------	|-------------------	|----------------	|----------------------------	|--------------	|---------------	|
|     Ledger          	|     1             	|     Current    	|     Lease expense          	|     1,000    	|               	|
|     Ledger          	|     4             	|     Current    	|     Clearing account       	|              	|     1,000     	|

Then following standard Dynamics functionality, an AP clerk, outside of the Asset leasing module, will create an invoice to pay for the lease, but instead of selecting "lease expense" as the debit account, they will select clearing account and generate the following entry.

### AP Process - 1/31/2020 - JE 110

|     Account type    	|     Account No    	|     Layer      	|     Account Description    	|     Debit       	|     Credit      	|
|---------------------	|-------------------	|----------------	|----------------------------	|-----------------	|-----------------	|
|     Ledger          	|     4             	|     Current    	|     Clearing account       	|     1,000.00    	|                 	|
|     Ledger          	|     2             	|     Current    	|     Bank fee               	|     3.00        	|                 	|
|     Ledger          	|     3             	|     Current    	|     VAT expense            	|     5.00        	|                 	|
|     Vendor          	|     5             	|     Current    	|     Accounts payable       	|                 	|     1,008.00    	|

Once the payable is issued to the vendor, the user will follow its normal payment process using standard Dynamics functionality. The following journal entry will be generated during the payment process.

### Cash payment - 1/31/2020 -- JE 120

|     Account type    	|     Account No    	|     Layer      	|     Account Description    	|     Debit       	|          	|     Credit      	|
|---------------------	|-------------------	|----------------	|----------------------------	|-----------------	|----------	|-----------------	|
|     Vendor          	|     5             	|     Current    	|     Accounts Payable       	|     1,008.00    	|          	|                 	|
|     Bank            	|     9             	|     Current    	|     Cash                   	|                 	|          	|     1,008.00    	|

At this point the user has fully accounted for this lease under statutory reporting requirements and will be able to extract its trial balance using the current layer. Dynamics will return a trial balance with the following figures:

*There seems to be a table here, but I'm not sure what the columns and rows are intended to be.*

In order to then be able to run the same trial balance but with the IFRS 16 figures, we first need to reverse the statutory accounting journal entries, and then book the IFRS 16 journal entries. In order to reverse the statutory journal entries, we have created a "reversal" book that has exactly the same setup as the "statutory" book but has an opposite posting profile. For example, the statutory book would have debited a lease expense account, but the "reversal" book will be crediting this account. These relationships are easily defined in the Asset lease posting accounts (Asset leasing > Setup > Asset leasing parameters).

The following journal entry will be made by the reversal book following the same process as the statutory book, with the major difference that the reversal book will be booking the reversing entries from the statutory book. The reversal entry will also be made to the "Custom" layer, thus when running a trial balance at the "Current" layer the reversal journal entries will not be included.

### Lease Payment - 1/31/2020 - JE 130

|     Account type    	|     Account No    	|     Layer     	|     Account Description    	|     Debit       	|     Credit      	|
|---------------------	|-------------------	|---------------	|----------------------------	|-----------------	|-----------------	|
|     Ledger          	|     4             	|     Custom    	|     Clearing account       	|     1,000.00    	|                 	|
|     Ledger          	|     1             	|     Custom    	|     Lease expense          	|                 	|     1,000.00    	|

Now that we have eliminated the statutory journal entries. We will book all the journal entries required by IFRS 16 in the IFRS 16 book. These includes the initial recognition of the ROU Asset and the Liability and the recording of interest and depreciation.

### Initial recognition -- 1/1/2020 - JE 140



The lease payment will be posted as the other lease payments. The purpose of use this clearing account is for cash to only be credited once.

### Lease payment -- 1/31/2020 - JE 150

|     Account type    	|     Account No    	|     Layer     	|     Account Description         	|     Debit       	|     Credit      	|
|---------------------	|-------------------	|---------------	|---------------------------------	|-----------------	|-----------------	|
|     Ledger          	|     7             	|     Custom    	|     Finance lease obligation    	|     1,000.00    	|                 	|
|     Ledger          	|     4             	|     Custom    	|     Clearing account            	|                 	|     1,000.00    	|

The interest expense journal entry will be generated from the liability amortization schedule.

### Interest expense -- 1/31/2020 - JE 160

|     Account type    	|     Account No    	|     Layer     	|     Account Description         	|     Debit    	|     Credit    	|
|---------------------	|-------------------	|---------------	|---------------------------------	|--------------	|---------------	|
|     Ledger          	|     8             	|     Custom    	|     Interest expense            	|     94.97    	|               	|
|     Ledger          	|     7             	|     Custom    	|     Finance lease obligation    	|              	|     94.97     	|

The depreciation expense journal entry will be generated from the Asset depreciation schedule.

### Depreciation expense -- 1/31/2020 - JE 170

|     Account type    	|     Account No    	|     Layer     	|     Account Description         	|     Debit     	|     Credit    	|
|---------------------	|-------------------	|---------------	|---------------------------------	|---------------	|---------------	|
|     Ledger          	|     10            	|     Custom    	|     Depreciation expense        	|     949.75    	|               	|
|     Ledger          	|     11            	|     Custom    	|     Accumulated depreciation    	|               	|     949.75    	|

After all these journal entries, the see the "custom layer" values below. You will note the last column includes the bank fee, VAT expense and the reduction to cash from the previous layer, but does not include the statutory reporting journal entries, thus achieving true dual reporting capabilities. From here, all that the company would need to do is run their trial balance and combined both the current layer and the custom layer in order to create an IFRS trial balance.


