---
title: Wave is not eligible for cleanup
description: Wave is not eligible for cleanup
author: perlynne
ms.date: 04/15/2021
ms.topic: troubleshooting
ms.search.form: WHSWaveTable_WHSWaveProcessingDataCleanup
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-05-15
ms.dyn365.ops.version: 10.0.18
---

# Wave is not eligible for cleanup

Error code: WaveNotEligibleForCleanup

The system displays the following error message:

> Wave %1 is not eligible for cleanup.

## Issue description

The wave data can't be cleaned up and you see one of the following symptoms:

- The **Wave status** is set to *Executing*.
- On the Action Pane, open the **Wave** tab and, from the **Wave** group, select **Batch job**. The **Status** is not set to *Ended*, *Error*, or *Canceled*, indicating that a batch job is currently running.

## Resolution

The wave is currently being processed. On the Action Pane, open the **Wave** tab and, from the **Wave** group, select **Batch job** and do one of the following:

- If the **Status** is set to *Executing*: On the Action Pane, open the **Batch job** tab and from the **Batch job** group, select **View tasks**. The progress can be followed by refreshing the **Batch tasks** page.
- If the **Status** is not set to *Executing*: On the Action Pane, open the **Batch job** tab and from the **Functions** group, select **Change status**. In the **Select new status** field, select *Waiting*. Select **OK**.
