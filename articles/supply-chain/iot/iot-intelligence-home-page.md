---
# required metadata

title: IoT Intelligence core insights home page
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

# Dual-write home page

[!include [banner](../../includes/banner.md)]

These topics describe IoT Intelligence Core Insights.

Internet of things (IoT) Intelligence supports the following core insights and action scenarios:

+ **Delayed orders** : Provides notification services and actions for managing delayed production orders. Displays impacted operations. Provides users with the ability to define order-delay metrics for combinations of resources and products, and notifies users when exceptions to these thresholds occur. Enables users to take relevant business actions for delayed orders, including the ability to view impact or create a maintenance request.
+ **Equipment down**: Provides notification services and actions for managing equipment-down scenarios. Displays impacted operations. Provides users with the ability to define metrics for machine-down thresholds and notifies users when an exception to these thresholds occurs. Enables users to take relevant business actions for delayed orders, including the ability to view impact or create a maintenance work order.
+ **Quality anomaly**: Provides notification services and actions for managing quality anomalies. Provides users with the ability to define quality attributes for products and get notified when exceptions to these attributes occur.

## Setup

You can setup and configure core insights without writing any code. The basic steps in setup are:

+ [JSON formats for IoT Intelligence core insights](iot-json-setup.md): Configure your devices to send telemetry to IoT Hub, and define the JSON message format.
+ [Azure setup for IoT Intelligence core insights](iot-azure-setup.md): Create an Azure key vault with an IoT hub and a Redis cache.
+ [LCS setup for IoT Intelligence core insights](iot-lcs-setup.md): Install the add-in in Lifecycle Services (LCS), and configure the Azure secrets.
+ [](): Create a OneBox environment, and give the appropriate SQL users access to environment for IoT Intelligence.
+ [Scenario setup for IoT Intelligence core insights](iot-scenario-setup.md): Setup the scenarios in Supply Chain Management.
+ [Metrics setup for IoT Intelligence core insights](iot-metrics-setup.md): Setup metrics in Supply Chain Management.

## Tracking and maintenance

+ [How to view the monitors in Supply Chain Management](iot-management.md#)
+ [How to disable a scenario](iot-management.md#)
+ [How to uninstall the add-in](iot-management.md#)
+ [Modify a running IoT Intelligence scenario](iot-management.md#)
+ [Simulation options](iot-management.md#)
