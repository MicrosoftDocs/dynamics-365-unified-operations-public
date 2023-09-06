---
# required metadata

title: Configure manual decisions in a workflow
description: This article explains how to configure the properties of a manual decision.
author: ChrisGarty
ms.date: 06/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 192101
ms.assetid: 0bccad77-1a44-4f08-967b-12c62c02afc7
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure manual decisions in a workflow

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article explains how to configure the properties of a manual decision.

To configure a manual decision in the workflow editor, right-click the manual decision, and then click **Properties** to open the **Properties** page. Then use the following procedures to configure the properties of the manual decision.

## Name the decision

Follow these steps to enter a name for the manual decision.

1. In the left pane, click **Basic Settings**.
2. In the **Name** field, enter a unique name for the manual decision.

## Enter a subject line and instructions

You must provide a subject line and instructions to users who are assigned to the manual decision. For example, if you're configuring a decision for purchase requisitions, the user who is assigned to the decision sees the subject line and instructions on the **Purchase requisitions** page. The subject line appears in a message bar on the page. The user can then click the icon in the message bar to view the instructions. Follow these steps to enter a subject line and instructions.

1. In the left pane, click **Basic Settings**.
2. On the **Instructions** tab, in the **Work item subject** field, enter the subject line.
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

## Specify the possible outcomes of a decision

Typically, when a document is assigned to a decision maker, the decision maker is asked a question. The answer to this question is usually **Yes** or **No**, or **True** or **False**. Follow these steps to specify the possible outcomes of the manual decision.

1. In the left pane, click **Basic Settings**.
2. On the **Outcomes** tab, in the **Outcome 1** field, enter the name of the outcome, or the option.
3. To add translations of the outcome, follow these steps:

    1. Click **Translations**.
    2. On the page that appears, click **Add**.
    3. In the list that appears, select the language that you're entering the text in.
    4. In the **Translated text** field, enter the text.
    5. Click **Close**.

4. In the **Outcome 2** field, enter the name of the outcome, or the option.
5. To add translations of the outcome, follow these steps:

    1. Click **Translations**.
    2. On the page that appears, click **Add**.
    3. In the list that appears, select the language that you're entering the text in.
    4. In the **Translated text** field, enter the text.
    5. Click **Close**.

## Specify when notifications are sent

You can send notifications to people when a decision has been made, delegated, or escalated. Follow these steps to specify when notifications are sent, and who the notifications are sent to.

1. In the left pane, click **Notifications**.
2. Select the check box next to the events that notifications should be sent for:

    - **\[Choice 1\]** – The assigned user has selected **\[Choice 1\]**.
    - **\[Choice 2\]** – The assigned user has selected **\[Choice 2\]**.
    - **Delegate** – The assigned user has assigned the decision to another user.
    - **Escalate** – The assigned user hasn't made the decision in the allotted time.

3. Select the row for an event that you selected in step 2.
4. On the **Notification text** tab, in the text box, enter the text of the notification.
5. To personalize the notification, you can insert placeholders. Placeholders are replaced with appropriate data when the notification is show to users. Follow these steps to insert a placeholder:

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
    <li>In the <strong>Participant</strong> list, select the group or to send notifications to.</li>
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

## Assign a decision

Follow these steps to specify who a manual decision should be assigned to.

1. In the left pane, click **Assignment**.
2. On the **Assignment type** tab, select one of the options in the following table, and then follow the additional steps for that option before you go to step 3.

    <table>
    <thead>
    <tr>
    <th>Option</th>
    <th>Users that the decision is assigned to</th>
    <th>Additional steps</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Participant</td>
    <td>Users who are assigned to a specific group or role</td>
    <td>
    <ol>
    <li>After you select <strong>Participant</strong>, on the <strong>Role based</strong> tab, in the <strong>Type of participant</strong> list, select the type of group or role to assign the decision to.</li>
    <li>In the <strong>Participant</strong> list, select the group or role to assign the decision to.</li>
    </ol>
    </td>
    </tr>
    <tr>
    <td>Hierarchy</td>
    <td>Users in a specific organizational hierarchy</td>
    <td>
    <ol>
    <li>After you select <strong>Hierarchy</strong>, on the <strong>Hierarchy selection</strong> tab, in the <strong>Hierarchy type</strong> list, select the type of hierarchy to assign the decision to.</li>
    <li>The system must retrieve a range of user names from the hierarchy. These names represent users that the decision can be assigned to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves:
    <ol>
    <li>To specify the starting point, select a person in the <strong>Start from</strong> list.</li>
    <li>To specify the ending point, click <strong>Add condition</strong>. Then enter a condition that determines where in the hierarchy the system stops retrieving names.</li>
    </ol>
    </li>
    <li>On the <strong>Hierarchy options</strong> tab, specify which users in the range the decision should be assigned to:
    <ul>
    <li><strong>Assign to all users retrieved</strong> – The decision is assigned to all users in the range.</li>
    <li><strong>Assign only to last user retrieved</strong> – The decision is assigned to only the last user in the range.</li>
    <li><strong>Exclude users with the following condition</strong> – The decision isn't assigned to any users in the range who meet a specific condition. Click <strong>Add condition</strong> to specify the condition.</li>
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
    <li>The <strong>Available users</strong> list includes all users. Select the users to assign the decision to, and then move those users to the <strong>Selected users</strong> list.</li>
    </ol>
    </td>
    </tr>
    </tbody>
    </table>

3. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to make the decision. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to make the decision. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to make the decision. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to make the decision.
    - **Months** – Select the day and week that the user must make the decision by. For example, you might want the user to make the decision by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must make the decision by. For example, you might want the user to make the decision by Friday of the third week of December.

    If the user doesn't make the decision in the allotted time, the decision is overdue. A decision that is overdue is escalated, based on the options that you select in the **Escalation** area of the page.

## Specify what happens when a decision is overdue

If a user doesn't make the decision in the allotted time, the decision is overdue. A decision that is overdue can be escalated, or automatically assigned to another user. Follow these steps to escalate the decision if it's overdue.

1. In the left pane, click **Escalation**.
2. Select the **Use escalation path** check box to create an escalation path. The system automatically assigns the decision to the users who are listed in the escalation path. For example, the following table represents an escalation path.

    | Sequence | Escalation path            |
    |----------|----------------------------|
    | 1        | Assign to: Donna           |
    | 2        | Assign to: Erin            |
    | 3        | Final action: \[Choice 1\] |

    In this example, the system assigns the overdue decision to Donna. If Donna doesn't make the decision in the allotted time, the system assigns the decision to Erin. If Erin doesn't make the decision in the allotted time, the system selects **\[Choice 1\]** as the decision.

3. To add a user to the escalation path, click **Add escalation**. Select one of the options in the following table, and then follow the additional steps for that option before you go to step 4.

    <table>
    <thead>
    <tr>
    <th>Option</th>
    <th>Users that the decision is escalated to</th>
    <th>Additional steps</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Hierarchy</td>
    <td>Users in a specific organizational hierarchy</td>
    <td>
    <ol>
    <li>After you select <strong>Hierarchy</strong>, on the <strong>Hierarchy selection</strong> tab, in the <strong>Hierarchy type</strong> list, select the type of hierarchy to escalate the decision to.</li>
    <li>The system must retrieve a range of user names from the hierarchy. These names represent users that the decision can be escalated to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves:
    <ol>
    <li>To specify the starting point, select a person in the <strong>Start from</strong> list.</li>
    <li>To specify the ending point, click <strong>Add condition</strong>. Then enter a condition that determines where in the hierarchy the system stops retrieving names.</li>
    </ol>
    </li>
    <li>On the <strong>Hierarchy options</strong> tab, specify which users in the range the decision should be escalated to:
    <ul>
    <li><strong>Assign to all users retrieved</strong> – The decision is escalated to all users in the range.</li>
    <li><strong>Assign only to last user retrieved</strong> – The decision is escalated to only the last user in the range.</li>
    <li><strong>Exclude users with the following condition:</strong> – The decision isn't escalated to any users in the range who meet a specific condition. Click <strong>Add condition</strong> to specify the condition.</li>
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
    <li>The <strong>Available users</strong> list includes all users. Select the users to escalate the decision to, and then move those users to the <strong>Selected users</strong> list.</li>
    </ol>
    </td>
    </tr>
    </tbody>
    </table>

4. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to make the decision. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to make the decision. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to make the decision. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to make the decision.
    - **Months** – Select the day and week that the user must make the decision by. For example, you might want the user to make the decision by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must make the decision by. For example, you might want the user to make the decision by Friday of the third week of December.

5. Repeat steps 3 through 4 for each user that should be added to the escalation path. You can change the order of the users.
6. If the users in the escalation path don't make the decision in the allotted time, the system makes the decision. To specify the option that the system selects, select the **Action** row, and then, on the **End action** tab, select an option.

## Set a time limit

Follow these steps if the decision must be made in a specific time.

> [!NOTE]
> The options that you select in this procedure override the options that you selected in the **Assignment** and **Escalation** areas of the page.

1. In the left pane, click **Advanced settings**.
2. Select the **Set a time limit for the workflow element** check box.
3. In the **Duration** field, specify when the decision must be made. Select one of the following options:

    - **Hours** – Enter the number of hours. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks.
    - **Months** – Select the day and week that the decision must be made by. For example, you might want the decision to be made by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the decision must be made by. For example, you might want the decision to be made by Friday of the third week of December.

4. If the time limit is exceeded, the system makes the decision. In the **Action** list, select the option that the system should select.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
