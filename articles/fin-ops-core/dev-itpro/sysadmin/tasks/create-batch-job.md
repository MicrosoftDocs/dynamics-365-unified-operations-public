--- 
# required metadata 
 
title: Create a batch job
description: A batch job is a group of tasks that are submitted to an Application Object Server (AOS) instance for automatic processing. 
author: maertenm
manager: AnnBe 
ms.date: 06/21/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: BatchJob, SysRecurrence, BatchAlerts   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: maertenm
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a batch job

[!include [banner](../../includes/banner.md)]

A batch job is a group of tasks that are submitted to an Application Object Server (AOS) instance for automatic processing. Batch jobs are run by using the security credentials of the user who created the job. Use the following procedure to create a batch job. The demo data company used to create this procedure is USMF.


## Create the batch job
1. Go to **Navigation pane > Modules > System administration > Inquiries > Batch jobs**.
2. Click **New**.
3. In the **Job description** field, type a value.
4. In the **Scheduled start date/time** field, enter a date and time.
5. Click **Save**.

## Create a recurrence
1. On the Action Pane, click **Batch job**.
2. Click **Recurrence**. Use these options to enter a range and pattern for the recurrence.  
3. Click **OK**.

## Add alerts
1. On the Action Pane, click **Batch job**.
2. Click **Alerts**. Indicate if you want alert messages sent when the batch job ends, has an error, or is canceled. Then specify if you want the alerts to be displayed as pop-up messages.   
3. Click **OK**.

## Adjust batch job status
1. Go to **System administration > Inquiries > Batch jobs**.
2. Select the appropriate batch job.
3. On the Action Pane, click **Batch job > Functions > Change status**.
4. Select the appropriate status:
    - **Withhold**: Set the batch job as **withhold** so it is withheld from the batch job scheduler. Equivalent to *stop*.
    - **Waiting**: Set the batch job as **waiting** so it is waiting to be picked up by the batch job scheduler. Equivalent to *go*.
5. Click **OK**.
