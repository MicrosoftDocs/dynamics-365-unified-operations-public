---
# required metadata

title: Dual reporting
description: This topic walks through an example of the capaibility in Asset leasing to fulfill both IFRS and statutory reporting requirements. 
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

This topic walks through an example of the capaibility in Asset leasing to fulfill both IFRS and statutory reporting requirements. Familiarity with posting layers in Dynamics 365 Finance is required will make the example easier to understand.

## Fact Pattern

The following example accounts for a lease under Italian statutory reporting using both cash-basis method and IFRS reporting methods. The company must establish three books to account for both the Italian statutory requirements and the IFRS 16 requirements. The books that are needed include one for IFRS 16, a book for statutory requirements, and a book to automatically reverse statutory postings. The books are set up as shown in the following tables. 

This first book is set up to comply with the IFRS 16 accounting standard. All entries posted in this book will post to a custom layer.

|     Name                                       	|     Description     	|
|------------------------------------------------	|---------------------	|
|     Book type                                  	|     IFRS 16         	|
|     Book description                           	|     IFRS 16         	|
|     Posting Layer                              	|     Custom layer 1   	|
|     Lease Type                                 	|     Finance         	|
|     Accounting Framework                       	|     IFRS 16         	|
|     Lease Term / Useful life Set Up            	|     0.00            	|
|     Present Value / Asset Fair Value Set Up    	|     0.00            	|
|     Short-term threshold                       	|     12              	|
|     Low Value Threshold                        	|     5,000.00        	|
|     Pay to Vendor                              	|     No              	|

The statutory book is a cash-basis book where the company will account for the lease expense as the amount of cash paid each month for rent. This book will not produce a right-of-use asset or lease liability.

|     Name                                       	|     Description    	|
|------------------------------------------------	|--------------------	|
|     Book type                                  	|     Statutory      	|
|     Book description                           	|     Local GAAP     	|
|     Posting Layer                              	|     Current        	|
|     Lease Type                                 	|     Automatic      	|
|     Accounting Framework                       	|     Cash basis     	|
|     Lease Term / Useful life Set Up            	|     0.00           	|
|     Present Value / Asset Fair Value Set Up    	|     0.00           	|
|     Short term threshold                       	|     0              	|
|     Low Value Threshold                        	|     0              	|
|     Pay to Vendor                              	|     No             	|

The statutory reversal book will be set up identically to the statutory book.

|     Name                                       	|     Description                       	|
|------------------------------------------------	|---------------------------------------	|
|     Book type                                  	|     Statutory - Reversal              	|
|     Book description                           	|     Book to reverse statutory book    	|
|     Posting Layer                              	|     Custom layer 1                     	|
|     Lease Type                                 	|     Automatic                          	|
|     Accounting Framework                       	|     Cash basis                        	|
|     Lease Term / Useful life Set Up            	|     0.00                              	|
|     Present Value / Asset Fair Value Set Up    	|     0.00                              	|
|     Short-term threshold                       	|     0                                 	|
|     Low Value Threshold                        	|     0                                 	|
|     Pay to Vendor                              	|     No                                	|

Assume that a lease with the following entries has been created and is visible in the **General** tab.

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

The entries for the Payment schedule lines are as follows.

|     Field                	|     Value         	|
|--------------------------	|-------------------	|
|     Start date           	|     1/1/2020      	|
|     Period interval      	|     Months        	|
|     Periods              	|     24            	|
|     End date             	|     12/31/2020    	|
|     Payment frequency    	|     Monthly       	|
|     Payment amount       	|     1,000         	|

In order to account for this lease under two frameworks, we will use a current posting layer and a custom posting layer 1. The figure below is an example of each journal entry required to fairly represent the financials under each reporting standard. We will be walking through each journal entry in detail for the 1st month of the lease.

*There seemed to be a table at this location in the Word document, but I'm not sure what the columns and rows are intended to be. Something didn't come across the right way.*
*Considering to reduce adjust headers since GitHub could not recognize multiple headers. Number of columns are too many, consider to reduce them as well.*



You will see that three books are required to report under both statutory reporting and IFRS. The statutory book will record the lease payment according to the rules for cash basis accounting under the current layer, the reversal book will reverse the statutory journal entries, and the IFRS 16 book will create the journal entries that are required under IFRS 16. You will need only to enter a lease once, and then navigate to the **Books** page to see all the books associated with a lease. When you create the books, note that all three books must be associated with the same lease record.

The first journal entry will record the lease expense under the statutory book. You'll be able to either create these payments in batch, or by selecting the payment schedule in the statutory book.

Assume the following journal entry is produced for the statutory book from the payment schedule.

### Lease payment -- 1/31/2020 -- JE 100

|     Account type    	|     Account No    	|     Layer      	|     Account Description    	|     Debit    	|     Credit    	|
|---------------------	|-------------------	|----------------	|----------------------------	|--------------	|---------------	|
|     Ledger          	|     1             	|     Current    	|     Lease expense          	|     1,000    	|               	|
|     Ledger          	|     4             	|     Current    	|     Clearing account       	|              	|     1,000     	|

Following standard Dynamics functionality, an accounts payable clerk, will create an invoice to pay for the lease outside of the Asset leasing module, but instead of selecting **Lease expense** as the debit account, they will select clearing account to generate the following entry.

### AP Process - 1/31/2020 - JE 110

|     Account type    	|     Account No    	|     Layer      	|     Account Description    	|     Debit       	|     Credit      	|
|---------------------	|-------------------	|----------------	|----------------------------	|-----------------	|-----------------	|
|     Ledger          	|     4             	|     Current    	|     Clearing account       	|     1,000.00    	|                 	|
|     Ledger          	|     2             	|     Current    	|     Bank fee               	|     3.00        	|                 	|
|     Ledger          	|     3             	|     Current    	|     VAT expense            	|     5.00        	|                 	|
|     Vendor          	|     5             	|     Current    	|     Accounts payable       	|                 	|     1,008.00    	|

When the statement is issued to the vendor, you'll follow the normal payment process. The following journal entry will be generated during the payment process.

### Cash payment - 1/31/2020 -- JE 120

|     Account type    	|     Account No    	|     Layer      	|     Account Description    	|     Debit       	|     Credit      	|
|---------------------	|-------------------	|----------------	|----------------------------	|-----------------	|-----------------	|
|     Vendor          	|     5             	|     Current    	|     Accounts Payable       	|     1,008.00    	|                 	|
|     Bank            	|     9             	|     Current    	|     Cash                   	|                 	|     1,008.00    	|

At this point, you will have fully accounted for this lease under statutory reporting requirements and will be able to generate a trial balance using the current layer. The system will return a trial balance with the following figures:

   *There seemed to be a table at this location in the Word document, but I'm not sure what the columns and rows are intended to be. Something didn't come across the right way.*
   
| Account No | Description              |  JE\-100    	 |   JE\-110      | JE\-120        | Current Layer \- Totals |
|------------|--------------------------|----------------|----------------|----------------|-------------------------|
| 1          | Lease expense            | 1,000\.00      |                |                | 1,000\.00               |
| 2          | Bank fee                 |                | 3\.00          |                | 3\.00                   |
| 3          | VAT expense              |                | 5\.00          |                | 5\.00                   |
| 4          | Clearing account         | \-1,000\.00    | 1,000\.00      |                | 0\.00                   |
| 5          | Accounts payable         |                | \-1,008\.00    | 1,008\.00      | 0\.00                   |
| 6          | ROU asset                |                |                |                | 0\.00                   |
| 7          | Finance lease obligation |                |                |                | 0\.00                   |
| 8          | Interest expense         |                |                |                | 0\.00                   |
| 9          | Cash                     |                |                | \-1,008\.00    | \-1,008\.00             |
| 10         | Depreciation expense     |                |                |                | 0\.00                   |
| 11         | Accumulated depreciation |                |                |                | 0\.00                   |

To run the same trial balance using the IFRS 16 figures, the statutory accounting journal entries must be reversed, and the IFRS 16 journal entries must be posted. To reverse the statutory journal entries, this example includes a "reversal" book with the same as the *statutory* book but has an opposite posting profile. For example, the statutory book will have debited a lease expense account, but the "reversal" book will be crediting this account. These relationships are easily defined in the Asset lease posting accounts (**Asset leasing > Setup > Asset leasing parameters**).

The following journal entry will be made from the reversal book following the same process that was used with the statutory book. The difference is that the reversal book will book the reversing entries from the statutory book. The reversing entry will also be made to the custom layer. When running a trial balance at the current layer, the reversing journal entries will not be included.

### Lease Payment - 1/31/2020 - JE 130

|     Account type    	|     Account No    	|     Layer     	|     Account Description    	|     Debit       	|     Credit      	|
|---------------------	|-------------------	|---------------	|----------------------------	|-----------------	|-----------------	|
|     Ledger          	|     4             	|     Custom    	|     Clearing account       	|     1,000.00    	|                 	|
|     Ledger          	|     1             	|     Custom    	|     Lease expense          	|                 	|     1,000.00    	|

Now that we have eliminated the statutory journal entries. We will book all the journal entries required by IFRS 16 in the IFRS 16 book. These entries include the initial recognition of the ROU Asset and the Liability and the recording of interest and depreciation.

### Initial recognition -- 1/1/2020 - JE 140

|     Account type    	|     Account No    	|     Layer     	|     Account Description         	|     Debit        	|     Credit       	|
|---------------------	|-------------------	|---------------	|---------------------------------	|------------------	|------------------	|
|     Ledger          	|     6             	|     Custom    	|     ROU Asset                   	|     22,793.90    	|                  	|
|     Ledger          	|     7             	|     Custom    	|     Finance lease obligation    	|                  	|     22,793.90    	|

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

After all these journal entries are created and posted, see the "custom layer 1" values below. You will note the last column includes the bank fee, VAT expense and the reduction of cash from the previous layer, but does not include the statutory reporting journal entries, thus achieving true dual reporting capabilities. From here, all that the company would need to do is run their trial balance and combined both the current layer and the custom layer in order to create an IFRS trial balance.


