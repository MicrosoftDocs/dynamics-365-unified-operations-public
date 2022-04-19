---
# required metadata

title: Message processor messages
description: This topic provides information about the Message processor messages feature for scale unit workloads.
author: perlynne
ms.date: 04/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysMessageProcessorMessage, BusinessEventsWorkspace   
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
ms.search.validFrom: 2021-04-21
ms.dyn365.ops.version: 10.0.19
---

# Message processor messages

[!include [banner](../includes/banner.md)]

Message processor messages are used when running cloud and edge scale units for [manufacturing workloads](cloud-edge-workload-manufacturing.md) and [warehouse management workloads](cloud-edge-workload-warehousing.md).

The hub and scale unit deployment environments exchange a large amount of data to remain in sync. Some of the exchanged data will trigger additional logic in the *message processor*. You can view the messages that have been processed by the message processor by going to **System administration > Message processor > Message processor messages**.

## Message grid columns and filters

You can use the fields at the top of the **Message processor messages** page to help find any particular messages you are looking for. Most of these filters match the column headings in the message grid. The following filters and column headings are available:

- **Message type** – Specifies the type of message.
- **Message queue** – Specifies the name of the queue in which the message is to be processed. The following queues are provided:
  - *Scale unit to hub*
  - *Hub to warehouse execution scale unit*
  - *Hub to manufacturing execution scale unit*
- **Message state** – Specifies the state of the message. The following states exists:
  - *Queued* – The message is ready to be processed by the message processor.
  - *Processed* – The message was successfully processed by the message processor.
  - *Canceled* – The message was processed, but processing failed.
- **Message content** – This filter does a full-text search of message content. (Message content is not shown in the grid.) The filter treats most special symbols (such as "-") as spaces, and treats all space characters as Boolean OR operators. For example, this means if you search for a specific `journalid` value equal "USMF-123456", the system will find all messages that contain "USMF" or "123456", which is likely to be a long list. Therefore, it would be better to enter just "123456" alone because that will return more specific results.

## Example message type: Request inventory adjustment financial update

For example, the **Message type** *Request inventory adjustment financial update* is used to create and post a counting journal on the hub when a worker uses the warehouse app to [register an inventory adjustment](cloud-edge-warehouse-inventory-adjustment.md) on a scale unit warehouse management workload. Because this specific process originates from a scale unit, the **Message queue** field will show the value *Scale unit to hub*.

For this message type, a scale unit workload records the message as part of a warehouse app inventory adjustment operation. The message data is then transferred to the hub as part of the same process used for the [Commerce data exchange architecture](../../commerce/commerce-architecture.md). The message will be updated to show **Message state** as *Queued*. The message processor then attempts to process the message and updates the **Message state** to *Processed* on success, or *Canceled* on failure.

## View the message log, message content, and details

You can find detailed information about a message by selecting it in the grid and then opening the **Log** or **Message content** tabs under the message grid, where each processing event is shown.

The **Message content** depends on the **Message type** and will therefore have different text length. A typical message content text will start with a **{** and end with a **}** and in between have field names such as `journalId` followed by a **:** and a value such as *USMF-123456*.

The toolbar on the **Log** tab includes the following buttons:

- **Log** – Displays the processing results. This is especially helpful for understanding the reasons for a processing failure for messages having a **Processing result** of *Failed*.
- **Bundle** – Multiple message processing operations can run as part of the same batch process. Select this button to view this detailed data. For example, you can see whether dependencies exist that require the system to process certain messages in a specific sequence.

## Message processor batch job

When running a distributed hybrid topology with scale units, the *Message processor* batch job will automatically be evoked when a new message is created for processing, so you should not need to schedule this job manually.

If necessary, you can access the batch job by going to **System administration > Message  processor > Message processor**.

## Manually process or cancel a message

If needed, you can manually process or cancel a message, depending on its current state. To do so, select the message in the grid and then select **Process** or **Cancel** on the Action Pane

## Set up business events to deliver alerts for failed processing results

In addition to filtering on the **Message state** value *Canceled* to inquire for failed messages, you can set up [Business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) on the hub to alert you to failed processing results. To do so, activate the business event named *Message processor message processed*  on the **Business events catalog** page (**System administration > Setup > Business events > Business events catalog**).

As part of the activation process, you will be guided to specify whether the event is specific to one or all legal entities and provide an **Endpoint name**, which must be defined first.

>[!NOTE]
> If **When a Business Event occurs** is set to *Microsoft Power Automate* (rather than *HTTPS*, for example), the **Endpoint name** will automatically be created in Supply Chain Management based on the *Microsoft Power Automate* setup.

### Microsoft Power Automate example

In this example, use **When a Business Event occurs** with *Microsoft Power Automate* sends emails containing InfoLog messages and hyperlinks to open the **Message processor messages** page for a specific failed message on the hub deployment. If needed, you can add extra logic to send the notifications in parallel using different channels and control the recipients based on the event data.

1. In [Power Automate](https://preview.flow.microsoft.com), create a new automated cloud flow for the flow trigger **When a Business Event occurs - Fin & Ops App (Dynamics 365)** followed by the **Parse JSON** and **Send an email** steps, as shown in the following illustration.

    :::image type="content" source="./media/cloud-edge-power-automate-example1.png" alt-text="Power Automate automated cloud flow.":::

1. In the **When a Business Event occurs** step, you can look up or enter the hub **Instance** following the **Category** and then the **Business event** *Message processor message processed*, as shown in the following illustration.

    :::image type="content" source="./media/cloud-edge-power-automate-example2.png" alt-text="Power Automate When a Business Event occurs step.":::

1. For the **Parse JSON** step, enter a **Schema** that defines the extended fields. You can use the *Download schema* option on the **Business events catalog** page in Supply Chain Management or start by pasting in the example schema text. This example text is provided after the following illustration.

    :::image type="content" source="./media/cloud-edge-power-automate-example3.png" alt-text="Power Automate Parse JSON step.":::

    ```json
    {
        "properties": {
            "BusinessEventId": {
                "type": "string"
            },
            "ControlNumber": {
                "type": "integer"
            },
            "EventId": {
                "type": "string"
            },
            "EventTime": {
                "type": "string"
            },
            "MajorVersion": {
                "type": "integer"
            },
            "MessageContent": {
                "type": "string"
            },
            "MessageDestinationCompanyId": {
                "type": "string"
            },
            "MessageDestinationOperationalSiteId": {
                "type": "string"
            },
            "MessageDestinationWarehouseId": {
                "type": "string"
            },
            "MessageDestinationWorkloadName": {
                "type": "string"
            },
            "MessageInfolog": {
                "type": "string"
            },
            "MessageProcessingResult": {
                "type": "string"
            },
            "MessageProcessingResultLabel": {
                "type": "string"
            },
            "MessageProcessorMessagePageUrl": {
                "type": "string"
            },
            "MessageQueue": {
                "type": "string"
            },
            "MessageQueueLabel": {
                "type": "string"
            },
            "MessageSourceCompanyId": {
                "type": "string"
            },
            "MessageSourceOperationalSiteId": {
                "type": "string"
            },
            "MessageSourceWarehouseId": {
                "type": "string"
            },
            "MessageSourceWorkloadName": {
                "type": "string"
            },
            "MessageState": {
                "type": "string"
            },
            "MessageStateLabel": {
                "type": "string"
            },
            "MessageType": {
                "type": "string"
            },
            "MessageTypeLabel": {
                "type": "string"
            },
            "MinorVersion": {
                "type": "integer"
            }
        },
        "type": "object"
    }
    ```

1. In the **Send an email** step, you can select the individual fields or start by pasting the email body example into the **Body** field. This example is provided after the following illustration.

    :::image type="content" source="./media/cloud-edge-power-automate-example4.png" alt-text="Power Automate send an email step.":::

    ```plaintext
    Message queue: @{body('Parse_JSON')?['MessageQueue']}
    Message queue label: @{body('Parse_JSON')?['MessageQueueLabel']}
    Message type: @{body('Parse_JSON')?['MessageQueueType']}
    Message type label: @{body('Parse_JSON')?['MessageQueueTypeLabel']}
    Message content: @{body('Parse_JSON')?['MessageContent']}
    Message state: @{body('Parse_JSON')?['MessageState']}
    Message state label: @{body('Parse_JSON')?['MessageStateLabel']}
    Message processing result: @{body('Parse_JSON')?['MessageProcessingResult']}
    Message processing result label: @{body('Parse_JSON')?['MessageProcessingResultLabel']}
    Message infolog: @{body('Parse_JSON')?['MessageInfolog']}
    Message source company ID: @{body('Parse_JSON')?['MessageSourceCompanyId']}
    Message source workload name: @{body('Parse_JSON')?['MessageSourceWorkloadName']}
    Message source site ID: @{body('Parse_JSON')?['MessageSourceOperationalSiteId']}
    Message source warehouse ID: @{body('Parse_JSON')?['MessageSourceWarehouseId']}
    Message destination company ID: @{body('Parse_JSON')?['MessageDestinationCompanyId']}
    Message destination workload name: @{body('Parse_JSON')?['MessageDestinationWorkloadName']}
    Message destination site ID: @{body('Parse_JSON')?['MessageDestinationOperationalSiteId']}
    Message destination warehouse ID: @{body('Parse_JSON')?['MessageDestinationWarehouseId']}
    Message processor message page URL: @{body('Parse_JSON')?['MessageProcessorMessagePageUrl']}
    ```

1. When you save the business event, it will automatically be activated and ready to use as part of Supply Chain Management.
