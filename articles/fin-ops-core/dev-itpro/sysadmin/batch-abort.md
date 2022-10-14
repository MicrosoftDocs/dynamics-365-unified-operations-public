---
# required metadata

title: Cancel an executing batch job
description: This article provides information about how to cancel an executing batch job.
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

## Cancelling a batch job

Wherever there is a requirement to cancel an executing batch job, you can change the status of the batch job to cancelling.
This will prevent batch from picking up new tasks for execution. The tasks which are not picked up for execution will be marked as not run and executing tasks will be marked as cancelling, but it will wait till tasks terminate gracefully i.e. finish or error out.  
<br/>
![Cancelling a batch job](./media/cancelling-a-batch-job.png)  
<br/>
State of the batch job and its tasks after cancelling:  
<br/>
![Cancelled batch job](./media/cancelled-batchjob.png)
<br/>

## Aborting tasks in a batch job

Sometimes jobs stay in cancelling state for long time and waiting for graceful termination may not be possible. This option provides a system administrator or batch job manager with the ability to abort all the tasks that are in cancelling state for the batch job. This forces the cancelling tasks in the job to immediately stop their execution.
>[!NOTE]
>
> * It is important to note that this feature should be used with caution. When you abort a running process, it is an inherently unsafe action that can lead to data corruption, resulting in either orphaned or incomplete data. This action should only be used to mitigate other issues caused by the running tasks.  
> * This cannot stop the execution of tasks that are stuck in an unmanaged wait. e.g. Tasks that are stuck due to SQL deadlocks or DIXF related tasks. In cases like these, tasks will be aborted once the task is out from unmanaged wait.  

To abort all cancelling tasks of the batch job, in the batch job form, go to **Batch tasks** tab, click on **Abort**, and then click **Yes**.

![Aborting a batch job](./media/aborting-a-batch-job.png)

### Enhanced abort feature

>[!IMPORTANT]  
>Starting 10.0.31, we have added a drain period i.e. respective batch servers will not pickup new tasks, of maximum 15 minutes on use of enhanced abort. This will allow other tasks that are in executing state on those servers to finish properly.
Once there are no tasks in executing state on those servers or 15 minutes have passed, batch servers will be restarted.

Before you begin, enable the **Enhanced batch abort** feature in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace. After enabling this feature abort will restart all the batch servers currently running the batch tasks of the job that you are attempting to abort. When the servers are restarted there could be other tasks running on those servers which will also be interrupted. 
Restarting of the server makes the functionality more resilient to limitations of abort, and ensures that tasks of the job you are trying to cancel are truly preempted. 

To use this functionality, refer to the following steps:

1. To abort all cancelling tasks of the batch job, in the batch job form, go to **Batch tasks** tab, click on **Abort**.
2. This can potentially disrupt a list of other batch jobs which will be displayed on the dialog. If you are okay with disrupting those jobs click **Yes**.

![Confirm that you want to end the canceling tasks.](./media/enhanceabort-a-batchjob.png)

If you do not want to cancel other running batch tasks on the server and would prefer the old behavior of canceling only the tasks under the batch job and not all the jobs running, you can turn off the **Enhanced batch abort** feature in the Feature management workspace and try to [abort a batch job](#aborting-tasks-in-a-batch-job) again.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
