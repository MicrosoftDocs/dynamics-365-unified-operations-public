---
title: Mobile device user accounts
description: This topic describes how to set up and manage user accounts that enable workers to sign in and use the warehouse app.
author: Mirzaab
ms.date: 09/15/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-09-15
ms.dyn365.ops.version: 10.0.22
---

# Mobile device user accounts

[!include [banner](../includes/banner.md)]

Every time that a worker starts to use the warehouse app, they must sign in by using a user name and password. Any number of warehouse app users can be associated with each worker in the system, and warehouses are typically associated with each of those warehouse app users. Various options are also configured for each worker, to establish default settings and other settings that are relevant to using the warehouse app.

## Set up the required worker and employee records

Before you can set up warehouse app users, each worker must already exist as a Supply Chain Management employee or worker in the **Human Resources** module.

## <a name="set-wma-users"></a>Set up mobile device user accounts

After the required workers and employees are set up in Human Resources, you can assign warehouse app users to each of them and set up other options that affect how they can use the app.

1. Go to **Warehouse management \> Setup \> Worker**.
1. To edit an existing worker, select it in the list pane. To add a new record, select **New** on the Action Pane.
1. If you're setting up a new worker, follow these steps:

    1. In the **Worker** field, select the target user in the list of employees.
    1. Select **Select**.
    1. On the Action Pane, select **Save**.

1. A default profile can be used to guide the warehouse worker at the packing station through the process that is required there. Alternatively, the default profile can be used to save the preferred profile settings for the worker. On the **Profile** FastTab, set the following fields:

    - **Container packing policy** – Select a container packing policy that defines how containers at the packing station should be processed. The container packing policy that is selected here will be pre-selected for the worker when they open the packing station. For more information, see the following blog post: [Improved packing functionality](https://cloudblogs.microsoft.com/dynamics365/no-audience/2016/12/01/improved-packing-functionality-dynamics-365-for-operations-1611),
    - **Packing profile ID** – Select a packing profile ID that defines the packing policy and container settings that are used. If the selected packing profile ID is associated with a container packing policy, you won't be able to change the **Container packing policy** setting on this page.

1. On the **Default packing station** FastTab, set the following fields to define the default packing station that applies when the worker signs in. The worker can still select another packing station as required.

    - **Site** – Select the site where the default packing station is located.
    - **Warehouse** – Select the warehouse where the default packing station is located.
    - **Location** – Select the location of the default packing station.

1. The **Users** FastTab lets you create any number of warehouse app user accounts for the selected worker. Each account is associated with a specific warehouse or warehouses. Use the toolbar to add or remove user accounts, reset the password for a selected account, or assign warehouses to a selected account. For each user account, set the following fields:

    - **User ID** – Enter a unique ID.
    - **User name** – Enter a name for the ID.
    - **Default warehouse** – Set the default warehouse where the worker usually works. You can use the toolbar to assign additional warehouses, and the worker can switch between warehouses by using the **Change warehouse** indirect activity of the mobile device menu item.
    - **Menu name** – Select the root menu that will be the starting page for the worker. The ability to set up a root menu for each worker is useful because it lets you control the menu structure that each worker can use. For example, the menu for workers that are active only in the outbound area can be tailored for tasks that are related to outbound operations for that area.
    - **Inactive** – A selected checkbox indicates that the user account is inactive. The user account is automatically inactivated if a worker enters the wrong password five times in a row in the warehouse app. However, you can also manually select this checkbox. Clear the checkbox to make the user active again.

1. On the **Work** FastTab, set the following fields:

    - **Allow pick location override** – Set this option to *Yes* to allow the worker to override the location for picking steps. This capability can be useful if the physical inventory doesn't match the system-suggested location.
    - **Allow put location override** – Set this option to *Yes* to allow the worker to override the location for put steps. This capability can be useful if the suggested put location is currently full or unavailable, or if staging locations changed.
    - **Allow sales over picking** – Set this option to *Yes* to allow the worker to over-pick when sales orders are picked. For more information, see [Over-picking for sales orders and transfer orders](over-picking-for-sales-and-transfer-orders.md).
    - **Allow transfer order over picking** – Set this option to *Yes* to allow the worker to over-pick when transfer orders are picked. For more information, see [Over-picking for sales orders and transfer orders](over-picking-for-sales-and-transfer-orders.md).
    - **Allow movement of inventory with associated work** – Set this option to *Yes* to allow the worker to move inventory that is already reserved or already associated with other work. For more information, see [Movement of inventory with associated work in Warehouse management](move-inventory-associated-work.md).
    - **Allow manual item reallocation** – Set this option to *Yes* to enable manual reallocation for the worker during short picking. Item reallocation guides workers to pick inventory from another location. Although automatic reallocation is available for all workers, manual reallocation requires explicit setup for a worker. The ability to control manual reallocation for each worker can be helpful because it lets you control the visibility that each worker has when, for example, item picking from the quarantine or bulk area is limited to trusted workers. For more information, see the following blog post: [Automatic and manual item reallocation during short picking](https://cloudblogs.microsoft.com/dynamics365/no-audience/2016/11/07/automatic-and-manual-item-reallocation-during-the-short-picking-dynamics-365-for-operations-1611/).
    - **Is a cycle count supervisor** – Set this option to *Yes* to make the worker a cycle count supervisor. In this case, all cycle counts that the worker performs on the warehouse app will be immediately approved. The **Maximum percentage limit**, **Maximum quantity limit**, and **Maximum value limit** fields aren't considered for workers that this option is set to *Yes* for.
    - **Maximum percentage limit** – Enter the highest percentage limit that a cycle count can vary from the expected count without requiring approval by a cycle count supervisor.
    - **Maximum quantity limit** – Enter the total quantity that the entered quantity can differ from the expected quantity (in units) without requiring approval by a cycle count supervisor.
    - **Maximum value limit** – Enter the maximum amount that the cost of the inventory can differ from the expected cost without requiring approval by a cycle count supervisor.

1. On the Action Pane, select **Save**.
1. If you added a new user account, the **Set password** dialog box appears, where you can create a simple password that the user can use to sign in to the mobile app. Enter the simple password two times, and then select **Save password** to continue.

## Set the language, number formats, and time zone for each warehouse app user

When a worker signs in to the Warehouse Management mobile app, the language, number formats, and time zone change to match that worker's preferences. The account settings for the worker that is selected in step 3 in the [Set up mobile device user accounts](#set-wma-users) section determines the settings that are used. If you require separate settings for each user, use different worker accounts. The following procedure shows how to change the language, number formats, and time zone for each warehouse app user.

1. Go to **Warehouse management \> Setup \> Worker**.
1. Find the name of the worker that you want to set up. Make sure that the worker has all the required warehouse app user accounts that are listed on the **Users** FastTab. Create a new worker and/or add warehouse app user accounts as required, by following the steps in the [Set up mobile device user accounts](#set-wma-users) section.
1. Go to **System administration \> Users \> Users**.
1. Select the user account where the **Person** column shows the name of the worker that you found in step 2.

    > [!IMPORTANT]
    > The **User ID** values that are listed on the **Users** page are *not* related to the value that are shown on the **Users** FastTab of the **Worker** page that you opened in step 1.

1. On the Action Pane, select **User options**.
1. On the **Preferences** tab, set the following fields:

    - **Language** – Select the language that the worker prefers. This field also controls the number format that is shown in the warehouse app.
    - **Date, time, and number format** – Select the date and time format that the worker prefers. The warehouse app uses the number format associated with the language chosen for the **Language** field instead of this setting.
    - **Time zone** – Select the time zone where the worker works. This field affects the time stamp for all registrations that the worker makes by using the app.

> [!NOTE]
> In some cases, the warehouse app won't be able to find specific worker settings that establish the language, number formats, and time zone. The following rules apply:
>
> - If the app isn't connected to a Supply Chain Management environment (for example, the first time that the app is started after it's installed), the language of the local device is used. When the device language changes, the app language also changes. For more information about how to configure the language for the local device, see the documentation for your device and/or operating system.
> - If the app is connected to a Supply Chain Management environment, but no preferences are set for the signed-in worker, the language, number formats, and time zone are selected based on the account that is associated with the client ID that the device uses to connect to Supply Chain Management. For more information, see [Create and configure a user account in Supply Chain Management](install-configure-warehouse-management-app.md#user-azure-ad).

> [!TIP]
> If you notice that incorrect time stamps are shown for registrations that are made by using the warehouse app, you might have to adjust the time zone that is set for the user account that workers use to sign in and/or authenticate with Supply Chain Management. As was previously mentioned, the time zone setting might come from the user account that is used to sign in to the warehouse app, as set up on the **Worker** page. Alternatively, if the user account isn't set on the **Worker** page, the time zone comes from the user account that is associated with the client ID that is used for authentication, as set up on the **[Azure Active Directory applications](install-configure-warehouse-management-app.md)** page.
