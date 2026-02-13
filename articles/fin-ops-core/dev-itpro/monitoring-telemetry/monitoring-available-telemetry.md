---
title: Available telemetry
description: Get an overview of the telemetry that is available in the Monitoring and telemetry feature.
author: rijoshi1 
ms.topic: overview
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 01/15/2026
ms.author: rijoshi 
ms.reviewer: twheeloc
ms.custom: bap-template
---

# Available telemetry

[!include [banner](../includes/banner.md)]

[!INCLUDE[finops-product-name-long](includes/finops-product-name-long.md)] include robust, out-of-box telemetry capabilities when you enable Application Insights. These capabilities provide critical insights into various aspects of the system and help you monitor performance, diagnose issues, and optimize operations. This article provides an overview of the types of telemetry that are available and corresponding resources.

## Form run telemetry

Form run telemetry captures detailed information about application forms. It provides insights into the following details:

- Opened forms
- Users who accessed the forms
- Form load times

Use this data to:

- Analyze average load times, P90 values, and other performance metrics to improve user experience.
- Identify frequently accessed forms and optimize them for better usability.
- Detect patterns in user behavior to enhance form design and navigation.
- Monitor trends in form usage to prioritize resources and updates effectively.

### Resources

- Plug-and-play dashboard: [Forms Telemetry Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/tree/main/Dashboards/AzureDataExplorer/Forms)

## X++ exceptions

The platform captures and logs all X++ layer exceptions to Application Insights. Use this telemetry to:

- Monitor and diagnose errors to keep the app stable.
- Track exception trends to spot recurring issues.
- Prioritize fixes based on exception frequency and severity.
- Analyze exception impact on user tasks and workflows.
- Set alerts for specific exceptions in critical processes and spikes in overall exception trends for quick response.

### Resources

- Plug-and-play dashboard: [X++ Errors Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/tree/main/Dashboards/AzureDataExplorer/Errors)

## Warehouse telemetry

The warehouse module generates telemetry data. The data shows the following telemetry:

- Warehouse operations and workflows
- Performance metrics to identify and fix bottlenecks

Use the provided Power BI dashboards to visualize the telemetry.

### Resources

- Documentation: [View telemetry data in Application Insights](/dynamics365/supply-chain/warehousing/application-insights-monitor-usage-performance#view-telemetry-data-in-power-bi).
- Power BI dashboard: [Warehouse Power BI dashboard](https://github.com/microsoft/d365-scm-telemetry/tree/main/samples/PowerBI/Appsource).

## DMF errors

The Data Management Framework (DMF) logs errors to the Custom Events table in Application Insights. Exceptions that bubble up to the X++ layer go to the Exceptions table. Each logged error has an associated error code. For error code details, see [Data management error descriptions and known limitations](../data-entities/dm-error-descriptions.md).

- Identify and fix integration issues
- Monitor data pipeline health

## Batch telemetry

> [!IMPORTANT]
> - This feature is available in **PU69/10.0.45 (build >= 7.0.7690.21)** and **PU68/10.0.44 (build >= 7.0.7606.126)**.

Batch telemetry is controlled by the following 3 flights: If it's not enabled in your environments, reach out to Microsoft support.
1. **BatchTelemetryConfigurationFlight**
1. **BatchThreadInfoTelemetryFlight**
1. **BatchTelemetryCallstackFlight**

If it's not enabled in your environments, reach out to Microsoft support.

After the flights are enabled, new telemetry signals appear under the **Configure** tab:

- **Batch Start Time** - Logs when a batch job starts.
- **Batch Stop Time** - Logs when a batch job completes. Supports duration tracking.
- **Batch Throttling** - Captures throttling events and related system metrics (CPU, memory, SQL DTU).
- **Batch Failure** - Adds diagnostic details when a batch job or task can't schedule. It complements existing Infolog errors by correlating telemetry with the originating batch job.
- **Batch Queue** - Shows queue sizes for different queues in the priority-based scheduling framework.
- **Batch Threads** - Shows active threads to help diagnose thread availability issues.

With batch telemetry, you can:
- Diagnose performance and scheduling bottlenecks
- Enable proactive monitoring through alerts and dashboards
- Accelerate resolution of operational issues

### Resources

- Plug and play dashboard: [Batch Monitoring Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/tree/main/Dashboards/AzureDataExplorer/Batch)
  
## DMF telemetry (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
[!INCLUDE [preview-note-d365](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

We're enhancing the **Monitoring** and **Telemetry** features by introducing **DMF telemetry** integration with Application Insights. This capability is currently behind feature flights. While you might notice additional events in the UI, the underlying telemetry is planned for preview in January 2026. We share additional details as soon as the feature becomes available.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
