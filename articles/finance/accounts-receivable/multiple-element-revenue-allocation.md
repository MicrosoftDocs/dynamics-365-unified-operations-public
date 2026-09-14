---
title: Configure Multiple element revenue allocation (preview)
description: Multiple element revenue allocation termination revenue adjustments let you terminate a complete billing schedule, allocate amounts, and clear deferred contract revenue account balances. 
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 09/08/2026
ms.topic: article
---

# Multiple element revenue allocation termination revenue adjustments overview (preview)

This functionality is available as a preview in Microsoft Dynamics 365 Finance version 10.0.49.

The **Multiple element revenue allocation termination revenue adjustment (preview)** feature is a Subscription billing capability that supports complete termination of a billing schedule containing lines that participate in a Multiple element revenue allocation arrangement. Termination must be initiated from the billing schedule header. During termination, the system evaluates the Multiple element revenue allocation arrangement, allocates applicable termination amounts according to extended standalone selling price proportions, and clears remaining deferred contract revenue account balances when required. The accounting treatment depends on the selected termination method.

If the termination is later removed and the related transactions remain eligible for reversal, the system restores the affected schedule and reverses a Multiple element revenue allocation clearing journal only when one was created during termination processing.

This feature supports complete billing schedule termination only. Line-level termination and mass termination aren't supported. Mass termination uses line-level processing and therefore doesn't meet the complete-schedule requirement.

## Prerequisites

- Microsoft Dynamics 365 Finance version 10.0.49 or later.
- The following Subscription Billing modules enabled:
  - Subscription Billing
  - Revenue and expense deferrals
  - Recurring contract billing
  - Multiple element revenue allocation
- The **Multiple element revenue allocation termination revenue adjustment (preview)** feature enabled in **Feature management**.

For more information about Subscription billing and Multiple element revenue allocation, see [Subscription billing overview](subscription-billing-summary.md).

### Termination adjustment journal configuration

The **Multiple element revenue allocation parameters** control automatic adjustment processing during billing schedule termination. To update the parameters, go to **Subscription billing** > **Multiple element revenue allocation** > **Setup** > **Multiple element revenue allocation parameters**.

In the **Multiple element revenue allocation termination adjustment** section:

- **Create Multiple element revenue allocation adjustment journal entry** option:
  - Set this option to **Yes** and specify the journal name in the **Journal name** field to use for Multiple element revenue allocation clearing entries. The default journal name is **GenJrn**.
  - Set this option to **No** to clear the **Journal name** field.

The system creates a separate clearing journal only for termination methods that require it. The **Issue credit** method adjusts the credit-note voucher itself instead of creating a separate clearing journal for the credit transaction.

### Termination processing for Multiple element revenue allocation billing schedules

When you terminate a billing schedule that contains Multiple element revenue allocation lines, the system:

- Evaluates all eligible Multiple element revenue allocation lines in the billing schedule as one complete termination event.
- Processes Revenue Split parent and child lines together through the parent. Child lines aren't processed independently.
- Calculates the applicable termination refund and determines whether it needs to clear a deferred contract revenue account balance.
- Allocates the applicable termination amount among eligible Multiple element revenue allocation lines according to their extended standalone selling price proportions.
- Assigns any rounding remainder to the final eligible Multiple element revenue allocation line.
- Creates or updates accounting entries according to the selected termination method.
- Updates the termination status for the billing schedule and associated eligible lines.

### Accounting treatment by termination method

The system uses different accounting treatment depending on the termination method.

| Termination method | Accounting treatment |
| ---- | ---- |
| No credit | Creates a separate **Multiple element revenue allocation clearing** journal when an adjustment is required to clear the remaining deferred contract revenue account balance. |
| Credit adjustment | Creates a separate **Multiple element revenue allocation clearing** journal for the required **Multiple element revenue allocation** adjustment. |
| Issue credit | Adjusts the accounting distribution on the credit-note voucher itself. A separate **Multiple element revenue allocation clearing** journal isn't created for the credit transaction. |

### Adjustment entry review

To view entries associated with a termination, use the termination adjustment inquiry on the billing schedule. Follow these steps:

1. Go to **Billing schedule** \> **Line details** \> **Termination** \> **Adjustment entries inquiries**.
1. After the termination is processed, the voucher reflects the following results:

- The deferred contract revenue account balance for the fully terminated Multiple element revenue allocation arrangement is 0.00 when clearing is required.
- A clearing entry reverses the existing deferred contract revenue account balance instead of increasing it.
- Allocated termination amounts equal the total amount to be distributed.
- The allocation follows each eligible line's extended standalone selling price proportion.
- Any rounding remainder is assigned to the final eligible Multiple element revenue allocation line.
- The accounting entry corresponds to the selected termination method: a separate clearing journal for **No credit** or **Credit adjustment**, or an adjusted credit-note voucher for **Issue credit**.

#### Termination removal

You can remove a termination only while the related termination transactions remain eligible for reversal.
To remove a termination, follow these steps:

1. Go to **Subscription billing** > **Recurring contract billing** > **Billing schedules** > **All billing schedules**. 
1. Open the terminated billing schedule. 
1. Select **Remove termination**.

When you remove a termination, the system:

- Reactivates the eligible revenue split parent and child lines.
- Reverses the termination adjustment journal that it previously created.
- Clears the stored termination credit shares and adjustment journal reference.

You can't remove a termination in the following situations:

- The termination credit note is invoiced.
- A related free text invoice termination adjustment exists.
- An unbilled and deferred line has a recognized deferral adjustment that you must remove first.
- Another posted credit adjustment prevents the termination from being reversed.

### Considerations and limitations

- You can only terminate a complete billing schedule when you initiate termination from the billing schedule header.
- Line-level termination isn't supported.
- Mass termination isn't supported because it uses line-level termination processing.
- The system processes Revenue Split parent and child lines together through the parent; it doesn't process child lines independently.
- The system reverses a clearing journal during Remove termination only when it creates one during termination processing.
- The system doesn't support combined Multiple element revenue allocation and Customer split scenarios until the combined scenario is validated.

## Examples

### Complete schedule termination with No credit

A billing schedule contains multiple performance obligations that participate in a Multiple element revenue allocation arrangement. You terminate the complete schedule from the billing schedule header and select **No credit**.

The system closes the eligible Multiple element revenue allocation lines, evaluates the remaining deferred contract revenue account balance, and creates a separate clearing journal when an adjustment is required. The journal clears the residual balance so that the fully terminated arrangement doesn't retain a stranded deferred contract revenue account balance.

### Complete schedule termination with credit adjustment

A billing schedule contains two performance obligations with equal extended standalone selling price proportions. You terminate the complete schedule from the billing schedule header by using **Credit adjustment**.

| Performance obligation | Standalone selling price proportion | Adjustment amount |
|----------------------------|--------------------|-----------------------|
| Services                   | 50%                | 1,000 USD             |
| Consumption                | 50%                | 1,000 USD             |

For a total termination adjustment of 2,000 USD, the system allocates 1,000 USD to each performance obligation and creates a separate Multiple element revenue allocation clearing journal for the required adjustment.

### Complete schedule termination with Issue credit

Use **Issue credit** to completely terminate a billing schedule that participates in a Multiple element revenue allocation arrangement from the billing schedule header. The system applies the Multiple element revenue allocation arrangement to the accounting distribution on the credit-note voucher. It doesn't create a separate Multiple element revenue allocation clearing journal for the credit transaction.

#### Benefits

The Multiple element revenue allocation termination revenue adjustments feature provides several benefits:

- Improves accuracy of revenue allocation during contract termination.
- Reduces reliance on manual adjustment journals.
- Helps eliminate residual balances that require manual intervention.
- Simplifies reconciliation and month-end close activities.
- Improves visibility into termination-related accounting events.
- Supports revenue allocation processes that rely on standalone selling price allocation methodologies.
