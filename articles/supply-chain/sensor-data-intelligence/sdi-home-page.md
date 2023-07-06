---
title: Sensor Data Intelligence home page
description: This article provides an overview of Sensor Data Intelligence. Organizations can use this feature to drive business processes in Microsoft Dynamics 365 Supply Chain Management, based on Internet of Things (IoT) signals from machines and equipment on the production floor.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# Sensor Data Intelligence home page

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

Sensor Data Intelligence for Microsoft Dynamics 365 Supply Chain Management enables organizations to drive business processes in Supply Chain Management, based on Internet of Things (IoT) signals from machines and equipment on the production floor. It's an updated, renamed version of the *IoT Intelligence* feature that was previously available for Supply Chain Management.

Sensor Data Intelligence lets you perform the following tasks:

- Collect details from machines and equipment to update maintenance asset counter values in Supply Chain Management and drive predictive maintenance.
- Set up the solution by using a simple onboarding wizard instead of manually installing and configuring components in Microsoft Dynamics Lifecycle Services (LCS).
- Deploy components on your own subscription, so that you have more flexibility to manage Azure components.
- Configure, scale, and extend the solution as business logic that runs on Azure components. Those components are now managed on your own subscription. Therefore, you can customize them as required to meet your unique business needs.

## Business scenarios

Sensor Data Intelligence enables several types of functionality, each of which is represented by a specific *scenario* in the system. Each scenario provides a specialized set of configuration options in the system, as detailed in the following table.

| Scenario | Description |
|---|---|
| [Anomaly detection](sdi-scenario-anomaly.md) | Detect anomalies in sensor readings for machine assets, and notify supervisors when anomalies occur. |
| [Asset downtime](sdi-scenario-asset-downtime.md) | Accurately track the efficiency of machine assets by using sensor data to track machine downtime. |
| [Asset maintenance](sdi-scenario-asset-maintenance.md) | Minimize maintenance cost and extend asset life by improving maintenance plans based on sensor readings of critical control points for machine assets. |
| [Machine status](sdi-scenario-equipment-downtime.md) | Ensure operation efficiency by using sensor readings to notify planners about machine outages and provide options for mitigating potential delays. |
| [Product quality](sdi-scenario-product-quality.md) | Ensure the quality of product batches by comparing sensor readings for actual properties of each product batch, such as moisture, temperature, or custom-defined quality metrics. The system will notify users when deviations occur. |
| [Production delays](sdi-scenario-production-delays.md) | Use sensor readings to compare actual cycle time to planned cycle time, and notify supervisors when production isn't on schedule. Supervisors can then intervene as required to ensure maximum operation efficiency. |

## Architecture

The following architectural diagram provides an overview of the solution and its components.

![Sensor Data Intelligence architectural diagram.](media/sdi-architecture.png "Sensor Data Intelligence architectural diagram")
