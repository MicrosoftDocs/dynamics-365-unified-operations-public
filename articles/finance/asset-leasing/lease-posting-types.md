---
# required metadata

title: Lease posting types
description: This topic describes posting types used for asset leasing transactions.
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

# Lease Posting Types

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes posting types used for asset leasing transactions. 

|     Type               	|     Description                   	|     Example journal entries                  	|
|------------------------	|------------------------------------	|---------------------------------------------- |
|     Lease asset        	|     The account associated with the right-of-use asset. This   account will be debited when initially recognizing a lease under the new   standards IFRS 16 and ASC 842. This account may either be debited or credited   for a modified lease, depending on whether the modification increases or   decreases the lease liability.    	|     **Initial recognition** <br> <br> Dr. Lease asset XXX <br> <br>  Cr. Lease liability XXX                                                                                                                                                                         	|
|     Lease liability    	|     The account associated with the lease liability arising   from the discounting of payments under the new standards IFRS 16 and ASC 842.   This account will be credited upon initial recognition under the new   standards. This account will be debited for lease payments and credited for   interest accruals.                  	|     **Initial recognition**  <br> <br>   Dr. Lease asset XXX  <br> <br>  Cr. Lease liability XXX  <br> <br>  **Interest accrual**  <br> <br>  Dr. Interest expense XXX  <br> <br>  Cr. Lease liability XXX  <br> <br> **Lease payment**  <br> <br>  Dr. Lease liability XXX  <br> <br>  Cr. Vendor payable/lease payment XXX    	|
|     Etc.               	|     Etc.                                     	|     Etc.                             	|

*Complete original content follows.*

## Lease asset
The account associated with the right-of-use asset. This account will be debited when initially recognizing a lease under the new standards IFRS 16 and ASC 842. This account may either be debited or credited for a modified lease, depending on whether the modification increases or decreases the lease liability.

**Example journal entries**
**Entry**: Initial recognition **Debit**: Lease asset XXX **Credit**: Lease liability XXX

|     Transaction   type       	|     Debit          	|     Credit               	|
|------------------------------	|--------------------	|--------------------------	|
|     Initial   recognition    	|     Lease asset    	|     Lease   liability    	|

## Lease liability
The account associated with the lease liability arising from the discounting of payments under the new standards IFRS 16 and ASC 842. This account will be credited upon initial recognition under the new standards. This account will be debited for lease payments and credited for interest accruals.

#### Example journal entries
Initial recognition **Debit**: Lease asset XXX **Credit**: Lease liability XXX

Interest Accrual **Debit**: Interest expense XXX **Credit**: Lease liability XXX

Lease payment **Debit**: Lease liability XXX **Credit**: Vendor payable/lease payment XXX

|     Transaction   type       	|     Debit                  	|     Credit                            	|
|------------------------------	|----------------------------	|---------------------------------------	|
|     Initial   recognition    	|     Lease asset            	|     Lease   liability                 	|
|     Interest accrual         	|     Interest   expense     	|     Lease liability                   	|
|     Lease payment            	|     Lease   liability      	|     Vendor   payable/lease payment    	|

## Short-term lease liability
The account associated with the short-term lease liability when the short-term lease liability reclass journal entry is posted. This account will be credited for the short-term liability from the amortization schedule on the last day of the month while the same amount will be debited on the first day of the next month.
Example journal entries:

Short-term lease liability reclass
Dr. Lease liability XXX
Cr. Short-term lease liability XXX
Dr. Short-term lease liability XXX
Cr. Lease liability XXX

## Depreciation Expense
The account associated with the expense related to the depreciation of the right-of-use asset under IFRS 16, ASC 842, and finance leases under IAS 17 and ASC 840. This account will be debited when a right-of-use asset is depreciated each month.

Example journal entries:
Depreciation Accrual
Dr. Depreciation expense XXX
Cr. Accumulated Depreciation XXX

## Gain/loss on lease modification
The account associated with any gains or losses that arise from lease modifications. A gain may arise during a lease modification if the modification decreases the lease liability by an amount greater than the carrying value of the right-of-use asset.

For example, assume a lease with a current carrying value of the lease liability of $150,000 and carrying value of the right of use asset of $100,000. There is a modification of the lease resulting in a new present value of future minimum lease payments of $40,000. The lease liability would be debited by $110,000 ($150,000 - $40,000). Since the right of use asset is only $100,000, the decrease of $110,000 would decrease the asset past 0, therefore the accounting guidance states the remainder should be booked to a gain account. The final journal entry would be a debit to the lease liability for $110,000, a credit to the lease asset of $100,000, and a credit to the gain account of $10,000.

Example journal entry:
Lease modification
Dr. Lease liability XXX
Cr. Lease Asset XXX
Cr. Gain XXX

## Accumulated depreciation
The account associated with the contra-asset account of the right-of-use asset. This account will be credited when depreciation expense is posted.

Example journal entries:
Depreciation Accrual
Dr. Depreciation expense XXX
Cr. Accumulated depreciation XXX

## Retained earnings
The account associated with retained earnings. This account may be either debited or credited on a transition adjustment journal entry using the Full Retrospective Approach or the Cumulative Catchup Option A approach. The difference between the initial right-of-use asset and lease liability will be booked to retained earnings. In rare cases, the retained earnings may also be impacted during lease modifications when a lease changes classification from finance to operating in order to write up or down the right-of-use asset to equal the lease liability.

Example journal entries:
Transition Adjustment (Full retrospective or cumulative catchup A):
Dr. Lease liability XXX
Cr. Lease asset XXX
Cr. Retained earnings XXX

## Variable payment
The account associated with variable lease payments resulting from an index revaluation under ASC 842, ASC 840, and IAS 17 leases. Variable payments are included in the lease payment schedule under the column "Variable payment". This account will be debited when an invoice is created against a payment schedule line containing a variable payment.

Example journal entries:
Lease payment:
Dr. Lease liability XXX
Dr. Variable payment XXX
Cr. Vendor payable/lease payment XXX

## Deferred rent asset (liability)
The account associated with the deferred rent asset or liability resulting from a deferred rent treatment lease. This account will be debited when an invoice is posted against a deferred rent treatment lease if the lease payment amount is greater than that period's straight-line rent expense. This account will be credited if the lease payment is less than that period's straight-line rent expense.

Example journal entry:
Lease payment (deferred rent treatment lease):
Dr. Lease expense XXX
Cr. Deferred rent liability XXX
Cr. Vendor payable/lease payment XXX

## Lease expense
The account associated with the lease expense if the lease is classified as a deferred rent treatment lease. This account will be debited when an invoice is posted against a deferred rent treatment lease.

Example Journal Entry:
Lease payment (deferred rent treatment lease):
Dr. Lease expense XXX
Cr. Deferred rent liability XXX
Cr. Vendor payable/lease payment XXX

## Impairment expense
The account to be posted against when a lease is impaired. This account will be debited while the right-of-use asset account will be directly credited.

Example journal entry:
Lease payment:
Dr. Impairment expense XXX
Cr. ROU asset XXX

## Lease payment
The account to be posted against if the 'Pay to Vendor' parameter is disabled. This account will be credited in place of the vendor payable if the parameter is disabled.

Example journal entry:
Lease payment:
Dr. Lease liability XXX
Cr. Lease payment XXX

## Expense type postings
The account selected for each expense type will be debited when a payment for that selected expense type is generated. For example, the account specified for expense type "Insurance" will be debited whenever an invoice/payment journal entry is created from the executory costs schedule for insurance expense.

Example journal entry:
Insurance payment:
Dr. Insurance expense type account XXX
Cr. Offset account* XXX

*The offset account is chosen on the lease level on the Executory Costs payment Schedule Lines. This can be directly to the vendor, to a bank account, or to a ledger account.
