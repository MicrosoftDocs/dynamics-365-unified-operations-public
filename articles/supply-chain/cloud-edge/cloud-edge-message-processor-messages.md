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

This feature is used when running [Cloud and edge scale units for manufacturing and warehouse management workloads](cloud-edge-workload-warehousing.md). A lot of data exchange happens between the hub and scale unit deployment environments to keep the data between the environments in sync, but only a few of these data exchanges will end up getting processes via **System administration > Message processor > Message processor messages**. By looking in the Message type field you can inquire and filter on all the supported message types.

## Example message type: Request inventory adjustment financial update 

Let’s use an example of the message type *Request inventory adjustment financial update* which is used to create and post a counting journal on the hub when a scale unit warehouse management workload does an [inbound or outbound warehouse app inventory adjustment update](cloud-edge-warehouse-inventory-adjustment.md). Because this specific process originates from a scale unit the **Message queue** field will contain the value *Scale unit to hub*. Other message type values are *Hub to warehouse execution scale unit* and *Hub to manufacturing execution scale unit*.

For the message type *Request inventory adjustment financial update* a scale unit workload will record this message as part of a Warehouse app inventory adjustment operation. This message data gets transferred to the hub as part of the same process as used for the [Commerce data exchange architecture](../../commerce/commerce-architecture.md) and the message will get updated to the *Queued* state, from where it will either end up as *Processed* when succeeded or *Canceled* when failing during the message processing.

The **Message state** field can be used to filter the messages; the following states exists:
-	Queued
-	Processed
-	Canceled

You can as well use the **Message content** field to filter a full-text search of message content. The filter treats most special symbols (such as "-") as spaces, and treats all space characters as Boolean OR operators. This means that, if you e.g. search for a specific journalid value equal "USMF-123456", the system will find all messages that contain "USMF" or "123456". Therefore, it would be best just to enter "123456" because that will return more accurate results.

## Log and Message content
For each message you can find detailed information as part of the **Log** and **Message content** sections where each processing event can get viewed. The **Message content** depends on the **Message type** and will therefore have different text length. A typically message content text will start with a **{** and end with a **}** and in between have field names like for example **“journalId”** following a **:** and the value like **“USMF-123456”**.

In this area you will find the **Log** button where the processing results can get viewed. This is especially interesting for messages having a **Processing result** as *Failed* to understand the reason for the processing fail.

Note that multiple message processing operations can run as part of the same batch process, this detailed data can get inquired by selecting the **Bundle** button where you e.g. will be able to see if dependencies between messages exists where the processing must happen in a specific sequence.

Most of the message types can get reprocesses when being in a failed state by moving the message back into the *Queued* state. This gets achieved by selecting the **Queue** button.
A message can as well manually get processed or canceled depending on the current message state by selecting the buttons **Process** and **Cancel**.

> [!Note]
 When running the cloud and edge deployments the batch job **System administration > Message  processor > Message processor** will automatically get evoked when a new message gets created for processing and thereby you do not need to manually schedule this batch job.

# Business events for failed processing results

Besides filtering on the **Message state** value *Canceled* to inquire for failed messages you can on the hub deployment setup [Business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to inform about failed processing result by activating the business event name *Message processor message processed* via **System administration > Setup > Business events > Business events catalog**.

As part of the activation process you will get guided to specify if the event is going to be specific to one or all legal entities and provide an **Endpoint name** which needs to get defined upfront.

>[!Note]
 When using the *Microsoft Power Automate* **When a Business Event occurs** rather than for example *HTTPS* the **Endpoint name** will automatically get created in Microsoft Dynamics 365 Supply Chain Management via the *Microsoft Power Automate* setup.

## Microsoft Power Automate example
As an example, let’s use the *Microsoft Power Automate* **When a Business Event occurs** to send e-mails containing InfoLog messages and hyperlinks to open the **Message processor messages** page for a specific failed message on the hub deployment. You can of course add additional logic like sending out the notifications in parallel via different channels and control the recipients based on the event data, but below you can see a simple example.  
First you in [Power Automate](https://preview.flow.microsoft.com/en-us/) create a new *Automated cloud flow* for the *flow trigger* **When a Business Event occurs - Fn & Ops App (Dynamics 365)** following the **Parse JSON** and **Send an email** steps:
:::image type="content" source="./media/cloud-edge-power-automate-example1.png" alt-text="Power Automate example":::

In the **When a Business Event occurs** step, you can look-up or enter the hub *Instance* following the *Category and Business event* **Message processor message processed**.
:::image type="content" source="./media/cloud-edge-power-automate-example2.png" alt-text="Power Automate example":::
 
For the **Parse JSON** step you can use the **Download schema** option in the Microsoft D365 SCM **Business events catalog** page or paste in the below schema example text containing extended fields into the schema section.  
:::image type="content" source="./media/cloud-edge-power-automate-example3.png" alt-text="Power Automate example":::
 ```plaintext 
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

In the Send an email step you can select the individual fields or simple paste the below email body example into the email body section:
:::image type="content" source="./media/cloud-edge-power-automate-example4.png" alt-text="Power Automate example":::
 
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

When saving the business event, it will automatically get activated and ready to be used as part of Microsoft Dynamics 365 SCM.
