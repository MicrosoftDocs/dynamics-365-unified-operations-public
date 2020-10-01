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

## Lease asset
The account associated with the right-of-use asset. This account will be debited when initially recognizing a lease under the new standards IFRS 16 and ASC 842. This account may either be debited or credited for a modified lease, depending on whether the modification increases or decreases the lease liability.

**Example journal entries**: Initial recognition <br> 
**Debit**: Lease asset XXX <br> 
**Credit**: Lease liability XXX <br>

## Lease liability
The account associated with the lease liability arising from the discounting of payments under the new standards IFRS 16 and ASC 842. This account will be credited upon initial recognition under the new standards. This account will be debited for lease payments and credited for interest accruals.

**Example journal entries** Initial recognition <br>
**Debit**: Lease asset XXX <br> 
**Credit**: Lease liability XXX <br>

**Example journal entries**: Interest Accrual <br> 
**Debit**: Interest expense XXX <br> 
**Credit**: Lease liability XXX <br>

**Example journal entries**: Lease payment <br> 
**Debit**: Lease liability XXX <br> 
**Credit**: Vendor payable/lease payment XXX <br>

## Short-term lease liability
The account associated with the short-term lease liability when the short-term lease liability reclass journal entry is posted. This account will be credited for the short-term liability from the amortization schedule on the last day of the month while the same amount will be debited on the first day of the next month.
Example journal entries:

**Example journal entries**: Short-term lease liability reclass <br>
**Debit** Lease liability XXX <br>
**Credit** Short-term lease liability XXX <br>
**Debit** Short-term lease liability XXX <br>
**Credit** Lease liability XXX <br>

## Depreciation Expense
The account associated with the expense related to the depreciation of the right-of-use asset under IFRS 16, ASC 842, and finance leases under IAS 17 and ASC 840. This account will be debited when a right-of-use asset is depreciated each month.

**Example journal entries**: Depreciation Accrual <br>
**Debit** Depreciation expense XXX <br>
**Credit** Accumulated Depreciation XXX <br>

## Gain/loss on lease modification
The account associated with any gains or losses that arise from lease modifications. A gain may arise during a lease modification if the modification decreases the lease liability by an amount greater than the carrying value of the right-of-use asset.

For example, assume a lease with a current carrying value of the lease liability of $150,000 and carrying value of the right of use asset of $100,000. There is a modification of the lease resulting in a new present value of future minimum lease payments of $40,000. The lease liability would be debited by $110,000 ($150,000 - $40,000). Since the right of use asset is only $100,000, the decrease of $110,000 would decrease the asset past 0, therefore the accounting guidance states the remainder should be booked to a gain account. The final journal entry would be a debit to the lease liability for $110,000, a credit to the lease asset of $100,000, and a credit to the gain account of $10,000.

**Example journal entries**: Lease modification <br>
**Debit** Lease liability XXX <br>
**Credit** Lease Asset XXX <br>
**Credit** Gain XXX <br>

## Accumulated depreciation
The account associated with the contra-asset account of the right-of-use asset. This account will be credited when depreciation expense is posted.

**Example journal entries**: Depreciation Accrual <br>
**Debit** Depreciation expense XXX <br>
**Credit** Accumulated depreciation XXX <br>

## Retained earnings
The account associated with retained earnings. This account may be either debited or credited on a transition adjustment journal entry using the Full Retrospective Approach or the Cumulative Catchup Option A approach. The difference between the initial right-of-use asset and lease liability will be booked to retained earnings. In rare cases, the retained earnings may also be impacted during lease modifications when a lease changes classification from finance to operating in order to write up or down the right-of-use asset to equal the lease liability.

**Example journal entries**: Transition Adjustment (Full retrospective or cumulative catchup A) <br>
**Debit** Lease liability XXX <br>
**Credit** Lease asset XXX <br>
**Credit** Retained earnings XXX <br>

## Variable payment
The account associated with variable lease payments resulting from an index revaluation under ASC 842, ASC 840, and IAS 17 leases. Variable payments are included in the lease payment schedule under the column "Variable payment". This account will be debited when an invoice is created against a payment schedule line containing a variable payment.

**Example journal entries**: Lease payment <br>
**Debit** Lease liability XXX <br>
**Debit** Variable payment XXX <br>
**Credit** Vendor payable/lease payment XXX <br>

## Deferred rent asset (liability)
The account associated with the deferred rent asset or liability resulting from a deferred rent treatment lease. This account will be debited when an invoice is posted against a deferred rent treatment lease if the lease payment amount is greater than that period's straight-line rent expense. This account will be credited if the lease payment is less than that period's straight-line rent expense.

**Example journal entries**: Lease payment (deferred rent treatment lease) <br>
**Debit** Lease expense XXX <br>
**Credit** Deferred rent liability XXX <br>
**Credit** Vendor payable/lease payment XXX <br>

## Lease expense
The account associated with the lease expense if the lease is classified as a deferred rent treatment lease. This account will be debited when an invoice is posted against a deferred rent treatment lease.

**Example journal entries**: Lease payment (deferred rent treatment lease) <br>
**Debit** Lease expense XXX <br>
**Credit** Deferred rent liability XXX <br>
**Credit** Vendor payable/lease payment XXX <br>

## Impairment expense
The account to be posted against when a lease is impaired. This account will be debited while the right-of-use asset account will be directly credited.

**Example journal entries**: Lease payment <br>
**Debit** Impairment expense XXX <br>
**Credit** ROU asset XXX <br>

## Lease payment
The account to be posted against if the 'Pay to Vendor' parameter is disabled. This account will be credited in place of the vendor payable if the parameter is disabled.

**Example journal entries**: Lease payment <br>
**Debit** Lease liability XXX <br>
**Credit** Lease payment XXX <br>

## Expense type postings
The account selected for each expense type will be debited when a payment for that selected expense type is generated. For example, the account specified for expense type "Insurance" will be debited whenever an invoice/payment journal entry is created from the executory costs schedule for insurance expense.

**Example journal entries**: Insurance payment <br>
**Debit** Insurance expense type account XXX <br>
**Credit** Offset account* XXX <br>

*The offset account is chosen on the lease level on the Executory Costs payment Schedule Lines. This can be directly to the vendor, to a bank account, or to a ledger account.
