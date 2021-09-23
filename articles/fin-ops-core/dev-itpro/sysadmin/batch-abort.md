---
# required metadata

title: Cancel an executing batch job
description: This topic provides information about how to cancel an executing batch job.
author: karimelazzouni
ms.date: 03/26/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 62333
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
ms.search.region: Global
# ms.search.industry: 
ms.author: kaelazzo
ms.search.validFrom: 2019-05-08
ms.dyn365.ops.version: Platform update 27

---

# <a id="legacy-abort"></a>Cancel an executing batch job
[!include [banner](../includes/banner.md)]

> [!NOTE] 
> This feature is available as of Platform update 27.

Sometimes canceling a batch job can take a long time if already executing tasks will take a long time to finish. This option provides a system administrator or batch job manager with the ability to cancel already executing tasks for jobs that are in the process of being canceled. This provides a much faster mechanism to cancel a long running job that is impacting system usage elsewhere.

>[!NOTE]
> It is important to note that this feature should be used with caution. When you cancel a running process, it is an inherently unsafe action that can lead to data corruption, resulting in either orphaned or incomplete data. This action should only be used to mitigate other issues caused by the running tasks.

Complete the following steps to immediately cancel the running task.

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
2. Select a batch job that has a **Status** of **Canceling**.
3. On the **Batch tasks** tab, select **Abort** on the task, and then select **OK**.

## Enhanced cancellation feature
Starting in version 10.0.16, an enhancement to the batch cancellation functionality has been introduced. Upon confirmation, this will restart the batch server currently running the batch tasks that you are attempting to cancel. This makes the functionality more resilient to limitations, and ensures that tasks of the job you are trying to cancel are truly preempted.

To use the new functionality, refer to the following steps:

1. Make sure you are running version 10.0.16 or later, or have the necessary quality package installed.
2. Enable the **Enhanced batch abort** feature in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace.
3. Follow the same instructions to [cancel an executing batch job](#legacy-abort).
 
You will be prompted that the batch server, which is running the canceling tasks, will be restarted. This can potentially disrupt a list of other batch jobs. You must proceed in order to end the canceling tasks.

![Confirm that you want to end the canceling tasks.](https://user-images.githubusercontent.com/7556912/112464897-ba820680-8d6c-11eb-871a-e1aff1d82665.png)

If you do not want to cancel other running batch jobs on the server and would prefer the old behavior of canceling a single task and not all the jobs running, you can turn off the **Enhanced batch abort** feature in the Feature management workspace and try to [cancel the executing batch job](#legacy-abort) again.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]