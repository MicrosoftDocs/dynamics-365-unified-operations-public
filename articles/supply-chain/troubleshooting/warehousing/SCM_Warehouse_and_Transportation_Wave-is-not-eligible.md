---
# required metadata

title: Wave is not eligible for cleanup
description: Wave is not eligible for cleanup
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSWaveTable_WHSWaveProcessingDataCleanup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: hja@microsoft.com

---

# Wave is not eligible for cleanup

Error code: WaveNotEligibleForCleanup

The system displays the following error message:

> Wave %1 is not eligible for cleanup.

## Symptoms
The wave data can’t be cleaned up. See one of the following symptoms:
-The **Wave status** is set to *Executing*.
-On the Action Pane, open the **Wave** tab and, from the **Wave** group, select **Batch job**. The **Status** is not set to *Ended*, *Error* or *Canceled*, indicating that a batch job is currently running.




## Resolution
The wave is currently being processed. On the Action Pane, open the **Wave** tab and, from the **Wave** group, select **Batch job** and do one of the following:
- The **Status** is set to *Executing*. On the Action Pane, open the **Batch job** tab and from the **Batch job** group, select **View tasks**. The progress can be followed by refreshing the **Batch tasks** page.
- The **Status** is not set to *Executing*. On the Action Pane, open the **Batch job** tab and from the **Functions ** group, select **Change status**. In the **Select new status** field, select *Waiting*. Select **OK**.



