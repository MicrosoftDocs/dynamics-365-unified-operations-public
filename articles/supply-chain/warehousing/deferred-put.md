---
# required metadata

title: Deferred processing of warehouse work
description: This topic describes the functionality that allows deferred processing of warehouse work put operations in Dynamics 365 for Finance and Operations.
author: josaw1
manager: AnnBe
ms.date: 06/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-6-31
ms.dyn365.ops.version: 10.0.5

---

# Deferred processing of warehouse work

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/pivate-preview-banner.md)]

This topic describes the functionality that enables deferred processing of warehouse work put operations in Dynamics 365 for Finance and Operations.

Deferred processing functionality allows warehouse workers to continue with other work while the put operation is processed in the background. Deferred processing is useful when a large number of work lines needs to be processed and the worker can let that work process asynchronously, or when the server can have ad-hoc or unplanned increases of processing time that would have a negative impact on the user's productivity.

Background processing is achieved by using the SysOperation framework. For more information, see [SysOperation Framework Overview](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/sysoperation-framework-overview).

## Configuration of the work processing policies

To use the deferred processing, a work processing policy must be configured and used.

Policies are configured on the **Work processing policy** page.

| **Option**                      | **Description**           |
|---------------------------------|--------------------------------------------------------------|
| Work processing policy name     | The name of the work processing policy.                      |
| Work order type                 | The work order type for which the policy will be applied to.                             |
| Operation                       | The operation that is processed using the policy.                                               |
| Work processing method          | The method used to process the work line. If Immediate processing is used the behavior will be similar to processing the line without using work processing policies. If the method is set to Deferred the deferred processing using the batch framework will be used.                                                                |
| Deferred processing threshold   | If the threshold is set to zero it will be interpreted as no threshold and the deferred processing will be used if possible. If the specific threshold calculation is below the threshold the immediate method will be used; otherwise, the deferred method will be used if possible. For Sales and Transfer related work the threshold is calculated as the number of associated source load lines that is being processed for the work. For replenishment work the threshold is calculated as the number of work lines that are being replenished by the work. By setting a threshold of e.g. 5 for sales, small works with less than 5 initial source load lines will not use deferred processing but larger works will. If the processing method is not Deferred the threshold will not have any impact. |
| Deferred processing batch group | The batch group that will be used for processing.                                            |

## Assigning the work creation policy

The work creation policy can be assigned at the warehouse management parameters as well as at the individual warehouses. If the policy is assigned to the warehouse, it will be applied for work created for that warehouse. If no policy is set at the warehouse level, the policy from the warehouse management parameters will be applied.

## Viewing the deferred put processing tasks

The deferred put processing tasks can be viewed on the **Deferred put processing tasks** page.

By default, the **Completed tasks** are  shown.

| **Field**        | **Description**    |
|------------------|--------------|
| Status           | The status of the task.    |
| Batch job status | The status of the related batch job. If the batch job has been processed the Batch history will contain the log and information from the batch job. |

-   Awaiting: The related batch job is awaiting processing on the batch server.

-   Failed: The processing failed. Either task can be reprocessed by using the action **Process deferred put**, or the task can be canceled by using the action **Cancel deferred put**.

-   Completed: The job completed.

## Impact on closed work dates

When using deferred put processing, the closed work date is set as the created date/time value of the deferred put processing tasks, since this is the best estimate for when the put operation completed.

## Reprocessing a failed task

A failed task can be processed by selecting it on the page and clicking **Process deferred put**. Reprocessing corresponds to the user completing the put-away from the mobile device as if it was set to immediate processing.

## Cancelling failed tasks

Only failed tasks can be cancelled. When cancelling, a task can be assigned to a new user or remain assigned to the user that processed the work. The cancel action corresponds to bringing back the work to the mobile device as if the last pick step has just completed and the work needs to be put-away. However, the user will have an indication that the work is "different", as the work will contain only a put-away step with a location corresponding to the location the first user that processed the work had as a final put location.

When the task is cancelled, the work is no longer blocked by the deferred put processing blocking reason and it can be reprocessed using the mobile device. The task record is deleted when it is cancelled.

## Configuring the mobile device menu to skip the deferred processing policy

The mobile device menu item can be configured so the deferred processing policy is not used and the work is processed like it would have been when no deferred processing policy was used. This is done by setting the **Deferred put processing policy** to **Override settings and process put synchronously.** This functionality enables a supervisor to use a specific menu item where the deferred put is not used.

## Restrictions when the deferred put processing is not applied

There are multiple scenarios where the deferred put processing will not be applied although the policy is configured. Some examples are listed below.

-   Manual work completion is used.

-   The work is completed using auto-completion.

-   Audit templates are used.

-   The work uses containers.

## Monitoring the deferred processing tasks from the Outbound work monitoring workspace

The **Outbound work monitoring** workspace has two tiles that help you monitor deferred put processing tasks.

The **Failed deferred put processing tasks** tile shows the number of failed tasks. If there are failed tasks, they must either be reprocessed or cancelled by the warehouse manager since they will not be reprocessed automatically.

The **Awaiting deferred put processing tasks** tile shows the number of tasks that have been in the awaiting state for more than 10 minutes. If the tile is populated, it may indicate a problem with the batch processing. It is possible to manually process the awaiting tasks. If the batch job for the task is processed afterwards it will simply fail because the task is already processed, and there will be no impact.

## Deleting completed tasks

Deferred put processing tasks that are completed can be deleted by multiselecting them and deleting them on the page.
