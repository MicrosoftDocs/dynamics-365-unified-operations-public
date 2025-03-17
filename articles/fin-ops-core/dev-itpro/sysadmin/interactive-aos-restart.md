---
title: Understand Interactive Application Object Server (AOS) restarts
description: Learn about Interactive Application Object Server (AOS) restarts.
author: dvats
ms.author: dvats
ms.topic: overview
ms.date: 01/09/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-01-01
ms.dyn365.ops.version: AX 7.0.0
---

# Understand Interactive Application Object Server (AOS) restarts

[!include [banner](../includes/banner.md)]


The interactive Application Object Server (AOS) might be restarted for several reasons. Here's an overview of these reasons:

- **Routine maintenance activities** – During routine maintenance activities, such as patching, there might be temporary interruptions to AOS services. To understand the effect of maintenance activities and access-known maintenance schedules, see the following articles:

   - [Operating System Maintenance Schedule](../deployment/plannedmaintenance-selfservice.md) – Learn more about planned operating system maintenance schedules.
   - [Experience during the nZDT Maintenance Window](../deployment/plannedmaintenance-selfservice.md#interactive-usage) – Gain insights into system behavior during the nZDT maintenance window.

- **Interactive AOS server failures ("crashes")** – Failures on Interactive servers might occur because of application services that are currently running. Detailed failure information is available in Microsoft Dynamics Lifecycle Services. For more information about how to monitor failure information, see [Monitoring and telemetry using Application Insights](monitoring-and-telemetry-appinsights.md).
- **Infrastructure failover** – Restarts can occur if infrastructure issues lead to an internal failover. Autoscaling and capacity management are used to ensure optimal environmental performance and availability.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
