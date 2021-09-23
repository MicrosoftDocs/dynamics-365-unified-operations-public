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

Before you can set up warehouse app users, each worker must already exist as a Supply Chain Management employee or worker in the **Human Resources** module.

## <a name="set-wma-users"></a>Set up mobile device user accounts

Once the required workers and employees are set up in the **Human Resources** module, you can assign warehouse app users to each of them and set up other options that affect how they can use the app.

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

## Set the language, number formats, and time zone for each warehouse app user

 When a worker signs in to the Warehouse Management mobile app, the language, date/time formats, and time zone will change to match that worker's preferences. The account settings for the **Worker** selected in step 3 of [Set up mobile device user accounts](#set-wma-users) section determines the settings used. Use different worker accounts if you need separate settings per user. The following procedure shows how to change the language, date/time formats, and time zone for each warehouse app user.

1. Go to **Warehouse management \> Setup \> Worker** and find the name of the worker you want to set up. Make sure that worker has all of the required warehouse app user accounts listed on the **Users** FastTab. If necessary, create a new worker and/or add warehouse app user accounts as described in [Set up mobile device user accounts](#set-wma-users).
1. Go to **System administration \> Users \> Users**.
1. Select the user account where the **Person** column shows the name of the worker you found in step 1. <!-- KFM: Please confirm this step and the following note. -->
    > [!IMPORTANT]
    > The **User ID** values you see listed here are *not* related to those shown on the **Users** FastTab of the **Worker** page you looked at in step 1.

1. On the Action Pane, select **User options**.
1. Open the **Preferences** tab.
1. Make the following settings:
    - **Language** – Select the language preferred by this worker. This setting will also control the date format seen on the warehouse app. <!-- KFM: Does this really affect the date format? What about the next setting? -->
    - **Date, time, and number format** – Select the language that will determine the date, time, and number formats seen on the warehouse app.
    - **Time zone** – Select the time zone where the worker works. This will affect the time stamp for all registrations the worker makes using the app. <!-- KFM: Please confirm this step -->

> [!NOTE]
> In some cases, the warehouse app won't be able to find specific worker settings for establishing the language, date/time formats, and time zone. The following rules apply:
>
> - When the app is not connected to a Supply Chain Management environment (for example the first time the app is installed and is started) the device language is used. Changing the device language will change the language of the app. See the documentation for your device and/or operating system for details about how to make this settings for the local device.
> - When the app is connected to a Supply Chain Management environment, but no preferences are set for the signed-in worker, the language, date/time formats, and time zone are selected based on the Warehouse Management mobile app user used to establish the connection to the Azure AD application. For more information, see [Create and configure a user account in Supply Chain Management](install-configure-warehouse-management-app.md#user-azure-ad) <!-- KFM: Is it really a mobile app user that we set there? I think it's an SCM user. -->


<!-- KFM: Add a note about time zones, as requested by support? -->