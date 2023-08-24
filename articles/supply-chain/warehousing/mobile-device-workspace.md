---
title: Warehouse mobile device workspace
description: XXXX
author: MichaelFruergaardPontoppidan
ms.author: mfp 
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse mobile device workspace

[!include [banner](../includes/banner.md)]

The **Warehouse mobile devices** workspace lets you monitor the health of all handheld devices being used in your warehouses.

The first time a user signs in to the Warehouse Management mobile app on a new device, the system will collect information about that device and add to this workspace. Thereafter, the system will continuously monitor the status of each device to make sure it's running a supported operation system and the latest version of the mobile app. Devices remain listed here listed here until they are [manually deleted](delete-devices). <!-- KFM: Please confirm this paragraph.-->

## Prerequisites

This feature requires Supply Chain Management version 10.0.37 or later. <!-- KFM: Please confirm. Anything else? (e.g., feature management, mobile app version) -->

## Open the Warehouse mobile device workspace

To open the **Warehouse mobile devices** workspace, go to **Warehouse management \> Workspaces \> Warehouse mobile devices**.

## Summary information

The **Summary** FastTab of the **Warehouse mobile devices** workspace provides tiles that show and link to the following information:

- **Device licenses used across all companies** – Shows the number of device licenses required to cover all of the devices currently in use across all companies (legal entities). If a single device is used across multiple companies, it's only counted once here. Use this information to confirm how many licenses you need. For more information about licenses,see the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544).
- **Device licenses** – Shows the number of device licenses used in the current company (legal entity). Select this tile to see a list with details about each licensed device. From the list page, you can change the licensing status for each device if needed (see also [Update device licensing information](#change-license)).
- **Devices supported** – Shows the number of healthy and compliant devices. Select this tile to see a list with details about each supported device.
- **Soon out of support devices** – Shows the number of devices that are currently healthy and compliant, but will soon become unsupported. To keep your warehouses running smoothly, be sure to upgrade or replace these devices before it's too late. Select this tile to see a list with details about each device that will soon go out of support.
- **Unsupported devices** – Shows the number of devices that are no longer supported and may not work properly. These devices may soon become blocked without further warning from Microsoft. To keep your warehouses running smoothly, be sure to upgrade or replace these devices as soon as possible. Select this tile to see a list with details about each device that is no longer unsupported. If the list includes devices that you are no longer using, you can [delete them](#delete-devices).
- **Blocked devices** – Shows the number of devices that are now blocked by Microsoft. Any attempt to sign in to one of these devices will be rejected by the system. Microsoft controls which devices are blocked, and will use this mechanism as a last resort to protect system integrity and compliance. If the list includes devices that you are no longer using, you can [delete them](#delete-devices).

## Devices needing attention

The **Devices needing attention** FastTab of the **Warehouse mobile devices** workspace provides a quick overview of devices that require attention. It provides the following two tabs:

- **Devices to update** – Open this tab to see a list of devices that are running an old version of the Warehouse Management application. You should update each of these to the latest version to ensure optimal compliance, performance, and user experience. For details about the latest version of the app, see [What's new or changed in the Warehouse Management mobile app](whats-new-wma.md). For information about how to mass deploy installations and updates for the Warehouse Management mobile app, see [Mass deploy the Warehouse Management mobile app](warehouse-app-intune.md).
- **Devices to replace** – Open this tab to see a list of devices that are running an operation system that is no longer supported. These devices could expose a risk to the system integrity and compliance, so you should replace them as soon as possible. If the list includes devices that you are no longer using, you can [delete them](#delete-devices).

## <a name="change-license"></a>Update device licensing information

If necessary, you can modify the licensing information for each device. For example, you can change the device license status from *Licensed* to *License required* if you need to free up a license for another device. Or, you can change the device license status from *License required* to *Licensed* if you have acquired a new license for the device.

To update licensing information for a device.

1. Go to **Warehouse management \> Workspaces \> Warehouse mobile devices**.
1. From the company picker, select the company (legal entity) that the device is used in.
1. Expand the **Summary** FastTab and select **Device licenses** (or whichever tile will make it easiest to find the device you are looking for <!--KFM: correct? -->).
1. Find the target device in the list and select it.
1. On the Action Pane, open the **Change device licensing** and select one of the following values to assign a new license state:
    - *Auto* – When the device is used by a shared worker, the device license become *License required*.
    - *License required* – The device needs a license that has not yet been acquired. The system selects this automatically based on usage when **Device licensing** is *Auto*.
    - *Licensed* – This indicates that the device is licensed. Select this after acquiring the needed license(s).
Block share usage	Select this to prevent the device from requiring a device license. The device can only be used by licensed users. This setting will prevent warehouse users sharing a worker account to login on the device.

## <a name="delete-devices"></a>Remove a device


