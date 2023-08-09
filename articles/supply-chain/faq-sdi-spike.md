---
title: FAQ for the Detect spikes and deviations in sensor data feature
description: This FAQ provides answers to frequently asked questions about the AI technology that's used in the "Detect spikes and deviations in sensor data" feature in Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 07/20/2023
ms.custom: 
  - transparency-note
ms.topic: article
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
---

# FAQ for the Detect spikes and deviations in sensor data feature

This transparency note describes the AI impact of the *Detect spikes and deviations in sensor data* feature in Microsoft Dynamics 365 Supply Chain Management.

## What is the Detect spikes and deviations in sensor data feature?

The *Detect spikes and deviations in sensor data* feature monitors the behavior of a machine and generates an alert if any abnormal patterns or deviations from the usual behavior are detected. This scenario requires the installation of a sensor that continuously collects data and sends it to the Microsoft Azure IoT hub for analysis. The anomaly detection system analyzes the data in real time and triggers an alert if it identifies any anomalies or deviations from normal operating conditions. This proactive approach helps identify potential issues before they become significant problems. Therefore, it enables timely maintenance or intervention to minimize downtime and optimize machine performance.

## What are capabilities of the Detect spikes and deviations in sensor data feature?

The feature uses the [Azure Anomaly Detector](/azure/ai-services/anomaly-detector/overview) to monitor and detect anomalies in your time series data using artificial intelligence. The Anomaly Detector is a component in the Azure AI services. When an anomaly is detected, supervisors will receive a notification with relevant information, which is provided in a Supply Chain Management workspace.

## What is the intended use of the Detect spikes and deviations in sensor data feature?

The intended use of the feature is to help supervisors to identify and predict problems before they become urgent. Supervisors can then act to solve the issue proactively to help prevent costly downtime on machines and equipment.

## How was the Detect spikes and deviations in sensor data feature evaluated? What metrics are used to measure performance?

The feature underwent substantial testing before it was released. It uses the Azure Anomaly Detector (part of Azure AI services), which is widely adopted by many organizations.

## What are the limitations of the Detect spikes and deviations in sensor data feature? How can users minimize the impact of these limitations when using it?

When configuring the feature, supervisors have the option to set thresholds that control how sensitive the detection system should be when identifying an anomaly, which affects how often notifications are generated. Notifications don't impact any other business data or processes and are only used for providing awareness.

## What operational factors and settings allow for effective and responsible use of the Detect spikes and deviations in sensor data feature?

Supervisors should familiarize themselves with the options available to configure the anomaly detection component. The following options are available:

- **Sensitivity** – Defines the sensitivity of the anomaly detection algorithm. The higher the value, the more sensitive the system will be and the more notifications you'll receive.
- **Maximum anomaly ratio** – Defines the maximum number of anomaly alerts that the sensor should generate per period. The higher the value, the more notifications you'll receive.

## See also

- [Anomaly detection scenario](sensor-data-intelligence/sdi-scenario-anomaly.md)
- [What is Anomaly Detector?](/azure/ai-services/anomaly-detector/overview)
