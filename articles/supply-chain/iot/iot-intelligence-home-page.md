---
# required metadata

title: IoT Intelligence home page
description: This topic provides links to information about IoT Intelligence.
author: robinarh
manager: AnnBe
ms.date: 04/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2020-04-25
ms.dyn365.ops.version: AX 7.0.0
---

# IoT Intelligence home page

[!include [banner](../../includes/banner.md)]

> [!IMPORTANT]
> **Availability**<br>Not available for Dynamics 365 Finance and Operations apps operated by 21Vianet in China.

IoT Intelligence is an add-in for Microsoft Dynamics 365 Supply Chain Management. The add-in integrates IoT signals from machinery, for example, inventory and quality, to enable manufacturers and distributors to manage production and stock in real time. IoT Intelligence supports the following scenarios:

+ **Production delays**: This scenario compares measured cycle time to planned cycle time. Supply Chain Management notifies you when production is not on schedule so that you can intervene to maximize operating efficiency and avoid order delays.
+ **Equipment downtime**: This scenario compares measured uptime to user-defined parameters. Supply Chain Management notifies you when an outage threshold is exceeded so that you can take actions like rescheduling a production work order or creating a maintenance work order.
+ **Product quality**: This scenario compares sensor readings, like moisture and temperature, to user-defined quality metrics. Supply Chain Management notifies you when a deviation occurs so that you can intervene to maintain quality standards and minimize waste.

## Setup

You can setup and configure IoT Intelligence without writing any code. The basic steps are:

1. [Azure setup for IoT Intelligence](iot-azure-setup.md): Create an IoT hub, a Redis cache, and a key vault that is accessible from Supply Chain Management.
2. [Schema formats for IoT Hub messages](iot-json-setup.md): Configure your devices to send messages to IoT Hub, and define the JSON message format.
3. [Lifecycle Services setup for IoT Intelligence](iot-lcs-setup.md): Install the add-in in Lifecycle Services (LCS), and configure the Azure secrets.
4. [Metrics setup for IoT Intelligence](iot-metrics-setup.md): Setup metrics in Supply Chain Management.
5. [Scenario setup for IoT Intelligence](iot-scenario-setup.md): Setup the scenarios in Supply Chain Management.

## Tracking and maintenance

+ [How to view the monitors in Supply Chain Management](iot-management.md#monitor-scenarios)
+ [How to disable a scenario](iot-scenario-setup.md#how-to-disable-a-scenario)
+ [How to uninstall the add-in](iot-lcs-setup.md#uninstall-addin)
+ [Modify a running IoT Intelligence scenario](iot-management.md#modify-a-running-iot-intelligence-scenario)
+ [Simulation options](iot-management.md#simulation-options)
