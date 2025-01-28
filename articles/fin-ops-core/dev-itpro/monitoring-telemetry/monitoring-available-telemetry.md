---
title: Available telemetry
description: Get an overview of the telemetry that is available in the Monitoring and telemetry feature.
author: kennysaelen
ms.topic: overview
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 01/20/2025
ms.author: kesaelen
ms.reviewer: johnmichalak
ms.custom: bap-template
---

# Available telemetry

[!include [banner](../includes/banner.md)]

[!INCLUDE[finops-product-name-long](includes/finops-product-name-long.md)] include robust, out-of-box telemetry capabilities when Application Insights is enabled. These capabilities provide critical insights into various aspects of the system and help customers monitor performance, diagnose issues, and optimize operations. This article provides an overview of the types of telemetry that are available and corresponding resources.

## Form run telemetry

Form run telemetry captures detailed information about forms within the application. It provides insights into the following details:

- The forms that were opened
- The users who accessed the forms
- Load times for the forms

Customers can use this data for the following purposes:

- Analyze average load times, P90s, and other performance metrics to improve the user experience.
- Identify frequently accessed forms, and optimize them for better usability.
- Detect patterns in user behavior to enhance form design and navigation.
- Monitor trends in form usage to prioritize resources and updates effectively.

### Resources

- Plug-and-play dashboard: [Forms Telemetry Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/tree/main/Dashboards/AzureDataExplorer/Forms)

## X++ exceptions

All exceptions that occur in the X++ layer are captured and logged to Application Insights. Customers can use this telemetry for the following purposes:

- Monitor and diagnose application errors to maintain application stability.
- Track exception trends over time to identify recurring issues.
- Prioritize resolution efforts based on the frequency and severity of exceptions.
- Analyze the impact of exceptions on user operations and workflows.
- Set up alerts for specific exceptions in critical processes or overall exception trend spikes to ensure timely responses.

### Resources

- Plug-and-play dashboard: [X++ Errors Dashboard](https://github.com/microsoft/Dynamics-365-FastTrack-FSCM-Telemetry-Samples/tree/main/Dashboards/AzureDataExplorer/Errors)

## Warehouse telemetry

The warehouse module generates extensive telemetry data. The data offers insights into the following details:

- Warehouse operations and workflows
- Performance metrics, so that bottlenecks can be identified and fixed

This telemetry can be visualized by using the Power BI dashboards that are provided.

### Resources

- Documentation: [View telemetry data in Application Insights](/dynamics365/supply-chain/warehousing/application-insights-monitor-usage-performance#view-telemetry-data-in-power-bi)
- Power BI dashboard: [Warehouse Power BI Dashboard](https://github.com/microsoft/d365-scm-telemetry/tree/main/samples/PowerBI/Appsource)

## DMF errors

Errors from the Data Management Framework (DMF) are logged to the Custom Events table in Application Insights (Since lot of DMF errors coudl be user errors live invalid/missing data etc. We do not want to mix those with exceptions and have false flags for system exceptions). These errors include issues that are encountered during data import and export operations. Customer can use this information for the following purposes:

- Quickly identify and address integration issues.
- Monitor the health of data pipelines.
- List of DMF errors can be found here : https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dm-error-descriptions

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
