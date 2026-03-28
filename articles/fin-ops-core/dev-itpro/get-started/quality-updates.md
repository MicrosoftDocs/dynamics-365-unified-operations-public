---
title: Proactive quality updates overview
description: Learn about proactive quality updates (PQUs). It explains what they are and why they're used, and describes some of their benefits.
author: rashmansur
ms.author: rashmim
ms.topic: concept-article
ms.date: 03/26/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-08-19
ms.dyn365.ops.version: 10.0.29
---

# Proactive quality updates overview

[!include[banner](../../../finance/includes/banner.md)]

This article provides information about proactive quality updates (PQUs). It explains what they are and why they're used, and describes some of their benefits.

## What are PQUs?

PQUs are cumulative builds of hotfixes that Microsoft delivers with [near-zero downtime](../deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean). PQUs follow a push model, where Microsoft applies updates to a Microsoft Dynamics Lifecycle Services environment in the background with minimal impact on customers. Microsoft deploys every PQU region by region, following a "safe deployment process" that tracks problems found within each region during deployment. The safe deployment process helps identify and fix problems before the PQU is deployed to more regions. PQUs are fully automated and contain important bug fixes and high-priority product features that are ready after the service update is generally available.

## Why is Microsoft introducing PQUs?

Before the introduction of PQUs, most customers didn't receive fixes for service problems until they deployed their next service update. Therefore, businesses could be unnecessarily affected by service problems that a fix was already available for. PQUs get fixes to customers more quickly.

## What investments is Microsoft making to enable safe deployments of PQUs?

Microsoft invested in the following technologies and processes to make the PQU process nondisruptive:

- **Higher-quality concise payloads** – The changes that PQU payloads contain are limited to bug fixes and regulatory changes that flighting supports. Microsoft applies extra diligence when backporting changes into a PQU, to further reduce the risk of unintended regressions.
- **Safe deployment rollout process** – Deployment of PQUs follows a safe deployment process. Microsoft first delivers each PQU to a single region that contains a small group of customers who have the highest tolerance for risk. Then, if no regressions are identified, the process continues through a broader group of customers, based on geographies (stations), until all customers are using the new version. Microsoft uses this deployment model across its online services to help build confidence in an update as it's delivered to more customers, and to help minimize the impact if unforeseen problems are detected.
- **Fallback via flighting** – Flighting is used to enable or disable changes that PQUs introduce. If a change must be turned off after a PQU deployment, the flight system can turn it off to help reduce the impact.

## Additional resources

- [Release schedule for proactive quality updates](quality-updates-schedule.md)
- [Proactive quality updates FAQ](quality-updates-faq.md)
