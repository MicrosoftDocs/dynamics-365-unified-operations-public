---
title: Monitor and control message processor messages
description: Learn how to monitor and control the processing of all message types by using the Message processor messages page.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: SysMessageProcessorMessage, BusinessEventsWorkspace 
ms.topic: how-to
ms.date: 11/18/2024
ms.custom: 
  - bap-template
---

# Monitor and control message processor messages

[!include [banner](../includes/banner.md)]

The message processor is a framework for processing messages that represent events. It has the following properties:

- It processes messages in the correct order. (Dependent messages are processed in sequence.)
- It's scalable. (Independent messages can be processed in parallel.)
- It uses the required system resources.
- It avoids exhaustion of system resources if a spike in messages occurs.
- It's reliable.
- It's traceable.

You might use this framework, for example, to develop and manage custom integration with external systems, and to process other custom functionality. Microsoft Dynamics 365 Supply Chain Management includes, for example, several out-of-box features that use predefined message types and message queues. These features include [third-party manufacturing execution system (MES) integration](../production-control/mes-integration.md), [deferred posting](../production-control/deferred-posting.md), and [packing slip posting during container close](../warehousing/packing-containers.md#set-up-the-packing-process). [Warehouse management only mode](../warehousing/wms-only-mode-overview.md) uses the message processor framework to manage *inbound and outbound shipment orders*.

This article describes how to monitor and control the processing of all message types by using the **Message processor messages** page.

## <a name="message-processor-page"></a>Message processor messages page

Use the **Message processor messages** page to view the list of incoming messages, view the message log, manually process messages, and troubleshoot issues.

### Open the Message processor messages page

To view the list of messages that have been processed by the message processor, go to **System administration \> Message processor \> Message processor messages**.

### Grid columns and filters on the Message processor messages page

You can use the fields at the top of the **Message processor messages** page to find specific messages that you're looking for. Most of these filters match the column headings in the message grid. The following filters and column headings are available:

- **Message type** – The type of message.
- **Message queue** – The name of the queue that the message will be processed in. The following queues are provided:

    - *Manufacturing Execution 3rd Party* – This queue holds messages that are created as part of the *Manufacturing execution system integration* feature. These messages are also listed on the **Manufacturing execution systems integration** page, which is like the **Message processor messages** page but is focused exclusively on that feature. Learn more in [Integrate with third-party manufacturing execution systems](../production-control/mes-integration.md).
    - *Production* – This queue holds messages that are created as part of the *Make finished goods physically available before posting to journals* feature. These messages are also listed on the **Deferred production order posting** page, which is like the **Message processor messages** page but is focused exclusively on that feature. Learn more in [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md).
    - *Warehouse*  – This queue holds messages that are created for warehouse management, such as to post a sales packing slip when the last shipment container is closed as part of a [manual packing process](../warehousing/packing-containers.md). (This message has a message type of *Run packing slip for container*.)
    - *Shipment Orders* – This queue holds messages that support [Warehouse management only mode](../warehousing/wms-only-mode-overview.md).
    - *Source System Products* – This queue holds messages that support [source product master data](../warehousing/wms-only-mode-exchange-data.md).
    - *External warehouse shipment order updates* – This queue holds messages that support [external shared warehouse processing](../warehousing/wms-only-mode-external-shared-warehouse.md).
    - *Dynamics 365 Sales Integration* – This queue holds messages that integrate with Dynamics 365 Sales. For more information about this feature and the messages that it might add to this queue, see [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](../../fin-ops-core/dev-itpro/data-entities/dual-write/add-efficiency-in-quote-to-cash-use.md).
    - *\<Custom queues\>* – If your system has been customized to support additional types of queues, they'll also be listed here. For more information about how to add custom queues, see [Implement a new queue](developer/message-processor-develop.md#custom-queue).

- **Message state** – The state of the message. The following states exist:

    - *Queued* – The message is ready to be processed by the message processor.
    - *Processed* – The message was successfully processed by the message processor.
    - *Canceled* – The message was canceled by a user.
    - *Failed* – The message failed to be processed.

- **Message content** – This filter does a full-text search of message content. (Message content isn't shown in the grid.) The filter treats most special symbols (such as hyphens) as spaces, and it treats all space characters as Boolean OR operators. For example, if you search for a specific `journalid` value that equals *USMF-123456*, the system will find all messages that contain either "USMF" or "123456," and the list is likely to be long. Therefore, it's better to enter just *123456* in this case, because more specific results will be returned.

### <a name = "view-message-log"></a> View the message log, message content, and details

To view detailed information about a message, select it in the grid, and then select the **Log** or **Message content** tab under the message grid, where each processing event is shown.

The text on the **Message content** tab depends on the **Message type** value. Therefore, the text length varies. A typical message content text will start with an opening brace (**\{**) and end with a closing brace (**\}**). In between will be field names (for example, `journalId`), each of which is followed by a colon and a value (for example, *USMF-123456*).

The toolbar on the **Log** tab includes the following buttons:

- **Log** – Select this button to show the processing results. This function is especially helpful when messages have a **Processing result** value of *Failed*, and you want to understand the reasons for the processing failure.
- **Bundle** – Multiple message processing operations can run as part of the same batch process. Select this button to view the detailed data. For example, you can see whether dependencies exist that require the system to process some messages in a specific sequence.

### Manually process, cancel, or requeue a message

Depending on the current state of a message, you can manually process or cancel it as you require. Select the message in the grid, and then select **Process** or **Cancel** on the Action Pane.

If you want to requeue a message that was previously canceled, select it in the grid, and then select **queue** on the Action Pane. The system will process the message as usual.

## <a name="processor-batch-job"></a>Schedule message processing by using the message processor batch job

To process a message queue, you must set up a batch job to run it. Usually you'll set up a fixed, regular schedule for processing each queue. However, you can also run any queue on demand. To create and schedule the required batch jobs, follow these steps.

1. Go to **System administration \> Message processor \> Message processor**.
1. In the **Message processor** dialog box, in the **Message queue** field, select the message queue that's associated with the messages that you want to process. The queue that you select will depend on the feature or system that generated the messages.
1. On the **Run in the background** FastTab, set up batch and scheduling options as you require, just as you would do for [other types of jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to run or schedule the job based on your settings.

## Message processor queue setup

You can configure the number of processor tasks that should be dedicated to each message processor queue and set rules for how often the queue should cleaned of processed and canceled messages. Unconfigured queues will use a default value that you can override as you require. Follow these steps to customize one or more queues.

1. Go to **System administration \> Message processor \> Message queue setup**.
1. Follow one of these steps:

    - To edit an existing queue, select **Edit** on the Action Pane, and then select the target queue in the grid.
    - To add a new configuration, select **Add** on the Action Pane to add a new row to the grid. Then, in the **Message queue** field for the new row, select the name of the queue that you want to configure.

1. For the new or selected row, make the following settings:
    - **Number of processor tasks** – Specify the number of processor tasks that should be dedicated to the specified queue. The maximum value is *8*. The minimum value depends on the minimum number of batch threads that are configured for your system (typically *2*).
    - **Days before processed message deletion** – Specify the number of days before processed messages should be cleaned up (deleted). Set this field to zero (0) to turn off processed message cleanup. Learn more in [Clean up processed and canceled message processor messages](message-processor-cleanup.md).
    - **Days before canceled message deletion** – Specify of days before canceled messages should be cleaned up (deleted).  Set this field to zero (0) to turn off canceled message cleanup. Learn more in [Clean up processed and canceled message processor messages](message-processor-cleanup.md).

1. On the Action Pane, select **Save**.

## Related information

- [Clean up processed and canceled message processor messages](message-processor-cleanup.md)
- [Business events, custom message queues, and custom message types](developer/message-processor-develop.md)
- [Message processor messages for warehouse management processes](../warehousing/warehouse-message-processor-messages.md)
- [Exchange data between systems](../warehousing/wms-only-mode-exchange-data.md)
- [Integrate with third-party manufacturing execution systems](../production-control/mes-integration.md)
- [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](../../fin-ops-core/fin-ops/data-entities/add-efficiency-in-quote-to-cash-enable.md)
- [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md)
