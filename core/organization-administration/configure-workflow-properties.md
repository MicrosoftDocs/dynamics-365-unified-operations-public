---
# required metadata

title: Configure the properties of a workflow
description: This topic explains how to configure the various properties of a workflow.
author: sericks007
manager: AnnBe
ms.date: 2016-09-30 20 - 52 - 55
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 196083
ms.assetid: 742a7ae4-d571-441c-a126-1cccf6b1d600
ms.search.region: Global
# ms.search.industry: 
ms.author: donaldc
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Configure the properties of a workflow

This topic explains how to configure the various properties of a workflow.

To configure the properties of a workflow, open the workflow in the workflow editor. Click the canvas of the workflow editor, and then click **Properties** to open the **Properties** page. You can then use the following procedures to configure the various properties of the workflow.

## Name the workflow
Follow these steps to enter a name for the workflow.

1.  In the left pane, click **Basic Settings**.
2.  In the **Name** field, enter a unique name for the workflow. For example, if you create a purchase requisition workflow for each country/region that you operate in, you can name the purchase requisition workflow **Purchase Requisitions Denmark** or **Purchase Requisitions Spain**.

## Specify the workflow owner
The workflow owner is the person who manages and maintains the workflow. Follow these steps to specify the workflow owner.

1.  In the left pane, click **Basic Settings**.
2.  In the **Owner** list, select the name of the person who will manage the workflow.

## Select an email template
Follow these steps to select the email template that is used to generate notification messages about the workflow.

1.  In the left pane, click **Basic Settings**.
2.  In the **Email template for workflow notifications** list, select the template.

## Enter instructions for users
You can provide instructions to users who submit documents for processing and approval. These users are also referred to as *originators*. For example, you're creating a purchase requisition workflow, and you enter instructions. Those instructions can then be viewed by users who enter purchase requisitions on the **Purchase requisitions** page. To view instructions, the originator clicks the icon in the workflow message bar. Follow these steps to enter instructions for users.

1.  In the left pane, click **Basic Settings**.
2.  In the **Submission instructions** field, enter the instructions.
3.  To personalize the instructions, you can insert placeholders. Placeholders are replaced with the appropriate data when the instructions are shown to users. To insert a placeholder, follow these steps:
    1.  Click in the **Submission instructions** field to specify where the placeholder should appear.
    2.  Click **Insert placeholder**.
    3.  In the list that appears, select the placeholder to insert.
    4.  Click **Insert**.

4.  To add translations of the instructions, follow these steps:
    1.  Click **Translations**.
    2.  On the page that appears, click **Add**.
    3.  In the list that appears, select the language that you will enter the text in.
    4.  In the **Translated text** field, enter the text.
    5.  To personalize the text, you can insert placeholders. For instructions about how to enter a placeholder, see step 3.
    6.  Click **Close**.

## Specify when this workflow is used
You can create multiple workflows that are based on the same type. For example, you can create a purchase requisition workflow for each country/region that you operate in, such as Purchase Requisitions Denmark and Purchase Requisitions Spain. When you have multiple workflows that are based on the same type, you must specify when each workflow is used. For the preceding example, you specify the following conditions:

-   Purchase Requisitions Denmark is used when: country/region = DK
-   Purchase Requisitions Spain is used when: country/region = ES

Follow these steps to specify when the workflow that you're configuring is used.

1.  In the left pane, click **Activation**.
2.  Select the **Set the conditions for running this workflow** check box.
3.  Click **Add condition**.
4.  Enter a condition.
5.  Enter any additional conditions that are required.
6.  To verify that the conditions that you entered are set correctly, follow these steps:
    1.  Click **Test**.
    2.  On the **Test workflow condition** page, in the **Validate condition** area, select a record.
    3.  Click **Test**. The system evaluates the record to determine whether it meets the conditions that you specified. For example, if you're creating a purchase requisition workflow for Spain, the **Validate condition** area of the page shows a list of purchase requisitions. When you click **Test**, the system evaluates the selected purchase requisition to determine whether the country/region is ES.
    4.  Click **OK** or **Cancel** to return to the **Properties** page.

## Specify when notifications are sent
When a document is submitted for processing, a workflow instance is created. You can send notifications to users when workflow instances that are based on the workflow are started, completed, terminated, or stopped because of an error. Follow these steps to specify when notifications are sent.

1.  In the left pane, click **Notifications**.
2.  Select the check box for each event that should trigger notifications:
    -   **Started** – Send notifications when a workflow instance is started.
    -   **Stopped** – Send notifications when a workflow instance is stopped because of an error.
    -   **Completed** – Send notifications when a workflow instance is completed.
    -   **Unrecoverable** – Send notifications when a workflow instance is stopped because of an unrecoverable error.
    -   **Terminated** – Send notifications when a workflow instance is terminated.

3.  Select the row for an event that you selected in step 2.
4.  On the **Notification text** tab, enter the text of the notification.
5.  To personalize the text, you can insert placeholders. Placeholders are replaced with the appropriate data when the text is shown to users. To insert a placeholder, follow these steps:
    1.  Click in the field to specify where the placeholder should appear.
    2.  Click **Insert placeholder**.
    3.  In the list that appears, select the placeholder to insert.
    4.  Click **Insert**.

6.  To add translations of the text, follow these steps:
    1.  Click **Translations**.
    2.  On the page that appears, Click **Add**.
    3.  In the list that appears, select the language that you will enter the text in.
    4.  In the **Translated text** field, enter the text.
    5.  To personalize the text, you can insert placeholders. For instructions about how to enter a placeholder, see step 5.
    6.  Click **Close**.

7.  On the **Recipient** tab, use the following options to specify who should receive the notifications.
    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Option</th>
    <th>Notifications are sent to these users</th>
    <th>To send notifications, follow these steps</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Participant</td>
    <td>Users who are assigned to a specific group or role</td>
    <td><ol>
    <li>On the <strong>Recipient</strong> tab, click <strong>Participant</strong>.</li>
    <li>On the <strong>Role based</strong> tab, in the <strong>Type of participant</strong> list, select the type of group or role to send notifications to.</li>
    <li>In the <strong>Participant</strong> list, select the group or role to send notifications to.</li>
    </ol></td>
    </tr>
    <tr class="even">
    <td>Workflow user</td>
    <td>Users who are participants in this workflow</td>
    <td><ol>
    <li>On the <strong>Recipient</strong> tab, click <strong>Workflow user</strong>.</li>
    <li>On the <strong>Workflow user</strong> tab, in the <strong>Workflow user</strong> list, select a participant in this workflow.</li>
    </ol></td>
    </tr>
    <tr class="odd">
    <td>User</td>
    <td>Specific Dynamics 365 for Operations users</td>
    <td><ol>
    <li>On the <strong>Recipient</strong> tab, click <strong>User</strong>.</li>
    <li>On the <strong>User</strong> tab, the <strong>Available users</strong> list includes all Dynamics 365 for Operations users. Select the users to send notifications to, and move those users into the <strong>Selected users</strong> list.</li>
    </ol></td>
    </tr>
    </tbody>
    </table>

8.  Repeat steps 3 through 7 for each event that you selected in step 2.

## Enter comments about the changes that you made to the workflow
To enter comments about the changes that you made to the workflow, follow these steps.

1.  In the left pane, click **Notes**.
2.  In the **Enter comments about the workflow** field, enter your comments.
3.  Review your comments. After you add comments, you can't modify them.
4.  Click **Add** to add your comments to the **Comment history** area.


