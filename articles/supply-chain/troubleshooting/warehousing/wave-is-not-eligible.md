---
title: Wave isn't eligible for cleanup
description: Wave isn't eligible for cleanup
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

# Wave isn't eligible for cleanup

Error code: WaveNotEligibleForCleanup

## Symptoms

The system shows the following error message:

> Wave %1 is not eligible for cleanup.

The wave data can't be cleaned up.  

## Cause

The wave is currently being processed, as indicated by one of the following conditions:

- The **Wave status** field is set to *Executing*.
- When you select **Batch job** in the **Wave** group on the **Wave** tab of the Action Pane, the **Status** field isn't set to *Ended*, *Error*, or *Canceled*. Therefore, a batch job is currently running.

## Resolution

On the Action Pane, on the **Wave** tab, in the **Wave** group, select **Batch job**, and then follow one of these steps:

- If the **Status** field is set to *Executing*: On the Action Pane, on the **Batch job** tab, in the **Batch job** group, select **View tasks**. You can follow the progress by refreshing the **Batch tasks** page.
- If the **Status** field isn't set to *Executing*: On the Action Pane, on the **Batch job** tab, in the **Functions** group, select **Change status**. In the **Select new status** field, select *Waiting*. Then select **OK**.
