---
title: Monitor mobile device usage and performance
description: The Warehouse Management mobile app emits telemetry data, which lets you monitor and analyze the activities and general health of your devices. You can use the information to diagnose issues and analyze operations that affect performance.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/18/2022
audience: Application User
ms.custom: bap-template
---

# Monitor mobile device usage and performance

[!include [banner](../includes/banner.md)]

The Warehouse Management mobile app emits telemetry data, which lets you monitor and analyze the activity and general health of your mobile devices. You can use the information to diagnose issues and analyze operations that affect performance. Telemetry data is collected and processed by using [Application Insights](/azure/azure-monitor/app/app-insights-overview), a Microsoft Azure service that is optimized for this purpose.

## Prerequisites

Before you can collect and analyze telemetry data for your mobile devices, the following prerequisites must be in place for your system:

- **Supply Chain Management version** – You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.29 or later.
- **Application Insights** – You must have an Application Insights resource in Azure, and you must configure your Supply Chain Management environment to send telemetry data to it. For instructions, see [Enable warehousing telemetry with Application Insights](application-insights-warehousing.md).

## Available telemetry

In Application Insights, telemetry from the Warehouse Management mobile app is logged as custom events. The following table lists the data that is currently logged as custom dimensions on each event.

| Name | Description |
|---|---|
| `backendProcessingTime` | Information about the processing time of the request on the server. |
| `batteryLevel` | Information about the device's battery level. |
| `batterySession` | Information about the battery session of the device. If the device is charging, the telemetry logs it as such. Otherwise, a globally unique identifier (GUID) is logged that represents an on-battery session. Every time that the device charges, the GUID for the on-battery session is changed. |
| `batteryState` | Information about the charging status of the device. For more information, see [BatteryState Enum](/dotnet/api/xamarin.essentials.batterystate). |
| `deviceId` | The GUID of the device that performs the call. |
| `eventid` | A constant that identifies the telemetry that is emitted by the Warehouse Management mobile app. This information helps you distinguish mobile app data from other warehousing telemetry events that are emitted from Supply Chain Management. |
| `isEnergySaverTurnedOn` | Information about the energy saver status of the device. |
| `powerSource` | Information about the power source of the device. For more information, see [BatteryPowerSource Enum](/dotnet/api/xamarin.essentials.batterypowersource). |
| `renderingDurationInMilliseconds` | Information about the time that the  Warehouse Management mobile app takes to render page controls after it calls the server. |
| `roundTripLatencyDurationInMilliseconds` | Information about the total time of a server call, from the request to the response. |
| `serverAadTenantId` | The Azure Active Directory (Azure AD) tenant ID of the connected Supply Chain Management environment. |
| `serverEnvironmentId` | The environment ID of the connected Supply Chain Management environment. |

## View telemetry data in Application Insights

Telemetry is stored in Azure Monitor Logs in the *customEvents* table. You can view the collected data by writing log queries in the Kusto Query Language (KQL). For more information, see [Azure Monitor Logs overview](/azure/azure-monitor/logs/data-platform-logs) and [Log queries in Azure Monitor](/azure/azure-monitor/logs/log-query-overview).

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
