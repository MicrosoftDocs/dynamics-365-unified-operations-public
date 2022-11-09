---
# required metadata

title: Message processor messages for warehouse management processes
description: This topic provides information about the Message processor messages feature for warehouse management.
author: perlynne
manager: 
ms.date: 08/11/2022
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SysMessageProcessor, SysMessageProcessorMessage, BusinessEventsWorkspace   
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: perlynne
ms.search.validFrom: 2023-01-30
ms.dyn365.ops.version: 10.0.32
---

# Message processor messages for warehouse management processes

[!include [banner](../includes/banner.md)]

Message processor messages are used when running asynchronously processes, for example this can be used to post the sales packing slip when closing the last shipment container as part of a [manual packing process](packing-containers.md).

You can view the messages processed by the message processor by going to **System administration > Message processor > Message processor messages**.

## Message grid columns and filters

You can use the fields at the top of the **Message processor messages** page to help find any particular messages you are looking for. Most of these filters match the column headings in the message grid. The following filters and column headings are available:

- **Message type** – Specifies the type of message.
- **Message queue** – Specifies the name of the queue in which the message is to be processed. For the warehouse management specific messages this value will be *Warehouse*.
- **Message state** – Specifies the state of the message. The following states exists:
  - *Queued* – The message is ready to be processed by the message processor.
  - *Processed* – The message was successfully processed by the message processor.
  - *Canceled* – The message was canceled.
  - *Failed* - The message failed.
- **Message content** – This filter does a full-text search of message content. (Message content is not shown in the grid.) The filter treats most special symbols (such as "-") as spaces, and treats all space characters as Boolean OR operators. T=For example, this means if you search for a specific `ContainerId` value equal "CONT-000000054", the system will find all messages that contain "CONT" or "000000054", which is likely to be a long list. Therefore, it would be better to enter just "000000054" alone because that will return more specific results.

## Example message type: Run packing slip for container

For example, the **Message type** *Run packing slip for container* is used to create and post a sales packing slip when a warehouse worker closes the last container in a shipment. The message will get inserted with a *Queued* message state, waiting to get picked up by the **Message processor** batch job.

## View the message log, message content, and details
You can find detailed information about a message by selecting it in the grid and then opening the **Log** or **Message content** tabs under the message grid, where each processing event is shown.

The **Message content** depends on the **Message type** and will therefore have different text length. A typical message content text will start with a **{** and end with a **}** and in between have field names such as `ContainerId` followed by a **:** and a value such as *CONT-00000005*.

The toolbar on the **Log** tab includes the following buttons:

- **Log** – Displays the processing results. This is especially helpful for understanding the reasons for a processing failure for messages having a **Processing result** of *Failed*.
- **Bundle** – Multiple message processing operations can run as part of the same batch process. Select this button to view this detailed data. For example, you can see whether dependencies exist that require the system to process certain messages in a specific sequence.

## Message processor batch job
You should schedule a periodic running batch job to process the messages by going to **System administration > Message  processor > Message processor**.
In this dialog you select the *Message queue* like e.g. *Warehouse* and the processing interval for the *Batch processing* as part of the setup in the *Run in background* section.

## Manually process or cancel a message
If needed, you can manually process or cancel a message, depending on its current state. To do so, select the message in the grid and then select **Process** or **Cancel** on the Action Pane

## Set up business events to deliver alerts for failed processing results
In addition to filtering on the **Message state** value *Failed* to inquire for failed messages, you can set up [Business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to alert you about failed processing results. To do so, activate the Business event ID *SysMessageProcessorMessageProcessedBusinessEvent* named *Message processor message processed* on the **Business events catalog** page (**System administration > Setup > Business events > Business events catalog**).
