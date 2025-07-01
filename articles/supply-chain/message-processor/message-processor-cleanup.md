---
title: Clean up processed and canceled message processor messages
description: Learn how to set up a cleanup job for the message processor
author: juhnkim
ms.author: juhnkim
ms.reviewer: kamaybac
ms.search.form: SysMessageQueueSetup, DiagnosticsValidationRule, ProcessScheduleSeries
ms.topic: how-to
ms.date: 07/28/2025
ms.custom: 
  - bap-template
---

# Clean up processed and canceled message processor messages

<!-- KFM: Who is the PM for this feature? We normally use the PM as the author in metadata. -->

The [message processor](../message-processor/message-processor.md) is a framework that processes messages in the system. It can handle various types of messages, such as those related to inventory transactions, sales orders, and more. Over time, processed and canceled messages, which are no longer needed, can accumulate in the system, potentially affecting performance and data management. Therefore, you should periodically clean up these messages to maintain system efficiency. <!-- KFM: I added this intro. Please confirm and enhance as needed. -->

## Prerequisites

To use the cleanup functionality described in this article, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.45 or later. No feature management settings are required.

## Set up message cleanup for each message processor queue

You set up message cleanup using the **Message queue setup** page, which allows you to specify how long processed and canceled messages should be retained for each queue before they're deleted.

To configure message cleanup, follow these steps:

1. Go to **System administration \> Message processor \> Message queue setup**.
1. Follow one of these steps:
    - To edit an existing queue, select **Edit** on the Action Pane, and then select the target queue in the grid.
    - To add a new configuration, select **Add** on the Action Pane to add a new row to the grid. Then, in the **Message queue** field for the new row, select the name of the queue that you want to configure.

1. For the new or selected row, make the following settings:
    - **Number of processor tasks** – Specify the number of processor tasks that should be dedicated to the specified queue. The maximum value is *8*. The minimum value depends on the minimum number of batch threads that are configured for your system (typically *2*). This setting isn't related to the cleanup job, but it's important to ensure that the queue can process messages efficiently.
    - **Days before processed message deletion** - Specify the number of days to wait before processed messages should be cleaned up (deleted). To turn off processed message cleanup, set this field to zero (0).
    - **Days before canceled message deletion** - Specify of days to wait before canceled messages should be cleaned up (deleted). To turn off canceled message cleanup, set this field to zero (0).

1. On the Action Pane, select **Save**. The system automatically creates a background process to run the cleanup job. By default, the process is set to run daily, but you can modify this schedule in the [Process automation](../../fin-ops-core/fin-ops/sysadmin/process-automation.md) workspace, as described in the next section.
1. Go to **System administration** \> **Setup** \> **Process automation** and, on the Action Pane, select **Initialize process automation**. <!-- KFM: It doesn't seem like this step is needed. For me, the job was added automatically when I configured the queues and when I selected **Initialize process automation**, the system said automation was already initialized (as it will probably already be for almost all of our readers) -->

## Review and manage cleanup jobs

Whenever you have at least one message queue set to be cleaned up, the system automatically creates a background process to run the cleanup operation on a regular basis. Follow these steps to review, schedule, and manage this process in the [Process automation](../../fin-ops-core/fin-ops/sysadmin/process-automation.md) workspace:

1. Go to **System administration** \> **Setup** \> **Process automation**.
1. Open the **Background processes** tab to view the list of background processes.
1. Use the **Filter** field to search for the process that has a **Name** of *Cleanup job for the message processor*.
1. Select the process in the grid and then select **Edit** from the toolbar.
1. The **Edit background process** dialog opens. Use the settings here to view and modify the schedule and other settings for the cleanup job.
1. Select **OK** when you're done.

## Optimization advisor

The [Optimization advisor](../../fin-ops-core/fin-ops/sysadmin/optimization-advisor-overview.md) can remind you to manage outdated messages when they exist in the message processor<!-- KFM: Is this considered an alternative to using the scheduled task? Is there a scenario where we would use both? -->. The Optimization advisor includes a diagnostic called *Check for aged processed or canceled messages*<!-- KFM: where do we see this name? --> , which checks for processed or canceled messages that are older than a specified number of days <!-- KFM: how many days? can we configure this? -->and creates an optimization opportunity for them so you can take action directly from the **Optimization advisor** workspace. By default<!-- KFM: Can we change this? How? -->, the *Check for aged processed or canceled messages* rule runs on a monthly basis.

To view and act on your optimization opportunities, including those related to cleaning up aged messages, follow these steps.

1. Go to **System administration** \> **Workspaces** \> **Optimization advisor**. Here, you can see a list of optimization opportunities that the system has identified, including those related to message processor cleanup.
1. Select the relevant optimization opportunity from the list <!-- KFM: please specify how to identify it by **Area** and **Optimization opportunity** values. -->
1. From the toolbar, select **More information** to learn more about the opportunity and the recommended action.
1. If you want to act on the opportunity, select **Take action** from the toolbar to open the **Message queue setup** page, where you can configure the cleanup settings as described previously in this article.

## Additional resources

- [Monitor and control message processor messages](message-processor.md)
- [Business events, custom message queues, and custom message types for the message processor](developer/message-processor-develop.md)
- [Message processor messages for warehouse management processes](warehouse-message-processor-messages.md)
- [Exchange data between systems](wms-only-mode-exchange-data.md)
- [Integrate with third-party manufacturing execution systems](../production-control/mes-integration.md)
- [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](../../fin-ops-core/fin-ops/data-entities/add-efficiency-in-quote-to-cash-enable.md)
- [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md)
