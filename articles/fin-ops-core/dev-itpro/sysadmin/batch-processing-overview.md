---
# required metadata

title: Batch processing overview
description: This article provides an overview of batch processing.
author: Peakerbl
ms.date: 07/23/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Batch processing overview

[!include [banner](../includes/banner.md)]

This article provides an overview of batch processing.

Many tasks in finance and operations can be run as part of batch jobs. For example, batch jobs can include tasks for printing reports, performing maintenance, or sending electronic documents. By using batch jobs, you can avoid slowing down your computer or the server during typical working hours. 

The tasks in a batch job can run either sequentially or at the same time. Additionally, you can create dependencies between tasks. In other words, the sequence of tasks can differ, depending on whether an earlier task succeeds or fails. 

You can set up recurrence patterns for batch jobs. For example, you can set up a job to process invoices automatically at the end of every month. 

To monitor batch jobs, you can set up alerts. Alerts can be sent when the batch job succeeds, fails, or has finished running. 

After a batch job has been processed, you can view the history. The history includes any messages that were encountered while the job was running. 

Use batch groups to categorize batch tasks and run them on specific servers. The servers in your environment might have different software installed, or they might be available at different times of the day. Batch groups are used to direct batch tasks to the most appropriate server. Tasks in the same batch job can belong to different batch groups. 

For example, server A is set up to print reports, and server B is set up to send electronic documents. You can use batch groups to make sure that reporting tasks are run on server A and electronic documents are processed by server B.

For more information, see [Batch processing and batch servers](batch-server-overview.md).


## Batch functions

Administrators and Batch managers can perform common tasks including creating and copying batch jobs, changing a batch job user, and specifying a time period in which a job should not execute. For more information about these tasks, see the following topics:

-  [Create a batch job](tasks/create-batch-job.md)
-  [Batch manager security role](runby.md)
-  [Active batch periods](activeperiod.md)
-  [Copy a batch job](copy-batch-job.md)
-  [Set up alerts](alerts.md)
-  [Enhanced batch forms](enhanced-forms.md)
-  [Clean up the batch job history](batch-history-cleanup.md)
-  [Abort an executing batch job](batch-abort.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
