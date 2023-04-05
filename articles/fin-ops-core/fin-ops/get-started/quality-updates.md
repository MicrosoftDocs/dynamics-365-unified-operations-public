---
# required metadata

title: Proactive quality updates
description: This article provides information about proactive quality updates (PQUs). It explains what they are and why they're used, and describes some of their benefits.
author: rashmansur
ms.date: 04/05/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: rashmim
ms.search.validFrom: 2022-08-19
ms.search.form:
ms.dyn365.ops.version: 10.0.29
---

# Proactive quality updates

[!include[banner](../includes/banner.md)]

This article provides information about proactive quality updates (PQUs). It explains what they are and why they're used, and describes some of their benefits.

## What are PQUs?

PQUs are cumulative builds of hotfixes that are delivered with [near-zero downtime](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean). PQUs follow a push model, where updates are applied to a Microsoft Dynamics Lifecycle Services environment in the background and have minimal impact on customers. Every PQU is deployed region by region, by following a "safe deployment process" that tracks issues that are found within each region during deployment. The safe deployment process helps identify and fix issues before the PQU is deployed to more regions. PQUs are 100-percent automated and contain important bug fixes that are ready after the service update is generally available.

## Why is Microsoft introducing PQUs?

Before the introduction of PQUs, most customers didn't receive fixes for service issues until they deployed their next service update. Therefore, businesses could be unnecessarily affected by service issues that a fix was already available for. PQUs get fixes to customers more quickly.

## What investments is Microsoft making to enable safe deployments of PQUs?

Microsoft has invested in the following technologies and processes to make the PQU process non-disruptive:

- **Higher-quality concise payloads** – The changes that PQU payloads contain are limited to bug fixes and regulatory changes that are supported by flighting. We apply extra diligence when we backport changes into a PQU, to further reduce the risk of unintended regressions.
- **Safe deployment rollout process** – Deployment of PQUs follows a safe deployment process. Each PQU is first delivered to a single region that contains a small group of customers who have the highest tolerance for risk. Then, if no regressions are identified, the process continues through a broader group of customers, based on geographies (stations), until all customers are using the new version. This deployment model is used across Microsoft online services to help build confidence in an update as it's delivered to more customers, and to help minimize the impact if unforeseen issues are detected.
- **Fallback via flighting** – Flighting is used to enable or disable changes that are introduced in PQUs. If a change must be turned off after a PQU deployment, the flight system can be used to turn it off, to help reduce the impact.
