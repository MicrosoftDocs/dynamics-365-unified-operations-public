---
title: Monitor mobile device usage and performance
description: The Warehouse Management mobile app emits telemetry data, which lets you monitor and analyze the activities and general health of your devices. You can use this information to diagnose problems and analyze operations that affect performance.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/18/2022
ms.custom: bap-template
---

# Monitor mobile device usage and performance

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The Warehouse Management mobile app emits telemetry data, which lets you monitor and analyze the activity and general health of your mobile devices. You can use this information to diagnose problems and analyze operations that affect performance. Telemetry data is collected and processed using [Application Insights](/azure/azure-monitor/app/app-insights-overview), which is an Azure service optimized for this purpose.

## Prerequisites

To use Warehouse Management mobile app, the following prerequisites must be in place for your system:

- **Supply Chain Management version** – You must be running Supply Chain Management version 10.0.29 or higher.
- **Application Insights** – you must have an Application Insights resource in Azure and configure your Supply Chain Management environment to send telemetry data to it. For instructions, see [Enable warehousing telemetry with Application Insights](application-insights-warehousing.md).

## Available telemetry

In Application Insights, telemetry from the Warehouse Management mobile app is logged as custom events. The following table lists the data that is currently logged as custom dimensions on each event.

| Name | Description |
|---|---|
| `backendProcessingTime` | Provides information about the processing time of the request on the server. |
| `batteryLevel` | Provides information about the device's battery level. |
| `batterySession` | Provides information about the battery session of the device. </br></br>If the device is charging, the telemetry logs it as such. Otherwise, a GUID is logged that represents an on-battery session. Every time the device charges, the on-battery session GUID is changed. |
| `batteryState` | Provides information about the charging status of the device.</br></br>For more information, see [BatteryState Enum](/dotnet/api/xamarin.essentials.batterystate). |
| `deviceId` | The GUID of the device that performs the call. |
| `eventid` | A constant that identifies the telemetry emitted by the Warehouse Management mobile app. This information helps you tell mobile-app data apart from other warehousing telemetry events emitted from Supply Chain Management. |
| `isEnergySaverTurnedOn` | Provides information about the energy saver status of the device. |
| `powerSource` | Provides information about the power source of the device.</br></br>For more information, see [BatteryPowerSource Enum](/dotnet/api/xamarin.essentials.batterypowersource). |
| `renderingDurationInMilliseconds` | Provides information about the time the mobile app takes to render page controls after calling the server. |
| `roundTripLatencyDurationInMilliseconds` | Provides information about the total time of a server call, from the request to the response. |
| `serverAadTenantId` | Provides the Azure AD Tenant ID of the connected Supply Chain Management environment. |
| `serverEnvironmentId` | Provides the environment ID of the connected Supply Chain Management environment. |

## View telemetry data in Application Insights

Telemetry is stored in Azure Monitor Logs in the *customEvents* table. You can view the collected data by writing log queries using the Kusto Query Language (KQL). For more information, see [Azure Monitor Logs overview](/azure/azure-monitor/logs/data-platform-logs) and [Log queries in Azure Monitor](/azure/azure-monitor/logs/log-query-overview).

As a simple example, follow these steps:

1. In the Azure portal, open your Application Insights resource.
1. From the **Monitoring** menu, select **Logs**.
1. On the **New Query** tab, type the following code to view the last 100 customEvents:

    ```plaintext
    kql
    customEvents
    \| take 100
    \| sort by timestamp desc
    ```

## Set up alerts on telemetry events

You can configure the system to send you an alert message if something happens in your environment or app that requires immediate action. Azure Application Insights makes it easy to define such alerts. For more information and instructions, see [What are Azure Monitor Alerts](/azure/azure-monitor/alerts/alerts-overview).

## Pricing

Azure Application Insights is billed based on the volume of telemetry data your application sends (data ingestion) and how long time you want data to be available (data retention). For up-to-date information on pricing, see  [Azure Monitor pricing](https://azure.microsoft.com/pricing/details/monitor/).
