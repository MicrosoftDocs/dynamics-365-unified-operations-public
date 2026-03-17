---
title: Monitoring and telemetry overview
description: Learn how to get started with the Application Insights integration for finance and operations apps
author: kennysaelen
ms.topic: get-started
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 03/09/2026
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Monitoring and telemetry overview

[!include [banner](../includes/banner.md)]

The [!INCLUDE[monitoringtelemetry](includes/finops-monitoring-feature-name.md)] feature provides a direct integration between an instance of [!INCLUDE[d365foscm](./includes/finops-product-name-long.md)] and the target [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] destination. [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] is a service that's hosted in Azure and gathers telemetry data for analysis and presentation. 

This feature addresses the following needs:

- Gather telemetry to gain insights into how users use the application.
- Let developers and admins gather additional information for diagnosing scenarios.
- Improve efficiency in issue detection, diagnosis, and troubleshooting, and therefore reduce the overall time to resolution.
- Enable proactive alerting through standard capabilities that [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] provides.

:::image type="content" source="images/monitoring-overview-userflows.png" alt-text="Screenshot of a diagram that shows user flows for the Monitoring and telemetry feature." lightbox="images/monitoring-overview-userflows.png":::

> [!NOTE]
> Microsoft doesn't collect the emitted telemetry for support or other operational reporting. Instead, the data is customer-owned and customer-driven.

## Gather monitoring requirements

It's easy and straightforward to configure and enable telemetry signals so that you can get the signals that are provided out of the box. However, before you can build the right experience for your team, it's important that you define the correct set of requirements that the monitoring solution must meet. Learn more in [Gather monitoring requirements](monitoring-gathering-requirements.md).

## Get started

Learn how to start to configure and use [!INCLUDE[monitoringtelemetry](includes/finops-monitoring-feature-name.md)] in [Get started with telemetry for finance and operations apps](monitoring-getting-started.md).

## Available telemetry

[!INCLUDE[d365foscm](includes/finops-product-name-short.md)] provide a set of telemetry signals out of the box. You can get a list of available signals in [Available telemetry](monitoring-available-telemetry.md).

## Extend telemetry

In addition to the out-of-the-box telemetry signals, you can add custom telemetry signals that emit information about your specific processes. To learn more, see [Add custom telemetry signals](monitoring-developer-add-custom-signals.md).

## Understand cost and pricing options

Storing telemetry in [!INCLUDE[appinsights](includes/azure-application-insights-name.md)] incurs a cost. To learn about associated costs and pricing options, see [Understand and control costs](monitoring-understanding-and-controlling-cost.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
