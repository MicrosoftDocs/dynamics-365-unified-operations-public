---
title: Work remains blocked
description: Work remains blocked
author: perlynne
ms.date: 04/15/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTableListPage_WHSWorkUnblocking
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-05-15
ms.dyn365.ops.version: 10.0.18
---

# Work remains blocked

Error code: WHSWorkBlockingExecutingWaveReason_ErrorMessage

## Symptoms

The system shows the following error message:

> Work %1 remains blocked because the related wave %2 has status %3.

## Cause

The work is currently being processed on a wave and can't be unblocked, as indicated by one of the following conditions:

- On the **Blocking reasons** tab, the **Work blocking reason** field for one or more lines is set to *Processing wave*.
- When you select **Wave** in the **Related information** group on the **Related information** tab of the Action Pane, the **Wave status** field is set to *Processing*.

## Resolution

On the Action Pane, on the **Related information** tab, in the **Related information** group, select **Wave**. Then, on the **Waves** page, on the Action Pane, on the **Wave** tab, in the **Wave** group, select **Cleanup wave data**.

## Workaround

If the previous steps didn't fix the issue, you can cancel the work by following these steps.

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the ID of the work that you want to cancel, and that currently has a **Work status** value of *Open*, *In progress*, *Canceled*, *Combined*, or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md).
