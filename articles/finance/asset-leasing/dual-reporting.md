---
# required metadata

title: Confirm payment schedules in batch
description:  This topic walks through an example of the dual reporting capabilities in Asset leasing for both IFRS and statutory reporting. 
author: moaamer
manager: Ann Beebe
ms.date: 08/07/2020
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
ms.search.validFrom: 2020-08-07
ms.dyn365.ops.version: 10.0.14
---

# Dual reporting

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic walks through an example of the dual reporting capabilities in Asset leasing for both IFRS and statutory reporting. For purposes of this example, familiarity with posting layers in Dynamics is required.

## Fact Pattern

The lease below will be account for under both Italian statutory reporting under a cash-basis method and IFRS reporting methods. The company must establish three books in order to account for both Italian statutory requirements and IFRS 16 requirements -- a book for IFRS 16, a book for statutory requirements, and a book to automatically reverse the statutory postings. The book setup details are explained as follows.

This first book is to comply with the IFRS 16 accounting standard. All entries posted in this book will post to a custom layer.

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

You will see that there are 3 books required in order to report under both statutory reporting and IFRS. The statutory book will record the lease payment under cash basis under the current layer, the reversal book will reverse the statutory journal entries, and the IFRS 16 book will book journal entries required under IFRS 16. The user will only need to enter a lease once and navigate to books, in order to see all the books associated to a lease. When entering the books, you will note all three books are associated to one lease record.

The first journal entry will record the lease expense under the statutory book. The user will be able to either create these payments in batch, or by selecting the payment schedule in the statutory book.

Assume the following journal entry is produced for the Statutory book from the Payment schedule:

### Lease payment -- 1/31/2020 -- JE 100

|     Account type    	|     Account No    	|     Layer      	|     Account Description    	|     Debit    	|     Credit    	|
|---------------------	|-------------------	|----------------	|----------------------------	|--------------	|---------------	|
|     Ledger          	|     1             	|     Current    	|     Lease expense          	|     1,000    	|               	|
|     Ledger          	|     4             	|     Current    	|     Clearing account       	|              	|     1,000     	|




