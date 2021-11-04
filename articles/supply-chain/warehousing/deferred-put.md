---
# required metadata

title: Deferred processing of warehouse work
description: This topic describes the functionality that makes deferred processing of warehouse work put operations available in  Dynamics 365 Supply Chain Management.
author: Mirzaab
ms.date: 11/18/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form: WHSWorkProcessingPolicy, WHSWorkDeferredPutProcessingTask
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2019-6-31
ms.dyn365.ops.version: 10.0.5

---

# Deferred processing of warehouse work

[!include [banner](../includes/banner.md)]

This topic describes the functionality that makes deferred processing of put operations for warehouse work available in Dynamics 365 Supply Chain Management.

The deferred processing functionality lets warehouse workers continue to do other work while the put operation is processed in the background. Deferred processing is useful when many work lines must be processed and the worker can let that work be processed asynchronously. It's also useful when the server can have ad-hoc or unplanned increases in processing time, and the increased processing time might affect the user's productivity.

Background processing is achieved by using the SysOperation framework. For more information, see [SysOperation Framework Overview](/dynamicsax-2012/developer/sysoperation-framework-overview).

## Configuring the work processing policies

To use deferred processing, you must configure and use a work processing policy.

Policies are configured on the **Work processing policies** page. The following table describes the fields on that page.

| Field                           | Description |
|---------------------------------|-------------|
| Work processing policy name     | The name of the work processing policy. |
| Work order type                 | The work order type that the policy is applied to. |
| Operation                       | The operation that is processed by using the policy. |
| Work processing method          | The method that is used to process the work line. If the method is set to **Immediate**, the behavior resembles the behavior when no work processing policies are used to process the line. If the method is set to **Deferred**, deferred processing that uses the batch framework is used. |
| Deferred processing threshold   | A value of **0** (zero) indicates that there is no threshold. In this case, deferred processing is used if it can be used. If the specific threshold calculation is below the threshold, the Immediate method is used. Otherwise, the Deferred method is used if it can be used. For sales and transfer-related work, the threshold is calculated as the number of associated source load lines that are being processed for the work. For replenishment work, the threshold is calculated as the number of work lines that are being replenished by the work. By setting a threshold of, for example, **5** for sales, smaller works that have fewer than five initial source load lines won't use deferred processing, but larger works will use it. The threshold has an effect only if the work processing method is set to **Deferred**. |
| Deferred processing batch group |The batch group that is used for processing. |

For deferred put-processing, the following work order types are supported: sales order, transfer order issue, and replenishment.

## Assigning the work creation policy

The work creation policy can be assigned in the warehouse management parameters. It can also be assigned at the level of individual warehouses. If the policy is assigned to a warehouse, it's applied only to work that is created for that warehouse. If no policy is assigned at the warehouse level, the policy from the warehouse management parameters is applied.

## Viewing the deferred put processing tasks

You can view deferred put processing tasks on the **Deferred put processing tasks** page.

By default, the **Completed** tasks are shown.

| Field            | Description |
|------------------|-------------|
| Status           | The status of the task. |
| Batch job status | The status of the related batch job. If the batch job has been processed, the batch history contains the log and information from the batch job. |

Here is an explanation of the possible statuses:

- **Awaiting** – The related batch job is awaiting processing on the batch server.
- **Failed** – The processing failed. The task can be reprocessed by using the **Process deferred put** action, or it can be canceled by using the **Cancel deferred put** action.
- **Completed** – The job was completed.

## Impact on closed work dates

When deferred put processing is used, the closed work date is set as the created date/time of the deferred put processing tasks. The closed work date is used because it's the best estimate for when the put operation was completed.

## Reprocessing a failed task

You can reprocess a failed task by selecting it on the page and then selecting **Process deferred put**. Reprocessing corresponds to a situation where the user completes the put-away from the mobile device as if it was set for immediate processing.

## Canceling failed tasks

Only failed tasks can be canceled. When you cancel a task, you can assign it to a new user. Alternatively, the task can remain assigned to the user who processed the work. Cancellation corresponds to a situation where the work is brought back to the mobile device as if the last pick step was just completed and the work must be put away. However, the user will be able to determine that the work is "different," because it will have only a put-away step, and the location will correspond to the location that the first user who processed the work had as a final put location.

When a task is canceled, the work is no longer blocked by the deferred put processing blocking reason. It can be reprocessed by using the mobile device.

The task record is deleted when the task canceled.

## Configuring the mobile device menu to skip the deferred processing policy

You can configure the mobile device menu item so that the deferred processing policy isn't used. The work is then processed as it is when no deferred processing policy is used. This functionality lets a supervisor use a specific menu item where deferred put isn't used. To configure it, set the **Deferred put processing policy** field to **Override settings and process put synchronously**. 

## Restrictions when the deferred put processing isn't applied

There are several scenarios where deferred put processing isn't applied even though the policy is configured. Here are some examples:

- Manual work completion is used.
- The work is completed by using auto-completion.
- Audit templates are used.


## Monitoring the deferred processing tasks from the Outbound work monitoring workspace

The **Outbound work monitoring** workspace has two tiles that help you monitor deferred put processing tasks:

- **Failed deferred put processing tasks** – This tile shows the number of failed tasks. If there are failed tasks, the warehouse manager must either reprocess them or cancel them, because they won't be reprocessed automatically.
- **Awaiting deferred put processing tasks** – This tile shows the number of tasks that have been in the **Awaiting** status for more than 10 minutes. If the tile shows a number, it might indicate that an issue occurred during batch processing. You can manually process the **Awaiting** tasks. If the batch job for a task is processed later, it will just fail, because it has already been processed. There will be no impact.

## Deleting completed tasks

You can delete deferred put processing tasks that have been completed by selecting them and deleting them on the page.

## Additional resources

- [Deferred processing of manual inventory movement operation](deferred-processing-manual-inventory-movement.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]