---
# required metadata

title: Configure approval steps in a workflow
description: This article explains how to configure the properties of an approval step.
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
ms.custom: 192161
ms.assetid: 8b478e3d-d6b4-403b-aae0-f639a71ca36c
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure approval steps in a workflow

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

This article explains how to configure the properties of an approval step.

To configure an approval step in the workflow editor, right-click the approval step, and then click **Properties** to open the **Properties** page. Then use the following procedures to configure the properties of the approval step.

## Name the step
Follow these steps to enter a name for the approval step.

1. In the left pane, click **Basic Settings**.
2. In the **Name** field, enter a unique name for the approval step.

## Enter a subject line and instructions

You must provide a subject line and instructions to users who are assigned to the approval step. For example, if you're configuring an approval step for purchase requisitions, the user who is assigned to the step sees the subject line and instructions on the **Purchase requisitions** page. The subject line appears in a message bar on the page. The user can then click the icon in the message bar to see the instructions. Follow these steps to enter a subject line and instructions.

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

## Assign the approval step

Follow these steps to specify who the approval step should be assigned to.

1. In the left pane, click **Assignment**.
2. On the **Assignment type** tab, select one of the options in the following table, and then follow the additional steps for that option before you go to step 3.

    <table>
    <thead>
    <tr>
    <th>Option</th>
    <th>Users that the approval step is assigned to</th>
    <th>Additional steps</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Participant</td>
    <td>Users who are assigned to a specific group or role</td>
    <td>
    <ol>
    <li>After you select <strong>Participant</strong>, on the <strong>Role based</strong> tab, in the <strong>Type of participant</strong> list, select the type of group or role to assign the step to.</li>
    <li>In the <strong>Participant</strong> list, select the group or role to assign the step to.</li>
    </ol>
    </td>
    </tr>
    <tr>
    <td>Hierarchy</td>
    <td>Users in a specific organizational hierarchy</td>
    <td>
    <ol>
    <li>After you select <strong>Hierarchy</strong>, on the <strong>Hierarchy selection</strong> tab, in the <strong>Hierarchy type</strong> list, select the type of hierarchy to assign the step to.</li>
    <li>The system must retrieve a range of user names from the hierarchy. These names represent users that the step can be assigned to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves:
    <ol>
    <li>To specify the starting point, select a person in the <strong>Start from</strong> list.</li>
    <li>To specify the ending point, click <strong>Add condition</strong>. Then enter a condition that determines where in the hierarchy the system stops retrieving names.</li>
    </ol>
    </li>
    <li>On the <strong>Hierarchy options</strong> tab, specify which users in the range the step should be assigned to:
    <ul>
    <li><strong>Assign to all users retrieved</strong> – The step is assigned to all users in the range.</li>
    <li><strong>Assign only to last user retrieved</strong> – The step is assigned to only the last user in the range.</li>
    <li><strong>Exclude users with the following condition</strong> – The step isn't assigned to any users in the range who meet a specific condition. Click <strong>Add condition</strong> to specify the condition.</li>
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
    <li>The <strong>Available users</strong> list includes all system users. Select the users to assign the step to, and then move those users to the <strong>Selected users</strong> list.</li>
    </ol>
    </td>
    </tr>
    </tbody>
    </table>

3. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to take action on, or respond to, documents that reach the approval step. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to respond. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to respond. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to respond.
    - **Months** – Select the day and week that the user must respond by. For example, you might want the user to respond by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must respond by. For example, you might want the user to respond by Friday of the third week of December.

    If the user doesn't take action on the document in the allotted time, the document is overdue. A document that is overdue is escalated, based on the options that you select in the **Escalation** area of the page.

4. If you assigned the approval step to multiple users or a group of users, on the **Completion policy** tab, select one of the following options:

    - **Single approver** – The action that is applied to the document is determined by the first person who responds. For example, Sam has submitted an expense report for USD 15,000. The expense report is currently assigned to Sue, Jo, and Bill. If Sue is the first person who responds to the document, the action that Sue takes is applied to the document. If Sue rejects the document, it's rejected and sent back to Sam. If Sue approves the document, it's sent to Ann for approval.

        ![Workflow that has an approval process.](./media/workflow_multipleusersinstep.gif)

    - **Majority of approvers** – The action that is applied to the document is determined when most of the approvers respond. For example, Sam has submitted an expense report for USD 15,000. The expense report is currently assigned to Sue, Jo, and Bill. If Sue and Jo are the first two approvers who respond, the action that they take is applied to the document.

        - If Sue approves the document, but Jo rejects it, the document is rejected and sent back to Sam.
        - If both Sue and Jo approve the document, it's sent to Ann for approval.

    - **Percentage of approvers** – The action that is applied to the document is determined when a specific percentage of the approvers respond. For example, Sam has submitted an expense report for USD 15,000. The expense report is currently assigned to Sue, Jo, and Bill, and you entered **50** as the percentage. If Sue and Jo are the first two approvers who respond, the action that they take is applied to the document, because they meet the requirement for 50 percent of approvers.

        - If Sue approves the document, but Jo rejects it, the document is rejected and sent back to Sam.
        - If both Sue and Jo approve the document, it's sent to Ann for approval.

    - **All approvers** – All the approvers must approve the document. Otherwise, the workflow can't continue. For example, Sam has submitted an expense report for USD 15,000. The expense report is currently assigned to Sue, Jo, and Bill. If Sue and Joe approve the document, but Bill rejects it, the document is rejected and sent back to Sam. If Sue, Jo, and Bill all approve the document, it's sent to Ann for approval.

## Specify when the approval step is required

You can specify when the approval step is required. The approval step can always be required, or it can be required only if specific conditions are met.

### The approval step is always required

Follow these steps if the approval step is always required.

1. In the left pane, click **Condition**.
2. Select the **Always run this step** option.

### The approval step is required in specific conditions

The approval step that you're configuring might be required only if specific conditions are met. For example, if you're configuring an approval step for a purchase requisition workflow, you might want the approval step to occur only if the amount of the purchase requisition is more than USD 10,000. Follow these steps to specify when the approval step is required.

1. In the left pane, click **Condition**.
2. Select the **Run this step only when the following condition is met** option.
3. Enter a condition.
4. Enter any additional conditions that are required.
5. To verify that the conditions that you entered are configured correctly, follow these steps:

    1. Click **Test**.
    2. On the **Test workflow condition** page, in the **Validate condition** area, select a record.
    3. Click **Test**. The system evaluates the record to determine whether it meets the conditions that you defined.
    4. Click **OK** or **Cancel** to return to the **Properties** page.

## Specify what happens when the document is overdue

If a user doesn't take action on a document in the allotted time, the document is overdue. A document that is overdue can be escalated, or automatically assigned to another user for approval. Follow these steps to escalate the document if it's overdue.

1. In the left pane, click **Escalation**.
2. Select the **Use escalation path** check box to create an escalation path. The system automatically assigns the document to the users who are listed in the escalation path. For example, the following table represents an escalation path.

    | Sequence | Escalation path      |
    |----------|----------------------|
    | 1        | Assign to: Donna     |
    | 2        | Assign to: Erin      |
    | 3        | Final action: Reject |

    In this example, the system assigns the overdue document to Donna. If Donna doesn't respond in the allotted time, the system assigns the document to Erin. If Erin doesn't respond in the allotted time, the system rejects the document.

3. To add a user to the escalation path, click **Add escalation**. On the **Assignment type** tab, select one of the options in the following table, and then follow the additional steps for that option before you go to step 4.

    <table>
    <thead>
    <tr>
    <th>Option</th>
    <th>Users that the document is escalated to</th>
    <th>Additional steps</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Hierarchy</td>
    <td>Users in a specific organizational hierarchy</td>
    <td>
    <ol>
    <li>After you select <strong>Hierarchy</strong>, on the <strong>Hierarchy selection</strong> tab, in the <strong>Hierarchy type</strong> list, select the type of hierarchy to escalate the document to.</li>
    <li>The system must retrieve a range of user names from the hierarchy. These names represent users that the document can be escalated to. Follow these steps to specify the starting point and ending point of the range of user names that the system retrieves:
    <ol>
    <li>To specify the starting point, select a person in the <strong>Start from</strong> list.</li>
    <li>To specify the ending point, click <strong>Add condition</strong>. Then enter a condition that determines where in the hierarchy the system stops retrieving names.</li>
    </ol>
    </li>
    <li>On the <strong>Hierarchy options</strong> tab, specify which users in the range the document should be escalated to:
    <ul>
    <li><strong>Assign to all users retrieved</strong> – The document is escalated to all users in the range.</li>
    <li><strong>Assign only to last user retrieved</strong> – The document is escalated to only the last user in the range.</li>
    <li><strong>Exclude users with the following condition</strong> – The document isn't escalated to any users in the range who meet a specific condition. Click <strong>Add condition</strong> to specify the condition.</li>
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
    <li>The <strong>Available users</strong> list includes all users. Select the users to escalate the document to, and then move those users to the <strong>Selected users</strong> list.</li>
    </ol>
    </td>
    </tr>
    </tbody>
    </table>

4. On the **Time limit** tab, in the **Duration** field, specify how much time the user has to take action on, or respond to, documents. Select one of the following options:

    - **Hours** – Enter the number of hours that the user has to respond. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days that the user has to respond. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks that the user has to respond.
    - **Months** – Select the day and week that the user must respond by. For example, you might want the user to respond by Friday of the third week of the month.
    - **Years** – Select the day, week, and month that the user must respond by. For example, you might want the user to respond by Friday of the third week of December.

5. Repeat steps 3 through 4 for each user that should be added to the escalation path. You can change the order of the users.
6. If the users in the escalation path don't respond in the allotted time, the system automatically take action on the document. To specify the action that the system takes, select the **Action** row, and then, on the **End action** tab, select an action.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
