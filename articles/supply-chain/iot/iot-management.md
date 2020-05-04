---
# required metadata

title: Monitor and manage IoT Intelligence
description: This topic describes how to view the monitor and manage IoT Intelligence.
author: robinarh
manager: AnnBe
ms.date: 08/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2020-04-04
ms.dyn365.ops.version: 10.0.5

---

# Managing IoT Intelligence

[!include [banner](../../includes/banner.md)]

This topic describes how to view the monitor and manage IoT Intelligence.

## <a id="monitor-scenarios"/>How to monitor scenarios in Dynamics 365 Supply Chain Management

There are several places to monitor IoT Intelligence processing:

+ **Modules \> Production control \> Inquiries and reports \> IoT Intelligence \> Notifications**. Here you can see the list of unresolved notifications.
+ **Modules \> Production control \> Inquiries and reports \> IoT Intelligence \> Closed notifications**. Here you can see the notifications that have been resolved or dismissed.
+ **Modules \> Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys**. Here you can see the metric keys for the Resource Status times series graphs.
+ **Modules \> Production control \> Manufacturing execution \> Resource status**. Here you can track specific metrics using the **Configure** dialog. If a scenario detects an exception, a notification with the exception details will appear.
+ **Workspaces \> Production floor management \> Notifications**. Here you can see the list of unresolved notifications.

## Modify a running IoT Intelligence scenario

When a scenario is running, you can make these modifications:

+ Add new sensor schema definitions.
+ Select new signal data values.
+ Unselect existing signal data values.
+ Add and map new signal data values.
+ Update threshold values.

When a scenario is running, these modifications are prohibited:

+ Delete or modify any schema definitions currently consumed by an enabled scenario.
+ Change the enabled scenario's selected schema paths.

## Simulation options

You can simulate factory machine signals. For more information, see these topics:

+ [Connect IoT DevKit AZ3166 to Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-arduino-iot-devkit-az3166-get-started)
+ [Connect Raspberry Pi online simulator to Azure IoT Hub (Node.js)](https://docs.microsoft.com/azure/iot-hub/iot-hub-raspberry-pi-web-simulator-get-started)
+ [Device Simulation solution accelerator overview](https://docs.microsoft.com/azure/iot-accelerators/iot-accelerators-device-simulation-overview)
