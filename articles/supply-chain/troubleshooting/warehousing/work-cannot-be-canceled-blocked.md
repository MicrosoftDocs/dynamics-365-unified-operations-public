---
title: Work can't be canceled because it's blocked
description: Work can't be canceled because it's blocked
author: perlynne
ms.date: 04/15/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTable_WHSWorkCancel
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-05-15
ms.dyn365.ops.version: 10.0.18
---

# Work can't be canceled because it's blocked

Error code: WHSCancellationOfWorkBlockedByExecutingWave_ErrorMessage

## Symptoms

The system shows the following error message:

> Work %1 cannot be cancelled because it is blocked by reason type %2. The work must be unblocked before it can be cancelled.

## Cause

The work is blocked and can't be canceled.

On the **Work** page, on the **General** tab, the **Blocked** option is set to *Yes*. This setting indicates that the work is blocked. The **Blocking reasons** tab shows why the work was blocked.

## Resolution

To unblock the work, select the **Blocking reasons** tab, and then follow one of these steps:

- If the **Work blocking reason** field is set to *Undefined reason*: On the Action Pane, on the **Work** tab, in the **Work** group, select **Unblock work**.
- If the **Work blocking reason** field is set to *Processing wave*: On the Action Pane, on the **Related information** tab, in the **Related information** group, select **Wave**. Then, on the **Waves** page, on the Action Pane, on the **Wave** tab, in the **Wave** group, select **Cleanup wave data**.

## Workaround

If the previous steps didn't fix the issue, you can cancel the work by following these steps.

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the ID of the work that you want to cancel, and that currently has a **Work status** value of *Open*, *In progress*, *Canceled*, *Combined*, or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md).
