---
title: Mobile device user accounts
description: Learn how to set up and manage warehouse worker records and their associated mobile device user accounts, which enable workers to sign in and use the warehouse app.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 03/07/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Mobile device user accounts

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

Every time that a worker starts to use the warehouse app, they must sign in by using a user name and password. Any number of warehouse app users can be associated with each warehouse worker in the system, and warehouses are typically associated with each of those warehouse app users. Various options are also configured for each warehouse worker record, to establish default settings and other settings that are relevant to using the warehouse app.

> [!IMPORTANT]
> This article assumes that you're using user-based authentication. If you're still using service-based authentication (which is now deprecated), you must set up Microsoft Dynamics 365 Supply Chain Management slightly differently. Learn more in [Service-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-service-based.md). Then follow the instructions in the [Set up mobile device user accounts](#set-wma-users) section of this article. Those instructions apply to both types of authentication methods.

## Assign Microsoft Entra ID accounts to the mobile app in Azure

The Warehouse Management mobile app connects to Supply Chain Management through an *enterprise application* that's set up in Azure. Azure provides tools for creating Microsoft Entra ID user accounts and assigning them to the enterprise application.

Depending on the [authentication scenario](warehouse-app-authenticate-user-based.md#scenarios) that you're using, you must set up a unique Microsoft Entra ID user account either for each mobile device or for each human worker that will authenticate with Supply Chain Management. Make a note of the **User principal name** value of each Microsoft Entra ID account that you use for this purpose. You'll need these values later, when you set up the Supply Chain Management user record for each account.

For more information about how to set up an enterprise application for the Warehouse Management mobile app, see [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md).

For more information about how to assign Microsoft Entra ID user accounts to enterprise applications in Azure, see [Manage users and groups assignment to an application](/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

## Set up employee records for each device or human worker

For each Microsoft Entra ID user account that you set up in the previous section, you must have a matching employee record in Supply Chain Management. Later, you'll link each employee record to the related Supply Chain Management user record and warehouse worker record.

To create, view, and manage employee records, go to **Human resources** \> **Workers** \> **Employees**.

## Set up Supply Chain Management user records for each device or human worker

For each employee record that you set up in the previous section, you must have a matching Supply Chain Management user record that identifies both the Microsoft Entra ID user account and the employee record. Follow these steps to set up a Supply Chain Management user record.

1. Go to **System administration** \> **Users** \> **Users**.
1. On the Action Pane, select **New**.
1. Set the following fields for the new user record:

    - **User ID** – Enter a unique ID for the user or device.
    - **User name** – Enter a descriptive name for the user or device.
    - **Provider** – Leave this field set to its default value.
    - **Email** – Enter the **User principal name** value of the Microsoft Entra ID account that you set up for the user or device.
    - **Telemetry ID** – Leave this field set to its default value.
    - **Company** – Select the legal entity (company) where the user works or the device is used.
    - **Person** – Select the employee record that corresponds to the user or device.
    - **Enabled** – Set this option to *Yes*.

1. On the **User's roles** FastTab, assign the *Warehouse mobile device user* role to the user account. The user must have this role to sign in to the warehouse app.

## <a name="set-wma-users"></a>Set up mobile device user accounts

For each user record that you created in the previous section, you must create a *warehouse worker record* and assign one or more *mobile device user accounts* to it.

1. Go to **Warehouse management** \> **Setup** \> **Worker**.
1. To edit an existing worker, select it in the list pane. To add a new record, select **New** on the Action Pane.
1. If you're setting up a new worker, follow these steps:

    1. In the **Worker** field, select the related employee record from the **Human Resources** module. This value must match the **Person** value that's selected for the related Supply Chain Management user record.
    1. Select **Select**.
    1. On the Action Pane, select **Save**.

1. A default profile can be used to guide the warehouse worker at the packing station through the process that's required there. Alternatively, the default profile can be used to save the preferred profile settings for the worker. On the **Profile** FastTab, set the following fields:

    - **Container packing policy** – Select a container packing policy that defines how containers at the packing station should be processed. The container packing policy that you select here will be preselected for the worker when they open the packing station. For more information, see the following blog post: [Improved packing functionality](https://cloudblogs.microsoft.com/dynamics365/no-audience/2016/12/01/improved-packing-functionality-dynamics-365-for-operations-1611).
    - **Packing profile ID** – Select a packing profile ID that defines the packing policy and container settings that are used. If the selected packing profile ID is associated with a container packing policy, you won't be able to change the **Container packing policy** setting on this page.

1. On the **Default packing station** FastTab, set the following fields to define the default packing station that applies when the worker signs in. The worker can still select another packing station as required.

    - **Site** – Select the site where the default packing station is located.
    - **Warehouse** – Select the warehouse where the default packing station is located.
    - **Location** – Select the location of the default packing station.

1. The **Users** FastTab lets you create any number of mobile device user accounts for the selected worker. Each account is associated with a specific warehouse or warehouses. Use the toolbar to add or remove mobile device user accounts, reset the password for a selected account, or assign warehouses to a selected account. For each mobile device user account, set the following fields:

    - **User ID** – Enter a unique ID.
    - **User name** – Enter a name for the ID.
    - **Default warehouse** – Set the default warehouse where the worker usually works. You can use the toolbar to assign additional warehouses, and the worker can switch between warehouses by using the **Change warehouse** indirect activity of the mobile device menu item.
    - **Menu name** – Select the root menu that will be the starting page for the worker. The ability to set up a root menu for each worker is useful because it lets you control the menu structure that each worker can use. For example, the menu for workers that are active only in the outbound area can be tailored for tasks that are related to outbound operations for that area.
    - **Inactive** – A selected checkbox indicates that the mobile device user account is inactive. The mobile device user account is automatically inactivated if a worker enters the wrong password five times in a row in the warehouse app. However, you can also manually select this checkbox. Clear the checkbox to make the user active again.
    - **Default user** – Select this checkbox for the mobile device user account that should be the default account for the worker, if the worker should have a default account. If you're using a sign-in scenario where you have a unique Microsoft Entra ID user account for each human warehouse worker, the Warehouse Management mobile app automatically signs in by using the default mobile device user account when the human worker signs in to the device by using their Microsoft Entra ID user account. (Learn more in [Scenarios for managing devices, Microsoft Entra ID users, and mobile device users](warehouse-app-authenticate-user-based.md#scenarios).)

1. On the **Work** FastTab, set the following fields:

    - **Allow pick location override** – Set this option to *Yes* to allow the worker to override the location for picking steps. This capability can be useful if the physical inventory doesn't match the system-suggested location.
    - **Allow put location override** – Set this option to *Yes* to allow the worker to override the location for put steps. This capability can be useful if the suggested put location is currently full or unavailable, or if staging locations changed.
    - **Allow sales over picking** – Set this option to *Yes* to allow the worker to over-pick when sales orders are picked. Learn more in [Over-picking for sales orders and transfer orders](over-picking-for-sales-and-transfer-orders.md).
    - **Allow transfer order over picking** – Set this option to *Yes* to allow the worker to over-pick when transfer orders are picked. Learn more in [Over-picking for sales orders and transfer orders](over-picking-for-sales-and-transfer-orders.md).
    - **Allow movement of inventory with associated work** – Set this option to *Yes* to allow the worker to move inventory that's already reserved or already associated with other work. Learn more in [Movement of inventory with associated work in Warehouse management](move-inventory-associated-work.md).
    - **Allow manual item reallocation** – Set this option to *Yes* to enable manual reallocation for the worker during short picking. Item reallocation guides workers to pick inventory from another location. Although automatic reallocation is available for all workers, manual reallocation requires explicit setup for a worker. The ability to control manual reallocation for each worker can be helpful because it lets you control the visibility that each worker has when, for example, item picking from the quarantine or bulk area is limited to trusted workers. For more information, see the following blog post: [Automatic and manual item reallocation during short picking](https://cloudblogs.microsoft.com/dynamics365/no-audience/2016/11/07/automatic-and-manual-item-reallocation-during-the-short-picking-dynamics-365-for-operations-1611/).
    - **Is a cycle count supervisor** – Set this option to *Yes* to make the worker a cycle count supervisor. In this case, all cycle counts that the worker performs on the warehouse app will be immediately approved. The **Maximum percentage limit**, **Maximum quantity limit**, and **Maximum value limit** fields aren't considered for workers that this option is set to *Yes* for.
    - **Maximum percentage limit** – Enter the highest percentage limit that a cycle count can vary from the expected count without requiring approval by a cycle count supervisor.
    - **Maximum quantity limit** – Enter the total quantity that the entered quantity can differ from the expected quantity (in units) without requiring approval by a cycle count supervisor.
    - **Maximum value limit** – Enter the maximum amount that the cost of the inventory can differ from the expected cost without requiring approval by a cycle count supervisor.

    > [!NOTE]
    > To skip supervisor approval, all limit checks must succeed. If you wish to allow all non-supervisor users to skip the approval step, set suitably high values for each of the **Maximum percentage limit**, **Maximum quantity limit**, and **Maximum value limit** fields. Provided all recorded values are below these limits, supervisor approval won't be required.

1. On the Action Pane, select **Save**.
1. If you added a new mobile device user account, the **Set password** dialog box appears, where you can create a simple password that the user can use to sign in to the mobile app. Enter the simple password two times, and then select **Save password** to continue.

## Set the language, number formats, and time zone for each warehouse app user

When a worker signs in to the Warehouse Management mobile app, the language, number formats, and time zone change to match that worker's preferences. The account settings for the worker that's selected in step 3 in the [Set up mobile device user accounts](#set-wma-users) section determines the settings that are used. If you require separate settings for each worker, use different worker accounts. The following procedure shows how to change the language, number formats, and time zone for a warehouse app user.

1. Go to **Warehouse management** \> **Setup** \> **Worker**.
1. Find the worker that you want to set up, and make a note of the value in the **Worker** field.
1. Go to **System administration** \> **Users** \> **Users**.
1. Open the user record where the **Person** column shows the **Worker** value that you found in step 2.

    > [!IMPORTANT]
    > The **User ID** values that are listed on the **Users** page are *not* related to the value that are shown on the **Users** FastTab of the **Worker** page that you opened in step 1.

1. On the Action Pane, select **User options**.
1. On the **Preferences** tab, set the following fields:

    - **Language** – Select the language that the worker prefers. This field also controls the number format that's shown in the warehouse app.
    - **Date, time, and number format** – Select the date and time format that the worker prefers. The warehouse app uses the number format associated with the language chosen for the **Language** field instead of this setting.
    - **Time zone** – Select the time zone where the worker works. This field affects the time stamp for all registrations that the worker makes by using the app.

> [!NOTE]
> In some cases, the warehouse app won't be able to find specific worker settings that establish the language, number formats, and time zone. The following rules apply:
>
> - If the app isn't connected to a Supply Chain Management environment (for example, the first time that the app is started after it's installed), the language of the local device is used. When the device language changes, the app language also changes. For more information about how to configure the language for the local device, see the documentation for your device and/or operating system.
> - If the app is connected to a Supply Chain Management environment, but no preferences are set for the signed-in worker, the language, number formats, and time zone are selected based on the account that's associated with the client ID that the device uses to connect to Supply Chain Management. Learn more in [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md#user-azure-ad) or [Service-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-service-based.md#user-azure-ad), depending on which authentication method you're using.

> [!TIP]
> If you notice that incorrect time stamps are shown for registrations that are made by using the warehouse app, you might have to adjust the time zone that's set for the mobile device user account that workers use to sign in and/or authenticate with Supply Chain Management. As was previously mentioned, the time zone setting might come from the mobile device user account that's used to sign in to the warehouse app, as set up on the **Worker** page. Alternatively, if the mobile device user account isn't set on the **Worker** page, the time zone comes from the mobile device user account that's associated with the client ID that's used for authentication, as set up on the **[Microsoft Entra applications](install-configure-warehouse-management-app.md)** page.
