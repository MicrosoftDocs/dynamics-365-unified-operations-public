---
title: Lease posting types
description: Learn about the posting types that are used for asset leasing transactions, including outlines on lease assets and lease liabilities.
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

# Lease posting types

[!include [banner](../includes/banner.md)]

This article describes the posting types that are used for asset leasing transactions.

## Lease asset

The account is associated with the right-of-use (ROU) asset. This account is debited when a lease is initially recognized under the new lease accounting standards, Accounting Standards Codification Topic 842 (ASC 842) and International Financial Reporting Standard 16 (IFRS 16). For a modified lease, this account might be either debited or credited, depending on whether the modification increases or decreases the lease liability.

**Example journal entries:** Initial recognition<br>
**Debit:** Lease asset XXX<br>
**Credit:** Lease liability XXX

## Lease liability

The account is associated with the lease liability that occurs when payments are discounted under the new IFRS 16 and ASC 842 standards. This account is credited when a lease is initially recognized under the new standards. It's debited for lease payments and credited for interest accruals.

**Example journal entries:** Initial recognition<br>
**Debit:** Lease asset XXX<br>
**Credit:** Lease liability XXX

**Example journal entries:** Interest accrual<br>
**Debit:** Interest expense XXX<br>
**Credit:** Lease liability XXX

**Example journal entries:** Lease payment<br>
**Debit:** Lease liability XXX<br>
**Credit:** Vendor payable/lease payment XXX

## Short-term lease liability

The account is associated with the short-term lease liability when the short-term lease liability reclass journal entry is posted. This account is credited for the short-term liability from the amortization schedule on the last day of the month. However, the same amount is debited on the first day of the next month.

**Example journal entries:** Short-term lease liability reclass<br>
**Debit:** Lease liability XXX<br>
**Credit:** Short-term lease liability XXX<br>
**Debit:** Short-term lease liability XXX<br>
**Credit:** Lease liability XXX

## Depreciation expense

The account is associated with the expense that is related to the depreciation of the ROU asset under IFRS 16, ASC 842, and finance leases under IAS 17 and ASC 840. This account is debited when an ROU asset is depreciated each month.

**Example journal entries:** Depreciation accrual<br>
**Debit:** Depreciation expense XXX<br>
**Credit:** Accumulated Depreciation XXX

## Gain/loss on lease modification

The account is associated with any gains or losses that arise from lease modifications. A gain might arise during a lease modification if the modification decreases the lease liability by an amount that exceeds the carrying value of the ROU asset.

For example, a lease has a current carrying value of the lease liability of $150,000 and a carrying value of the ROU asset of $100,000. The lease is modified, and this modification produces a new present value of the future minimum lease payments (PVFMLP) of $40,000. Therefore, the lease liability will be debited by $110,000 ($150,000 – $40,000). Because the ROU asset is only $100,000, the decrease of $110,000 will decrease the asset past 0 (zero). Therefore, the accounting guidance states that the remainder should be booked to a gain account. In this case, the final journal entry will be a debit to the lease liability for $110,000, a credit to the lease asset for $100,000, and a credit to the gain account for $10,000.

**Example journal entries:** Lease modification<br>
**Debit:** Lease liability XXX<br>
**Credit:** Lease Asset XXX<br>
**Credit:** Gain XXX

## Accumulated depreciation

The account is associated with the contra-asset account of the ROU asset. This account is credited when a depreciation expense is posted.

**Example journal entries:** Depreciation accrual<br>
**Debit:** Depreciation expense XXX<br>
**Credit:** Accumulated depreciation XXX

## Variable payment

The account is associated with variable lease payments that are produced by an index revaluation under ASC 842, ASC 840, and IAS 17 leases. In the lease payment schedule, variable payments are included in the **Variable payment** column. This account is debited when an invoice is created against a payment schedule line that contains a variable payment.

**Example journal entries:** Lease payment<br>
**Debit:** Lease liability XXX<br>
**Debit:** Variable payment XXX<br>
**Credit:** Vendor payable/lease payment XXX

## Deferred rent asset (liability)

The account is associated with the deferred rent asset or liability that is produced by a deferred rent treatment lease. This account is debited when an invoice is posted against a deferred rent treatment lease, if the lease payment amount is more than the period's straight-line rent expense. It's credited if the lease payment is less than the period's straight-line rent expense.

**Example journal entries:** Lease payment (deferred rent treatment lease)<br>
**Debit:** Lease expense XXX<br>
**Credit:** Deferred rent liability XXX<br>
**Credit:** Vendor payable/lease payment XXX

## Lease expense

The account is associated with the lease expense if the lease is classified as a deferred rent treatment lease. This account is debited when an invoice is posted against a deferred rent treatment lease.

**Example journal entries:** Lease payment (deferred rent treatment lease)<br>
**Debit:** Lease expense XXX<br>
**Credit:** Deferred rent liability XXX<br>
**Credit:** Vendor payable/lease payment XXX

## Impairment expense

The account is posted against when a lease is impaired. This account is debited, whereas the ROU asset account is directly credited.

**Example journal entries:** Lease payment<br>
**Debit:** Impairment expense XXX<br>
**Credit:** ROU asset XXX

## Lease payment

The account is posted against if the **Pay to Vendor** parameter is turned off. This account is credited instead of the vendor payable if the parameter is turned off.

**Example journal entries:** Lease payment<br>
**Debit:** Lease liability XXX<br>
**Credit:** Lease payment XXX

## Expense type postings

The account that is selected for each expense type is debited when a payment for that expense type is generated. For example, the account that is specified for the **Insurance** expense type is debited whenever an invoice or payment journal entry is created from the executory cost schedule for insurance expense.

**Example journal entries:** Insurance payment<br>
**Debit:** Insurance expense type account XXX<br>
**Credit:** Offset account XXX

> [!NOTE]
> The offset account is selected at the lease level on the lines for the executory cost payment schedule. This offset account can associated with the vendor, or with a ledger account.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
