--- 
# required metadata 
 
title: Create a batch job
description: A batch job is a group of tasks that are submitted to an Application Object Server (AOS) instance for automatic processing. 
author: maertenm
ms.date: 11/16/2021
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: BatchJob, SysRecurrence, BatchAlerts   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a batch job

[!include [banner](../../includes/banner.md)]

A batch job is a group of tasks that are submitted to an Application Object Server (AOS) instance for automatic processing. Batch jobs are run by using the security credentials of the user who created the job. Use the following procedure to create a batch job. The demo data company used to create this procedure is USMF.


## Create the batch job
1. Go to **Navigation pane > Modules > System administration > Inquiries > Batch jobs**.
2. Click **New**.
3. In the **Job description** field, enter a description for the batch job.
4. In the **Scheduled start date/time** field, enter a date and time you want the batch job to run..
5. Click **Save**.

## Create a recurrence
1. On the Action Pane, click **Batch job**.
2. Click **Recurrence**. Use these options to enter a range and pattern for the recurrence.  
3. Click **OK**.

## Add alerts
1. On the Action Pane, click **Batch job**.
2. Click **Alerts**. Indicate if you want alert messages sent when the batch job ends, has an error, or is canceled. Then specify if you want the alerts to be displayed as pop-up messages.   
3. Click **OK**.

## Add a task to a batch job
1.	In the **Batch jobs** form, click the **View tasks** button.
2.	Press CTRL+N to create a new task.
3.	Enter a description for the batch task.
4.	In the **Company accounts** field, select the company database in which the task will run.
5.	In the **Class name** field, select the process that you want the task to run. 
6.	If appropriate, select a batch group for the task.
Client tasks must be assigned to a batch group, and they are automatically assigned to the default batch group (also known as the Empty batch group).
7.	Press CTRL+S to save the task.
8.	To make the selected task dependent on another task in the job, click in the **Has conditions** grid, and follow these steps.
a.	Press CTRL+N to create a new condition.
b.	Select the task ID of the parent task.
c.	Select the status that the parent task must reach before the dependent task can run.
d.	Press CTRL+S to save the condition.
If you have entered more than one condition, and if all conditions must be met before the dependent task can run, select a condition type of **All**. Select a condition type of **Any** if the dependent task can run after any of the conditions has been met.
9.	Choose how to handle task failures. To ignore the failure of a specific task, on the General tab, mark the Ignore task failure option for that task. If this option is marked, the failure of the task will not cause the job to fail. You can also use the Maximum retries field to specify the number of times that a task should be retried before it is considered to have failed.As a best practice we recommend not to set maximum retry more than **5**.

Learn more about the options about batch retry https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/retryable-batch

## Adjust batch job status
1. Go to **System administration > Inquiries > Batch jobs**.
2. Select the appropriate batch job.
3. On the Action Pane, click **Batch job > Functions > Change status**.
4. Select the appropriate status:
    - **Withhold**: Set the batch job as **withhold** so it is withheld from the batch job scheduler. Equivalent to *stop*.
    - **Waiting**: Set the batch job as **waiting** so it is waiting to be picked up by the batch job scheduler. Equivalent to *go*.
5. Click **OK**.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
