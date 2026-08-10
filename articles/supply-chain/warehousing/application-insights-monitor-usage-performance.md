---
title: Monitor Warehouse Management usage and performance
description: The Supply Chain Management tenant emit telemetry data, which lets you monitor and analyze the activities and general health of your system.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 08/10/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Monitor Warehouse Management usage and performance

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management emits telemetry data for various Warehouse Management activities and operations, including both the Supply Chain Management tenant and the Warehouse Management mobile app. Telemetry data helps provide insight into the activities and general health of your tenants and devices, so that you can diagnose problems and analyze operations that affect performance. Use [Application Insights](/azure/azure-monitor/app/app-insights-overview), an Azure service that's optimized for this purpose, to collect and process telemetry data.

## Prerequisites

Before you can collect and analyze Warehouse Management telemetry data, ensure that your system meets the following prerequisites:

- **Supply Chain Management version** – Telemetry with Application Insights requires Supply Chain Management version 10.0.29 or later. Additional telemetry features require later versions. See the tables later in this article for details about which features require which versions of Supply Chain Management.
- **Warehouse Management mobile app version** – Telemetry with Application Insights requires Warehouse Management mobile app version 2.0.28 or later. Additional telemetry features require later versions of the app. See the tables later in this article for details about which features require which versions of Supply Chain Management and the Warehouse Management mobile app.
- **Application Insights** – You must have an Application Insights resource in Azure, and you must configure your Supply Chain Management environment to send telemetry data to it. For instructions, see [Enable warehousing telemetry with Application Insights](application-insights-warehousing.md).

## View telemetry data in Power BI

The fastest and easiest way to get started viewing your warehousing telemetry is to download and set up the Power BI reports provided by Microsoft. The downloadable reports and instructions for how to set them up are available in the [Supply Chain Management telemetry repository on GitHub](https://github.com/microsoft/d365-scm-telemetry/tree/main/samples/PowerBI/Appsource).

## Technical details of all available telemetry data

In Application Insights, telemetry data from Supply Chain Management tenants and the Warehouse Management mobile app are logged as custom events. Technical details of all custom events and all data that could be logged for each event are available in the Supply Chain Management telemetry repository on GitHub. This information can help you design your own custom Power BI reports and explore the data directly in Application Insights. The following sample query files list all of the available event IDs, field names, and version requirements:

- For Supply Chain Management tenant telemetry details, see the [WarehouseManagement.kql example query on GitHub](https://github.com/microsoft/d365-scm-telemetry/blob/main/samples/KQL/example_queries/WarehouseManagement.kql).
- For Warehouse Management mobile app telemetry details, see the [WarehouseMobileApp.kql example query on GitHub](https://github.com/microsoft/d365-scm-telemetry/blob/main/samples/KQL/example_queries/WarehouseMobileApp.kql).

## Analyze how long work takes in the mobile app (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]

Warehouse Management mobile app version 4.1.5.0 and later emits telemetry that describes how long work takes in the app, rather than only how long the server takes to answer. Use this telemetry to find the steps where workers lose the most time, and to tell a slow server apart from a page that's simply hard to complete.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

### Time spent on each page

Every request that the app sends to the server reports how long the worker spent on the page that the request replaces. The app splits this time into two separate measurements:

- **Active time** – Time when the app is in the foreground and the worker can act on the page.
- **Idle time** – Time when the app is in the background, or the device is locked or asleep.

The app reports these measurements separately because a page that's left open on a locked device during a break otherwise looks the same as a page that a worker struggles to complete. Only the active time indicates that a page is hard to fill in.

A page is new when its structure changes. The structure refers to the page layout and the set of fields and buttons on it. Retyping a value or correcting an entry doesn't start a new measurement because the worker is still completing the same step.

### Completed operations

The app reports a summary for each unit of work that a worker completes, such as a full putaway or a picking run, instead of a single page or request. Each summary covers the whole flow, from the moment the worker starts the operation until the server confirms it. The summary describes the following aspects of the flow:

- How many pages the worker moved through and how many requests the app sent.
- How many buttons the worker pressed and how often the worker had to open a dialog box to enter or edit a value.
- How many error messages the server returned during the flow.
- How the worker entered data, including how much of the flow the worker spent scanning with the camera compared to a dedicated scanner such as a ring scanner.
- How the elapsed time divided between waiting for the server, filling in pages, and idle time.

The app also reports operations that a worker abandons. These operations indicate how the flow ended, such as whether the worker canceled it or signed out. The app includes abandoned operations so that the data doesn't reflect only the flows that succeeded, which are the flows that are least likely to need attention.

Because each summary covers a complete flow, you can compare the same operation across sites, shifts, and devices. You can see the effect of a configuration change on the time that the operation takes end to end.

### Correlate app telemetry with server telemetry

Mobile app events include the identifier of the server session that the worker signed in to. Because Supply Chain Management also records the identifier, you can join the events that the app emits to the corresponding server-side activity. You can follow a single worker's session across both.

Use this identifier when the app reports a slow step, so you can determine whether the worker spent the time on the device or in Supply Chain Management. Keep the detailed diagnostic information in the server-side telemetry, and use the session identifier to find it, instead of increasing the volume of data that each device sends.

For the field names that carry this data, and the app and Supply Chain Management versions that are required for each field, see the [WarehouseMobileApp.kql example query on GitHub](https://github.com/microsoft/d365-scm-telemetry/blob/main/samples/KQL/example_queries/WarehouseMobileApp.kql).

## View telemetry data in Application Insights

As an alternative to Power BI, you can view your telemetry data directly in Application Insights. Telemetry is stored in Azure Monitor Logs in the `customEvents` table. You can view the collected data by writing log queries in the Kusto Query Language (KQL). For more information, see [Azure Monitor Logs overview](/azure/azure-monitor/logs/data-platform-logs) and [Log queries in Azure Monitor](/azure/azure-monitor/logs/log-query-overview).

As a simple example, follow these steps:

1. In the [Azure portal](https://portal.azure.com/), open your Application Insights resource.
1. On the **Monitoring** menu, select **Logs**.
1. On the **New Query** tab, enter the following code to view the last 100 custom events.

    ```plaintext
    kql
    customEvents
    | take 100
    | sort by timestamp desc
    ```

## Review sample code, FAQs, and more in the Supply Chain Management telemetry GitHub repository

For more examples of how to work with KQL, plus answers to frequently asked questions, and tips about using Supply Chain Management telemetry with Excel, Power Automate, Power BI, PowerShell, and more, see the [Supply Chain Management telemetry repository on GitHub](https://github.com/microsoft/d365-scm-telemetry).

## Set up alerts on telemetry events

You can configure the system to send you an alert message if something occurs in your environment or app that requires immediate action. Application Insights makes it easy to define these alerts. For more information and instructions, see [What are Azure Monitor Alerts](/azure/azure-monitor/alerts/alerts-overview).

## Pricing

Application Insights is billed based on the volume of telemetry data that your application sends (data ingestion) and the length of time that you want data to be available (data retention). For up-to-date information about pricing, see  [Azure Monitor pricing](https://azure.microsoft.com/pricing/details/monitor/).
