---
# required metadata

title: Monitor and manage IoT Intelligence
description: This topic explains how to monitor and manage IoT Intelligence.
author: johanhoffmann
ms.date: 08/16/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2020-04-04
ms.dyn365.ops.version: 10.0.5

---

# Monitor and manage IoT Intelligence

[!include [banner](../../includes/banner.md)]

This topic explains how to monitor and manage IoT Intelligence.

## <a id="monitor-scenarios"></a>Monitor scenarios in Microsoft Dynamics 365 Supply Chain Management

You can monitor IoT Intelligence processing from several places:

+ **Modules \> Production control \> Inquiries and reports \> IoT Intelligence \> Notifications** – View the list of unresolved notifications.
+ **Modules \> Production control \> Inquiries and reports \> IoT Intelligence \> Closed notifications** – View the list of notifications that have been resolved or dismissed.
+ **Modules \> Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys** – View the metric keys for the **Resource Status** times series charts.
+ **Modules \> Production control \> Manufacturing execution \> Resource status** – Track specific metrics by using the **Configure** dialog box. If a scenario detects an exception, a notification shows the details of the exception.
+ **Workspaces \> Production floor management \> Notifications** – View the list of unresolved notifications.

## Modify a running IoT Intelligence scenario

When a scenario is running, you can make these changes:

+ Add new sensor schema definitions.
+ Select new signal data values.
+ Cancel the selection of existing signal data values.
+ Add and map new signal data values.
+ Update threshold values.

When a scenario is running, these changes are prohibited:

+ Delete or modify any schema definitions that are currently consumed by an enabled scenario.
+ Change the enabled scenario's selected schema paths.

## Simulation options

You can simulate factory machine signals. For more information, see these topics:

+ [Connect IoT DevKit AZ3166 to Azure IoT Hub](/azure/iot-hub/iot-hub-arduino-iot-devkit-az3166-get-started)
+ [Connect Raspberry Pi online simulator to Azure IoT Hub (Node.js)](/azure/iot-hub/iot-hub-raspberry-pi-web-simulator-get-started)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
