---
# required metadata

title: Configure manual tasks in a workflow
description: This article explains how to configure the properties for a manual task.
author: ChrisGarty
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 192191
ms.assetid: 27f1afde-ff26-4b6f-8c11-27ec49130bbb
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure manual tasks in a workflow

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

This article explains how to configure the properties for a manual task.

To configure a manual task in the workflow editor, right-click the task, and then click **Properties** to open the **Properties** page. Then use the following procedures to configure the properties for the manual task.

## Name the task

Follow these steps to enter a name for the manual task.

1. In the left pane, click **Basic Settings**.
2. In the **Name** field, enter a unique name for the task.

## Enter a subject line and instructions

You must provide a subject line and instructions to users who are assigned to the task. For example, if you're configuring a task for purchase requisitions, the user who is assigned to the task sees the subject line and instructions on the **Purchase requisitions** page. The subject line appears in a message bar on the page. The user can then click the icon in the message bar to view the instructions. Follow these steps to enter a subject line and instructions.

1. In the left pane, click **Basic Settings**.
2. In the **Work item subject** field, enter the subject line.
3. To personalize the subject line, you can insert placeholders. Placeholders are replaced with appropriate data when the subject line is shown to users. Follow these steps to insert a placeholder:

    1. In the text box, click where the placeholder should appear.
    2. Click **Insert placeholder**.
    3. In the list that appears, select the placeholder to insert.
    4. Click **Insert**.

4. To add translations of the subject line, follow these steps:

    1. Click **Translations**.
    2. On the page that appears, click **Add**.
    3. In the list that appears, select the language that you're entering the text in.
    4. In the **Translated text** field, enter the text.
    5. To personalize the text, you can insert placeholders as described in step 3.
    6. Click **Close**.

5. In the **Work item instructions** field, enter the instructions.
6. To personalize the instructions, you can insert placeholders. Placeholders are replaced with appropriate data when the instructions are shown to users. Follow these steps to insert a placeholder:

    1. In the text box, click where the placeholder should appear.
    2. Click **Insert placeholder**.
    3. In the list that appears, select the placeholder to insert.
    4. Click **Insert**.

7. To add translations of the instructions, follow these steps:

    1. Click **Translations**.
    2. On the page that appears, click **Add**.
    3. In the list that appears, select the language that you're entering the text in.
    4. In the **Translated text** field, enter the text.
    5. To personalize the text, you can insert placeholders as described in step 6.
    6. Click **Close**.

## Assign the task

Follow these steps to specify who the manual task should be assigned to.

1. In the left pane, click **Assignment**.
2. On the **Assignment type** tab, select one of the options in the following table, and then follow the additional steps for that option before you go to step 3.

    <table>
    <thead>
    <tr>
    <th>Option</th>
    <th>Users that the task is assigned to</th>
    <th>Additional steps</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Participant</td>
    <td>Users who are assigned to a specific group or role</td>
    <td>
    <ol>
    <li>After you select <strong>Participant</strong>, on the <strong>Role based</strong> tab, in the <strong>Type of participant</strong> list, select the type of group or role to assign the task to.</li>
    <li>In the <strong>Participant</strong> list, select the group or role to assign the task to.</li>
    </ol>
    </td>
    </tr>
    <tr>
    <td>Hierarchy</td>
    <td>Users in a specific organizational hierarchy</td>
    <td>
    <ol>
    <li>After you select <strong>Hierarchy</strong>, on the <strong>Hierarchy selection</strong> tab, in the <strong>Hierarchy type</strong> list, select the type of hierarchy to assign the task to.</li>
    <li>The system must retrieve a range of user names from the hierarchy. These names represent users that the task can be assigned to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves:
    <ol>
    <li>To specify the starting point, select a person in the <strong>Start from</strong> list.</li>
    <li>To specify the ending point, click <strong>Add condition</strong>. Then enter a condition that determines where in the hierarchy the system stops retrieving names.</li>
    </ol>
    </li>
    <li>On the <strong>Hierarchy options</strong> tab, specify which users in the range the task should be assigned to:
    <ul>
    <li><strong>Assign to all users retrieved</strong> – The task is assigned to all users in the range.</li>
    <li><strong>Assign only to last user retrieved</strong> – The task is assigned to only the last user in the range.</li>
    <li><strong>Exclude users with the following condition</strong> – The task isn't assigned to users in the range who meet a specific condition. Click <strong>Add condition</strong> to specify the condition.</li>
    </ul>
    </li>
    </ol>
    </td>
    </tr>
    <tr>
    <td>Workflow user</td>
    <td>Users in the current workflow</td>
    <td>
    <ul>
    <li>After you select <strong>Workflow user</strong>, on the <strong>Workflow user</strong> tab, in the <strong>Workflow user</strong> list, select a user who participates in the workflow.</li>
    </ul>
    </td>
    </tr>
    <tr>
    <td>User</td>
    <td>Specific users</td>
    <td>
    <ol>
    <li>After you select <strong>User</strong>, click the <strong>User</strong> tab.</li>
    <li>The <strong>Available users</strong> list includes all users. Select the users to assign the task to, and then move those users to the <strong>Selected users</strong> list.</li>
    </ol>
    </td>
    </tr>
    <tr>
    <td>Queue</td>
    <td>A work item queue</td>
    <td>
    <ol>
    <li>After you select <strong>Queue</strong>, click the <strong>Queue based</strong> tab.</li>
    <li>To assign the task to a specific queue, follow these steps:
    <ol>
    <li>In the <strong>Queue type</strong> list, select <strong>Work item queues</strong>.</li>
    <li>In the <strong>Queue name</strong> list, select the queue.</li>
    </ol>
    </li>
    <li>If a specific condition should determine which queue the task is assigned to, follow these steps:
    <ol>
    <li>In the <strong>Queue type</strong> list, select <strong>Conditional work item queues</strong>.</li>
    <li>In the <strong>Queue name</strong> list, select <strong>Conditional queue</strong>.</li>
    </ol>
    </li>
    </ol>
    <strong>NOTE: </strong>This option is used for only a few workflows, such as Case management.
    </td>
    </tr>
    </tbody>
    </table>

3. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to complete the task. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to complete the task. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to complete the task. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to complete the task.
    - **Months** – Select the day and week that the user must complete the task by. For example, you might want the user to complete the task by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must complete the task by. For example, you might want the user to complete the task by Friday of the third week of December.

    If the user doesn't complete the task in the allotted time, the task is overdue. A task that is overdue can be escalated, based on the options that you select in the **Escalation** area of the page.

## Specify what happens when the task is overdue

If a user doesn't complete the manual task in the allotted time, the task is overdue. A task that is overdue can be escalated, or automatically assigned to another user. Follow these steps to escalate the task if it's overdue.

1. In the left pane, click **Escalation**.
2. Select the **Use escalation path** check box to create an escalation path. The system automatically assigns the task to the users who are listed in the escalation path. For example, the following table represents an escalation path.

    | Sequence | Escalation path      |
    |----------|----------------------|
    | 1        | Assign to: Donna     |
    | 2        | Assign to: Erin      |
    | 3        | Final action: Reject |

    In this example, the system assigns the overdue task to Donna. If Donna doesn't complete the task in the allotted time, the system assigns the task to Erin. If Erin doesn't complete the task in the allotted time, the system rejects the document that was submitted for processing.

3. To add a user to the escalation path, click **Add escalation**. On the **Assignment type** tab, select one of the options in the following table, and then follow the additional steps for that option before you go to step 4.

    <table>
    <thead>
    <tr>
    <th>Option</th>
    <th>Users that the task is escalated to</th>
    <th>Additional steps</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Hierarchy</td>
    <td>Users in a specific organizational hierarchy</td>
    <td>
    <ol>
    <li>After you select <strong>Hierarchy</strong>, on the <strong>Hierarchy selection</strong> tab, in the <strong>Hierarchy type</strong> list, select the type of hierarchy to escalate the task to.</li>
    <li>The system must retrieve a range of user names from the hierarchy. These names represent users that the task can be escalated to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves:
    <ol>
    <li>To specify the starting point, select a person in the <strong>Start from</strong> list.</li>
    <li>To specify the ending point, click <strong>Add condition</strong>. Then enter a condition that determines where in the hierarchy the system stops retrieving names.</li>
    </ol>
    </li>
    <li>On the <strong>Hierarchy options</strong> tab, specify which users in the range the task should be escalated to:
    <ul>
    <li><strong>Assign to all users retrieved</strong> – The task is escalated to all users in the range.</li>
    <li><strong>Assign only to last user retrieved</strong> – The task is escalated to only the last user in the range.</li>
    <li><strong>Exclude users with the following condition</strong> – This task isn't escalated to users in the range who meet a specific condition. Click <strong>Add condition</strong> to specify the condition.</li>
    </ul>
    </li>
    </ol>
    </td>
    </tr>
    <tr>
    <td>Workflow user</td>
    <td>Users in the current workflow</td>
    <td>
    <ul>
    <li>After you select <strong>Workflow user</strong>, on the <strong>Workflow user</strong> tab, in the <strong>Workflow user</strong> list, select a user who participates in the workflow.</li>
    </ul>
    </td>
    </tr>
    <tr>
    <td>User</td>
    <td>Specific users</td>
    <td>
    <ol>
    <li>After you select <strong>User</strong>, click the <strong>User</strong> tab.</li>
    <li>The <strong>Available users</strong> list includes all users. Select the users to escalate the task to, and then move those users to the <strong>Selected users</strong> list.</li>
    </ol>
    </td>
    </tr>
    </tbody>
    </table>

4. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to complete the task. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to complete the task. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to complete the task. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to complete the task.
    - **Months** – Select the day and week that the user must complete the task by. For example, you might want the user to complete the task by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must complete the task by. For example, you might want the user to complete the task by Friday of the third week of December.

5. Repeat steps 3 through 4 for each user that should be added to the escalation path. You can change the order of the users.
6. If the users in the escalation path don't complete the task in the allotted time, the system takes action on the task. To specify the action that the system takes, select the **Action** row, and then, on the **End action** tab, select an action.

## Specify when the system automatically acts on the task

You can configure the system to take action on the manual task if specific conditions are met. For example, a task requires that a member of the Expense reports department review the receipts that are submitted together with an expense report. According to company policy, this task must be performed if the total amount of the expense report is more than USD 100. In this scenario, you can configure the system to automatically mark the task as **Complete** when the total amount is less than 100. Follow these steps to specify when the system takes action on the manual task.

1. In the left pane, click **Automatic actions**.
2. Select the **Enable automatic actions** check box.
3. Click **Add condition**.
4. Enter a condition.
5. Enter any additional conditions that are required.
6. To verify that the conditions that you entered are configured correctly, follow these steps:

    1. Click **Test**.
    2. On the **Test workflow condition** page, in the **Validate condition** area, select a record.
    3. Click **Test**. The system evaluates the record to determine whether it meets the conditions that you defined.
    4. Click **OK** or **Cancel** to return to the **Properties** page.

7. In the **Auto complete action** list, select the action that the system should take on the task.

## Specify when notifications are sent

You can send notifications to people when a manual task has been delegated, escalated, completed, or rejected, or when a change has been requested. Follow these steps to specify when notifications are sent, and who the notifications are sent to.

1. In the left pane, click **Notifications**.
2. Select the check box next to the events that notifications should be sent for:

    - **Delegate** – The task has been assigned to another user.
    - **Escalate** – The assigned user hasn't completed the task in the allotted time.
    - **Complete** – The assigned user has completed the task.
    - **Reject** – The assigned user has rejected the document that was submitted.
    - **Request change** – The assigned user has requested a change to the document that was submitted.

3. Select the row for an event that you selected in step 2.
4. On the **Notification text** tab, in the text box, enter the text of the notification.
5. To personalize the notification, you can insert placeholders. Placeholders are replaced with appropriate information when the notification is shown to users. Follow these steps to insert a placeholder:

    1. In the text box, click where the placeholder should appear.
    2. Click **Insert placeholder**.
    3. In the list that appears, select the placeholder to insert.
    4. Click **Insert**.

6. To add translations of the notification, follow these steps:

    1. Click **Translations**.
    2. On the page that appears, click **Add**.
    3. In the list that appears, select the language that you're entering the text in.
    4. In the **Translated text** field, enter the text.
    5. To personalize the text, you can insert placeholders as described in step 5.
    6. Click **Close**.

7. On the **Recipient** tab, specify who the notifications are sent to. Select one of the options in the following table, and then follow the additional steps for that option before you go to step 8.

    <table>
    <thead>
    <tr>
    <th>Option</th>
    <th>Notification recipients</th>
    <th>Additional steps</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Participant</td>
    <td>Users who are assigned to a specific group or role</td>
    <td>
    <ol>
    <li>After you select <strong>Participant</strong>, on the <strong>Role based</strong> tab, in the <strong>Type of participant</strong> list, select the type of group or role to send notifications to.</li>
    <li>In the <strong>Participant</strong> list, select the group or role to send notifications to.</li>
    </ol>
    </td>
    </tr>
    <tr>
    <td>Workflow user</td>
    <td>Users in the current workflow</td>
    <td>
    <ul>
    <li>After you select <strong>Workflow user</strong>, on the <strong>Workflow user</strong> tab, in the <strong>Workflow user</strong> list, select a user who participates in the workflow.</li>
    </ul>
    </td>
    </tr>
    <tr>
    <td>User</td>
    <td>Specific users</td>
    <td>
    <ol>
    <li>After you select <strong>User</strong>, click the <strong>User</strong> tab.</li>
    <li>The <strong>Available users</strong> list includes all users. Select the users to send notifications to, and then move those users to the <strong>Selected users</strong> list.</li>
    </ol>
    </td>
    </tr>
    </tbody>
    </table>

8. Repeat steps 3 through 7 for each event that you selected in step 2.

## Set a time limit

Follow these steps if the manual task must be completed in a specific time.

> [!NOTE]
> The options that you select in this procedure override the options that you selected in the **Assignment** and **Escalation** areas of the page.

1. In the left pane, click **Advanced settings**.
2. Select the **Set a time limit for the workflow element** check box.
3. In the **Duration** field, specify when the task must be completed. Select one of the following options:

    - **Hours** – Enter the number of hours that the task must be completed in. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the task must be completed in. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the task must be completed in.
    - **Months** – Select the day and week that the task must be completed by. For example, you might want the task to be completed by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the task must be completed by. For example, you might want the task to be completed by Friday of the third week of December.

4. If the time limit is exceeded, the system takes action on the task. In the **Action** list, select the action that the system should take.

## Specify which actions are available to the user

When the manual task is assigned to a user, the user must take action on the task. Follow these steps to specify which actions the user can take on the task.

> [!NOTE]
> The actions that are available vary, depending on the design of the task.

1. In the left pane, click **Advanced settings**.
2. Select the **Complete** check box if the user should be able to mark the task as **Complete**.
3. Select the **Reject** check box if the user should be able to reject the document that was submitted.
4. Select the **Request change** check box if the user should be able to request changes to the document that was submitted.
5. Select the **Delegate** check box if the user should be able to assign the task to another user.
6. Select the **Reassign** check box if the user should be able to reassign the task to another user in the work item queue.
7. Select the **Release** check box if the user should be able to reassign the task to the work item queue. Another user can then complete the task.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
