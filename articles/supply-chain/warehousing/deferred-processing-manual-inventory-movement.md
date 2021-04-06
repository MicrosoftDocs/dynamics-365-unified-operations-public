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

This topic describes the functionality that makes deferred processing of inventory movement warehouse work available in  Dynamics 365 Supply Chain Management.

The deferred processing functionality was introduced first in the 2019 release wave 2, it lets warehouse workers continue to do other work while the put operation is processed in the background. Deferred processing is useful when the server can have ad-hoc or unplanned increases in processing time, and the increased processing time might affect the user's productivity. Now, the Inventory movement work order type has been added to work order types supported by this feature.

Background processing is achieved by using the [Process warehouse app events feature](warehouse-app-events.md).

## Turn on this feature for your system

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. *Organization-wide work blocking*
1. *Process warehouse app events*
1. *Deferred put operations*
1. *Deferred processing of manual inventory movement operation*

## Configuring the work processing policies

To use deferred processing, you must configure and use a work processing policy. For deferred put-processing, the work order types supported by the [Deferred processing of warehouse work](deferred-put.md) feature are: *Sales order*, *Transfer order issue*, and *Replenishment*. The following work order type was added: *Inventory movement*.

Policies are configured on the **Work processing policies** page. The following table describes the fields on that page.

| Field                           | Description |
|---------------------------------|-------------|
| Work processing policy name     | The name of the work processing policy. |
| Work order type                 | The work order type that the policy is applied to. |
| Operation                       | The operation that is processed by using the policy. The new work order type does not require to select the value in the **Operation** field, as both pick and put operations are processed as a single event.|
| Work processing method          | The method that is used to process the work line. If the method is set to **Immediate**, the behavior resembles the behavior when no work processing policies are used to process the line. If the method is set to **Deferred**, deferred processing that uses the batch framework is used. |
| Deferred processing threshold   | A value of **0** (zero) indicates that there is no threshold. In this case, deferred processing is used if it can be used. If the specific threshold calculation is below the threshold, the Immediate method is used. Otherwise, the Deferred method is used if it can be used. For sales and transfer-related work, the threshold is calculated as the number of associated source load lines that are being processed for the work. For replenishment work, the threshold is calculated as the number of work lines that are being replenished by the work. By setting a threshold of, for example, **5** for sales, smaller works that have fewer than five initial source load lines won't use deferred processing, but larger works will use it. The threshold has an effect only if the work processing method is set to **Deferred**. |
| Deferred processing batch group |The batch group that is used for processing. The new work order type does not require to select the value in the **Deferred processing batch group** field, because it is selected in the **Process warehouse app events** dialog|

## Assigning the work creation policy

See the [Deferred processing of warehouse work](deferred-put.md) feature for details.

## Set up a batch job to process warehouse app events

To use the new deferred processing of manual inventory movement operation process, you must set up a scheduled batch job at **Warehouse management > Periodic tasks > Process warehouse app events**.

You need to enable **Batch processing** and select **Recurrence** to process the events based on the interval needed for your business. 

## Inquire the warehouse app events

You can view the event queue and events messages generated by the warehouse app by going to **Warehouse management > Inquiries and reports > Mobile device logs > Warehouse app events**.

The *Inventory movement* event messages will receive the status *Queued* right after creation, which means that the **Process warehouse app events** batch job will now pick up and process the event messages. When the *Inventory movement* status is updated to *Completed*, all the related events are deleted from the queue.

All of the *Inventory movement* events are accumulated under one collection per event type and warehouse.

Because the **Warehouse app events** will be processed by the batch job according to its recurrence set in the batch dialog, you will need to look up the warehouse ID by the **Identifier** field before the message is processed. The **Identifier** field is in the header of the **Warehouse app events** page.

The details of the message contain the details of the movement (**From** and **To** locations etc.)

For more information, see the [Warehouse app event processing](warehouse-app-events.md).

## Configuring the mobile device menu to skip the deferred processing policy

See the [Deferred processing of warehouse work](deferred-put.md) feature for details.

## Impact on closed work dates

See the [Deferred processing of warehouse work](deferred-put.md) feature for details.

## Additional resources

- [Deferred processing of warehouse work](deferred-put.md)
- [Warehouse app event processing](warehouse-app-events.md)
- [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]