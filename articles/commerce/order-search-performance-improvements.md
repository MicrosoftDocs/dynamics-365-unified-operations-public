---
title: Performance improvements of Commerce Order search
description: This article explains how to improve search order performance by enabling the use of intermediate order totals 
author: ashishMSFT
ms.date: 12/05/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 10.0.0 
ms.custom: 85493
ms.assetid: a22c9493-c000-4514-bb0d-b3cc674439d9
ms.search.industry: Retail
---

# Performance improvements of Commerce Order search

This feature allows you to improve search order performance by enabling the use of intermediate order totals calculated by “Calculate sales totals” job.  To enable this feature, navigate to “Feature management” and locate ‘Improve performance of Commerce Order search’ to enable it. 

![Enable order search performance improvements from feature management](./media/EnableFeatureImproveOrderSearchPerformance.png)


### Prior to enabling ‘Improve performance of Commerce order search’ from feature management 

Navigate to ‘Sales and marketing’ > Periodic tasks > ‘Calculate sales total’ 
_This feature helps improve performance by enabling the system to use parallel processing when it calculates sales totals in a batch. The feature adds a new Number of threads field to the Calculate sales totals dialog box. If you choose to run the calculation in a batch, you can use this field to set the maximum number of threads. If you set the value to 0 (zero) or 1, a single thread will be used. Values above 1 enable multithreading. It is advisable to enable the following feature ‘Calculate sales totals using multiple threads’ to speed up totals processing in case if there is a large number of ‘Sales orders and quotations.’_

![Launch calculate sales totals](./media/LaunchCalculateSalesTotals.png)

To properly schedule this job we use these steps:
1.	Navigate to Batch Jobs and click “+New”, give a good name, e.g.: Calculate Sales Totals
2.	While new job is in Withhold state, configure the task:
a.	Give similar name to the batch task
b.	Put “SalesTotalsCalculateBatch” as a Class name.
c.	Select company/LE, e.g.: USRT
d.	In parameters of the task set both toggles to Yes as shown on the picture below:

![Schedule calculate sales total batch job](./media/ScheduleCalculateSalesTotals.png)

e. 	Schedule the job recurrence to run every 5-10 minutes.
f.	Change status to “Waiting”
g.	Go to “Batch job history” and inspect 100% correct execution.



