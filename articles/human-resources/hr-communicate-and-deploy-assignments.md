---
title: Communicate with and deploy assignments to workers
description: Learn how to send messages to workers during registration and assign workers to temporary assignments and groups in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.date: 05/14/2026
ms.topic: install-set-up-deploy
f1_keywords:
- absence
- plan
audience: Application User
ms.search.region: Global
---

# Communicate with and deploy assignments to workers

Human resources responsibilities include registering times for various workers in bulk. This article discusses how to send messages to display in job registration pages. This process includes ending messages to selected workers and terminals, and assigning workers to temporary groups.

## Send messages to workers during registration

If you're a supervisor or manager, you can send messages that display on the **Job registration** page to workers who use the page to log on. When you send messages, consider the following:

- You can send a message to specific workers or to specific terminals.

- The message appears when workers log on to the **Job registration** page. The message doesn't display when workers log off.

- When you send a message to a specific worker, you can require the worker to confirm that they read the message.

- An icon displays with the message to indicate whether the message is for information only, important, or urgent.

### Create a message to all workers

1. Select **Human resources** > **Common** > **Time and attendance** > **Handle messages**.
1. Press **CTRL+N** to create a line.
1. In the **Subject** field, enter the heading of the message.
1. In the **From time** and **To time** fields, enter the time period when the message is visible to the recipients.
1. Select the **Public message** checkbox to send the message to all workers who log on to the **Job registration** page.
1. In the **Message type** field, select the level of importance for the message.
1. In the **Information** field, enter the message text.
1. Select **Close**.

### Send a message to selected workers or terminals

When you send a message to selected workers, the message appears only when the workers log on to the **Job registration** page. If you send a message to selected terminals, the message appears only when a worker logs on to one of the selected terminals.

1. Select **Human resources** > **Common** > **Time and attendance** > **Handle messages**.
1. Press **CTRL+N** to create a line.
1. In the **Subject** field, enter the heading of the message.
1. In the **From time** and **To time** fields, enter the time period when the message is visible to the recipients.
1. Select the **Receipt** checkbox to receive a notification that the worker reads the message.

    When the worker confirms the message as read, the **Read** checkbox on the **Workers** tab of the **Recipients** tab is selected.

1. In the **Message type** field, select the level of importance for the message.
1. In the **Information** field, enter the message text.
1. Press CTRL+S to save the message.
1. On the **Recipients** tab, select the workers or terminals to send the message to. You can select recipients individually or by creating queries.

    To select the recipients individually:

    1. Select the **Workers** tab to add workers, or the **Terminals** tab to add terminals.
    1. Select the **Select workers** or **Select terminals** buttons to add a worker or terminal to the list.
    1. Select the worker in the **Worker** field. The name of the worker appears in the **Name** field.

        _or_

        Select the terminal in the **Terminal** field. The description of the terminal appears in the **Description** field.

    1. Repeat these steps to add more recipients.
    1. Close the page when you add all the recipients.

    To select the recipients by creating a query:

    1. On the **Recipients** tab, select **Select workers** to create a query for workers or **Select terminals** to create a query for terminals.
    1. Select the criteria for the query.
    1. Repeat these steps to add more recipients to the list.
    1. Close the page when you add all the recipients.

## Temporary group assignment

Workers in **Time and attendance** are divided into calculation groups and approval groups. A supervisor or manager is responsible for calculating the registrations from workers who are associated with a calculation group.

### Seconding and approvals

To handle a situation where a worker is seconded to another team, a supervisor can second a worker to another calculation group or approval group for a specific period of time.

> [!NOTE]
> The person who approves registrations that are calculated isn't always the same. For example, a manager or a payroll administrator might approve registrations from workers belonging to a particular approval group.

## Second workers to another group

You can temporarily assign workers to other calculation or approval groups than the groups they're normally associated with. You can make this change on a specific date or for a period of time.

1. Select **Human resources** > **Common** > **Workers** > **Time registration workers**.
1. Select the worker, select the **Time registration** tab, and on the Action Pane select **Set up time registration worker** and select **Temporary group assignment**.
1. Press Ctrl+N, or select **New** on the toolbar, to create a new record.
1. In the **Profile date** field, select the date on which the worker is seconded to another group.
1. If the worker is seconded to another calculation group, select the group in the **Calculation group** field.
1. If the worker is seconded to another approval group, select the group in the **Approval group** field.
1. If you want to second the worker to another group for a longer period of time:

    1. Select **Compose**.
    1. Select the start and end dates in the **From date** and **To date** fields.
    1. If the worker is seconded to another calculation group, select the group in the **Calculation group** field.
    1. If the worker is seconded to another approval group, select the group in the **Approval group** field.
    1. Select the **Overwrite** checkbox.

## See also

[Set up time and attendance information](hr-set-up-time-and-attendance-information.md)

[Register time for workers](hr-register-time.md)

[Calculate, approve, and transfer registrations](hr-about-calculate-approve-transfer-registrations.md)
