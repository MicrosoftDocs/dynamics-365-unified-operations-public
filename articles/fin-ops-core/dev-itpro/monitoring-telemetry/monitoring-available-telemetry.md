---
title: Available telemetry
description: Get an overview of the telemetry that is available in the Monitoring and telemetry feature.
author: rijoshi1 
ms.topic: overview
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 04/03/2026
ms.author: rijoshi 
ms.reviewer: twheeloc
ms.custom: bap-template
---

# Available telemetry

[!include [banner](../includes/banner.md)]

[!INCLUDE[finops-product-name-long](includes/finops-product-name-long.md)] includes robust, out-of-the-box telemetry capabilities when you enable Application Insights. These capabilities provide critical insights into various aspects of the system and help you monitor performance, diagnose issues, and optimize operations. This article provides an overview of the types of telemetry that are available and corresponding resources.

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

## Batch telemetry

> [!IMPORTANT]
>
> - This feature is available in **PU69/10.0.45 (build >= 7.0.7690.21)** and **PU68/10.0.44 (build >= 7.0.7606.126)**.

Three flights control batch telemetry:

1. **BatchTelemetryConfigurationFlight**
1. **BatchThreadInfoTelemetryFlight**
1. **BatchTelemetryCallstackFlight**

If these flights aren't enabled in your environments, contact Microsoft support.

When you enable the flights, new telemetry signals appear under the **Configure** tab:

- **Batch Start Time** - Logs when a batch job starts.
- **Batch Stop Time** - Logs when a batch job completes. Supports duration tracking.
- **Batch Throttling** - Captures throttling events and related system metrics (CPU, memory, SQL DTU).
- **Batch Failure** - Adds diagnostic details when a batch job or task can't schedule. It complements existing Infolog errors by correlating telemetry with the originating batch job.
- **Batch Queue** - Shows queue sizes for different queues in the priority-based scheduling framework.
- **Batch Threads** - Shows active threads to help diagnose thread availability issues.

By using batch telemetry, you can:

- Diagnose performance and scheduling bottlenecks.
- Enable proactive monitoring through alerts and dashboards.
- Accelerate resolution of operational issues.

### Resources

- Plug and play dashboard: [Batch Monitoring Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/tree/main/Dashboards/AzureDataExplorer/Batch)
  
## DMF telemetry (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
[!INCLUDE [preview-note-d365](~/../shared-content/shared/preview-includes/preview-note-d365.md)]


> [!IMPORTANT]
>
> - This feature is available in **PU71/10.0.47 (build >= 7.0.7858.68)**, **PU70/10.0.46 (build >= 7.0.7778.87)** and **PU69/10.0.45 (build >= 7.0.7690.137)**.

Data Management Framework (DMF) telemetry helps your organization get deeper visibility into Data management executions, such as import and export operations.
By using this integration, you can:

- Monitor import and export data management functions with start and end times.
- Monitor Job status from source to staging and staging to target
- Monitor Failures with error messages at granular level

DMF telemetry is controlled by the following 2 flights:

- **DMFTelemetryConfigurationFlight**
- **DMFEnableAppInsightsLogsAndErrors**
If these flights aren't enabled in your environments, contact Microsoft support.

When you enable the flights, new telemetry signals appear under the **Configure** tab:

- **DMFJob Start** - Logs when a DMF job starts.
- **DMFJob End** - Logs when a DMF job ends.
- **DMFJob Status** - Logs job status from source to staging tables and staging to target tables.

### Resources

- Plug and play dashboard: [DMF Monitoring Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/releases/tag/DMF-1.0.0.3)

## DMF errors

The Data Management Framework (DMF) logs errors to the Custom Events table in Application Insights. Exceptions that bubble up to the X++ layer go to the Exceptions table. Each logged error has an associated error code. For error code details, see [Data management error descriptions and known limitations](../data-entities/dm-error-descriptions.md).

- Identify and fix integration issues
- Monitor data pipeline health

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
