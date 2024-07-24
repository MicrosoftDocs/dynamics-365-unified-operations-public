---
title: Monitoring and diagnostics tools in Lifecycle Services
description: Learn about the tools that Microsoft Dynamics Lifecycle Services provides to help you monitor, diagnose, and analyze the health of the environments.
author: angelmarshall
ms.author: tsmarsha
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 07/24/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.assetid: eb056816-ccf4-43a5-aed3-cf72543353de
---

# Monitoring and diagnostics tools in Lifecycle Services

[!include [banner](../includes/banner.md)]
[!include [Lifecycle Services deprecation](../includes/lcs-deprecation.md)]

Monitoring capabilities in Lifecycle Services are being rebuilt in [Monitoring and telemetry using Application Insights](../sysadmin/monitoring-and-telemetry-appinsights.md) experiences for Finance and Operations apps.  Below you find a detailed description of the available pages in Lifecycle Services monitoring, however some capabilities begin to be disabled starting in September 2024.

## Overview

This tab provides a summary of the environment's health and performance. It includes general status information and demonstrates the number of AOS and Batch servers that are receiving traffic.

## Activity

The Activity tab displays user and system activities. You can filter activities by user, time, and specific actions. This helps in tracking and troubleshooting user-reported issues.

### Deprecated Activity Logs in September 2024
As part of the first wave of monitoring deprecation, the following queries are disabled because they now have feature parity in [Monitoring and telemetry using Application Insights](../sysadmin/monitoring-and-telemetry-appinsights.md).
* Get user Login Events
* Get Error Events for Form
* Get Connection Outages
* Get Slow Interactions
* Get All Events for Activity
* Get All Events for Failed Batch Job
* Get Errors for Activity
* Get Distinct Users
* Get Events for User
* Get Events for Browser Sessions
* Get Weak Ciphers Usage

## Health Metrics

The Health Metrics tab offers insights into system health indicators such as CPU usage, memory usage, and error rates. Key metrics are monitored to ensure optimal performance. This tab is in maintenance mode and no longer receiving support.

## SQL Insights

SQL Insights provide advanced SQL performance analysis tools. SQL Insights helps in diagnosing and troubleshooting SQL-related issues. 

### Deprecated SQL Insights in September 2024
As part of the first wave of monitoring deprecation, the following capabilities are disabled because they're now managed by Microsoft as part of the managed service.

* End SQL Process



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]


