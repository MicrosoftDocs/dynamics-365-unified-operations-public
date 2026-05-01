---
title: Configure workflow properties
description: Learn about how to configure the various properties of a workflow, including outlines on naming workflows and specifying the workflow owner.
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
ms.assetid: 192b7a98-7d04-4c7a-a986-29d797a8a837
---

# Configure workflow properties

[!include [banner](../includes/banner.md)]

This article explains how to configure the various properties of a workflow.

To configure the properties of a workflow, open the workflow in the workflow editor. Select the canvas of the workflow editor, and then select **Properties** to open the **Properties** page. Use the following procedures to configure the various properties of the workflow.

## Name the workflow

Follow these steps to enter a name for the workflow.

1. In the left pane, select **Basic Settings**.
1. In the **Name** field, enter a unique name for the workflow. For example, if you create a purchase requisition workflow for each country or region that you operate in, you can name the purchase requisition workflow **Purchase Requisitions Denmark** or **Purchase Requisitions Spain**.

## Specify the workflow owner

The workflow owner is the person who manages and maintains the workflow. Follow these steps to specify the workflow owner.

1. In the left pane, select **Basic Settings**.
1. In the **Owner** list, select the name of the person who will manage the workflow.

## Select an email template

Follow these steps to select the email template that is used to generate notification messages about the workflow.

1. In the left pane, select **Basic Settings**.
1. In the **Email template for workflow notifications** list, select the template.

## Enter instructions for users

You can provide instructions to users who submit documents for processing and approval. These users are also referred to as *originators*. For example, you create a purchase requisition workflow, and you enter instructions. Users who enter purchase requisitions on the **Purchase requisitions** page can view those instructions. To view instructions, the originator selects the icon in the workflow message bar. Follow these steps to enter instructions for users.

1. In the left pane, select **Basic Settings**.
1. In the **Submission instructions** field, enter the instructions.
1. To personalize the instructions, insert placeholders. Placeholders are replaced with the appropriate data when the instructions are shown to users. To insert a placeholder, follow these steps:

    1. Select the **Submission instructions** field to specify where the placeholder should appear.
    1. Select **Insert placeholder**.
    1. In the list that appears, select the placeholder to insert.
    1. Select **Insert**.

1. To add translations of the instructions, follow these steps:

    1. Select **Translations**.
    1. On the page that appears, select **Add**.
    1. In the list that appears, select the language for the text.
    1. In the **Translated text** field, enter the text.
    1. To personalize the text, insert placeholders. For instructions about how to enter a placeholder, see step 3.
    1. Select **Close**.

> [!NOTE]
> You can't add placeholders by using copy and paste because the target information isn't pasted in correctly. Use the interface to add placeholders.

## Specify when to use this workflow through activation conditions

You can create multiple workflows that use the same workflow type. When you have multiple workflows that use the same type, you must specify when to use each workflow through activation conditions. If activation conditions aren't met, the default workflow is used. Similarly, if you define only one workflow configuration for a workflow type, the workflow configuration is used regardless of the activation conditions.

For example, you can create a purchase requisition workflow for each country or region that you operate in, such as Purchase Requisitions Denmark and Purchase Requisitions Spain, with the following conditions:

- Use Purchase Requisitions Denmark when: country/region = DK
- Use Purchase Requisitions Spain when: country/region = ES

Follow these steps to specify when to use the workflow that you're configuring.

1. In the left pane, select **Activation**.
1. Select the **Set the conditions for running this workflow** check box.
1. Select **Add condition**.
1. Enter a condition.
1. Enter any additional conditions that you need.
1. Run through the workflow with some target records to verify that the condition correctly includes and excludes records.

## Specify when to send notifications

When you submit a document for processing, you create a workflow instance. You can send notifications to users when workflow instances that are based on the workflow start, complete, terminate, or stop because of an error. Follow these steps to specify when to send notifications.

1. In the left pane, select **Notifications**.
1. Select the check box for each event that should trigger notifications:

   - **Started** – Send notifications when a workflow instance starts.
   - **Stopped** – Send notifications when a workflow instance stops because of an error.
   - **Completed** – Send notifications when a workflow instance completes.
   - **Unrecoverable** – Send notifications when a workflow instance stops because of an unrecoverable error.
   - **Terminated** – Send notifications when a workflow instance terminates.

1. Select the row for an event that you selected in step 2.
1. On the **Notification text** tab, enter the text of the notification.
1. To personalize the text, insert placeholders. Placeholders are replaced with the appropriate data when the text is shown to users. To insert a placeholder, follow these steps:

   1. Select the field to specify where the placeholder should appear.
   1. Select **Insert placeholder**.
   1. In the list that appears, select the placeholder to insert.
   1. Select **Insert**.
   1. A common **Notification text** placeholder to include is "Last Notes: %Workflow.Last note%", which displays any comments from the previous step.

1. To add translations of the text, follow these steps:

   1. Select **Translations**.
   1. On the page that appears, select **Add**.
   1. In the list that appears, select the language for the text.
   1. In the **Translated text** field, enter the text.
   1. To personalize the text, insert placeholders. For instructions about how to enter a placeholder, see step 5.
   1. Select **Close**.

1. On the **Recipient** tab, use the following options to specify who should receive the notifications.

| Option | Notifications are sent to these users | To send notifications, follow these steps |
|---|---|---|
| Participant | Users who are assigned to a specific group or role | 1. On the **Recipient** tab, select **Participant**. 1. On the **Role based** tab, in the **Type of participant** list, select the type of group or role to send notifications to. 1. In the **Participant** list, select the group or role to send notifications to. |
| Workflow user | Users who are participants in this workflow | 1. On the **Recipient** tab, select **Workflow user**. 1. On the **Workflow user** tab, in the **Workflow user** list, select a participant in this workflow. |
| User | Specific users | 1. On the **Recipient** tab, select **User**. 1. On the **User** tab, the **Available users** list includes all users. Select the users to send notifications to, and move those users into the **Selected users** list. |

1. Repeat steps 3 through 7 for each event that you selected in step 2.

## Enter comments about the changes that you made to the workflow

To enter comments about the changes that you made to the workflow, follow these steps:

1. In the left pane, select **Notes**.
1. In the **Enter comments about the workflow** field, enter your comments.
1. Review your comments. After you add comments, you can't modify them.
1. Select **Add** to add your comments to the **Comment history** area.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
