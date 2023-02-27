---
title: Message processor messages for warehouse management processes
description: This article provides information about the Message processor messages feature for warehouse management.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: SysMessageProcessor, SysMessageProcessorMessage, BusinessEventsWorkspace 
ms.topic: how-to
ms.date: 01/30/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Message processor messages for warehouse management processes

[!include [banner](../includes/banner.md)]

Message processor messages are used for processes that run asynchronously. For example, you can use a message processor message to post a sales packing slip when the last shipment container is closed as part of a [manual packing process](packing-containers.md).

## Example message type: Run packing slip for container

For example, the *Run packing slip for container* message type is used to create and post a sales packing slip when a warehouse worker closes the last container in a shipment. The message that's inserted will be in a *Queued* message state. This state indicates that the message is waiting to be picked up by the **Message processor** batch job.

## View the message log, message content, and details

To view the messages that are processed by the message processor, go to **System administration \> Message processor \> Message processor messages**. For information about how to use the **Message processor messages** page to review messages, find and fix failed messages, and more, see [Message processor messages page](../supply-chain-dev/message-processor.md#message-processor-page).

## Message processor batch job

You should schedule a periodic batch job to process the messages, by going to **System administration \> Message processor \> Message processor**. In the dialog box that appears, you must select a value in the **Message queue** field (for example, *Warehouse*), and you must specify a processing interval. For more information, see [Schedule message processing by using the message processor batch job](../supply-chain-dev/message-processor.md#processor-batch-job).

## Set up business events to deliver alerts for failed processing results

On the **Message processor messages** page, you can filter on the  *Failed* value of the **Message state** field to inquire about failed messages. In addition, you can set up [business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to alert you about failed processing results. For more information, see [Set up business events to deliver alerts for failed processing results](../supply-chain-dev/message-processor.md#business-events).
