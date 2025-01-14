---
title: Available Telemetry
description: Overview of the available telemetry in the Monitoring and Telemetry feature.  
author: kesaelen
ms.topic: overview
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Available Telemetry

D365 Finance and SCM comes with robust out-of-the-box telemetry capabilities when Application Insights is enabled. These features provide critical insights into various aspects of the system, helping customers monitor performance, diagnose issues, and optimize operations. Below is an overview of the available telemetry and corresponding resources.

## **Form Run Telemetry**

Form run telemetry captures detailed information about forms within the application. It provides insights into:

- Which forms were opened.
- The user who accessed the forms.
- Load times for these forms.

This data allows customers to:

- Analyze average load times, P90s, and other performance metrics to improve user experience.
- Identify frequently accessed forms and optimize them for better usability.
- Detect patterns in user behavior to enhance form design and navigation.
- Monitor trends in form usage to prioritize resources and updates effectively.

### Resources:

- Plug-and-play dashboard: [Forms Telemetry Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/tree/main/Dashboards/AzureDataExplorer/Forms)

## X++ Exceptions

All exceptions that occur in the X++ layer are captured and logged to Application Insights. This telemetry enables customers to:

- Monitor and diagnose application errors to maintain application stability.
- Track exception trends over time to identify recurring issues.
- Prioritize resolution efforts based on the frequency and severity of exceptions.
- Analyze the impact of exceptions on user operations and workflows.
- Set up alerts for specific exceptions in critical processes or overall exception trend spikes to ensure timely responses.

### Resources:

- Plug-and-play dashboard: [X++ Errors Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/tree/main/Dashboards/AzureDataExplorer/Errors)

## Warehouse Telemetry

The warehouse module generates extensive telemetry data, offering insights into:

- Warehouse operations and workflows.
- Performance metrics to identify and resolve bottlenecks.

This telemetry can be visualized using the provided Power BI dashboards.

### Resources:

- Documentation: [Warehouse Telemetry in Application Insights](https://learn.microsoft.com/dynamics365/supply-chain/warehousing/application-insights-monitor-usage-performance#view-telemetry-data-in-power-bi)
- Power BI dashboard: [Warehouse Power BI Dashboard](https://github.com/microsoft/d365-scm-telemetry/tree/main/samples/PowerBI/Appsource)

## DMF Errors

Errors from the Data Management Framework (DMF) are logged to the exceptions table in Application Insights. These errors include issues encountered during data import and export operations, enabling customers to:

- Identify and address integration issues quickly.
- Monitor the health of data pipelines.
