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

The **Warehouse mobile devices** workspace provides instant information about the health of your fleet of handheld devices being used in your warehouses.

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

- **Devices to update** – Open this tab to see a list with information about devices that are running an old version of the Warehouse Management application. You should update each of these to latest version to ensure best compliance, performance, and experience. For more information about the latest version, see [What's new or changed in the Warehouse Management mobile app](whats-new-wma.md). For more information about how to mass deploy installations and updates for the Warehouse Management mobile app, see [Mass deploy the Warehouse Management mobile app](warehouse-app-intune.md).
- **Devices to replace** – Open this tab to see a list with information about devices that are running an operation system that is no longer supported. These devices could expose a risk to the system integrity and compliance, so you should replace them as soon as possible. If the list includes devices that you are no longer using, you can [delete them](#delete-devices).

## <a name="change-license"></a>Update device licensing information

 F
- 
- or each device you can change the device licensing by clicking Change device licensing.
Device licensing	Description
Auto	(Default) When the device is used by a shared worker the device license become License required.
License required	Select this to indicate that the device needs a license that has not yet been acquired. The system will select this automatically based on usage when Device licensing is Auto
Licensed	This indicates that the device is licensed. Select this after acquiring the needed license(s).
Block share usage	Select this to prevent the device from requiring a device license. The device can only be used by licensed users. This setting will prevent warehouse users sharing a worker account to login on the device.

## <a name="delete-devices"></a>Remove a device
