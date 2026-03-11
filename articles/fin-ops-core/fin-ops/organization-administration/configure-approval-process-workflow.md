---
title: Configure approval processes in a workflow
description: Learn how to configure the approval processes in a workflow, including outlines on naming the approval process and specifying when notifications are sent.
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
ms.assetid: f853f57b-83ae-4fb0-a9fa-06ea3fc34fa1
---

# Configure approval processes in a workflow

[!include [banner](../includes/banner.md)]

Use the following procedure to configure the properties of the approval process.

To configure an approval process, in the workflow editor, right-click the approval element, and then select **Properties** to open the **Properties** form.

## Name the approval process

Follow these steps to enter a name for the approval process.

1. In the left pane, select **Basic Settings**.
1. In the **Name** field, enter a unique name for the approval process.

## Specify when the system automatically acts on the document

You can configure the system to automatically act on the document if specific conditions are met. For example, the system can approve expense reports that have total amounts that are less than USD 100. Follow these steps to specify when the system acts on the document:

1. In the left pane, select **Automatic actions**.
1. Select the **Enable automatic actions** check box.
1. Select **Add condition**.
1. Enter a condition.
1. Enter additional conditions, if necessary.
1. To verify that the conditions you entered are configured correctly, complete the following steps:

    1. Select **Test** to open the **Test workflow condition** form.
    1. Select a record in the **Validate condition** area of the form.
    1. Select **Test**. The system evaluates the record to determine whether it meets the conditions that you defined.
    1. Select **OK** or **Cancel** to return to the **Properties** form.

1. In the **Auto complete action** list, select the action that the system should take on the document.

## Specify when to send notifications

You can send notifications to people when a document is approved, rejected, delegated, or escalated, or when a change is requested. Follow these steps to specify when to send notifications and who receives them.

1. In the left pane, select **Notifications**.
1. Select the check box next to the events to send notifications for:

    - **Delegate** – When a document is assigned to another user for approval.
    - **Escalate** – When the assigned user doesn't act on a document in the allotted time.
    - **Approve** – When a document is approved.
    - **Reject** – When a document is rejected.
    - **Request change** – When the assigned user requests a change to a submitted document.

1. Select the row for an event that you selected in step 2.
1. Select the **Notification text** tab.
1. In the text box, enter the text for the notification.
1. To personalize the text, insert placeholders, which are replaced with the appropriate data when they're displayed to users. To insert a placeholder, follow these steps:

    1. Select the text box at the location where the placeholder should appear.
    1. Select **Insert placeholder**.
    1. In the list that appears, select the placeholder to insert.
    1. Select **Insert**.

1. To add translations of the notification, select **Translations**. In the form that appears, follow these steps:

    1. Select **Add**.
    1. In the list that appears, select the language for the text.
    1. In the **Translated text** text box, enter the text.
    1. To personalize the text, insert placeholders.
    1. Select **Close**.

1. Select the **Recipient** tab.
1. Specify who receives the notifications. Select one of the options in the following table, and then follow the additional steps for the option before you go to step 10.

| Option | Notification recipients | Additional steps |
|---|---|---|
| **Participant** | Users who are assigned to a specific group or role | 1. After you select **Participant**, select the **Role based** tab. 1. In the **Type of participant** list, select the type of group or role to send notifications to. 1. In the **Participant** list, select the group or role to send notifications to. |
| **Workflow user** | Users who participate in the current workflow | 1. After you select **Workflow user**, select the **Workflow user** tab. 1. In the **Workflow user** list, select a user who participates in the workflow. |
| **User** | Specific users | 1. After you select **User**, select the **User** tab. 1. Select the users to send notifications to, and then move these users to the **Selected users** list. |

1. Repeat steps 3 through 9 for each event that you selected in step 2.

## Specify a final approver

To require extra approval when the user who submitted the document also approves it, specify a final approver for the approval step.

1. In the workflow editor, right-click the approval element, and then select **Properties** to open the **Properties** form.
1. In the left pane, select **Advanced settings**.
1. Select the **Use final approver** check box.
1. In the list, select a user to be the final approver.

## Prevent the submitter from approving steps in the workflow

To prevent users who submit documents for approval from approving the documents themselves, follow these steps:

1. Go to **System administration > Workflow > Workflow parameters > General > Approver**.
1. Update the **Disallow approval by submitter** setting on the workflow to **Yes**.

By default, this setting is **No**, and users can approve the document if they're included in the approval step's assignment settings.

If you set the workflow to **Disallow approval by submitter** and include approval steps with a final approver, make sure the final approver isn't a user who typically submits documents to workflow, since they can't complete the approval.

## Set a time limit

Follow these steps if you need to complete the approval process within a specific time.

> [!NOTE]
> The options that you select in these steps override the options that you selected in the **Assignment** and **Escalation** areas of each approval step.

1. In the left pane, select **Advanced settings**.
1. Select the **Set a time limit for the workflow** **element** check box.
1. In the **Duration** field, specify when the approval process must be completed. Select one of the following options:

    - **Hours** – Enter the number of hours in which the approval process must be completed. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Days** – Enter the number of days in which the approval process must be completed. Then select the calendar that your organization uses, and enter information about your organization's work week.
    - **Weeks** – Enter the number of weeks in which the approval process must be completed.
    - **Months** – Select the day and week by which the approval process must be completed. For example, you might want the approval process to be completed by Friday of the third week of the month.
    - **Years** – Select the day, week, and month by which the approval process must be completed. For example, you might want the approval process to be completed by Friday of the third week of December.

1. If the time limit is exceeded, the system acts on the document. In the **Action** list, select the action that the system should take.

## Specify which actions are available to the user

When you assign a document to a user for approval, the user must act on the document. Follow these steps to specify which actions the user can take on the submitted document.

1. In the left pane, select **Advanced settings**.
1. Select the **Approve** check box if the user can approve the document.
1. Select the **Reject** check box if the user can reject the document.
1. Select the **Request change** check box if the user can request changes to the document.
1. Select the **Delegate** check box if the user can assign the document to another user for approval.

> [!NOTE]
> The **Enable actions from the work list in Enterprise Portal** check box is deprecated.

## Configure the approval steps

An approval process consists of approval steps. Complete the following procedure to add steps to the approval process and configure the steps.

1. In the workflow editor, double-click the approval process. The workflow editor displays the steps of the approval process.
1. To add an approval step, drag the step from the **Workflow elements** area to the canvas.
1. To configure an approval step, see [Configure approval steps in a workflow](configure-approval-step-workflow.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
