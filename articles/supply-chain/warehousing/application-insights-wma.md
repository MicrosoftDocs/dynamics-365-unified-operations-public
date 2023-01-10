---
title: Monitor Warehouse Management usage and performance
description: The Supply Chain Management tenant and the Warehouse Management mobile app emit telemetry data, which lets you monitor and analyze the activities and general health of your system. You can use the information to diagnose issues and analyze operations that affect performance.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/10/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Monitor Warehouse Management usage and performance

[!include [banner](../includes/banner.md)]

Dynamics 365 Supply Chain Management emits telemetry data for various Warehouse Management activities and operations, including both the Supply Chain Management tenant and the Warehouse Management mobile app. Telemetry data helps provide you with insights into the activities and general health of your tenants and devices, enabling you to diagnose problems and analyze operations that affect performance. You can use the information to diagnose issues and analyze operations that affect performance. Telemetry data is collected and processed by using [Application Insights](/azure/azure-monitor/app/app-insights-overview), a Microsoft Azure service that is optimized for this purpose.

## Prerequisites

Before you can collect and analyze Warehouse Management telemetry data, the following prerequisites must be in place for your system:

- **Supply Chain Management version** – You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.29 or later. <!--KFM: Do we need a newer version to collet tenant telemetry? -->
- **Application Insights** – You must have an Application Insights resource in Azure, and you must configure your Supply Chain Management environment to send telemetry data to it. For instructions, see [Enable warehousing telemetry with Application Insights](application-insights-warehousing.md).

## Available telemetry for Supply Chain Management tenants

In Application Insights, telemetry from Supply Chain Management tenants is logged as custom events. The following table lists the events that are currently available.

| Event ID | Area | Name |
|---|---|---|
| WHS000001 | Location directives | Warehouse.LocationDirective.FindLocation |
| WHS000002 | Wave processing | Warehouse.WaveProcessing.PostWave |
| WHS000003 | Mobile application backend | Warehouse.MobileApp.NextPageRequest |
| WHS000004 | Mobile application backend | Warehouse.MobileApp.ImageRequest |
| WHS000005 | Work creation | Warehouse.WorkCreation.Log |
| WHS000007 | Wave processing | Warehouse.WaveProcessing.ShippingCreateWork |
| WHS000008 | Wave processing | Warehouse.WaveProcessing.CreateLoads |
| WHS000009 | Wave processing | Warehouse.WaveProcessing.ProcessWaveMethods |
| WHS000010 | Wave processing | Warehouse.WaveProcessing.ValidateWave |
| WHS000011 | Wave processing | Warehouse.WaveProcessing.AllocateWave |
| WHS000012 | Wave processing | Warehouse.WaveProcessing.Containerization |
| WHS000013 | Load posting | Warehouse.LoadPosting |
| WHS000014 | Wave processing | Warehouse.WaveDemandReplenishment |
| WHS000015 | Wave processing | Warehouse.WaveProcessing.KanbanCreateWork |
| WHS000016 | Wave processing | Warehouse.WaveProcessing.KanbanPickQuantity |
| WHS000017 | Wave processing | Warehouse.WaveProcessing.ProductionCreateWork |
| WHS000018 | Wave processing | Warehouse.WaveProcessing.ProductionPickQuantity |
| WHS000019 | Wave processing | Warehouse.WaveProcessing.Sorting |
| WHS000020 | Wave processing | Warehouse.WaveProcessing.WaveLabelPrinting |
| WHS000021 | Wave processing | Warehouse.CreateLoadFromShipment |
| WHS000022 | Work creation | Warehouse.ProcessTemporaryWorkLine |
| WHS000023 | Work creation | Warehouse.CreateRemainingWorkLines |
| WHS000024 | Wave processing | Warehouse.AllocateLoadLine |
| WHS000025 | Replenishment | Warehouse.RunDemandReplenishment |
| WHS000026 | Replenishment | Warehouse.ImmediateReplenishment |
| WHS000027 | Release to warehouse | Warehouse.WarehouseRelease.CreateShipments |

The following table lists the telemetry data that is logged as custom dimensions (not all of this data is logged for all events).

| Name | Description |
|---|---|
| `aadTenantId` | Azure AD Tenant ID of the connected Supply Chain Management environment. |
| `activityId` | Activity ID for the session during which the event was logged. |
| `activityGraph` | A graph that represents the level of the telemetry event based on the business process that was done. |
| `allocatedLoadLines` | Number of load lines that were allocated during wave processing. |
| `elapsedMilliseconds` | Duration (in milliseconds) measuring how long the event took from start to stop. |
| `environmentId` | Environment ID of the connected Supply Chain Management environment. |
| `eventId` | A constant that uniquely identifies the event. |
| `eventStatus` | Status of the event (can have a value of "start" or "stop"). |
| `foundInventoryQuantity` | Quantity (in inventory units) that was found at a location during the allocation process. |
| `foundLocationId` | Location ID of the location where the inventory was found during the allocation process. |
| `foundQuantity` | Quantity (in the unit specified by the `foundUnitOfMeasure` dimension) that was found at a location during the allocation process. |
| `foundUnitOfMeasure` | Unit of measure the `foundQuantity` dimension. |
| `immediateReplenishmentQuantity` | Requested quantity (in the unit specified by the `immediateReplenishmentUnitOfMeasure` dimension) that is used during immediate replenishment. |
| `immediateReplenishmentTemplateId` | Replenishment template ID used for the immediate replenishment. |
| `immediateReplenishmentUnitOfMeasure` | Unit of measure the `immediateReplenishmentQuantity` dimension. |
| `itemId` | Item ID that was processed. |
| `itemRecordId` | Item record ID that was processed. |
| `loadConsolidated` | Indicates whether a load was consolidated when it was created from shipment during wave processing. |
| `loadPostMethodName` | Name of the load posting method that was processed. |
| `loadId` | Load ID that was processed. |
| `locationsEvaluated` | Number of locations that were evaluated by the location directives. |
| `mobileDeviceId` | GUID of the device from which the Warehouse Management mobile app performed a call to the Supply Chain Management environment. |
| `mobileDeviceRequestActivityId` | GUID of the server request activity performed by the Warehouse Management mobile app. |
| `mobileDeviceRequestImageDetails` | Identifies an image requested by the Warehouse Management mobile app. |
| `mobileDeviceRequestImageIsThumbnail` | Indicates whether an image requested by the Warehouse mobile app was a thumbnail or not. |
| `orderNumber` | Source document order number (such as a sales order number, purchase order number, and so on). |
| `releaseToWarehouseId` | Release to warehouse ID used for processing a wave. |
| `replenishmentTemplateId` | Replenishment template ID used during replenishment. |
| `requestedInventoryQuantity` | Quantity (in inventory units) that was requested when finding a location while processing a location directive. |
| `shipmentId` | Shipment ID that was processed. |
| `shipmentsCreated` | Number of shipments created during processing. |
| `validateWaveSuccess` | Result of the wave validation (can have a value of "true" or "false"). |
| `warehouseId` | Warehouse ID of the warehouse where the process was done. |
| `waveId` | Wave ID that was processed. |
| `waveMethodsProcessed` | Number of wave processing methods that had been processed so far. |
| `waveStepCode` | Wave step code from wave processing method (for example, replenishment). |
| `waveProcessingId` | Wave processing ID. |
| `workCompleted` | Result of the work creation. Currently used to indicate that kanban work was fully created. Can have a value of "true" or "false". |
| `workCreationLogFailed` | Indicates whether work creation failed (can have a value of "true" or "false"). |
| `workCreationLogMessage` | Message logged during a processes (such as work creation or wave allocation). |
| `workCreationLogTransactionTime` | Timestamp for when the work creation log was created. |
| `workCreationNumber` | Work creation number used for the work creation process. |
| `WorkExecuteMode` | Work processing mode for the Warehouse Management mobile device app flow. |
| `WorkExecuteStep` | Work processing step for the Warehouse Management mobile device app flow. |
| `WorkId` | Work ID that was processed. |
| `workOrderType` | Work order type that was processed. |
| `worksCreated` | Number of work records that were created during the work creation process. |
| `workTemplateCode` | Work template code used in the work creation process. |
| `workType` | The work type for the work line used during the work creation process (for example, "pick" or "put"). |

## Available telemetry for the Warehouse Management mobile app

In Application Insights, telemetry from the Warehouse Management mobile app is logged as custom events on each server call. The following table lists the events that are currently available.

| Event ID | Area | Name |
|---|---|---|
| WHS000006 | Mobile application frontend | Warehouse.MobileApp.ClientRoundTrip |

The following table lists the telemetry data that is logged as custom dimensions on each event.

| Name | Description |
|---|---|
| `activityId` | GUID of the server request activity ID. |
| `activityGraph` | A constant that provides information about the place of the call in the activity hierarchy. Will always log the value "Warehouse.MobileApp.Interaction". |
| `backendProcessingTime` | Information about the processing time of the request on the server. |
| `batteryLevel` | Information about the device's battery level. |
| `batterySession` | Information about the battery session of the device. If the device is charging, the telemetry logs it as such. Otherwise, a globally unique identifier (GUID) is logged that represents an on-battery session. Every time that the device charges, the GUID for the on-battery session is changed. |
| `batteryState` | Information about the charging status of the device. For more information, see [BatteryState Enum](/dotnet/api/xamarin.essentials.batterystate). |
| `deviceId` | GUID of the device that performs the call. |
| `eventid` | A constant that identifies the telemetry that is emitted by the Warehouse Management mobile app. This information helps you distinguish mobile app data from other warehousing telemetry events that are emitted from Supply Chain Management. |
| `isEnergySaverTurnedOn` | Information about the energy saver status of the device. |
| `powerSource` | Information about the power source of the device. For more information, see [BatteryPowerSource Enum](/dotnet/api/xamarin.essentials.batterypowersource). |
| `renderingDurationInMilliseconds` | Information about the time that the Warehouse Management mobile app takes to render page controls after it calls the server. |
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
