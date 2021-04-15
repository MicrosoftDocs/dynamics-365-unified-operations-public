---
title: Work can't be canceled because it is blocked
description: Work can't be canceled because it is blocked
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTable_WHSWorkCancel
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-03-24
ms.dyn365.ops.version: 10.0.18
---

# Work can't be canceled because it is blocked

Error code: WHSCancellationOfWorkBlockedByExecutingWave_ErrorMessage

The system displays the following error message:

> Work %1 cannot be cancelled because it is blocked by reason type %2. The work must be unblocked before it can be cancelled.

## Issue description

The work is blocked and can't be canceled.

On the **Work** page, on the **General** tab, **Blocked** is set to *Yes*, which means the work is blocked. The **Blocking reasons** tab shows why it was blocked.

## Resolution

To unblock the work, go to the **Blocking reasons** tab and do one of the following:

- If the **Work blocking reason** is set to *Undefined reason*, then you can unblock the work. On the Action Pane, open the **Work** tab and, from the **Work** group, select **Unblock work**.
- If the **Work blocking reason** is set to *Processing wave*, then on the Action Pane, open the **Related information** tab and, from the **Related information** group, select **Wave**. On Action Pane of the **Waves** page, open the **Wave** tab and, from the **Wave** group, select **Cleanup wave data**.

## Workaround

If the previous steps didn't resolve the issue, you can cancel the work using the following steps:

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the work ID that you want to cancel, and which currently has a **Work status** of *Open*, *In progress*, *Canceled*, *Combined*, or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md)
