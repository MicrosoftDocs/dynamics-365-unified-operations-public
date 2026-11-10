---
title: Deferred processing of warehouse work
description: Learn about the functionality that makes deferred processing of warehouse work put operations available in  Dynamics 365 Supply Chain Management.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 11/10/2026
ms.custom:
ms.reviewer: kamaybac 
ms.search.form: WHSWorkProcessingPolicy, WHSWorkDeferredPutProcessingTask
---

# Deferred processing of warehouse work

[!INCLUDE [banner](../includes/banner.md)]

This article describes the functionality that makes deferred processing of put operations for warehouse work available in Dynamics 365 Supply Chain Management.

The deferred processing functionality lets warehouse workers continue to do other work while the put operation processes in the background. Deferred processing is useful when many work lines require processing and the worker can let that work be processed asynchronously. It's also useful when the server can have ad hoc or unplanned increases in processing time, and the increased processing time might affect the user's productivity.

Background processing uses the SysOperation framework. Learn more in [SysOperation Framework Overview](/dynamicsax-2012/developer/sysoperation-framework-overview).

## Configuring the work processing policies

To use deferred processing, configure and use a work processing policy.

Configure policies on the **Work processing policies** page. The following table describes the fields on that page.

| Field                           | Description |
|---------------------------------|-------------|
| Work processing policy name     | The name of the work processing policy. |
| Work order type                 | The work order type that the policy applies to. |
| Operation                       | The operation that the policy processes. |
| Work processing method          | The method that processes the work line. If you set the method to *Immediate*, the behavior resembles the behavior when no work processing policies are used to process the line. If you set the method to *Deferred*, the batch framework processes deferred processing. |
| Deferred processing threshold   | A value of *0* (zero) indicates that there's no threshold. In this case, deferred processing is used if it can be used. If the specific threshold calculation is below the threshold, the *Immediate* method is used. Otherwise, the *Deferred* method is used if it can be used. For sales and transfer-related work, the threshold is calculated as the number of associated source load lines that are processing for the work. For replenishment work, the threshold is calculated as the number of work lines that the work replenishes. For sorted inventory picking work, the threshold is calculated as the number of work inventory transactions for the final put line of the work. By setting a threshold of, for example, *5* for sales, smaller works that have fewer than five initial source load lines don't use deferred processing, but larger works use it. The threshold has an effect only if the work processing method is set to *Deferred*. |
| Deferred processing batch group |The batch group that is used for processing. |

For deferred put-processing, the following work order types are supported: sales order, transfer order issue, replenishment, sorted inventory picking, and packed container picking. Deferred put-processing for sorted inventory picking work requires Supply Chain Management version 10.0.32 or higher. Deferred put-processing for packed container picking work requires Supply Chain Management version 10.0.45 or higher.

## Assigning the work creation policy

You can assign the work creation policy globally on the **Warehouse management parameters** page or individually at the warehouse level. If you assign the policy to a warehouse, it applies only to work that you create for that warehouse. If you don't assign a policy at the warehouse level, the system applies the policy from the warehouse management parameters.

## Viewing the deferred put processing tasks

View deferred put processing tasks on the **Deferred put processing tasks** page. The page lists *Completed* tasks by default.

| Field            | Description |
|------------------|-------------|
| Status           | The status of the task. |
| Batch job status | The status of the related batch job. The batch history contains the log and information about processed batch job. |

The following list explains the possible statuses:

- *Awaiting* – The related batch job is awaiting processing on the batch server.
- *Failed* – The processing failed. Use the **Process deferred put** action to reprocess the task, or use the **Cancel deferred put** action to cancel it.
- *Completed* – The job is completed.

## Impact on closed work dates

When you use deferred put processing, the system sets the closed work date as the created date and time of the deferred put processing tasks. The system uses the closed work date because it's the best estimate for when the put operation was completed.

## Reprocessing a failed task

You can reprocess a failed task by selecting it on the page and then selecting **Process deferred put**. Reprocessing corresponds to a situation where you complete the putaway from the mobile device as if you set it for immediate processing.

## Canceling failed tasks

You can cancel only failed tasks. When you cancel a task, you can assign it to a new user or keep it assigned to the user who processed the work. Cancellation brings the work back to the mobile device as if the last pick step was just completed and the work must be put away. However, the user can determine that the work is "different," because it has only a put-away step, and the location corresponds to the location that the first user who processed the work had as a final put location.

When you cancel a task, the work is no longer blocked by the deferred put processing blocking reason. You can reprocess it by using the mobile device.

The system deletes the task record when you cancel the task.

## Configuring the mobile device menu to skip the deferred processing policy

You can configure the mobile device menu item so that the deferred processing policy isn't used. The work then processes as it does when no deferred processing policy is used. This functionality lets a supervisor use a specific menu item where deferred put isn't used. To configure it, set the **Deferred put processing policy** field to *Override settings and process put synchronously*.

## Restrictions when the deferred put processing isn't applied

Several scenarios exist where deferred put processing isn't applied even though the policy is configured. Here are some examples:

- Manual work completion is used.
- The work is completed by using auto-completion.
- Audit templates are used.

## Monitoring the deferred processing tasks from the Outbound work monitoring workspace

The **Outbound work monitoring** workspace has two tiles that help you monitor deferred put processing tasks:

- **Failed deferred put processing tasks** – This tile shows the number of failed tasks. If there are failed tasks, the warehouse manager must either reprocess them or cancel them, because they aren't reprocessed automatically.
- **Awaiting deferred put processing tasks** – This tile shows the number of tasks that have been in the *Awaiting* status for more than 10 minutes. If the tile shows a number, it might indicate that an issue occurred during batch processing. You can manually process the *Awaiting* tasks. If the batch job for a task is processed later, it fails, because it was already processed. There is no impact.

## Deleting completed tasks

You can delete deferred put processing tasks that are complete by selecting them and choosing **Delete**.

## Related information

- [Deferred processing of manual inventory movement operation](deferred-processing-manual-inventory-movement.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
