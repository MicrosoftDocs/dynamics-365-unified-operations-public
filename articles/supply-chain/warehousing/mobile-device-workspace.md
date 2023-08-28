---
title: Warehouse mobile devices workspace
description: This article provides information about the Warehouse mobile devices workspace, which lets you monitor the health of all handheld devices that are used in your warehouses.
author: MichaelFruergaardPontoppidan
ms.author: mfp 
ms.reviewer: kamaybac
ms.search.form: WHSMobileDeviceWorkspace, WHSMobileDevice
ms.topic: how-to
ms.date: 10/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse mobile devices workspace

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: preview until 10.0.37 GA -->

The **Warehouse mobile devices** workspace lets you monitor the health and license status of all handheld devices that are used in your warehouses.

The first time that a user signs in to the Warehouse Management mobile app on a new device, the system collects information about that device and adds it to the **Warehouse mobile devices** workspace. The system then continuously monitors the status of each device to make sure that it's running a supported operation system and the latest version of the mobile app. Devices remain listed in the workspace until they're [manually deleted](delete-devices).

The **Warehouse mobile devices** workspace also helps you confirm that you're in compliance with [licensing requirements](#licenses) by showing how many devices you're running and letting you assign a device license status to each device. However, the system doesn't enforce licensing requirements. Your organization is responsible for ensuring that you've acquired the correct number of licenses for your devices.

## Prerequisites

This feature requires Microsoft Dynamics 365 Supply Chain Management version 10.0.37 or later.

## Open the Warehouse mobile device workspace

To open the **Warehouse mobile devices** workspace, go to **Warehouse management \> Workspaces \> Warehouse mobile devices**.

## Summary information

The **Summary** FastTab of the **Warehouse mobile devices** workspace provides tiles that show and link to the following information:

- **Device licenses used across all companies** – This tile shows the number of device licenses that are required to cover all the devices that are currently used across all companies (legal entities). If a single device is used across multiple companies, it's counted only once here. This total includes previously used devices that are now blocked. You can [delete blocked devices](#delete-devices) to stop them from being counted here. Use this information to confirm how many licenses you need. This tile doesn't provide a drill-down link.
- **Device licenses** – This tile shows the number of device licenses that are required to cover all the devices that are currently used in the current company (legal entity). The devices that are counted here have a [licensing state](#license-state) of *License required* or *Licensed*. Select this tile to view a list that provides details about each device in this category.
- **Devices supported** – This tile shows the number of devices that are running current versions of the Warehouse Mobile app on a fully supported operating system. Select this tile to view a list that provides details about each supported device.
- **Soon out of support devices** – This tile shows the number of devices that are still healthy and compliant, but will soon become unsupported (typically because of the mobile app or operating system version that they're running). To help keep your warehouses running smoothly, be sure to upgrade or replace these devices before it's too late. Select this tile to view a list that provides details about each device that will soon become unsupported.
- **Unsupported devices** – This tile shows the number of devices that are no longer supported and might not work correctly. These devices might soon become blocked without further warning from Microsoft. To help keep your warehouses running smoothly, be sure to upgrade or replace these devices as soon as possible. Select this tile to view a list that provides details about each device that's no longer unsupported.
- **Blocked devices** – This tile shows the number of devices that are now blocked by Microsoft. Any attempt to sign in to one of these devices will be rejected by the system. Microsoft controls which devices are blocked and will use this mechanism as a last resort to help protect system integrity and compliance.

## Devices needing attention

The **Devices needing attention** FastTab of the **Warehouse mobile devices** workspace provides a quick overview of devices that require attention. It provides the following two tabs:

- **Devices to update** – Select this tab to view a list of devices that are running an old version of the Warehouse Management application. You should update each of these devices to the latest version to ensure optimal compliance, performance, and user experience. For details about the latest version of the app and a change history, see [What's new or changed in the Warehouse Management mobile app](whats-new-wma.md). For information about how to mass deploy installations and updates for the Warehouse Management mobile app, see [Mass deploy the Warehouse Management mobile app](warehouse-app-intune.md).
- **Devices to replace** – Select this tab to view a list of devices that are running an operation system that's no longer supported. These devices might pose a risk to system integrity and compliance. Therefore, you should replace them as soon as possible. If the list includes devices that you're no longer using, you can [delete them](#delete-devices).

## <a name="licenses"></a>Manage device licenses

### How devices are licensed

The following concepts apply to the way that the Warehouse Management mobile app is licensed:

- **Supply Chain Management user** – This type of user has a full Supply Chain Management user license. The user can access the web client and is also automatically licensed to use the Warehouse Management mobile app. No additional user license or device license is required. This type of user is usually an administrator, office worker, or warehouse manager instead of a warehouse worker.
- **Warehouse worker (shared work user)** – This type of user can sign in only by using the Warehouse Management mobile app (not the web client). Therefore, the user doesn't require a Supply Chain Management user license. This type of user is usually a warehouse worker. In Supply Chain Management, you typically set up users of this type by using a single [work user record](mobile-device-work-users.md) and then assigning multiple *user* accounts to it (one for each worker). This type of user is also referred to as a *shared work user*.
- **Warehouse Management mobile app user license** – A user license allows a specific warehouse worker to use a specific device. You can't view or manage user licenses in the **Warehouse mobile devices** workspace.
- **Warehouse Management mobile app device license** – A device license allows any number of shared work users (warehouse workers) to use a specific device. You can view and manage device licenses in the **Warehouse mobile devices** workspace.

For more information about how to set up mobile device user accounts, including both Supply Chain Management users and shared work users, see [Mobile device user accounts](mobile-device-work-users.md).

For complete licensing details, see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544).

### <a name="license-state"></a>Update licensing information for a device

The **Warehouse mobile devices** workspace lets you view information about each device that's connected to the system. It also lets you view and manage the device license status for each device. To update licensing information for a device, follow these steps.

1. Open the **Warehouse mobile devices** workspace.
1. On the **Summary** FastTab, select a tile to open the relevant device list (such as **Device licenses** or **Devices supported**).
1. Find the target device in the list, and select it.
1. On the Action Pane, select **Change device licensing**, and then select a new license state to assign to the selected device. The following license states are used:

    - *Auto* – This value is assigned to new devices and persists until the system has enough information to determine the correct license state.
    - *License required* – The device needs a license that hasn't yet been acquired. Usually, this value is automatically assigned the first time that a shared work user signs into the device.
    - *Licensed* – The device is licensed. Select this value to indicate that you've acquired the required licenses for the device.
    - *Block share usage* – The device doesn't require a device license. Devices in this license state can be used only by Supply Chain Management users (who don't require a user or device license to use the mobile app). This value prevents shared work users from signing in to the device.

## <a name="delete-devices"></a>Remove a device

After devices are discovered, they remain listed in the system until they're manually deleted. When you delete a device, its license is released and can be used with other devices. Follow these steps to remove a device from the system.

1. Open the **Warehouse mobile devices** workspace.
1. On the **Summary** FastTab, select a tile to open the relevant device list (such as **Blocked devices** or **Unsupported devices**).
1. Find the target device in the list, and select it.
1. On the Action Pane, select **Delete**.
