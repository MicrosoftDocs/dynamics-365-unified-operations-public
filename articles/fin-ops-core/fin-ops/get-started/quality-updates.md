---
# required metadata

title: Proactive quality updates
description: This article provides information about Product Quality Updates, what they are, why they're used, and describes some of their benefits.
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

# Proactive Quality Updates Overview

[!include[banner](../includes/banner.md)]

This article provides information about Product Quality Updates, what they are, why they're used, and describes some of their benefits.

## What are Proactive Quality Updates?

Proactive Quality Updates (PQUs) are cumulative builds of hot fixes that are delivered with [near zero downtime](../dev-itpro/deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean) (nZDT). PQUs follow a push model where updates are applied to a Microsoft Dynamics Lifecycle Services environment in the background with minimal impact to customers. Every PQU deploys region-by-region, following a "Safe Deployment Process or SDP" that tracks issues found within each region as we deploy. The SDP helps identify issues and then course correct issues before the PQU can be deployed to more regions. PQUs are 100% automated and contain important bug fixes that are ready after the service update is generally available.

## Why is Microsoft introducing Proactive Quality Updates?

Businesses are unnecessarily impacted when they're affected by a service issue for which a solution is already available. Before PQUs, most customers didn't receive fixes until they deploy their next Service Update. PQUs simply get fixes to customers more quickly.

## What are some of the investments Microsoft is making to enable safe deployments of PQUs?

Microsoft has invested in technology and processes to make the PQU process non-disruptive:

- **Higher quality concise payloads**: PQU payloads contain changes that are limited to bug fixes and regulatory changes that are supported by flighting. Extra diligence is applied when backporting changes into a PQU to further reduce the risk of unintended regressions.
- **Safe Deployment Rollout Process**: Deployment of PQUs follows a safe deployment process (SDP) where each PQU is first delivered to a single region with small group of customers with the highest tolerance for risk. Then, if no regressions are identified, the process continues through a broader group of customers based on geographies (stations) until all customers are using the new version. This deployment model is used across Microsoft online services to build confidence in an update as it is delivered to more customers and minimize impact if unforeseen issues are detected.
- **Fall Back via flighting**: Flighting is used to enable or disable changes introduced in PQUs. If it becomes necessary to turn off a change, after a PQU deployment, this can be done using the flight system to reduce impact.
- **Higher quality concise payloads**: PQU payloads contain hot fixes that are limited to bug fixes and regulatory changes that are supported by flighting.
