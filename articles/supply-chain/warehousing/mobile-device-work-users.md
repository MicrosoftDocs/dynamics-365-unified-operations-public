---
title: Mobile device user accounts
description: This topic describes how to set up and manage user accounts that enable workers to sign in and use the warehouse app.
author: MarkusFogelberg
ms.date: 09/15/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mafoge
ms.search.validFrom: 2021-09-15
ms.dyn365.ops.version: 10.0.22
---

# Mobile device user accounts

[!include [banner](../includes/banner.md)]

Each time a worker starts using the warehouse app, they must sign in using a username and password. Each worker in the system can have any number of warehouse app users associated with it (typically with warehouses associated with each of them), and is also configured with various options that establish default settings and other options relevant for using the warehouse app.

## Set up the required worker and employee records

Before you can set up warehouse app users, each worker must already exist as a Supply Chain Management employee or worker in the **Human Resources** module. <!-- KFM: Add links for more info and instructions. I can help find these... -->

## Set up mobile device user accounts

Once the required workers and employees are set up in the system, you can assign warehouse app users to each of them and set up other options that affect how they can use the app.

1. Go to **Warehouse management \> Setup \> Worker**.
1. Either select an existing worker from the list pane (to edit an existing one) or add a new record by selecting **New** on the Action Pane.
1. If you are setting up a new worker, do the following:
    1. In the **Worker** field, select the target user in the list of employees.
    1. Select **Select**.
    1. On the Action Pane, select **Save**.

1. On the **Profile** FastTab, make the following settings:
    - **Container packing policy** – <!-- KFM: Description needed. -->
    - **Packing profile ID** – <!-- KFM: Description needed. -->

1. On the **Default packing station** FastTab, make the following settings:
    - **Site** – <!-- KFM: Description needed. -->
    - **Warehouse** – <!-- KFM: Description needed. -->
    - **Location** – <!-- KFM: Description needed. -->

1. The **Users** FastTab lets you create any number of warehouse app user accounts for the selected worker. Each account is associated with a specific warehouse or warehouses. Use the toolbar to add or remove user accounts, reset the password for a selected account, or assign warehouses to a selected account. For each user account, make the following settings:

    - **User ID** – Enter a unique ID.
    - **User name** – Enter a name for the ID.
    - **Default warehouse** – <!-- KFM: Description needed. Also describe the **Warehouses** toolbar option and how those settings relate to this one (I think they let you associated more than one warehouse with the same account) -->
    - **Menu name** – <!-- KFM: Description needed. -->
    - **Inactive** – <!-- KFM: Description needed. -->

1. On the **Work** FastTab, make the following settings:

    - **Allow pick location override** – <!-- KFM: Description needed. -->
    - **Allow put location override** – <!-- KFM: Description needed. -->
    - **Allow sales over picking** – <!-- KFM: Description needed. -->
    - **Allow transfer order over picking** – <!-- KFM: Description needed. -->
    - **Allow movement of inventory with associated work** – <!-- KFM: Description needed. -->
    - **Allow manual item reallocation** – <!-- KFM: Description needed. -->
    - **Is a cycle count supervisor** – <!-- KFM: Description needed. -->
    - **Maximum percentage limit** – <!-- KFM: Description needed. -->
    - **Maximum quantity limit** – <!-- KFM: Description needed. -->
    - **Maximum value limit** – <!-- KFM: Description needed. -->

1. On the Action Pane, select **Save**.
1. If you added a new user account, the **Set password** dialog box appears, where you can create a simple password that the user can use to sign in to the mobile app. Enter a simple password (twice) and select **Save password** to continue.

## Select a preferred language for each warehouse app user

<!-- KFM: Description needed. -->

## Set the time zone for each warehouse app user

<!-- KFM: Description needed. -->