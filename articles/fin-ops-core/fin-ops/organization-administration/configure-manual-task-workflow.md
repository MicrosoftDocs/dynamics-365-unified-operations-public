---
title: Configure manual tasks in a workflow
description: Learn about how to configure the properties for a manual task, including outlines on naming tasks and entering subject lines and instructions.
author: ChrisGarty
ms.author: cgarty
ms.topic: how-to
ms.date: 03/10/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 27f1afde-ff26-4b6f-8c11-27ec49130bbb
---

# Configure manual tasks in a workflow

[!include [banner](../includes/banner.md)]

This article explains how to configure the properties for a manual task.

To configure a manual task in the workflow editor, right-click the task, and then select **Properties** to open the **Properties** page. Then use the following procedures to configure the properties for the manual task.

## Name the task

Follow these steps to enter a name for the manual task.

1. In the left pane, select **Basic Settings**.
1. In the **Name** field, enter a unique name for the task.

## Enter a subject line and instructions

You must provide a subject line and instructions for users assigned to the task. For example, if you configure a task for purchase requisitions, the user assigned to the task sees the subject line and instructions on the **Purchase requisitions** page. The subject line appears in a message bar on the page. The user can then select the icon in the message bar to view the instructions. Follow these steps to enter a subject line and instructions.

1. In the left pane, select **Basic Settings**.
1. In the **Work item subject** field, enter the subject line.
1. To personalize the subject line, insert placeholders. Placeholders are replaced with appropriate data when the subject line is shown to users. Follow these steps to insert a placeholder:

   1. In the text box, select where the placeholder should appear.
   1. Select **Insert placeholder**.
   1. In the list that appears, select the placeholder to insert.
   1. Select **Insert**.

1. To add translations of the subject line, follow these steps:

   1. Select **Translations**.
   1. On the page that appears, select **Add**.
   1. In the list that appears, select the language for the translation.
   1. In the **Translated text** field, enter the translated text.
   1. To personalize the text, insert placeholders as described in step 3.
   1. Select **Close**.

1. In the **Work item instructions** field, enter the instructions.
1. To personalize the instructions, insert placeholders. Placeholders are replaced with appropriate data when the instructions are shown to users. Follow these steps to insert a placeholder:

   1. In the text box, select where the placeholder should appear.
   1. Select **Insert placeholder**.
   1. In the list that appears, select the placeholder to insert.
   1. Select **Insert**.

1. To add translations of the instructions, follow these steps:

   1. Select **Translations**.
   1. On the page that appears, select **Add**.
   1. In the list that appears, select the language for the translation.
   1. In the **Translated text** field, enter the translated text.
   1. To personalize the text, insert placeholders as described in step 6.
   1. Select **Close**.

## Assign the task

Follow these steps to specify who should receive the manual task.

1. In the left pane, click **Assignment**.
1. On the **Assignment type** tab, select one of the options in the following table. Follow the additional steps for that option before you go to step 3.

    | Option | Users that the task is assigned to | Additional steps |
    |---|---|---|
    | Participant | Users who are assigned to a specific group or role | 1. After you select **Participant**, on the **Role based** tab, in the **Type of participant** list, select the type of group or role to assign the task to. 1. In the **Participant** list, select the group or role to assign the task to. |
    | Hierarchy | Users in a specific organizational hierarchy | 1. After you select **Hierarchy**, on the **Hierarchy selection** tab, in the **Hierarchy type** list, select the type of hierarchy to assign the task to. 1. The system retrieves a range of user names from the hierarchy. These names represent users that the task can be assigned to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves: 1. To specify the starting point, select a person in the **Start from** list. 1. To specify the ending point, select **Add condition** and then enter a condition that determines where in the hierarchy the system stops retrieving names. 1. On the **Hierarchy options** tab, specify which users in the range the task should be assigned to: **Assign to all users retrieved** – The task is assigned to all users in the range. **Assign only to last user retrieved** – The task is assigned to only the last user in the range. **Exclude users with the following condition** – The task isn't assigned to users in the range who meet a specific condition. Select **Add condition** to specify the condition. |
    | Workflow user | Users in the current workflow | After you select **Workflow user**, on the **Workflow user** tab, in the **Workflow user** list, select a user who participates in the workflow. |
    | User | Specific users | 1. After you select **User**, select the **User** tab. 1. The **Available users** list includes all users. Select the users to assign the task to, and then move those users to the **Selected users** list. |
    | Queue | A work item queue | 1. After you select **Queue**, select the **Queue based** tab. 1. To assign the task to a specific queue, follow these steps: 1. In the **Queue type** list, select **Work item queues**. 1. In the **Queue name** list, select the queue. 1. If a specific condition should determine which queue the task is assigned to, follow these steps: 1. In the **Queue type** list, select **Conditional work item queues**. 1. In the **Queue name** list, select **Conditional queue**. **NOTE:** This option is used for only a few workflows, such as Case management. |

1. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to complete the task. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to complete the task. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to complete the task. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to complete the task.
    - **Months** – Select the day and week that the user must complete the task by. For example, you might want the user to complete the task by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must complete the task by. For example, you might want the user to complete the task by Friday of the third week of December.

    If the user doesn't complete the task in the allotted time, the task is overdue. You can escalate an overdue task based on the options that you select in the **Escalation** area of the page.

## Specify what happens when the task is overdue

If a user doesn't complete the manual task in the allotted time, the task is overdue. You can escalate an overdue task or automatically assign it to another user. Follow these steps to escalate the task if it's overdue.

1. In the left pane, select **Escalation**.
1. Select the **Use escalation path** check box to create an escalation path. The system automatically assigns the task to the users who are listed in the escalation path. For example, the following table represents an escalation path.

    | Sequence | Escalation path      |
    |----------|----------------------|
    | 1        | Assign to: Donna     |
    | 2        | Assign to: Erin      |
    | 3        | Final action: Reject |

    In this example, the system assigns the overdue task to Donna. If Donna doesn't complete the task in the allotted time, the system assigns the task to Erin. If Erin doesn't complete the task in the allotted time, the system rejects the document that was submitted for processing.

1. To add a user to the escalation path, select **Add escalation**. On the **Assignment type** tab, select one of the options in the following table, and then follow the additional steps for that option before you go to step 4.

    | Option | Users that the task is escalated to | Additional steps |
    |---|---|---|
    | Hierarchy | Users in a specific organizational hierarchy | 1. After you select **Hierarchy**, on the **Hierarchy selection** tab, in the **Hierarchy type** list, select the type of hierarchy to escalate the task to. 1. The system must retrieve a range of user names from the hierarchy. These names represent users that the task can be escalated to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves: 1. To specify the starting point, select a person in the **Start from** list. 1. To specify the ending point, select **Add condition**. Then enter a condition that determines where in the hierarchy the system stops retrieving names. 1. On the **Hierarchy options** tab, specify which users in the range the task should be escalated to: **Assign to all users retrieved** – The task is escalated to all users in the range. **Assign only to last user retrieved** – The task is escalated to only the last user in the range. **Exclude users with the following condition** – This task isn't escalated to users in the range who meet a specific condition. Select **Add condition** to specify the condition. |
    | Workflow user | Users in the current workflow | After you select **Workflow user**, on the **Workflow user** tab, in the **Workflow user** list, select a user who participates in the workflow. |
    | User | Specific users | 1. After you select **User**, select the **User** tab. 1. The **Available users** list includes all users. Select the users to escalate the task to, and then move those users to the **Selected users** list. |

1. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to complete the task. Select one of the following options:

   - **Hours** – Enter the number of hours that the user has to complete the task. Then select the calendar that your organization uses, and enter information about your organization's work week.
   - **Days** – Enter the number of days that the user has to complete the task. Then select the calendar that your organization uses, and enter information about your organization's work week.
   - **Weeks** – Enter the number of weeks that the user has to complete the task.
   - **Months** – Select the day and week that the user must complete the task by. For example, you might want the user to complete the task by Friday of the third week of the month.
   - **Years** – Select the day, week, and month that the user must complete the task by. For example, you might want the user to complete the task by Friday of the third week of December.

1. Repeat steps 3 through 4 for each user that you want to add to the escalation path. You can change the order of the users.
1. If the users in the escalation path don't complete the task in the allotted time, the system takes action on the task. To specify the action that the system takes, select the **Action** row, and then, on the **End action** tab, select an action.

## Specify when the system automatically acts on the task

You can configure the system to take action on the manual task if specific conditions are met. For example, a task requires that a member of the Expense reports department review the receipts that are submitted together with an expense report. According to company policy, this task must be performed if the total amount of the expense report is more than $100. In this scenario, you can configure the system to automatically mark the task as **Complete** when the total amount is less than 100. Follow these steps to specify when the system takes action on the manual task.

1. In the left pane, select **Automatic actions**.
1. Select the **Enable automatic actions** check box.
1. Select **Add condition**.
1. Enter a condition.
1. Enter any additional conditions that are required.
1. To verify that the conditions you entered are configured correctly, follow these steps:

   1. Select **Test**.
   1. On **Test workflow condition**, in **Validate condition**, select a record.
   1. Select **Test**. The system evaluates the record to determine whether it meets the conditions that you defined.
   1. Select **OK** or **Cancel** to return to **Properties**.

1. In **Auto complete action**, select the action that the system should take on the task.

## Specify when to send notifications

You can send notifications to people when you delegate, escalate, complete, or reject a manual task, or when you request a change. Follow these steps to specify when to send notifications and who to send them to.

1. In the left pane, select **Notifications**.
1. Select the check box next to the events that you want to send notifications for:

   - **Delegate** – You assigned the task to another user.
   - **Escalate** – The assigned user didn't complete the task in the allotted time.
   - **Complete** – The assigned user completed the task.
   - **Reject** – The assigned user rejected the document that was submitted.
   - **Request change** – The assigned user requested a change to the document that was submitted.

1. Select the row for an event that you selected in step 2.
1. On the **Notification text** tab, enter the text of the notification.
1. To personalize the notification, insert placeholders. Placeholders are replaced with appropriate information when the notification is shown to users. Follow these steps to insert a placeholder:

   1. In the text box, select where the placeholder should appear.
   1. Select **Insert placeholder**.
   1. In the list that appears, select the placeholder to insert.
   1. Select **Insert**.

1. To add translations of the notification, follow these steps:

   1. Select **Translations**.
   1. On the page that appears, select **Add**.
   1. In the list that appears, select the language for the translation.
   1. In the **Translated text** field, enter the translated text.
   1. To personalize the text, insert placeholders as described in step 5.
   1. Select **Close**.

1. On the **Recipient** tab, specify who to send the notifications to. Select one of the options in the following table, and then follow the additional steps for that option before you go to step 8.

    | Option | Notification recipients | Additional steps |
    |---|---|---|
    | Participant | Users who are assigned to a specific group or role | 1. After you select **Participant**, on the **Role based** tab, in the **Type of participant** list, select the type of group or role to send notifications to. 1. In the **Participant** list, select the group or role to send notifications to. |
    | Workflow user | Users in the current workflow | After you select **Workflow user**, on the **Workflow user** tab, in the **Workflow user** list, select a user who participates in the workflow. |
    | User | Specific users | 1. After you select **User**, select the **User** tab. 1. The **Available users** list includes all users. Select the users to send notifications to, and then move those users to the **Selected users** list. |

1. Repeat steps 3 through 7 for each event that you selected in step 2.

## Set a time limit

Follow these steps if you need to complete the manual task within a specific time.

> [!NOTE]
> The options that you select in this procedure override the options that you selected in the **Assignment** and **Escalation** areas of the page.

1. In the left pane, select **Advanced settings**.
1. Select the **Set a time limit for the workflow element** check box.
1. In the **Duration** field, specify when the task must be completed. Select one of the following options:

   - **Hours** – Enter the number of hours for task completion. Then select the calendar that your organization uses, and enter information about your organization's work week.
   - **Days** – Enter the number of days for task completion. Then select the calendar that your organization uses, and enter information about your organization's work week.
   - **Weeks** – Enter the number of weeks for task completion.
   - **Months** – Select the day and week for task completion. For example, you might want the task to be completed by Friday of the third week of the month.
   - **Years** – Select the day, week, and month for task completion. For example, you might want the task to be completed by Friday of the third week of December.

1. If the time limit is exceeded, the system takes action on the task. In the **Action** list, select the action that the system should take.

## Specify which actions are available to the user

When you assign the manual task to a user, the user must take action on the task. Follow these steps to specify which actions the user can take on the task.

> [!NOTE]
> The available actions vary, depending on the design of the task.

1. In the left pane, select **Advanced settings**.
1. Select the **Complete** check box if the user should be able to mark the task as **Complete**.
1. Select the **Reject** check box if the user should be able to reject the document that was submitted.
1. Select the **Request change** check box if the user should be able to request changes to the document that was submitted.
1. Select the **Delegate** check box if the user should be able to assign the task to another user.
1. Select the **Reassign** check box if the user should be able to reassign the task to another user in the work item queue.
1. Select the **Release** check box if the user should be able to reassign the task to the work item queue. Another user can then complete the task.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
