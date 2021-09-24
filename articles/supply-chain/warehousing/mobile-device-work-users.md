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

1. The default profile can be used to guide the warehouse worker at the packing station on what process to use when operating at the packing station, or to save the preferred profile settings for the worker. On the **Profile** FastTab, make the following settings:
    - **Container packing policy** – The container packing policy defines how containers on the pack station should be processed. By specifying a container packing policy here it will be pre-selected for the worker when opening the pack station. <!-- MF: See blog post here: https://cloudblogs.microsoft.com/dynamics365/no-audience/2016/12/01/improved-packing-functionality-dynamics-365-for-operations-1611/ -->
    - **Packing profile ID** – The Packing profile ID can define which packing policy and container settings to use. If the Packing profile ID is associated with a Container packing policy, it is not possible to change the Container packing policy setting on this page. 

1. The **Default packing station** FastTab can be used to set default values on the pack station login for this worker. The can be changed when opening the pack station. On the **Default packing station** FastTab, make the following settings:
    - **Site** – Select the default Site to use.
    - **Warehouse** – Select the default Warehouse to use. 
    - **Location** – Specify the packing location to use.

1. The **Users** FastTab lets you create any number of warehouse app user accounts for the selected worker. Each account is associated with a specific warehouse or warehouses. Use the toolbar to add or remove user accounts, reset the password for a selected account, or assign warehouses to a selected account. For each user account, make the following settings:

    - **User ID** – Enter a unique ID.
    - **User name** – Enter a name for the ID.
    - **Default warehouse** – Set the default warehouse that the worker will be performing work in. Additional warehouses can be assigned in the toolbar, and the user can change between warehouses by using the mobile device menu item indirect activty "Change warehouse".
    - **Menu name** – Select the root menu that will be starting page for the user. Being able to set this up per worker is useful to control the menu structure each worker can use, for example workers only active in the outbound area could have a menu tailored for their work tasks. 
    - **Inactive** – If a worker enters the wrong password in the warehouse app 5 times their user will be set to inactive. You would then need to remove the inactive flag with this setting.

1. On the **Work** FastTab, make the following settings:

    - **Allow pick location override** – When selected, this setting will allow the user to override location on picking steps. This can be useful if the physical inventory doesn't match the system suggested location.
    - **Allow put location override** – When selected, this setting will allow the user to override location on put steps. This could be useful if the suggested put location is full or unavailable for the moment, or if staging locations changed.
    - **Allow sales over picking** – During sales order picking, when this setting is selected it will allow the user to over-pick. For more info see: https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/over-picking-for-sales-and-transfer-orders
    - **Allow transfer order over picking** – During transfer order picking, when this setting is selected it will allow the user to over-pick. For more info see: https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/over-picking-for-sales-and-transfer-orders
    - **Allow movement of inventory with associated work** – When selected, this setting will allow workers to move inventory, even if it has been reserved or is associated with other work already. For more info see: https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/move-inventory-associated-work
    - **Allow manual item reallocation** – During short-picking it is possible to have automatic and manual item reallocation so that users are guided to pick inventory from another location. While automatic reallocation is available for all users, manual reallocation requires explicit setup for that user. Controlling this per worker can be helpful to device the visibility each worker may have, as items in quaratine or bulk area might only be picked by trusted workers. <!-- MF: See blog post here: https://cloudblogs.microsoft.com/dynamics365/no-audience/2016/11/07/automatic-and-manual-item-reallocation-during-the-short-picking-dynamics-365-for-operations-1611/ -->
    - **Is a cycle count supervisor** – When selected, this user is set to be a cycle count supervisor and all cycle counts performed on the warehouse app will be immediately approved. The maximum percentage, quantity and value limits are not considered when this option is selected.
    - **Maximum percentage limit** – The highest percentate limit that a cycle count can vary from the expected count without requiring a supervisor approval.
    - **Maximum quantity limit** – The total quantity that the entered quantity can differ from the expected quantity in units withour requiring a supervisor approval.
    - **Maximum value limit** –  The maximum amount that the cost of the inventory can differ from the expected cost without requiring approval by a cycle count supervisor.

1. On the Action Pane, select **Save**.
1. If you added a new user account, the **Set password** dialog box appears, where you can create a simple password that the user can use to sign in to the mobile app. Enter a simple password (twice) and select **Save password** to continue.

## Set the language, number formats, and time zone for each warehouse app user

 When a worker signs in to the Warehouse Management mobile app, the language, number formats, and time zone will change to match that worker's preferences. The account settings for the **Worker** selected in step 3 of [Set up mobile device user accounts](#set-wma-users) section determines the settings used. Use different worker accounts if you need separate settings per user. The following procedure shows how to change the language, number formats, and time zone for each warehouse app user.

1. Go to **Warehouse management \> Setup \> Worker** and find the name of the worker you want to set up. Make sure that worker has all of the required warehouse app user accounts listed on the **Users** FastTab. If necessary, create a new worker and/or add warehouse app user accounts as described in [Set up mobile device user accounts](#set-wma-users).
1. Go to **System administration \> Users \> Users**.
1. Select the user account where the **Person** column shows the name of the worker you found in step 1.
    > [!IMPORTANT]
    > The **User ID** values you see listed here are *not* related to those shown on the **Users** FastTab of the **Worker** page you looked at in step 1.

1. On the Action Pane, select **User options**.
1. Open the **Preferences** tab.
1. Make the following settings:
    - **Language** – Select the language preferred by this worker. This setting will also control the date format seen on the warehouse app.
    - **Date, time, and number format** – Select the language that will determine the number formats seen on the warehouse app. Note that the date and time formats shown in the warehouse app are actually established by the **Language** field, not by this field.
    - **Time zone** – Select the time zone where the worker works. This will affect the time stamp for all registrations the worker makes using the app.

> [!NOTE]
> In some cases, the warehouse app won't be able to find specific worker settings for establishing the language, number formats, and time zone. The following rules apply:
>
> - When the app is not connected to a Supply Chain Management environment (for example the first time the app is installed and is started) the device language is used. Changing the device language will change the language of the app. See the documentation for your device and/or operating system for details about how to make this settings for the local device.
> - When the app is connected to a Supply Chain Management environment, but no preferences are set for the signed-in worker, the language, number formats, and time zone are selected based on the account associated with the client ID the device uses to connect to Supply Chain Management. For more information, see [Create and configure a user account in Supply Chain Management](install-configure-warehouse-management-app.md#user-azure-ad)

> [!TIP]
> If you notice that registrations made using the warehouse app show incorrect time stamps, then you may need to adjust the time zone set for the user account that workers are using to sign in and/or authenticate with Supply Chain Management. As mentioned previously, that settings may come from the user account used to sign in to the warehouse app (as set up on the **Worker** page), or (if not set there) from the user account associated with the client ID used to authenticate (as set up on the **[Azure Active Directory applications](install-configure-warehouse-management-app.md)** page).
