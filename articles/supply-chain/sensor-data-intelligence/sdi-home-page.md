---
title: Sensor Data Intelligence home page
description: Sensor Data Intelligence enables organizations to drive business processes in Supply Chain Management based on IoT signals from machines and equipment on the production floor.
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

The Sensor Data Intelligence Add-in for Dynamics 365 Supply Chain Management enables organizations to drive business processes in Supply Chain Management based on internet of things (IoT) signals from machines and equipment on the production floor. *Sensor Data Intelligence* is an updated, renamed version of the *IoT Intelligence* add-in previously available for Supply Chain Management. The new version of Sensor Data Intelligence enables you to:

- Collect details from machines and equipment to update maintenance asset counter values in Supply Chain Management to drive predictive maintenance.
- Leverage a simple onboarding wizard to set up the solution, as opposed to manually installing and configuring components in Lifecycle Services.
- Deploy components on your own subscription, allowing you additional flexibility to manage Azure components.
- Configure, scale, and extend the solution as business logic running on Azure components, which are now managed on your own subscription, giving you the freedom to customize as needed to meet your unique business needs.

## Business scenarios

Sensor Data Intelligence enables several types of functionality, each of which is represented as a specific *scenario* in the system that provides a specialized set of configuration options, as detailed in the following table.

| Scenario | Description |
|---|---|---|
| [Equipment downtime](sdi-scenario-equipment-downtime.md) | Secure operation efficiency by using sensor readings to notify planners about machine outages and provide options to mitigate potential delays. |
| [Product quality](sdi-scenario-product-quality.md) | Secure the quality of product batches by comparing sensor readings for actual properties of each product batch, such as moisture, temperature, or custom-defined quality metrics. The system will notify users when deviations occur.
| [Production delays](sdi-scenario-production-delays.md) | Use sensor readings to compare actual cycle time to planned cycle time and notify supervisors when production is not on schedule. Supervisors can then intervene when needed to secure maximum operation efficiency.
| [Asset maintenance](sdi-scenario-asset-maintenance.md) | Minimize maintenance cost and extend asset life by improving maintenance plans based on sensor readings of critical control points for machine assets.

## Architecture

The following architectural diagram provides an overview of the solution and its components.

![Sensor Data Intelligence architectural diagram](media/sdi-architecture.png "Sensor Data Intelligence architectural diagram")
