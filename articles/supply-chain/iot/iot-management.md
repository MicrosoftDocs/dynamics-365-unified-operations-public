---
# required metadata

title: Managing IoT Intelligence core insights
description: This topic describes how to view the message stream, and modify and uninstall core insights.
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

# Managing IoT Intelligence core insights

[!include [banner](../../includes/banner.md)]

## How to view the monitors in Supply Chain Management

There are several ways to view the messages processed in the scenario in Supply Chain Management:

+ **Production control \> Inquiries and reports \> IoT Intelligence \> Notifications**. Here you can see the list of unresolved notifications. A notification is generated when a machine is down.
+ **Production control \> Inquiries and reports \> IoT Intelligence \> Closed notifications**. Here you can see the notifications that have been resolved.
+ **Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys**. Here you can see a times series graph for each machine that you're processing.
+ **Production control \> Manufacturing execution \> Resource status**. You can configure this page to track specific machines using the **Configure** dialog. As messages are processed a graph is produced showing the parts produced. This page displays an error message if a machine is down, and there are buttons to resolve or dismiss the error message.
+ **Production control \> Setup \> IoT Intelligence \> Scenario parameters**. Click **Equipment downtime** to see all the machines that are available.

## How to disable a scenario

In Supply Chain Management, run the **Equipment downtime** configuration wizard, and disable the scenario.

## How to uninstall the add-in

1. In Supply Chain Management, run the **Equipment downtime** configuration wizard, and disable the scenario.
2. In LCS, uninstall the add-in.

## Modify a running IoT Intelligence scenario

List what can and cannot be updated while the scenario is running

## Simulation options

+ Setup IoT solutions to simulate factory machine signals:
    + https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-raspberry-pi-web-simulator-get-started
    + https://docs.microsoft.com/en-us/azure/iot-accelerators/quickstart-device-simulation-deploy
    + https://docs.microsoft.com/en-us/azure/iot-accelerators/iot-accelerators-device-simulation-create-simulation
    + https://docs.microsoft.com/en-us/azure/iot-accelerators/iot-accelerators-device-simulation-overview

+ Setup a MxChip to simulate a factory machine signal:
    + https://docs.microsoft.com/en-us/azure/iot-central/core/quick-create-simulated-device
    + https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-arduino-iot-devkit-az3166-translator
