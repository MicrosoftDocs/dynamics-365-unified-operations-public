---
# required metadata

title: Batch job to handle SQL index defragmentation
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: sericks
manager: AnnBe
ms.date: 02/21/2019
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


In PU22 a new system batchjob has been introduced to rebuild fragmented indexes.  Index fragmentation results in notable performance degradation in specific scenarios.  To address the fragmentation issues and keep the database is top performing state, this new system job will rebuild highly fragmented indexes periodically at a scheduled time. It is by default scheduled to run at 3:00 am local time every day for the maximum of 2 hours.  If the batch job finds not many fragmented indexes that needs rebuild, it will complete early.  

This system job can’t be cancelled.  But customers can change the schedule and its recurrence to suit their need to make it weekly.  System jobs expect they run at least once a week. [ganas: corrected my previous statement and added a new line]

They can change the parameter values  from ‘System Administration’ -> Setup -> ‘System job parameters’  to pick how long it can run and how many indexes it should target at max.   The DTU threshold is to prevent this job from kicking off when the system is busy.  The default DTU threshold is 50,  which means if the system is using 50% or more DTU during the time the index rebuild job scheduled to run, the job will do an early exit without rebuilding any indexes.
 
 <screen shot>
 
 When this job is executing there could be some impact.
1.	It takes SQL resources to process
2.	It may result in some blocking

## Changing the default scheduled time/recurrence
Go to ‘System administration’ -> Inquiries -> ‘Batch Jobs’.
Search for job description that contains ‘index rebuild’.   Select the record.  Click the menu item ‘BATCH JOB’-> recurrence.  Change the schedule time, recurrence that suits.

<screen shot>

<screen shot>

The results of Index rebuilds can be found by going to ‘System administration’ -> Inquiries -> Database ->  ‘SQL index fragmentation details’.  
Note: In some cases you may find the before and after fragmentation number or same or even higher.    Do not get alarmed.  This is because of the less intrusive ‘online’ rebuild option that we use.  In future we will introduce an optional offline rebuild option too.

<screen shot>




