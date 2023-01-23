---
title: Message processor messages for warehouse management processes
description: This topic provides information about the Message processor messages feature for warehouse management.
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

Message processor messages are used for processes that run asynchronously. For example, you could use a message processor message to post a sales packing slip when closing the last shipment container as part of a [manual packing process](packing-containers.md).

## Example message type: Run packing slip for container

For example, the **Message type** *Run packing slip for container* is used to create and post a sales packing slip when a warehouse worker closes the last container in a shipment. The message will get inserted with a *Queued* message state, waiting to get picked up by the **Message processor** batch job.

## View the message log, message content, and details

You can view the messages processed by the message processor by going to **System administration > Message processor > Message processor messages**. For information about how to use this page to review messages, find and fix failed messages, and more, see [Message processor messages page](../supply-chain-dev/message-processor.md#message-processor-page)

## Message processor batch job

You should schedule a periodic batch job to process the messages by going to **System administration > Message  processor > Message processor**. In this dialog, you must select a **Message queue** (such as *Warehouse*), and specify a processing interval. For details, see [Schedule message processing by using the message processor batch job](../supply-chain-dev/message-processor.md#processor-batch-job)

## Set up business events to deliver alerts for failed processing results

In addition to using the **Message processor messages** page, where you can filter on the **Message state** value *Failed* to inquire for failed messages, you can set up [Business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to alert you about failed processing results. See also [Set up business events to deliver alerts for failed processing results](../supply-chain-dev/message-processor.md#business-events).
