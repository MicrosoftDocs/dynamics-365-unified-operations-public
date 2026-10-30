---
title: Changes to customer and vendor transaction settlement storage 
description: Learn how to decouple settlements and exchange adjustments from customer and vendor transactions.
author: mukumarm
ms.author: mukumarm
ms.topic: concept-article
ms.date: 10/28/2026
ms.custom:
  - bap-template
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
---

# Changes to customer and vendor transaction settlement storage

Starting in Microsoft Dynamics 365 Finance version 10.0.50, the system automatically turns on a change to customer and vendor transaction settlement. You don't need to configure, set up, or opt in to this change. There's no change to how settlement, payments, or foreign-currency revaluation works for your users.

This change is the first step of a multistep initiative. It puts the foundation in place. The performance and integration benefits arrive in a later phase. In this phase, you shouldn't expect a measurable speed-up. For more information, see [What to expect for performance](#what-to-expect-for-performance).

## Overview

Every posted customer and vendor transaction keeps a set of state values that change over the life of the transaction. For example, these values show how much of the transaction is settled, when it was last settled, the settlement voucher, and the realized and unrealized exchange-rate adjustments for foreign-currency transactions. Historically, the system stores these values directly on the customer transaction (`CustTrans`) and vendor transaction (`VendTrans`) records. The system updates these values in place each time a settlement or exchange adjustment occurs.

Starting in Finance version 10.0.50, this changing state is moved into dedicated companion storage for each transaction. This change is a foundational, structural change. Your business processes, pages, reports, and postings behave exactly as before.

### Why this change matters

Because customer and vendor transaction tables are among the most heavily used tables, updating them in place every time a transaction is settled or revalued has three side effects:

- Database contention - Frequent in-place updates on very active tables can cause locking and blocking during high-volume settlement and payment runs.
- Heavier change tracking for integrations - Any change to a transaction row, even a small settlement update, is picked up by change-based exports such as Bring your own database (BYOD) and Azure Synapse Link for Dataverse / export to data lake, which produces more downstream data movement than necessary.
- Posted transactions aren't truly stable - Because the row keeps changing, a posted transaction can't be treated as an immutable, archivable record.

Separating the changing state from the stable transaction makes it possible, in a later release, to reduce lock contention, make integration change feeds more efficient, and treat posted transactions as stable records.

### What to expect for performance

In Finance version 10.0.50, don't expect a performance improvement. To build the foundation safely, the system writes settlement and exchange-adjustment updates to both the existing location and the new companion storage in parallel. That extra write is a small amount of additional work, so if anything, you might see a marginal increase in processing cost for settlement, payment, and revaluation operations rather than a decrease.

This change is a deliberate, temporary trade-off:

- The parallel write approach lets Microsoft validate that the new companion storage is correct and complete across every customer environment before anything depends on it.
- The actual performance and integration benefits come in a later release, when the system starts reading from the new companion storage and the duplicate writes are no longer needed.

### What you see after upgrading to Finance version 10.0.50

- No functional or UI change - Settlement, payments, prepayments, withholding tax, transaction reversal, and foreign-currency revaluation all behave exactly the same. Balances, aging, vouchers, and reports are unchanged.
- No performance improvement yet, and possibly a small overhead - For more information, see [What to expect for performance](#what-to-expect-for-performance).
- New companion tables - Two new tables, `CustTransState` and `VendTransState`, are added. There's a one-to-one relationship between each posted transaction and its companion state record.
- Automatic backfill of existing data - For transactions that you posted before you upgraded, a background process automatically populates the companion state records after the update is applied. This process runs online, in the background, and requires no manual action. It's throttled to avoid impacting day-to-day operations and completes on its own.
- Automatic data-integrity self-healing - The system continuously keeps each companion state record consistent with its transaction. Whenever a transaction is created or updated, it verifies that the companion record matches and, if any difference is detected, corrects it automatically in the same operation. This correction happens inline, with no batch job to schedule and no action required from you.

### Impact on integrations and extensions

In Finance version 10.0.50, the existing settlement and exchange-adjustment fields on `CustTrans` and `VendTrans` are kept and continue to be maintained exactly as before. This release adds the new companion data; it doesn't remove or change any existing fields.

As a result:

- Existing integrations, reports, and OData/data-entity queries that read the settlement or exchange-adjustment fields on `CustTrans` and VendTrans` continue to work with no change.
- BYOD, Synapse Link, and export-to-data-lake pipelines that include customer or vendor transactions continue to function. Over time, moving reads to the new companion tables is expected to reduce the volume of change events these pipelines process.
- New tables in metadata - If you enumerate tables or entities programmatically, you see the two new tables, `CustTransState` and `VendTransState`. During the automatic backfill, these tables are progressively populated for historical transactions.

If you maintain independent software vendor (ISV) solutions or customizations that read settlement or exchange-adjustment state, no changes are required for Finance version 10.0.50. Review your solutions so you're ready for the next release.

### Issues

Feature flights control this behavior internally. The overall parallel-write behavior is gated by **`CustVendTransParallelWriteFlight`** (kill switch `CustVendTransParallelWriteFlight_KillSwitch`). A separate flight, `CustVendTransParallelWriteReconUpdateDriftFlight` (kill switch `CustVendTransParallelWriteReconUpdateDriftFlight_KillSwitch`), gates the automatic self-healing correction on the update path.

If you encounter a problem that you believe is related to this change, open a support request with Microsoft and reference the relevant flight names in this section. Microsoft can turn the behavior off in your environment by using the corresponding kill switch. Because this release keeps the original settlement and exchange-adjustment fields on `CustTrans` and `VendTrans` fully maintained, disabling a flight only affects the new companion tables. It doesn't affect settlement, payments, revaluation, or any posted balances.

### Future releases

Finance version 10.0.50 is the first release of future changes:

- Finance version 10.0.50 - The companion state tables are introduced and kept in sync automatically, in parallel with the existing fields. The original fields on `CustTrans` and `VendTrans` remain the source that applications read from. This phase is on by default and low-risk because nothing depends on the new tables. Because it writes to both places, it doesn't yet deliver a performance gain.
- In a future release - Applications, reports, and integrations begin reading settlement and exchange-adjustment state from the new companion tables. This change reduces contention and lightens integration change feeds and, later, the original fields on `CustTrans` and `VendTrans` are deprecated and eventually removed. This change also ends the parallel-write overhead. This phase is opt-in and communicated separately, with guidance and lead time for updating integrations that read those fields directly.

#### Frequently asked questions

- Do I need to do anything to turn this feature on?
No. The feature is enabled automatically when you upgrade to Finance version 10.0.50.

- Will settlement, payment, or revaluation behavior change for my users?
No. There's no functional or user-experience change in this release.

- Will this change make settlement or payments faster in Finance version 10.0.50?
No. This release is a foundational step, not a performance release. It writes to both the existing fields and the new companion tables in parallel and you might see a small amount of extra processing cost rather than a speed-up. The performance benefits come in a later phase, once the system reads from the new tables and the parallel writes are removed. See [What to expect for performance](#what-to-expect-for-performance).

- Will my existing integrations break?
No, all existing settlement and exchange-adjustment fields on the customer and vendor transaction tables remain and are maintained exactly as before.

- How long does the background backfill take?
It depends on the volume of historical customer and vendor transactions in your environment. It runs in the background with throttling and completes on its own without manual intervention.

- How does the system keep the companion records accurate?
The system automatically maintains consistency. Each time you create or update a transaction, the system verifies the companion state record and corrects any discrepancy inline, in the same operation. This self-healing process runs continuously in the background of normal processing.

- Can I start using the new `CustTransState` and `VendTransState` tables now?
Not yet, in Finance version 10.0.50, the system populates and validates these tables but they aren't the source that application read from.
