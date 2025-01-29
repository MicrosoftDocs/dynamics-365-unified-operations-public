---
title: Monitor Warehouse Management usage and performance
description: The Supply Chain Management tenant emit telemetry data, which lets you monitor and analyze the activities and general health of your system.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 09/14/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Monitor Warehouse Management usage and performance

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management emits telemetry data for various Warehouse Management activities and operations, including both the Supply Chain Management tenant and the Warehouse Management mobile app. Telemetry data helps provide insight into the activities and general health of your tenants and devices, so that you can diagnose problems and analyze operations that affect performance. Telemetry data is collected and processed by using [Application Insights](/azure/azure-monitor/app/app-insights-overview), an Azure service that's optimized for this purpose.

## Prerequisites

Before you can collect and analyze Warehouse Management telemetry data, the following prerequisites must be in place for your system:

- **Supply Chain Management version** – Telemetry with Application Insights requires Supply Chain Management version 10.0.29 or later. Additional telemetry features require later versions of Supply Chain Management. See the tables later in this article for details about which features require which versions of Supply Chain Management.
- **Warehouse Management mobile app version** – Telemetry with Application Insights requires Warehouse Management mobile app version 2.0.28 or later. Additional telemetry features require later versions of the app. See the tables later in this article for details about which features require which versions of Supply Chain Management and the Warehouse Management mobile app.
- **Application Insights** – You must have an Application Insights resource in Azure, and you must configure your Supply Chain Management environment to send telemetry data to it. For instructions, see [Enable warehousing telemetry with Application Insights](application-insights-warehousing.md).

## View telemetry data in Power BI

The fastest and easiest way to get started viewing your warehousing telemetry is to download and set up the Power BI reports provided by Microsoft. The downloadable reports and instructions for how to set them up are available in the [Supply Chain Management telemetry repository on GitHub](https://github.com/microsoft/d365-scm-telemetry/tree/main/samples/PowerBI/Appsource).

## Technical details of all available telemetry data

In Application Insights, telemetry data from Supply Chain Management tenants and the Warehouse Management mobile app are logged as custom events. Technical details of all custom events and all data that could be logged for each event are available in the Supply Chain Management telemetry repository on GitHub. This information can help you to design your own custom Power BI reports and to explore the data directly in Application Insights. The following sample query files list all of the available event IDs, field names, and version requirements:

- For Supply Chain Management tenant telemetry details, see the [WarehouseManagement.kql example query on GitHub](https://github.com/microsoft/d365-scm-telemetry/blob/main/samples/KQL/example_queries/WarehouseManagement.kql).
- For Warehouse Management mobile app telemetry details, see the [WarehouseMobileApp.kql example query on GitHub](https://github.com/microsoft/d365-scm-telemetry/blob/main/samples/KQL/example_queries/WarehouseMobileApp.kql).

## View telemetry data in Application Insights

As an alternative to Power BI, you can view your telemetry data directly in Application Insights. Telemetry is stored in Azure Monitor Logs in the `customEvents` table. You can view the collected data by writing log queries in the Kusto Query Language (KQL). Learn more in [Azure Monitor Logs overview](/azure/azure-monitor/logs/data-platform-logs) and [Log queries in Azure Monitor](/azure/azure-monitor/logs/log-query-overview).

As a simple example, follow these steps.

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
