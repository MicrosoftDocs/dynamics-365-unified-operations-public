---
title: Configure manual decisions in a workflow
description: Learn about how to configure the properties of a manual decision, including outlines on naming decisions and specifying possible outcomes of decisions.
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
ms.assetid: 0bccad77-1a44-4f08-967b-12c62c02afc7
---

# Configure manual decisions in a workflow

[!include [banner](../includes/banner.md)]


This article explains how to configure the properties of a manual decision.

To configure a manual decision in the workflow editor, right-click the manual decision, and then select **Properties** to open the **Properties** page. Then use the following procedures to configure the properties of the manual decision.

## Name the decision

Follow these steps to enter a name for the manual decision.

1. In the left pane, select **Basic Settings**.
1. In the **Name** field, enter a unique name for the manual decision.

## Enter a subject line and instructions

You must provide a subject line and instructions for users assigned to the manual decision. For example, if you're configuring a decision for purchase requisitions, the user assigned to the decision sees the subject line and instructions on the **Purchase requisitions** page. The subject line appears in a message bar on the page. The user can then select the icon in the message bar to view the instructions. Follow these steps to enter a subject line and instructions.

1. In the left pane, select **Basic Settings**.
1. On the **Instructions** tab, in the **Work item subject** field, enter the subject line.
1. To personalize the subject line, insert placeholders. Placeholders are replaced with appropriate data when the subject line is shown to users. Follow these steps to insert a placeholder:

    1. In the text box, select where the placeholder should appear.
    1. Select **Insert placeholder**.
    1. In the list that appears, select the placeholder to insert.
    1. Select **Insert**.

1. To add translations of the subject line, follow these steps:

    1. Select **Translations**.
    1. On the page that appears, select **Add**.
    1. In the list that appears, select the language for the translation.
    1. In the **Translated text** field, enter the text.
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
    1. In the **Translated text** field, enter the text.
    1. To personalize the text, insert placeholders as described in step 6.
    1. Select **Close**.

## Specify the possible outcomes of a decision

Typically, when you assign a document to a decision maker, you ask a question. The answer to this question is usually **Yes** or **No**, or **True** or **False**. Follow these steps to specify the possible outcomes of the manual decision.

1. In the left pane, select **Basic Settings**.
1. On the **Outcomes** tab, in the **Outcome 1** field, enter the name of the outcome or the option.
1. To add translations of the outcome, follow these steps:

    1. Select **Translations**.
    1. On the page that appears, select **Add**.
    1. In the list that appears, select the language for the translation.
    1. In the **Translated text** field, enter the text.
    1. Select **Close**.

1. In the **Outcome 2** field, enter the name of the outcome or the option.
1. To add translations of the outcome, follow these steps:

    1. Select **Translations**.
    1. On the page that appears, select **Add**.
    1. In the list that appears, select the language for the translation.
    1. In the **Translated text** field, enter the text.
    1. Select **Close**.

## Specify when to send notifications

You can send notifications to people when a decision is made, delegated, or escalated. Follow these steps to specify when to send notifications and who receives them.

1. In the left pane, select **Notifications**.
1. Select the check box next to the events that send notifications:

    - **\[Choice 1\]** – The assigned user selects **\[Choice 1\]**.
    - **\[Choice 2\]** – The assigned user selects **\[Choice 2\]**.
    - **Delegate** – The assigned user assigns the decision to another user.
    - **Escalate** – The assigned user doesn't make the decision in the allotted time.

1. Select the row for an event that you selected in step 2.
1. On the **Notification text** tab, enter the text of the notification.
1. To personalize the notification, insert placeholders. Placeholders are replaced with appropriate data when the notification is shown to users. Follow these steps to insert a placeholder:

    1. In the text box, select where the placeholder should appear.
    1. Select **Insert placeholder**.
    1. In the list that appears, select the placeholder to insert.
    1. Select **Insert**.

1. To add translations of the notification, follow these steps:

    1. Select **Translations**.
    1. On the page that appears, select **Add**.
    1. In the list that appears, select the language for the translation.
    1. In the **Translated text** field, enter the text.
    1. To personalize the text, insert placeholders as described in step 5.
    1. Select **Close**.

1. On the **Recipient** tab, specify who receives the notifications. Select one of the options in the following table, and then follow the additional steps for that option before you go to step 8.

| Option | Notification recipients | Additional steps |
|--------|------------------------|------------------|
| Participant | Users who are assigned to a specific group or role | 1. After you select **Participant**, on the **Role based** tab, in the **Type of participant** list, select the type of group or role to send notifications to. 1. In the **Participant** list, select the group or to send notifications to. |
| Workflow user | Users in the current workflow | After you select **Workflow user**, on the **Workflow user** tab, in the **Workflow user** list, select a user who participates in the workflow. |
| User | Specific users | 1. After you select **User**, select the **User** tab. 1. The **Available users** list includes all users. Select the users to send notifications to, and then move those users to the **Selected users** list. |

1. Repeat steps 3 through 7 for each event that you selected in step 2.

## Assign a decision

Follow these steps to specify who should receive a manual decision.

1. In the left pane, select **Assignment**.
1. On the **Assignment type** tab, select one of the options in the following table. Follow the additional steps for that option before you go to step 3.

| Option | Users that the decision is assigned to | Additional steps |
|--------|---------------------------------------|------------------|
| Participant | Users assigned to a specific group or role | 1. After you select **Participant**, on the **Role based** tab, in the **Type of participant** list, select the type of group or role to assign the decision to. 1. In the **Participant** list, select the group or role to assign the decision to. |
| Hierarchy | Users in a specific organizational hierarchy | 1. After you select **Hierarchy**, on the **Hierarchy selection** tab, in the **Hierarchy type** list, select the type of hierarchy to assign the decision to. 1. The system retrieves a range of user names from the hierarchy. These names represent users that the decision can be assigned to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves: 1. To specify the starting point, select a person in the **Start from** list. 1. To specify the ending point, select **Add condition**. Then enter a condition that determines where in the hierarchy the system stops retrieving names. 1. On the **Hierarchy options** tab, specify which users in the range the decision should be assigned to: **Assign to all users retrieved** – The decision is assigned to all users in the range. **Assign only to last user retrieved** – The decision is assigned to only the last user in the range. **Exclude users with the following condition** – The decision isn't assigned to any users in the range who meet a specific condition. Select **Add condition** to specify the condition. |
| Workflow user | Users in the current workflow | After you select **Workflow user**, on the **Workflow user** tab, in the **Workflow user** list, select a user who participates in the workflow. |
| User | Specific users | 1. After you select **User**, select the **User** tab. 1. The **Available users** list includes all users. Select the users to assign the decision to, and then move those users to the **Selected users** list. |

1. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to make the decision. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to make the decision. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to make the decision. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to make the decision.
    - **Months** – Select the day and week that the user must make the decision by. For example, you might want the user to make the decision by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must make the decision by. For example, you might want the user to make the decision by Friday of the third week of December.

    If the user doesn't make the decision in the allotted time, the decision is overdue. You can escalate an overdue decision based on the options that you select in the **Escalation** area of the page.

## Specify what happens when a decision is overdue

If a user doesn't make the decision in the allotted time, the decision is overdue. You can escalate an overdue decision or automatically assign it to another user. Follow these steps to escalate the decision if it's overdue.

1. In the left pane, select **Escalation**.
1. Select the **Use escalation path** check box to create an escalation path. The system automatically assigns the decision to the users who are listed in the escalation path. For example, the following table represents an escalation path.

    | Sequence | Escalation path            |
    |----------|----------------------------|
    | 1        | Assign to: Donna           |
    | 2        | Assign to: Erin            |
    | 3        | Final action: \[Choice 1\] |

    In this example, the system assigns the overdue decision to Donna. If Donna doesn't make the decision in the allotted time, the system assigns the decision to Erin. If Erin doesn't make the decision in the allotted time, the system selects **\[Choice 1\]** as the decision.

1. To add a user to the escalation path, select **Add escalation**. Select one of the options in the following table, and then follow the additional steps for that option before you go to step 4.

| Option | Users that the decision escalates to | Additional steps |
|--------|----------------------------------------|------------------|
| Hierarchy | Users in a specific organizational hierarchy | 1. After you select **Hierarchy**, on the **Hierarchy selection** tab, in the **Hierarchy type** list, select the type of hierarchy to escalate the decision to. 1. The system retrieves a range of user names from the hierarchy. These names represent users that the decision can escalate to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves: 1. To specify the starting point, select a person in the **Start from** list. 1. To specify the ending point, select **Add condition**. Then enter a condition that determines where in the hierarchy the system stops retrieving names. 1. On the **Hierarchy options** tab, specify which users in the range the decision should escalate to: **Assign to all users retrieved** – The decision escalates to all users in the range. **Assign only to last user retrieved** – The decision escalates to only the last user in the range. **Exclude users with the following condition:** – The decision doesn't escalate to any users in the range who meet a specific condition. Select **Add condition** to specify the condition. |
| Workflow user | Users in the current workflow | After you select **Workflow user**, on the **Workflow user** tab, in the **Workflow user** list, select a user who participates in the workflow. |
| User | Specific users | 1. After you select **User**, select the **User** tab. 1. The **Available users** list includes all users. Select the users to escalate the decision to, and then move those users to the **Selected users** list. |

1. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to make the decision. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to make the decision. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to make the decision. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to make the decision.
    - **Months** – Select the day and week that the user must make the decision by. For example, you might want the user to make the decision by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must make the decision by. For example, you might want the user to make the decision by Friday of the third week of December.

1. Repeat steps 3 through 4 for each user that you want to add to the escalation path. You can change the order of the users.
1. If the users in the escalation path don't make the decision in the allotted time, the system makes the decision. To specify the option that the system selects, select the **Action** row, and then, on the **End action** tab, select an option.

## Set a time limit

Follow these steps if you need to make the decision by a specific time.

> [!NOTE]
> The options that you select in this procedure override the options that you selected in the **Assignment** and **Escalation** areas of the page.

1. In the left pane, select **Advanced settings**.
1. Select the **Set a time limit for the workflow element** check box.
1. In the **Duration** field, specify when the decision must be made. Select one of the following options:

    - **Hours** – Enter the number of hours. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks.
    - **Months** – Select the day and week that the decision must be made by. For example, you might want the decision to be made by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the decision must be made by. For example, you might want the decision to be made by Friday of the third week of December.

1. If the time limit is exceeded, the system makes the decision. In the **Action** list, select the option that the system should choose.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
