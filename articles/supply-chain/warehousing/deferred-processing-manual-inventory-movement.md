---
title: Deferred processing of manual inventory movement
description: This article describes how to use deferred processing of manual inventory movement in Microsoft Dynamics 365 Supply Chain Management.
author: Mirzaab
ms.date: 08/09/2022
ms.topic: article
ms.search.form: WHSWorkProcessingPolicy, WHSWorkDeferredPutProcessingTask
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-04-27
ms.dyn365.ops.version: 10.0.17
---

# Deferred processing of manual inventory movement

[!include [banner](../includes/banner.md)]

This article describes how to use deferred processing of manual inventory movement in Microsoft Dynamics 365 Supply Chain Management.

Deferred processing lets warehouse workers continue to do other work while a put operation is processed in the background. Deferred processing is useful when the server can have occasional or unplanned increases in processing time, and the increased processing time might affect worker productivity. The *Inventory movement* work type has now been added to the set of work types that this feature supports.

Background processing is achieved by using the [Process warehouse app events feature](warehouse-app-events.md).

## Turn on this feature for your system

To make this feature available, turn on the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). You must turn them on in this order:

1. *Organization-wide work blocking*<br>(As of Supply Chain Management version 10.0.21, this feature is mandatory and can't be turned off.)
1. *Process warehouse app events*<br>(As of Supply Chain Management version 10.0.25, this feature is turned on by default. As of Supply Chain Management version 10.0.29, this feature is mandatory and can't be turned off.)
1. *Deferred put operations*<br>(As of Supply Chain Management version 10.0.29, this feature is mandatory and can't be turned off.)
1. *Deferred processing of manual inventory movement operation*<br>(As of Supply Chain Management version 10.0.25, this feature is mandatory and can't be turned off.)

## Configure the work processing policies

To use deferred processing, you must set up and use a work processing policy. For deferred put processing, the [Deferred processing of warehouse work feature](deferred-put.md) supports the following work types: *Sales order*, *Transfer order issue*, and *Replenishment*. The *Deferred processing of manual inventory movement operation* features adds a new work type: *Inventory movement*.

To set up a work processing policy, follow these steps.

1. Go to **Warehouse management \> Setup \> Work \> Work processing policies**.
1. Either select an existing policy in the list, or create a new policy by selecting **New** on the Action Pane. The header of every policy has the following fields:

    - **Work processing policy name** – The name of the work processing policy.
    - **Description** – A description of the work processing policy.

1. On the **Processing rules** FastTab, set up the collection of rules that the policy will apply. Use the buttons on the toolbar to add or remove rules as you require. For each rule, set the following fields:

    - **Work order type** – Select the work type that the policy applies to.
    - **Operation** – Select the operation that the policy is used to process. If you selected *Inventory movement* in the **Work order type** field, you don't have to set this field, because both pick operations and put operations are processed as a single event.
    - **Work processing method** – Select the method that is used to process the work line. If you select *Immediate*, the behavior resembles the behavior when no work processing policies are used to process the line. If you select *Deferred*, the system will apply deferred processing that uses the batch framework.
    - **Deferred processing threshold** – If you set this field to *0* (zero), there is no threshold. In this case, the *Deferred* processing method is used if possible. If the specific threshold calculation is below the threshold, the *Immediate* method is used. Otherwise, the *Deferred* method is used if possible. For sales and transfer-related work, the threshold is calculated as the number of associated source load lines that are being processed for the work. For replenishment work, the threshold is calculated as the number of work lines that are being replenished by the work. By setting a threshold of, for example, *5* for sales, you ensure that smaller works that have fewer than five initial source load lines won't use deferred processing, but larger works will use it. The threshold has an effect only if the **Work processing method** field is set to *Deferred*.
    - **Deferred processing batch group** – Specify the batch group that is used for processing. If you selected *Inventory movement* in the **Work order type** field, you don't have to set this field, because the batch group is selected in the **Process warehouse app events** dialog box.

## Assign the work creation policy

For details about how to assign a work creation policy, see [Deferred processing of warehouse work](deferred-put.md).

## Set up a batch job to process warehouse app events

To use the *Deferred processing of manual inventory movement operation* process, set up a scheduled batch job.

1. Go to **Warehouse management \> Periodic tasks \> Process warehouse app events**.
1. In the **Process warehouse app events** dialog box, on the **Run in background** FastTab, set the **Batch processing** option to *Yes*.
1. Select **Recurrence**, and set up a run schedule that meets the requirements of your business.
1. Select **OK** in each dialog box.

## Inquire about the warehouse app events

You can view the event queue and event messages that the warehouse app generates by going to **Warehouse management \> Enquiries and reports \> Mobile device logs \> Warehouse app events**.

The *Inventory movement* event messages will have a status of *Queued* when they are first created. This status indicates that the **Process warehouse app events** batch job will pick up the event messages and process them. When the status is updated to *Completed*, all the related events are deleted from the queue.

All the *Inventory movement* events are accumulated under one collection per event type and warehouse.

The batch job will process the warehouse app events according to the recurrence that is set up in the **Process warehouse app events** dialog box. Therefore, until a message is processed, you can find the warehouse ID by looking in the **Identifier** field.

The details of the message contain the details of the movement (for example, the "from" and "to" locations).

For more information, see [Warehouse app event processing](warehouse-app-events.md).

## Configure the mobile device menu to skip the deferred processing policy

For details about how to configure the mobile device menu to skip the deferred processing policy, see [Deferred processing of warehouse work](deferred-put.md).

## Impact on closed work dates

For details about the impact on closed work dates, see [Deferred processing of warehouse work](deferred-put.md).

## Additional resources

- [Deferred processing of warehouse work](deferred-put.md)
- [Warehouse app event processing](warehouse-app-events.md)
- [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
