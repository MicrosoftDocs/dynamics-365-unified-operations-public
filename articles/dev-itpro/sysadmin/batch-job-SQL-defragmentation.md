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


In Platform update 22, a new system batch job has been introduced to rebuild fragmented indexes. Index fragmentation results in notable performance degradation in specific scenarios. To address the fragmentation issues and keep the database in a top-performing state, this new system job will rebuild highly-fragmented indexes periodically at a scheduled time. It is, by default, scheduled to run at 3:00 am local time every day for the maximum of 2 hours. If the batch job finds that not many fragmented indexes need to be rebuild, it will complete early.  

This system job can’t be cancelled. Customers can change the schedule and its recurrence to suit their need to make it weekly.  System jobs expect they run at least once a week. 

They can change the parameter values on the **Adjust system job parameters** page to pick how long it can run and how many indexes it should target at max. The DTU threshold is to prevent this job from kicking off when the system is busy. The default DTU threshold is 50,  which means that if the system is using 50% or more DTU during the time the index rebuild job is scheduled to run, the job will do an early exit without rebuilding any indexes.
 
![Screenshot of Adjust system job parameters page](media/SystemJobParameters.gif "Screenshot of Adjust system job parameters page")
 
When this job is executing, there could be some impact:
1.	It takes SQL resources to process
2.	It may result in some blocking

## Changing the default scheduled time/recurrence
1. Go to **System administration > Inquiries > Batch Jobs**.
2. Search for a job description that contains *index rebuild*.   
3. Select the record.  
4. Click the menu item **Batch Job > Recurrence**.  
5. Change the schedule time, recurrence that suits.

screen shot

screen shot

The results of index rebuilds can be found by going to **System administration > Inquiries > Database > SQL index fragmentation details**. 

> [!Note]
> In some cases you may find the before and after fragmentation number or same or even higher. Do not get alarmed. This is because of the less intrusive ‘online’ rebuild option that we use. In future we will introduce an optional offline rebuild option too.

screen shot




