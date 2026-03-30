---
title: Configure automated tasks in a workflow
description: Learn about how to configure the properties for an automated task, including outlines on naming tasks and specifying when notifications are sent.
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
ms.assetid: c0aceb57-b5e6-4ef3-91e7-89a21c9f048a
---

# Configure automated tasks in a workflow

[!include [banner](../includes/banner.md)]


This article explains how to configure the properties for an automated task.

To configure an automated task in the workflow editor, right-click the task, and then select **Properties** to open the **Properties** page. Then use the following procedures to configure the properties for the automated task.

## Name the task

Follow these steps to enter a name for the automated task.

1. In the left pane, select **Basic Settings**.
1. In the **Name** field, enter a unique name for the task.

## Specify when to send notifications

You can send notifications to people when an automated task runs or cancels. Follow these steps to specify when to send notifications and who receives them.

1. In the left pane, select **Notifications**.
1. Select the check box next to the events to send notifications for:

    - **Execution** – Send notifications when the task runs.
    - **Canceled** – Send notifications when the task cancels.

1. Select the row for an event that you selected in step 2.
1. On the **Notification text** tab, enter the text of the notification.
1. To personalize the notification, insert placeholders. Placeholders are replaced with appropriate data when the notification appears to users. Follow these steps to insert a placeholder:

    1. In the text box, select where the placeholder should appear.
    1. Select **Insert placeholder**.
    1. In the list that appears, select the placeholder to insert.
    1. Select **Insert**.

1. To add translations of the notification, follow these steps:

    1. Select **Translations**.
    1. On the page that appears, select **Add**.
    1. In the list that appears, select the language for the text.
    1. In the **Translated text** field, enter the text.
    1. To personalize the text, insert placeholders as described in step 5.
    1. Select **Close**.

1. On the **Recipient** tab, specify who receives the notifications. Select one of the options in the following table, and then follow the additional steps for that option before you go to step 8.

| Option | Notification recipients | Additional steps |
|---|---|---|
| Participant | Users assigned to a specific group or role | 1. After you select **Participant**, on the **Role based** tab, in the **Type of participant** list, select the type of group or role to send notifications to. 1. In the **Participant** list, select the group or role to send notifications to. |
| Workflow user | Users who participate in the current workflow | - After you select **Workflow user**, on the **Workflow user** tab, in the **Workflow user** list, select a user who participates in the workflow. |
| User | Specific users | 1. After you select **User**, select the **User** tab. 1. The **Available users** list includes all users. Select the users to send notifications to, and then move those users to the **Selected users** list. |

1. Repeat steps 3 through 7 for each event that you selected in step 2.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
