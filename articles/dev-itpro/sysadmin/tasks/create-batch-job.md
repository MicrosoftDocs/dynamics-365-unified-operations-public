--- 
# required metadata 
 
title: Create a batch job
description: A batch job is a group of tasks that are submitted to an Application Object Server (AOS) instance for automatic processing. 
author: maertenm
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: maertenm
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a batch job

[!include[task guide banner](../../includes/task-guide-banner.md)]

A batch job is a group of tasks that are submitted to an Application Object Server (AOS) instance for automatic processing. Batch jobs are run by using the security credentials of the user who created the job. Use the following procedure to create a batch job. The demo data company used to create this procedure is USMF.


## Create the batch job
1. Go to System administration > Inquiries > Batch jobs.
2. Click New.
3. In the Job description field, type a value.
4. In the Scheduled start date/time field, enter a date and time.
5. Click Save.

## Create a recurrence
1. On the Action Pane, click Batch job.
2. Click Recurrence.
    * Use these options to enter a range and pattern for the recurrence.  
3. Click OK.

## Add alerts
1. On the Action Pane, click Batch job.
2. Click Alerts.
    * Indicate if you want alert messages sent when the batch job ends, has an error, or is canceled. Then specify if you want the alerts to be displayed as pop-up messages.   
3. Click OK.

