---
title: Monitoring and Telemetry overview
description: This article explains how to get started with the Application Insights integration for finance and 
author: kesaelen
ms.topic: overview
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: kesaelen
ms.custom: bap-template
---

# Monitoring and telemetry using Application Insights

The [!INCLUDE[monitoringtelemetry](./includes/finops-monitoring-feature-name.md)] feature is a direct, point-to-point integration between a [!INCLUDE[d365foscm](./includes/finops-product-name-long.md)] instance and the target [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] destination. [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] is a service hosted within Azure that gathers telemetry data for analysis and presentation. 

This feature addresses the following needs:

- Gather telemetry to gain insights on how the application is used.
- Allows for developers and admins to gather additional information in diagnosing scenarios.
- Improve efficiency in detecting, diagnosing and troubleshooting issues, reducing the overall time resolution.
- Enable proactive alerting through standard capabilities provided by [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)].  

[![Monitoring and Telemetry Feature.](./images/monitoring-overview-userflows.png)](./monitoring-overview-userflows.png)

> [!NOTE]
> The emitted telemetry is not collected by Microsoft for support or other operational reporting. Instead, the data is customer owned and customer driven.

## Gathering monitoring requirements

It is easy and straightforward to configure and enable telemetry signals to get the out of the box provided signals. However, before being able to build the right experience for your team it is important to define the correct set of requirements that the monitoring solution must meet.

For more information, see [Gathering requirements](./monitoring-gathering-requirements.md).

## Getting started

To get started configuring and using [!INCLUDE[monitoringtelemetry](./includes/finops-monitoring-feature-name.md)], refer to [Getting started](./monitoring-getting-started.md).

## Available telemetry

[!INCLUDE[d365foscm](./includes/finops-product-name-long.md)] provides a set of telemetry signals out of the box. See [Available telemetry](./monitoring-available-telemetry.md) for a list of all available signals.

## Extending Telemetry

On top of the out of the box telemetry signals it is possible to add customer telemetry signals that emit information about your specific processes. See [Add custom telemetry signals](./monitoring-developer-add-custom-signals.md).

## Understanding cost and pricing options

Storing telemetry in [!INCLUDE[appinsights](./includes/azure-application-insights-name.md)] does come with a cost. To understand more about associated cost and pricing options, see [Controlling telemetry cost](./monitoring-controlling-telemetry-costs.md).
