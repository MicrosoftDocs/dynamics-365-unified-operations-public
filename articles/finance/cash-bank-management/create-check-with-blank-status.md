---
title: Create new checks or reuse existing checks
description: Learn how to create blank checks for a bank account and reuse available checks in Dynamics 365 Finance.
author: mukumarm
ms.author: mukumarm
ms.topic: how-to
ms.date: 07/20/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-09-17
ms.search.form: BankChequeTable
ms.dyn365.ops.version: AX 10.0.5
ms.assetid: d7e22bd8-fd0d-47e1-843f-45ab0193ff8d
---

# Create checks that have blank status

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to create blank checks. For example, you might create a blank check to record a check that you damaged and can't use for payment.

On the **Checks** page, you perform maintenance tasks for checks. For example, you can create new check numbers and delete checks. You can also create checks that have a status of **Blank**. After you create blank checks, you can't delete or reuse them in the system.

> [!NOTE]
> You can access this feature on the **Checks** page only if you turn on the **Create checks with a blank status on the Checks page** feature on the **Feature management** page. If you don't turn on the feature, you can create checks that have **Blank** status from the **Payment by check** dialog box during the payment generation process in Accounts payable.

1. Go to **Cash and bank management > Bank accounts > Bank accounts**.
1. On the Action Pane, on the **Manage payments** tab, in the **Related information** group, select **Checks**. Alternatively, go to **Cash and bank management > Inquiries and reports > Checks**.
1. To create checks that have **Blank** status, on the Action pane, select **Create blank checks**.
1. While the system creates the blank checks, it temporarily deactivates the associated bank account. This behavior reduces the risk that payments are generated at the same time that blank checks are created. When the processing finishes, the system reactivates the associated bank account.

## Reuse checks

The **Reuse checks** feature assigns an eligible check number to a new payment when the original payment wasn't completed. Reusing checks helps reduce check stock waste, maintain continuous check numbering, and improve auditability.

## Prerequisites

Before you can reuse checks, verify that:

1. The legal entity supports check reuse. The **Reuse checks** feature availability varies by country/region.
1. The bank account uses a fixed check number sequence.
1. Check reuse is enabled in **Cash and bank management parameters**.
1. The check isn't posted, paid, canceled, or permanently marked as unavailable.

### Enable check reuse

To enable the **Reuse checks** feature, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Cash and bank management parameters**.
1. On the **General** tab, turn on **Allow check reuse**.
1. Save your changes.

### Reuse a check

To reuse a check, follow these steps:

1. Go to **Accounts payable** > **Payments** > **Vendor payment journal**.
1. Create or open a payment journal.
1. Add a payment line.
1. Select **Generate payments** to assign a check number.
1. If the generated check can't be used before the payment is posted, select the payment line.
1. Select **Payment status** > **Reuse**.
1. Verify that the **payment status** changes back to **None** and that the check becomes available for reuse.
1. Select **Generate payments** again.
1. Confirm that the available check number is assigned to the new payment.
1. Post the payment journal.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
