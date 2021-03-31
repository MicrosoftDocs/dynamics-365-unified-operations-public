---
title: Work remains blocked
description: Work remains blocked
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021
ms.topic: troubleshooting
ms.search.form: WHSWorkTableListPage_WHSWorkUnblocking
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-03-24
ms.dyn365.ops.version: 10.0.18
---

# Work remains blocked

Error code: WHSWorkBlockingExecutingWaveReason_ErrorMessage

The system displays the following error message:

> Work %1 remains blocked because the related wave %2 has status %3.

## Issue description

The work is currently being processed on a wave and can't be unblocked and you see one of the following symptoms:

- On the **Blocking reasons** tab, the **Work blocking reason** is set to *Processing wave* for one or more of the lines.
- On the Action Pane, open the **Related information** and, from the **Related information** group, select **Wave**. The **Wave status** is set to *Processing*.

## Resolution

On the Action Pane, open the **Related information** and, from the **Related information** group, select **Wave**. On Action Pane of the **Waves** page, open the **Wave** tab and, from the **Wave** group, select **Cleanup wave data**.

## Workaround

If the previous steps didn't resolve the issue, you can cancel the work using the following steps:

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the work ID that you want to cancel, and which currently has a **Work status** of *Open*, *In progress*, *Cancelled*, *Combined* or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md)
