---

# required metadata
title: Improve master planning performance
description: 
author: t-benebo
manager: AnnBe
ms.date: 05/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2019-05-31
ms.dyn365.ops.version: AX 10.0.0


# Improve master planning performance
This article shows different parameters and actions to improve the performance and troubleshoot issues in Master Planning. It includes parameters and settings as well as recommended configurations and actions. The article is intended for system administrators or IT users with capability to troubleshoot as well as for the production or supply planner, as it includes parameters focused on the business planning requirements. It also includes a checklist summary of all the important parameters to consider when facing long running master planning jobs.  

## Master planning performance parameters 
There are different parameters to consider that will influence your MRP run time. Among them you can find the following parameters. 

### Number of threads 
This setting enables you to adjust the master scheduling process so that the process performs better on the specific data set. It is found under Master planning parameter options under Master Planning > Setup > Master Planning, under the General tab, under the section Performance.

The number of threads indicates the total amount of threads that are going to be used for running Master planning. It leads to the parallelization of the master planning run, which leads to a faster running time.  The number of threads is found in the Master planning run dialog. The best value for this parameter is found following a trial and error process. However, you can use the following formulas to calculate an initial value to start value:
If your industry is Manufacturing: #ofThreads = #PlannedOrders / 1000 
Otherwise: #ofThreads = #Items / 1000

The number of Helpers used during master planning needs to be less than or equal to the maximum number of threads allowed on the batch server. Note that increasing the number higher than the threads on the batch server, the extra threads would not perform any work. 

> ![Note]
> Setting the number of threads to zero increases the MRP running time. Therefore, it is recommended to always set a value higher than zero. 

### Number of tasks in helper task bundle (Bundle size)
Changing the number of tasks in the task bundle may have a positive effect on the runtime. The number of tasks in a bundle controls how many items are planned together by a single helper. For this value, it is recommended to follow a trial and error process before an optimal value is determined, as the optimal value will depend on your data. 
 
As a general rule, it is recommended to increase the number of tasks when the number of items is very large (hundreds of thousands) and decrease the number of tasks otherwise. This means that applying to industries: 
	- In **Retail and Distribution** (lots of independent items): use many helpers because there is no dependency between items. We recommend:
	- In **Manufacturing** (lots of BOMs and shared subcomponents): use less helpers because dependency between items may lead to waiting times.

It is recommended to start with a bundle size of 1 and then follow a trial and error process to find the optimal value. 

The parameter is found under Master planning parameter options under **Master Planning > Setup > Master Planning**, under the **General** tab, under the section **Performance**.

> ![Tip]
> If you have performance issues, it is recommended to reduce the number of helpers in task bundle to only 1. Then, you can start the trial and error process to find the optimal value for your setup. In general, performance issues are found when a single item takes longer time to process than the rest of the items. If this is the case that is causing your MRP to take longer time, you will be able to see that two subsequent tasks with the status Coverage in the MRP run take significant different time, in extreme cases up to 30 minutes. You can infer the time that the tasks are taking by looking at the Duration of each of the tasks. 

### Use of cache
This setting enables you to adjust the master scheduling process so that the process performs better on the specific data set. For example, you experience the following benefits:
	- More caching means collecting more data in data memory with hope that the data will be used again later. If the data is in memory, you may save some database requests. However, more caching raises memory requirements.
	- Less caching means that the same data may have to be fetched from the database more frequently. Additionally, Application Object Server (AOS) stores little data in memory throughout the process.
The effectiveness of caching depends heavily on the customer data. Perhaps cached data is never needed and that the memory is only wasted when you store data until the end of the scheduling process. In this case, if you configure less caching, performance may increase because AOS needs less memory and frees server resources for other tasks. 
It is difficult to predict which option is always better, because each case depends not only on data but also on hardware. For example, it is probably not a good idea to add the additional load that is produced by minimum caching on a database server that is already overloaded. 

> ![Tip}
> It is generally recommended to set the Use of cache to Maximum, as it is a performance-enhancing feature. Set to minimum, if you run on-premises with a limited memory (2GB aprox).

### Number of orders in firming bundle 
The number or orders in firming bundle indicates the total amount of orders that will be processed at a time by each thread/batch. This leads to parallelization of the autofirming. Autofirming parallelization is based on the orders to be processed together, which means if it is set to for instance 50, each thread/batch task will pick up 50 orders at a time and process them together. It is recommended to follow a trial and error process to find the optimal value. 
To start with you can use the following formula: #ofOrdersPerBundle = #DemandItems / #ofThreads

> ![Note]
> Setting it to 0  means that there will be no parallelization of the autofirming. So the whole process will run on a single batch task, thus will have a cumulative runtime, increasing the running time of your MRP. Therefore, we recommend to set it to a value larger than zero. 

This parameter is found under **Master planning parameter** options under **Master Planning > Setup > Master Planning**, under the **General** tab, under the section **Performance**.

### Time fences
The time fences indicate how far in the future the calculations are other requirements must be calculated by master planning. The bigger the time fence is, the longer it will take to run Master planning. Therefore, set the time fences according to your business requirements. You can read more about time fences here [(and add in there the link to the "Setup documentation")]

### Actions 
Among the time fences you can also find action message. Calculating action messages leads to longer master planning runtime. If action messages are not analyzed and applied on a regular basis (daily, weekly, etc), consider disabling the calculation during the master plan run, by making sure the Action message time fence is 0 on the master plan you are running (Master planning > Setup > Plans > Master plans). Also make sure all the coverage groups have Action message setting disabled. 

### Futures
Calculating futures leads to longer master planning runtime. If you are not planning BOMs or if propagating delays from supply to demand during planning is not needed for you, consider disabling futures calculation during MRP, by making sure the Futures time fence is 0 on the master plan you are running. Also make sure all the coverage groups have Futures setting disabled.


## One heavy routine at a time
When scheduling master planning, do not schedule any other batch job at the same time. Especially, do not schedule any other heavy routines,  such as Inventory close for example at the same time.  


## Review session log

More information about the tasks run during Master Planning can be collected by the system. To collect this information, enable **"Track processing time"** in the Master Planning run dialog. This information can be useful to find bottlenecks in the MRP run. For example, you can identify the item that takes the longest running time when the number of tasks in the helper task bundle is set to one. You can compare the running times for the different threads with the Status Coverage and compare the Duration for each of the tasks. 

To review the master planning runs of your system:
- From Master Planning workspace: choose the Master plan desired from the dropdown and click History. Then select the job and Inquiries > Process task duration.
- From Master plans page: select the plan desired on the left pane and click History. Then select the job and Inquiries > Process task duration. 

 When reviewing the session log take into account the following points:
- **Update** should not take long time (up to 30 min generally), however it is singled threaded.
- **Copy plan** should not take long time (1 min approximately)
- **Auto firming** usually takes 30 minutes and could take up to multiple hours, depending on the number of orders and complexity of the items 
- **Auto firming**: check that is takes less time than "Coverage"
- **Coverage**: should take the longest running time, relative to the rest. 
- **Action** and **Future message** can take long depending on data and number of BOMs. 


## Filtering
Using filters in the Master Planning run dialog affects the duration of the master planning run. Particularly, to exclude items from the Master Planning run it is recommended to filter by the lifecycle state of the item (and not by item numbers). When filtering by lifecycle state the "Update" process will take shorter than when filtering by item numbers.  


## Performance checklist summary
- **Number of threads**: set to higher than zero
- **Number of orders in firming bundle**: set to higher than zero (follow formulas above)
- **Use of cache**: set to Maximum, unless low on memory
- **Number of helpers in helper task bundle**: set to higher than zero (follow formulas above)
- **Actions and futures**: disable if you do not use them
- **Time fences**: adjust to your business needs
- **One heavy routine at a time**: do not run MRP with any other heavy routine
- **Review session log**
- **Filtering of items**: use the lifecycle state to exclude items from the master planning run (do not use the item numbers). 
