---
title: Decouple settlement from payment journal posting
description: Learn how delayed settlement lets you post customer and vendor payment journals even when settlement can't complete.
author: mukumarm
ms.author: mukumarm
ms.topic: how-to
ms.date: 07/09/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2026-01-01
ms.search.form:
ms.dyn365.ops.version: 
---
# Decouple settlement from payment journal posting

[!INCLUDE [banner](../../includes/banner.md)]

When you use delayed settlement, you can post customer and vendor payment journals successfully even if the related settlement can't be completed. The payment posts immediately, and the settlement is queued and processed separately - either automatically in the background or manually from a dedicated page.

This article describes the **Decouple settlement from journal posting** feature. After you turn on the feature in **Feature management**, you can enable it on the specific customer payment and vendor payment journals where you want the behavior.

## Prerequisites

- Microsoft Dynamics 365 Finance version 10.0.49.
- The **Decouple settlement from journal posting** feature turned on in Feature management.
- The behavior applies to **Customer payment** and **Vendor payment** journals only.

## Turn on the feature

1. Go to **Workspaces > Feature management**.
1. On the **All** tab, find **Decouple settlement from journal posting**.
1. Select the feature, and then select **Enable now**.

> [!IMPORTANT]
> If you later turn the feature off, any settlements that are already in the queue continue to be processed. Turning off the feature stops new settlements from being queued.

## Business value

In the standard payment journal workflow, payment posting and settlement run together during posting. When you create a payment journal and mark open transactions for settlement, both actions happen at the same time. If the settlement fails because of data inconsistencies, record locks, or validation problems, the entire journal posting fails, even when the payment data is valid.

This tight coupling creates several problems:

- Blocked payments - Valid payments can't post because of an unrelated settlement error, which delays payment processing.
- Added risk and manual overhead - Users must intervene to work around failures before payments can be completed.
- Performance bottlenecks - When settlement logic is slow or error-prone, it holds up the whole posting process.

Delayed settlement removes this dependency. The payment posts on its own, and settlement is handled as a separate step. A settlement problem never blocks a valid payment.

## How delayed settlement works

Without this feature, when you post a payment journal, the system also settles the marked transactions in real time. Because these two steps are linked, any failure in the settlement logic can stop the entire payment from posting.

When you enable delayed settlement, the posting logic changes: the system posts only the payment through the journal and stores the settlement relationship for later, instead of settling immediately. A background automation or you from the **Settlement in queue** page completes the queued settlement on its own.

The end-to-end flow is:

1. Post payment – The payment journal posts, even if settlement can't complete.
1. Queue settlement – The system stores the settlement relationship and adds it to the queue.
1. Process settlement – The system completes the settlement automatically every 5 minutes, or manually on demand.
1. Settle or retry – On success, the system settles; on failure, you retry it manually.

## Configure delayed settlement

### Enable it on a journal name

To enable the feature on a journal, follow these steps:

1. Go to **General ledger > Journal setup > Journal names**.
1. Turn on delayed settlement for the journal you want.
1. The toggle appears for customer payment and vendor payment journal types.

### Set the parameters

Use the customer and vendor payment settings to control how delayed settlement behaves.

| Setting | Controls |
|---|---|
| Decouple settlement on posting | Whether posting a payment journal decouples the settlement process, so the payment posts without settling immediately. |
| Access to **Settlement in queue** | Whether users can go to the **Settlement in queue** page to review and process delayed settlements. |

### Post a payment journal with delayed settlement

When delayed settlement is enabled, you can post a payment journal that has transactions marked for settlement even if:

- The settlement has validation issues, or
- The settlement process fails and only the payment is posted.

During posting, the system stores the settlement relationship, but doesn't settle it, and adds it to the settlement queue for separate processing.

> [!TIP]
> After posting, the system directs you to review delayed settlements separately on the **Settlement in queue** page.

### Automatic processing

A background process automation runs continuously and picks up queued settlements every five minutes, attempting to complete each one. No action is required for settlements that succeed automatically.

### Manual processing — the Settlement in queue page

To manually settle a journal, follow these steps:

1. Go to **Cash and bank management > Periodic tasks > Settlement in queue**.
1. Select one of the following options:

- **Settle now** – Trigger immediate settlement of the selected entry.
- **Settle in batch now** – Run the settlement as a batch job.
- **View marked transactions** – See the transactions linked to a queued settlement.
- **Cancel settlement** – Remove the settlement mark. This action doesn't reverse the posted payment (important for vendor payments).

<!-- TODO: capture and add screenshot before publishing -->
:::image type="content" source="media/settlement-in-queue.png" alt-text="Screenshot of the Settlement in queue page under Cash and bank management periodic tasks.":::

### Settlement status

Each queued settlement shows a status that tells you where it is in processing.

| Status | Meaning |
|---|---|
| Prepared | Queued and waiting to be processed. |
| Processing | Currently being processed. |
| Partial success | Some marked transactions settled; others still need to be processed. |
| Success | All marked transactions settled successfully. |
| Failed | The settlement attempt failed and needs a manual retry. |

For a **Partial success** entry, you can re-run the settlement action. The page shows the transactions that aren't processed yet so you can settle the remainder.

## Retry a failed settlement

The system doesn't automatically retry failed settlements. The background automation skips failed records, so you need to intervene manually. On the **Settlement in queue** page, review the recorded error log for the failed entry, and then select **Reset failed settlement** (or **Settle** / **Settle in batch now**) to try again.

> [!WARNING]
> Automation never reprocesses a **Failed** settlement on its own. If you don't retry it from the **Settlement in queue** page, the settlement stays open indefinitely.

## Transaction behavior while a settlement is queued

- Open transactions (invoices) involved in a queued settlement are **locked** - no manual edits or automatic settlement are allowed - until the settlement completes or is cancelled.
- Marked invoices show a delayed-settlement indicator on the settlement form so you can tell they're already committed to a queued settlement.
- Cancelling a queued settlement removes the mark but **doesn't reverse** the posted payment.

## Considerations and limitations

- Automatic and batch payment journal posting behavior is **unchanged**.
- The settlement logic itself is unchanged - how transactions are matched and applied stays the same.
- The system doesn't automatically retry failed settlements; you trigger the retry.
- Payments aren't reversed if the corresponding settlement fails.
- The way you mark transactions during journal entry doesn't change.
