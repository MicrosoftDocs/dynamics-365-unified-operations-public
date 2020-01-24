---
# required metadata

title: Batch job to handle SQL index defragmentation
description: This topic describes a system batch job that is used to rebuild fragmented indexes.
author: Peakerbl
manager: AnnBe
ms.date: 02/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: ganas
ms.search.validFrom: 2018-12-31 
ms.dyn365.ops.version: Platform update 22 
---

# Batch job to handle SQL index defragmentation

[!include[banner](../includes/banner.md)]


In Platform update 22, a new system batch job has been introduced to rebuild fragmented indexes. Index fragmentation results in notable performance degradation in specific scenarios. To address fragmentation issues and keep the database in a top-performing state, this batch job will rebuild highly fragmented indexes periodically at a scheduled time. By default, the job scheduled to run at 3:00 AM local time every day for a maximum of 2 hours. If the batch job finds that not many fragmented indexes need to be rebuilt, it will complete early.  

This system job cannot be canceled. You can change the schedule and its recurrence if you want to run it weekly. System jobs are expected to run at least once a week. 

You can change the parameter values on the **Adjust system job parameters** page to denote how long the job can run and how many indexes it should target, at a maximum. The DTU threshold is to prevent this job from starting when the system is busy. The default DTU threshold is 50,  which means that if the system is using 50 percent or more DTU during the time that the index rebuild job is scheduled to run, the job exit early without rebuilding any indexes.
 
![Screenshot of Adjust system job parameters page](media/SystemJobParameters.PNG "Screenshot of Adjust system job parameters page")
 
When this job is executing, there could be some impact on the following:
-	The time that it takes SQL resources to process.
- There may be blocking,

## Change the default scheduled time/recurrence
1. Go to **System administration > Inquiries > Batch Jobs**.
2. Search for a job description that contains *index rebuild*.   
3. Select the record.  
4. Click the menu item **Batch Job > Recurrence**.  
5. Change the schedule time and recurrence to suit your schedule.

The results of index rebuild can be found by going to **System administration > Inquiries > Database > SQL index fragmentation details**. 

> [!Note]
> In some cases, you may find that the before and after fragmentation number is the same or even higher. This is typical because Microsoft uses a less intrusive online rebuild option. In the future, we plan to introduce an optional offline rebuild option.
