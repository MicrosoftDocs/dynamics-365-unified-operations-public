---
title: Clean up processed and canceled message processor messages
description: Learn how to set up a cleanup job for the message processor.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: SysMessageQueueSetup, DiagnosticsValidationRule, ProcessScheduleSeries
ms.topic: how-to
ms.date: 07/28/2025
ms.custom: 
  - bap-template
---

# Clean up processed and canceled message processor messages

[!include [banner](../includes/banner.md)]

The [message processor](../message-processor/message-processor.md) is a framework that processes messages in the system, such as those related to inventory transactions, sales orders, and more. Over time, processed and canceled messages, that are no longer needed, can accumulate in the system, potentially affecting performance and data management. Therefore, you should periodically clean up these messages to maintain system efficiency.

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
    - **Number of processor tasks** – Specify the number of processor tasks that should be dedicated to the specified queue. The maximum value is *8*. The minimum value depends on the minimum number of batch threads that are configured for your system (typically *2*). This setting isn't related to the cleanup job, but ensures that the queue can process messages efficiently.
    - **Days before processed message deletion** – Specify the number of days to retain processed messages before deletion. To turn off processed message cleanup, set this field to 0.
    - **Days before canceled message deletion** – Specify the number of days to retain cancelled messages before deletion. To turn off cleanup, set this field to 0.

1. On the Action Pane, select **Save**. The system automatically creates a background process to run the cleanup job. By default, the process runs daily, but you can modify this schedule in the [Process automation](../../fin-ops-core/fin-ops/sysadmin/process-automation.md) workspace, as described in the next section.

## Review and manage cleanup jobs

Whenever you have at least one message queue set to be cleaned up, the system automatically creates a background process to run the cleanup operation regularly. Follow these steps to review, schedule, and manage this process in the [Process automation](../../fin-ops-core/fin-ops/sysadmin/process-automation.md) workspace:

1. Go to **System administration** \> **Setup** \> **Process automation**.
1. Open the **Background processes** tab to view the list of background processes.
1. Use the **Filter** field to search for the process that has a **Name** of *Cleanup job for the message processor*.
1. Select the process in the grid and then select **Edit** from the toolbar.
1. The **Edit background process** dialog opens. Use the settings here to view and modify the schedule and other settings for the cleanup job.
1. Select **OK** when you're done.

## Optimization advisor

The [Optimization advisor](../../fin-ops-core/fin-ops/sysadmin/optimization-advisor-overview.md) can remind you to manage outdated messages when they exist in the message processor. It includes a diagnostic rule called *Check for aged processed or canceled messages*, which identifies messages older than 30 days and creates an optimisation opportunity for them. You can take action directly from the **Optimization advisor** workspace. By default, this rule runs monthly.

To turn the rule on or off, or to change the frequency of the rule, follow these steps:

1. Go to **System administration** \> **Periodic tasks** \> **Maintain diagnostic validation rules**.
1. Find the row where **Rule name** is *Check for aged processed or canceled messages*.
1. Make the following settings for the rule as needed:
    - **Status** – Set to *Active* or *Inactive*.
    - **Run frequency** – Choose how often to run the check (*Daily*, *Weekly*, *Monthly*, or *Unscheduled*).

To view and act on your optimization opportunities, including those related to cleaning up aged messages, follow these steps.

1. Go to **System administration** \> **Workspaces** \> **Optimization advisor**. Here, you can see a list of optimization opportunities that the system has identified, including those related to message processor cleanup.
1. Select the row where **Area** is *SCM* and **Optimization opportunity** is *Cleanup job for message processor*.
1. From the toolbar, select **More information** to learn more about the opportunity and recommended actions.
1. If you want to act on the opportunity, select **Take action** from the toolbar to open the **Message queue setup** page, and configure the cleanup settings as described previously in this article.

## Related information

- [Monitor and control message processor messages](message-processor.md)
- [Business events, custom message queues, and custom message types](developer/message-processor-develop.md)
- [Message processor messages for warehouse management processes](../warehousing/warehouse-message-processor-messages.md)
- [Exchange data between systems](../warehousing/wms-only-mode-exchange-data.md)
- [Integrate with third-party manufacturing execution systems](../production-control/mes-integration.md)
- [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](../../fin-ops-core/fin-ops/data-entities/add-efficiency-in-quote-to-cash-enable.md)
- [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md)
