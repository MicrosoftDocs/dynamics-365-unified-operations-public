---
title: Understanding Interactive AOS restarts
description: Learn about Interactive AOS restarts.
author: dvats
ms.author: dvats
ms.topic: article
ms.date: 01/01/2025
ms.custom: 
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-01-01
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Understanding Interactive AOS restarts

[!include [banner](../includes/banner.md)]


The interactive Application Object Server (AOS)  might be restarted for several reasons. Here's an overview of these reasons:

- **Routine maintenance activities** – During routine maintenance activities, such as patching, there might be temporary interruptions to AOS services. To understand the effect of maintenance activities and access-known maintenance schedules, see the following articles:


	- [Operating System Maintenance Schedule](../deployment/plannedmaintenance-selfservice.md) – Learn more about planned operating system maintenance schedules.
	- [Experience during the nZDT Maintenance Window](../deployment/plannedmaintenance-selfservice.md#interactive-usage) – Gain insights into system behavior during the nZDT maintenance window.

- **Interactive AOS server failures ("crashes")** – Interactive server failures on Interactive servers might occur because of application services that are currently running on their respective servers. Detailed failure information is available in Microsoft Dynamics Lifecycle Services. For more information about how to monitor failure information, see [Monitoring and telemetry using Application Insights](monitoring-and-telemetry-appinsights.md).
- **Infrastructure failover** – Restarts can occur if infrastructure issues lead to an internal failover. Autoscaling and capacity management are used to ensure optimal environment performance and availability.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
