---
# required metadata

title: Message processor messages for cloud and edge workloads
description: This topic provides information about the Message processor messages feature for C&E workloads.
author: perlynne
manager: tfeyr
ms.date: 03/10/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
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
[!include [preview banner](../includes/preview-banner.md)]

Message processor messages are used when running cloud and edge scale units for [manufacturing workloads](cloud-edge-workload-manufacturing.md) and [warehouse management workloads](cloud-edge-workload-warehousing.md). 

A large amount of data is exchanged between the hub and scale unit deployment environments to keep them in sync, but only a few of these data exchanges will be processed using the **Message processor messages** page (**System administration > Message processor > Message processor messages**). By looking in the **Message type** field here, you can inquire and filter on all the supported message types.

## Example message type: Request inventory adjustment financial update

For example, the message type *Request inventory adjustment financial update* is used to create and post a counting journal on the hub when a worker does an [inventory adjustment using the warehouse app](cloud-edge-warehouse-inventory-adjustment.md) against a scale unit warehouse management workload. Because this specific process originates from a scale unit the **Message queue** field will contain the value *Scale unit to hub*. Other message type values are *Hub to warehouse execution scale unit* and *Hub to manufacturing execution scale unit*.

For the message type *Request inventory adjustment financial update*, a scale unit workload will record this message as part of a warehouse app inventory adjustment operation. This message data gets transferred to the hub as part of the same process as used for the [Commerce data exchange architecture](../../commerce/commerce-architecture.md) and the message will get updated to the *Queued* state, after which it will either end up as *Processed* when succeeded or *Canceled* when failing during the message processing.

The **Message state** field can be used to filter the messages. The following states exists:

- Queued
- Processed
- Canceled

You can use the **Message content** field to filter using a full-text search of message content. The filter treats most special symbols (such as "-") as spaces, and treats all space characters as Boolean OR operators. This means that, if you, for example, search for a specific `journalid` value equal "USMF-123456", the system will find all messages that contain "USMF" or "123456". Therefore, it would be best to enter "123456" alone because that will return more accurate results.

## Log and message content

For each message, you can find detailed information as part of the **Log** and **Message content** sections where each processing event is shown. The **Message content** depends on the **Message type** and will therefore have different text length. A typical message content text will start with a **{** and end with a **}** and in between have field names such as `journalId` followed by a **:** and a value such as *USMF-123456*.

This area includes a **Log** button, which you can use to view the processing results. This is especially helpful for understanding the reasons for a processing failure for messages having a **Processing result** of *Failed*.

Note that multiple message processing operations can run as part of the same batch process. You can view this detailed data by selecting the **Bundle** button where you, for example, can see whether dependencies between messages exists in which processing must occur in a specific sequence.

You can process most types of failed messages by selecting the **Queue** button, which moves selected messages back into the *Queued* state .

You manually process or cancel a message, depending its current state, by selecting **Process** or **Cancel**.

> [!Note]
> When running a cloud and edge deployment, the *Message processor* batch job (**System administration > Message  processor > Message processor**) will automatically be evoked when a new message is created for processing, so you don't need to schedule this job manually.

## Business events for failed processing results

In addition to filtering on the **Message state** value *Canceled* to inquire for failed messages, you set up [Business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) on the hub to inform about failed processing results. To do so, activate the business event named *Message processor message processed*  on the **Business events catalog** page (**System administration > Setup > Business events > Business events catalog**).

As part of the activation process, you will be guided to specify whether the event is specific to one or all legal entities and provide an **Endpoint name**, which must be defined upfront.

>[!Note]
> When **When a Business Event occurs** is set to *Microsoft Power Automate* rather than *HTTPS* for example, the **Endpoint name** will automatically be created in Supply Chain Management based on the *Microsoft Power Automate* setup.

## Microsoft Power Automate example

As an example, let's use **When a Business Event occurs** with *Microsoft Power Automate* to send e-mails containing InfoLog messages and hyperlinks to open the **Message processor messages** page for a specific failed message on the hub deployment. If needed, you can add extra logic to send out the notifications in parallel via different channels and control the recipients based on the event data, but in this section we will look at a simple example.

In [Power Automate](https://preview.flow.microsoft.com/en-us/), you start by creating a new automated cloud flow for the flow trigger **When a Business Event occurs - Fn & Ops App (Dynamics 365)** followed by the **Parse JSON** and **Send an email** steps, as shown in the following illustration.

:::image type="content" source="./media/cloud-edge-power-automate-example1.png" alt-text="Power Automate automated cloud flow":::

In the **When a Business Event occurs** step, you can look-up or enter the hub **Instance** following the **Category** and then the **Business event** *Message processor message processed*, as shown in the following illustration.

:::image type="content" source="./media/cloud-edge-power-automate-example2.png" alt-text="Power Automate When a Business Event occurs step":::

For the **Parse JSON** step, enter a **Schema** that defines the extended fields. You can use the *Download schema* option on the **Business events catalog** page in  Supply Chain Management or start by pasting in the example schema text provided after the illustration.  
:::image type="content" source="./media/cloud-edge-power-automate-example3.png" alt-text="Power Automate Parse JSON step":::

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

In the **Send an email** step, you can select the individual fields or start by pasting email body example provided after the following illustration into the **Body** field.

:::image type="content" source="./media/cloud-edge-power-automate-example4.png" alt-text="Power Automate send an email step":::

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

When you save the business event, it will automatically get activated and ready to be used as part of Supply Chain Management.
