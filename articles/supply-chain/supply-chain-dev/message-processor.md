---
title: Create and process custom message queues and message types
description: This article describes how to design custom message queues and message types using Visual Studio and how to monitor and control the processing of all message types using the message processor messages page.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SysMessageProcessorMessage, BusinessEventsWorkspace   
ms.topic: how-to
ms.date: 11/02/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create and process custom message queues and message types

[!include [banner](../includes/banner.md)]

The message processor is a framework for processing messages representing events. It has the following properties:

- Processes messages in the correct order (dependent messages are processed in sequence)
- Scalable (independent messages can be processed in parallel)
- Uses system resources needed
- Avoids exhaustion of system resources if a spike in messages occurs.
- Reliable
- Traceable

You might make use of this framework, for example, to develop and manage custom integration with external systems, and to process other custom functionality. Supply Chain Management includes two features that make use of predefined message types and message queues ([Third-party MES integration](../production-control/mes-integration.md) and [Deferred posting](../production-control/deferred-posting.md)). This article describes how to design your own custom message queues and message types using Visual Studio and how to monitor and control the processing of all message types (including the predefined message types) using the **Message processor messages** page.

## Prerequisites

To use the message processor, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.29 or later.
- At least one of the following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):
  - *Manufacturing execution system integration*
  - *(Preview) Make finished goods physically available before posting to journals*

## The message processor messages list

Use the **Message processor messages** page to view the list of incoming messages, view the message log, manually process messages, and troubleshoot issues.

### Open the message processor messages list

You can view the messages that have been processed by the message processor by going to **System administration \> Message processor \> Message processor messages**.

### Message processor messages grid columns and filters

You can use the fields at the top of the **Message processor messages** page to help find any particular messages you're looking for. Most of these filters match the column headings in the message grid. The following filters and column headings are available:

- **Message type** – Specifies the type of message.
- **Message queue** – Specifies the name of the queue in which the message is to be processed. The following queues are provided:
  - *Manufacturing Execution 3rd Party* – This queue holds messages created as part of the *Manufacturing execution system integration* feature. These messages are also listed on the **Manufacturing execution systems integration** page, which is similar to the **Message processor messages** page, but focuses on that feature only. See also [Integrate with third-party manufacturing execution systems](../production-control/mes-integration.md).
  - *Production* – This queue holds messages created as part of the *Make finished goods physically available before posting to journals* feature. These messages are also listed on the **Deferred production order posting** page, which is similar to the **Message processor messages** page, but focuses on that feature only. See also [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md).
  - *\<Custom queues\>* – If your system has been customized to support additional types of queues, they'll also be listed here. For more information about how to add custom queues, see [Implement a new queue](#custom-queue).
- **Message state** – Specifies the state of the message. The following states exist:
  - *Queued* – The message is ready to be processed by the message processor.
  - *Processed* – The message was successfully processed by the message processor.
  - *Canceled* – The message was canceled by a user.
  - *Failed* – The message failed to be processed.
- **Message content** – This filter does a full-text search of message content. (Message content isn't shown in the grid.) The filter treats most special symbols (such as "-") as spaces, and treats all space characters as Boolean OR operators. For example, this means if you search for a specific `journalid` value equal "USMF-123456", the system will find all messages that contain "USMF" or "123456", which is likely to be a long list. Therefore, it would be better to enter just "123456" alone because that will return more specific results.

### View the message log, message content, and details

You can find detailed information about a message by selecting it in the grid and then opening the **Log** or **Message content** tabs under the message grid, where each processing event is shown.

The **Message content** depends on the **Message type** and will therefore have different text length. A typical message content text will start with a **{** and end with a **}** and in between have field names such as `journalId` followed by a **:** and a value such as *USMF-123456*.

The toolbar on the **Log** tab includes the following buttons:

- **Log** – Select this button to show the processing results. This function is especially helpful for understanding the reasons for a processing failure for messages having a **Processing result** of *Failed*.
- **Bundle** – Multiple message processing operations can run as part of the same batch process. Select this button to view this detailed data. For example, you can see whether dependencies exist that require the system to process certain messages in a specific sequence.

### Manually process, cancel, or requeue a message

If needed, you can manually process or cancel a message, depending on its current state. To do so, select the message in the grid and then select **Process** or **Cancel** on the Action Pane.

If you would like to requeue a message that was previously canceled, select the message in the grid and then select **queue** on the Action Pane. The system will then process the message as usual.

## Schedule message processing using the message processor batch job

To process a message queue, you must set up a batch job to run it. Usually you'll set up a fixed, regular schedule for processing each queue, but you can also run any queue on demand. To create and schedule the required batch jobs, follow these steps:

1. Go to **System administration \> Message processor \> Message processor**.
1. The **Message processor** dialog opens. From the **Message queue** drop-down list, select the message queue associated with the messages you want to process. The value you pick will depend on which feature or system generated the messages you want to process.
1. On the **Run in the background** FastTab, set up batch and scheduling options as you require, just as you would do for [other types of jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to run or schedule the job based on your settings.

## Message processor queue setup

You can configure the number of processor tasks that should be dedicated to each message processor queue. Unconfigured queues will use a default value that you can override when needed. Follow these steps to customize one or more queues:

1. Go to **System administration \> Message processor \> Message queue setup**.
1. Do one of the following steps:
    - To edit an existing queue, select **Edit** on the Action Pane and then select the target queue in the grid.
    - To add a new configuration, select **Add** on the Action Pane to add a new row to the grid. Then set the **Message queue** drop-down list for the new row to the name of the queue you want to configure.
1. For your new or selected row, set Number of processor tasks to the number of processor tasks to dedicate to the specified queue. The maximum value is 8. The minimum value depends on the minimum number of batch threads configured for your system (typically 2).
1. Select **Save** on the Action Pane.

## Set up business events to deliver alerts for failed processing results

In addition to filtering on the **Message state** value *Failed* (or, possibly, *Canceled*) to inquire for failed messages, you can set up [Business events](../../fin-ops-core/dev-itpro/business-events/home-page.md) to alert you to failed processing results. To do so, activate the business event named *Message processor message processed*  on the **Business events catalog** page (**System administration \> Setup \> Business events \> Business events catalog**).

As part of the activation process, you'll be guided to specify whether the event is specific to one or all legal entities and provide an **Endpoint name**, which must be defined first.

>[!NOTE]
> If **When a Business Event occurs** is set to *Microsoft Power Automate* (rather than *HTTPS*, for example), the **Endpoint name** will automatically be created in Supply Chain Management based on the *Microsoft Power Automate* setup.

## Microsoft Power Automate example

In this example, using **When a Business Event occurs** with *Microsoft Power Automate* sends emails containing InfoLog messages and hyperlinks to open the **Message processor messages** page for a specific failed message. If needed, you can add extra logic to send the notifications in parallel using different channels and control the recipients based on the event data.

1. In [Power Automate](https://preview.flow.microsoft.com), create a new automated cloud flow for the flow trigger **When a Business Event occurs - Fin & Ops App (Dynamics 365)** followed by the **Parse JSON** and **Send an email** steps, as shown in the following illustration.

    :::image type="content" source="media/message-processor-power-automate-example1.png" alt-text="Power Automate automated cloud flow.":::

1. In the **When a Business Event occurs** step, you can look up or enter the **Instance** following the **Category** and then the **Business event** *Message processor message processed*, as shown in the following illustration.

    :::image type="content" source="media/message-processor-power-automate-example2.png" alt-text="Power Automate When a Business Event occurs step.":::

1. For the **Parse JSON** step, enter a **Schema** that defines the extended fields. You can use the *Download schema* option on the **Business events catalog** page in Supply Chain Management or start by pasting in the example schema text. This example text is provided after the following illustration.

    :::image type="content" source="media/message-processor-power-automate-example3.png" alt-text="Power Automate Parse JSON step.":::

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

    :::image type="content" source="media/message-processor-power-automate-example4.png" alt-text="Power Automate send an email step.":::

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

## Scheduler

The message processor has one scheduler. The class `SysMessageKeyDateTimeSequenceProcessorScheduler` schedules messages with dependencies based on a key, date, and time to be processed in the correct order. Messages to be processed are stored in the tables `SysMessageProcessorTaskBundle` and `SysMessageProcessorTaskBundleMessage`. Dependent messages must be in the same bundle.

The `SysMessageKeyDateTimeSequenceProcessorScheduler` is used by the [third-party manufacturing execution system (MES) integration](../production-control/mes-integration.md) feature to secure messages related to a production order, and are processed in the order they're received or created. The dependencies are defined by a key (production order number) and the time.

For example, suppose the system receives or creates the following messages:

- Production order 1 – Start message
- Production order 2 – Start message
- Production order 2 – Report as finished message
- Production order 1 – Report as finished message

In this case, the `SysMessageKeyDateTimeSequenceProcessorScheduler` will schedule the processing of messages in the following order:

1. Production order 1 – Start message
1. Production order 1 – Report as finished message
1. Production order 2 – Start message
1. Production order 2 – Report as finished message

Each report-as-finished message depends on the related start message being processed successfully.

Because a bottleneck can occur when picking up records to process for multiple tasks, and because there may be dependencies between the messages, the system bundles the messages. For example, if the bundle size is two, then the system will create the following bundles:

- Bundle 1 - Production order 1 – Start message
- Bundle 1 - Production order 1 – Report as finished message
- Bundle 2 - Production order 2 – Start message
- Bundle 2 - Production order 2 – Report as finished message

For scalability, you can configure the number of tasks that should process the bundles when you're developing a new queue (see also [Implement a new queue](#custom-queue)). If the configuration uses two message processor tasks, then the two bundles can be processed in parallel.

## Implementation examples

This section provides examples of how to develop new message queues and message types for use with the message processor.

### <a name="custom-queue"></a>Implement a new queue

This example shows how to add a new queue. Once created, you'll be able to submit messages to this queue, and those messages will be processed by the message processor according to the settings described previously.

1. In Visual Studio, create an extension for the enum `SysMessageQueue`.
1. Add a new enum value for the new queue.

    ![Add a new enum value for the new queue.](media/message-processor-implement-queue-enum.png "Add a new enum value for the new queue")

1. Set a feature class on the enum value.

    ![Set a feature class on the enum value.](media/message-processor-implement-queue-class.png "Set a feature class on the enum value")

1. Create a class that extends `SysMessageQueueMetadata` like below:

    ```xpp
    [SysMessageQueueFactory(SysMessageQueue::MyQueue)]
    public final class MyQueue extends SysMessageQueueMetadata
    {
    
        /// <summary>
        /// Gets the default number of message processor tasks.
        /// </summary>
        /// <returns>The default number of message processor tasks.</returns>
        public SysMessageProcessorsTasks getDefaultMessageProcessorsTasks()
        {
            return 1;
        }
    
        /// <summary>
        /// Get the maximum number of messages in a bundle.
        /// </summary>
        /// <returns>The maximum number of messages in a bundle.</returns>
        public SysMessageProcessorMaxBundleSize getMaxBundleSize()
        {
            return 10;
        }
    
        /// <summary>
        /// Determines if messages should be queued when sending or processing messages.
        /// </summary>
        /// <returns>true if messages should be queued when sending a message; otherwise false.</returns>
        public boolean queueMessageOnSend()
        {
            return true;
        }
    
        /// <summary>
        /// Determines if dependent messages should be committed per created transaction ID.
        /// </summary>
        /// <returns>true if dependent messages should be committed per created transaction ID.; otherwise false.</returns>
        public boolean commitPerCreatedTransactionID()
        {
            return false;
        }
    
    }
    ```

1. Create an extension for the class `SysMessageProcessorToggle` to enable message processor in the UI.

    ```xpp
    [ExtensionOf(classStr(SysMessageProcessorToggle))]
    final class MySysMessageProcessorToggle_Extension
    {
        /// <summary>
        /// Determines if the toggle is enabled.
        /// </summary>
        /// <returns>
        /// true if the toggle is enabled; otherwise, false.
        /// </returns>
        internal boolean isEnabled()
        {
            return next isEnabled() || MyFeature::instance().isEnabled();
        }
    
    }
    ```

### Implement a new message type

You'll create a new message type for each type of process you'd like to make available to the message processor. The message type establishes which processes can be executed by messages of that type. The name of the message type will be shown on the **Message processor messages** page to identify the purpose of each message in the queue.

Follow these steps to create a new message type.

1. In Visual Studio, create an extension for the enum `SysMessageType`.
1. Add a new enum value for the new message type.

    ![Add a new enum value for the new message type.](media/message-processor-implement-message-type-enum.png "Add a new enum value for the new message type")

1. Set a feature class on the enum value.

    ![Set a feature class on the enum value.](media/message-processor-implement-message-type-class.png "Set a feature class on the enum value")

1. Create a class that extends SysMessageTypeMetadata like below:

    ```xpp
    [SysMessageTypeFactory(SysMessageType::MyMessage)]
    public final class MyMessage extends SysMessageTypeMetadata
    {
        /// <summary>
        /// Validates if it is allowed to send a message on a given queue.
        /// </summary>
        /// <param name = "_messageQueue">A queue to send message to.</param>
        /// <param name = "_messageTarget">A message target.</param>
        /// <param name = "_sourceMessageTarget">A message source.</param>
        /// <returns>true if it is allowed to send a message; false, otherwise.</returns>
        public boolean canSendMessage(SysMessageQueue _messageQueue, SysMessageTargetRecId _messageTarget, SysMessageTargetRecId _sourceMessageTarget)
        {
            if (_messageQueue == SysMessageQueue::MyQueue)
            {
                return true;
            }
    
            return false;
        }
    
        /// <summary>
        /// Returns a list of allowed message state transitions.
        /// </summary>
        /// <returns>A list of allowed message state transitions.</returns>
        public Enumerator getAllowedMessageStateTransitions()
        {
            // Allow the following state transitions:
    
            // SysMessageState::None -> SysMessageState::Queued
            // SysMessageState::None -> SysMessageState::Processed
    
            // SysMessageState::Queued -> SysMessageState::Processed
    
            // SysMessageState::Failed -> SysMessageState::Queued
            // SysMessageState::Failed -> SysMessageState::Cancelled
            // SysMessageState::Failed -> SysMessageState::Processed
    
            return SysMessageStateTransition::getProcessedCancelledStateTransitions();
        }
    
        /// <summary>
        /// Returns dependencies related to a message.
        /// </summary>
        /// <param name = "_message">The message to add dependencies to.</param>
        /// <returns>A list of dependencies related to a message.</returns>
        public List getDependencies(SysMessage _message)
        {
            List dependencies = new List(Types::Record);
    
            // Add a dependency to the message if you need to process messages in order. 
            // For example, process a start message before an end message. 
            // The message will not be processed before the dependent message is processed or cancelled.
    
            // The default scheduler, SysMessageKeyDateTimeSequenceProcessorScheduler only supports one dependency per message.
            // Messages with different keys may be processed in parallel.
    
            SysMessageDependencyKey dependencyKey = strFmt('Mykey:%1', this.getContract(_message).parmMyKey());
            dependencies.addEnd(SysMessageKeyDateTimeSequenceDependency::create(dependencyKey));
    
            return dependencies;
        }
    
        /// <summary>
        /// Execute the logic associated with the given message state transition.
        /// </summary>
        /// <param name = "_message">The message.</param>
        /// <param name = "_messageStateTransition">The state transition to execute.</param>
        public void processMessageStateTransition(SysMessage _message, SysMessageStateTransition _messageStateTransition)
        {
            if (_messageStateTransition.isEqual(SysMessageStateTransition::newFromStates(SysMessageState::Queued, SysMessageState::Processed)))
            {
                this.processMessage(_message);
            }
            else if (_messageStateTransition.isEqual(SysMessageStateTransition::newFromStates(SysMessageState::Failed, SysMessageState::Processed)))
            {
                this.cancelMessage(_message);
            }
        }
    
        private void processMessage(SysMessage _message)
        {
            // Add logic to process the message.
        }
    
        private void cancelMessage(SysMessage _message)
        {
            // Add logic to cancel the message if needed.
        }
    
        private ClassId contractClass()
        {
            return classNum(MyContract);
        }
    
        protected MyContract getContract(SysMessage _message, ClassId _objectTypeId = this.contractClass())
        {
            var contract = FormJsonSerializer::deserializeObject(_objectTypeId, _message.Content) as MyContract;
    
            return contract;
        }
    
    }
    ```
