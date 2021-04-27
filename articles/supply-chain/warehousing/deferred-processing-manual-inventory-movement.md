---
# required metadata

title: Deferred processing of manual inventory movement operation
description: This topic describes the functionality that makes deferred processing of inventory movement warehouse work available in  Dynamics 365 Supply Chain Management.
author: Mirzaab
ms.date: 04/06/2021
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
ms.author: Mirzaab
ms.search.validFrom: 2021-4-30
ms.dyn365.ops.version: 10.0.17

---

# Deferred processing of manual inventory movement operation

[!include [banner](../includes/banner.md)]

This topic describes the functionality that makes deferred processing of manual inventory movement warehouse work available in Dynamics 365 Supply Chain Management.

Deferred processing lets warehouse workers continue to do other work while a put operation is processed in the background. Deferred processing is useful when the server can have ad-hoc or unplanned increases in processing time, and the increased processing time might affect workers' productivity. The *Inventory movement* work type has been added to the work types supported by this feature.

Background processing is achieved using the [Process warehouse app events feature](warehouse-app-events.md).

## Turn on this feature for your system

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. *Organization-wide work blocking*
1. *Process warehouse app events*
1. *Deferred put operations*
1. *Deferred processing of manual inventory movement operation*

## Configuring the work processing policies

To use deferred processing, you must set up and use a work processing policy. For deferred put-processing, the work types supported by the [Deferred processing of warehouse work](deferred-put.md) feature are: *Sales order*, *Transfer order issue*, and *Replenishment*. The *Deferred processing of manual inventory movement operation* features adds a new work type: *Inventory movement*.

To set up a work processing policy:

1. Go to **Warehouse management \> Setup \> Work \> Work processing policies**.
1. Either select an existing policy from the list or create a new one by selected **New** on teh Action Pane. Each policy has the following settings in the header:

    - **Work processing policy name** – The name of the work processing policy.
    - **Description** – A description of the work processing policy.

1. On the **Processing rules** FastTab, set up the collection of rules to be applied by this policy. Use the buttons on the toolbar to add or remove rules as needed. Make the following settings for each rule:

    - **Work order type** – The work type that the policy is applied to.
    - **Operation** – The operation that is processed using the policy. The *Inventory movement* work type does not require a selection for the **Operation** field, as both pick and put operations are processed as a single event.
    - **Work processing method** – The method that is used to process the work line. If the method is set to *Immediate*, the behavior resembles the behavior when no work processing policies are used to process the line. If the method is set to *Deferred*, the system will apply deferred processing that uses the batch framework.
    - **Deferred processing threshold** – A value of *0* (zero) indicates that there is no threshold. In this case, deferred processing is used if possible. If the specific threshold calculation is below the threshold, the *Immediate* method is used. Otherwise, the *Deferred* method is used if possible. For sales and transfer-related work, the threshold is calculated as the number of associated source load lines that are being processed for the work. For replenishment work, the threshold is calculated as the number of work lines that are being replenished by the work. By setting a threshold of, for example *5* for sales, smaller works that have fewer than 5 initial source load lines won't use deferred processing, but larger works will use it. The threshold has an effect only if the **Work processing method** is set to *Deferred*.
    - **Deferred processing batch group** – The batch group that is used for processing. The *Inventory movement* work type does not require this field to be set because this is selected in the **Process warehouse app events** dialog box.

## Assign the work creation policy

For details about how to assign a work creation policy, see the [Deferred processing of warehouse work](deferred-put.md).

## Set up a batch job to process warehouse app events

To use the *Deferred processing of manual inventory movement operation* process, set up a scheduled batch job.

1. Go to **Warehouse management > Periodic tasks > Process warehouse app events**.
1. The **Process warehouse app events** dialog box opens. Expand the **Run in background** FastTab.
1. Set **Batch processing** to *Yes*.
1. Select **Recurrence** and set up a run schedule based on the interval needed for your business.
1. Select **OK** in each dialog box.

## Inquire the warehouse app events

You can view the event queue and events messages generated by the warehouse app by going to **Warehouse management > Inquiries and reports > Mobile device logs > Warehouse app events**.

The *Inventory movement* event messages will have a status of *Queued* right after creation, which means that the **Process warehouse app events** batch job will now pick up and process the event messages. When the *Inventory movement* status is updated to *Completed*, all the related events are deleted from the queue.

All of the *Inventory movement* events are accumulated under one collection per event type and warehouse.

Because the warehouse app events will be processed by the batch job according to its recurrence set in the **Process warehouse app events** dialog box, you can look up the warehouse ID by reading the **Identifier** field until the message is processed.

The details of the message contain the details of the movement (**From** and **To** locations etc.)

For more information, see the [Warehouse app event processing](warehouse-app-events.md).

## Configure the mobile device menu to skip the deferred processing policy

For details about how to configure the mobile device menu to skip the deferred processing policy, see [Deferred processing of warehouse work](deferred-put.md).

## Impact on closed work dates

For details about the impact on closed work dates, see [Deferred processing of warehouse work](deferred-put.md).

## Additional resources

- [Deferred processing of warehouse work](deferred-put.md)
- [Warehouse app event processing](warehouse-app-events.md)
- [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]