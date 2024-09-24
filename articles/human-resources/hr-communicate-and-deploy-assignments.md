---
title: Communicate with and deploy assignments to workers
description: Learn how to send messages to workers during registration and assign workers to temporary assignments and groups in Dynamics 365 Human Resources.
author: twheeloc
ms.author: twheeloc
ms.date: 01/24/2024
ms.topic: article
f1_keywords:
- absence
- plan
audience: Application User
ms.search.region: Global
---

# Communicate with and deploy assignments to workers

Human resources' responsibilities include registering times for various workers in bulk. This article discusses how to send messages to be displayed in job registration forms. This includes ending messages to selected workers and terminals, and assigning workers to temporary groups.

## Send messages to workers during registration 

If you're a supervisor or manager, you can send messages that are displayed on the **Job registration** page to workers who are using the form to log on. When you send messages, consider the following:

  - You can send a message to specific workers or to specific terminals.

  - The message will be visible when workers log on to the **Job registration** page. The message isn't displayed when workers log off.

  - When you send a message to a specific worker, you can require the worker to confirm that he or she has read the message.

  - An icon is displayed with the message to indicate whether the message is for information only, important, or urgent.

### Create a message to all workers

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Handle messages**.
2.  Press **CTRL+N** to create a line.
3.  In the **Subject** field, enter the heading of the message.
4.  In the **From time** and **To time** fields, enter the time period when the message will be visible to the recipients.
5.  Select the **Public message** checkbox to send the message to all workers who log on to the **Job registration** page.
6.  In the **Message type** field, select the level of importance for the message.
7.  In the **Information** field, enter the message text.
8.  Click **Close**.

### Send a message to selected workers or terminals

When you send a message to selected workers, the message will be displayed only when the workers log on to the **Job registration** page. If you send a message to selected terminals, the message is displayed only when a worker logs on to one of the selected terminals.

1.  Click **Human resources** \> **Common** \> **Time and attendance** \> **Handle messages**.
2.  Press **CTRL+N** to create a line.
3.  In the **Subject** field, enter the heading of the message.
4.  In the **From time** and **To time** fields, enter the time period when the message will be visible to the recipients.
5.  Select the **Receipt** checkbox to receive a notification that the worker has read the message.
    
    When the worker confirms the message as having been read, the **Read** checkbox on the **Workers** tab of the **Recipients** tab will be selected.

6.  In the **Message type** field, select the level of importance for the message.
7.  In the **Information** field, enter the message text.
8.  Press CTRL+S to save the message.
9.  On the **Recipients** tab, select the workers or terminals to send the message to. You can select recipients individually or by creating queries.
    
    To select the recipients individually:
    
    1.  Click the **Workers** tab to add workers, or the **Terminals** tab to add terminals.
    2.  Click the **Select workers** or **Select terminals** buttons to add a worker or terminal to the list.
    3.  Select the worker in the **Worker** field. The name of the worker is displayed in the **Name** field.
        
        _or_
        
        Select the terminal in the **Terminal** field. The description of the terminal is displayed in the **Description** field.
    
    4.  Repeat these steps to add more recipients.
    5.  Close the page when you have added all the recipients.
    
    To select the recipients by creating a query:
    
    1.  On the **Recipients** tab, click **Select workers** to create a query for workers or **Select terminals** to create a query for terminals.
    2.  Select the criteria for the query.
    3.  Repeat these steps to add more recipients to the list.
    4.  Close the page when you have added all the recipients.

## Temporary group assignment 

Workers in **Time and attendance** are divided into calculation groups and approval groups. A supervisor or manager is responsible for calculating the registrations from workers who are associated with a calculation group.

### Seconding and approvals

In order to handle a situation where a worker is seconded to another team, it's possible for a supervisor to second a worker to another calculation group or approval group for a specific period of time.

> [!NOTE]
> It may not be the same person who approves registrations that have been calculated. For example, a manager, or a payroll administrator may have the task of approving registrations from workers belonging to a particular approval group.

## Second workers to another group

You can temporarily assign workers to other calculation or approval groups than they're normally associated with. This can be done on a specific date, or for a period of time.

1.  Click **Human resources** \> **Common** \> **Workers** \> **Time registration workers**.
2.  Select the worker, click the **Time registration** tab, and on the Action Pane click **Set up time registration worker** and select **Temporary group assignment**.
3.  Press Ctrl+N, or click **New** on the toolbar, to create a new record.
4.  In the **Profile date** field, select the date on which the worker is seconded to another group.
5.  If the worker is seconded to another calculation group, select the group in the **Calculation group** field.
6.  If the worker is seconded to another approval group, select the group in the **Approval group** field.
7.  If you want to second the worker to another group for a longer period of time:
    
    1.  Click **Compose**.
    2.  Select the start and end dates in the **From date** and **To date** fields.
    3.  If the worker is seconded to another calculation group, select the group in the **Calculation group** field.
    4.  If the worker is seconded to another approval group, select the group in the **Approval group** field.
    5.  Select the **Overwrite** checkbox.


## See also

[Set up time and attendance information](hr-set-up-time-and-attendance-information.md)

[Register time for workers](hr-register-time.md)

[Calculate, approve, and transfer registrations](hr-about-calculate-approve-transfer-registrations.md)
