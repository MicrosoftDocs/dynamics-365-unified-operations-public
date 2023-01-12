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

- **Supply Chain Management version** – Telemetry with Application Insights requires Supply Chain Management version 10.0.29 or higher. Additional telemetry features require later versions of Supply Chain Management. See the various tables in this article for details on which features require which versions of Supply Chain Management.
- **Warehouse Management mobile app version** – Telemetry with Application Insights requires Warehouse Management mobile app version XXXX or higher. <!-- KFM: Get version number -->
- **Application Insights** – You must have an Application Insights resource in Azure, and you must configure your Supply Chain Management environment to send telemetry data to it. For instructions, see [Enable warehousing telemetry with Application Insights](application-insights-warehousing.md).

## Available telemetry for Supply Chain Management tenants

In Application Insights, telemetry from Supply Chain Management tenants is logged as custom events. The following table lists the events that are currently available.

| Event ID | Area | Name | Supply Chain Management version |
|---|---|---|---|
| WHS000001 | Location directives | Warehouse.LocationDirective.FindLocation | 10.0.31 |
| WHS000002 | Wave processing | Warehouse.WaveProcessing.PostWave | 10.0.31 |
| WHS000003 | Mobile application backend | Warehouse.MobileApp.NextPageRequest | 10.0.31 |
| WHS000004 | Mobile application backend | Warehouse.MobileApp.ImageRequest | 10.0.31 |
| WHS000005 | Work creation | Warehouse.WorkCreation.Log | 10.0.31 |
| WHS000007 | Wave processing | Warehouse.WaveProcessing.ShippingCreateWork | 10.0.32 |
| WHS000008 | Wave processing | Warehouse.WaveProcessing.CreateLoads | 10.0.32 |
| WHS000009 | Wave processing | Warehouse.WaveProcessing.ProcessWaveMethods | 10.0.32 |
| WHS000010 | Wave processing | Warehouse.WaveProcessing.ValidateWave | 10.0.32 |
| WHS000011 | Wave processing | Warehouse.WaveProcessing.AllocateWave | 10.0.32 |
| WHS000012 | Wave processing | Warehouse.WaveProcessing.Containerization | 10.0.32 |
| WHS000013 | Load posting | Warehouse.LoadPosting | 10.0.32 |
| WHS000014 | Wave processing | Warehouse.WaveDemandReplenishment | 10.0.32 |
| WHS000015 | Wave processing | Warehouse.WaveProcessing.KanbanCreateWork | 10.0.32 |
| WHS000016 | Wave processing | Warehouse.WaveProcessing.KanbanPickQuantity | 10.0.32 |
| WHS000017 | Wave processing | Warehouse.WaveProcessing.ProductionCreateWork | 10.0.32 |
| WHS000018 | Wave processing | Warehouse.WaveProcessing.ProductionPickQuantity | 10.0.32 |
| WHS000019 | Wave processing | Warehouse.WaveProcessing.Sorting | 10.0.32 |
| WHS000020 | Wave processing | Warehouse.WaveProcessing.WaveLabelPrinting | 10.0.32 |
| WHS000021 | Wave processing | Warehouse.CreateLoadFromShipment | 10.0.32 |
| WHS000022 | Work creation | Warehouse.ProcessTemporaryWorkLine | 10.0.32 |
| WHS000023 | Work creation | Warehouse.CreateRemainingWorkLines | 10.0.32 |
| WHS000024 | Wave processing | Warehouse.AllocateLoadLine | 10.0.32 |
| WHS000025 | Replenishment | Warehouse.RunDemandReplenishment | 10.0.32 |
| WHS000026 | Replenishment | Warehouse.ImmediateReplenishment | 10.0.32 |
| WHS000027 | Release to warehouse | Warehouse.WarehouseRelease.CreateShipments | 10.0.32 |

The following table lists the telemetry data that is logged as custom dimensions (not all of this data is logged for all events).

| Name | Description | Supply Chain Management version |
|---|---|---|
| `aadTenantId` | Azure AD Tenant ID of the connected Supply Chain Management environment. | 10.0.31 |
| `activityId` | Activity ID for the session during which the event was logged. | 10.0.31 |
| `activityGraph` | A graph that represents the level of the telemetry event based on the business process that was done. | 10.0.31 |
| `allocatedLoadLines` | Number of load lines that were allocated during wave processing. | 10.0.32 |
| `elapsedMilliseconds` | Duration (in milliseconds) measuring how long the event took from start to stop. | 10.0.31 |
| `environmentId` | Environment ID of the connected Supply Chain Management environment. | 10.0.31 |
| `eventId` | A constant that uniquely identifies the event. | 10.0.31 |
| `eventStatus` | Status of the event (can have a value of "start" or "stop"). | 10.0.31 |
| `foundInventoryQuantity` | Quantity (in inventory units) that was found at a location during the allocation process. | 10.0.31 |
| `foundLocationId` | Location ID of the location where the inventory was found during the allocation process. | 10.0.31 |
| `foundQuantity` | Quantity (in the unit specified by the `foundUnitOfMeasure` dimension) that was found at a location during the allocation process. | 10.0.31 |
| `foundUnitOfMeasure` | Unit of measure the `foundQuantity` dimension. | 10.0.31 |
| `immediateReplenishmentQuantity` | Requested quantity (in the unit specified by the `immediateReplenishmentUnitOfMeasure` dimension) that is used during immediate replenishment. | 10.0.32 |
| `immediateReplenishmentTemplateId` | Replenishment template ID used for the immediate replenishment. | 10.0.32 |
| `immediateReplenishmentUnitOfMeasure` | Unit of measure the `immediateReplenishmentQuantity` dimension. | 10.0.32 |
| `itemId` | Item ID that was processed. | 10.0.31 |
| `itemRecordId` | Item record ID that was processed. | 10.0.31 |
| `loadConsolidated` | Indicates whether a load was consolidated when it was created from shipment during wave processing. | 10.0.32 |
| `loadPostMethodName` | Name of the load posting method that was processed. | 10.0.32 |
| `loadId` | Load ID that was processed. | 10.0.31 |
| `locationsEvaluated` | Number of locations that were evaluated by the location directives. | 10.0.31 |
| `mobileDeviceId` | GUID of the device from which the Warehouse Management mobile app performed a call to the Supply Chain Management environment. | 10.0.31 |
| `mobileDeviceRequestActivityId` | GUID of the server request activity performed by the Warehouse Management mobile app. | 10.0.31 |
| `mobileDeviceRequestImageDetails` | Identifies an image requested by the Warehouse Management mobile app. | 10.0.31 |
| `mobileDeviceRequestImageIsThumbnail` | Indicates whether an image requested by the Warehouse mobile app was a thumbnail or not. | 10.0.31 |
| `orderNumber` | Source document order number (such as a sales order number, purchase order number, and so on). | 10.0.31 |
| `releaseToWarehouseId` | Release to warehouse ID used for processing a wave. | 10.0.32 |
| `replenishmentTemplateId` | Replenishment template ID used during replenishment. | 10.0.32 |
| `requestedInventoryQuantity` | Quantity (in inventory units) that was requested when finding a location while processing a location directive. | 10.0.31 |
| `shipmentId` | Shipment ID that was processed. | 10.0.31 |
| `shipmentsCreated` | Number of shipments created during processing. | 10.0.32 |
| `validateWaveSuccess` | Result of the wave validation (can have a value of "true" or "false"). | 10.0.32 |
| `warehouseId` | Warehouse ID of the warehouse where the process was done. | 10.0.32 |
| `waveId` | Wave ID that was processed. | 10.0.31 |
| `waveMethodsProcessed` | Number of wave processing methods that had been processed so far. | 10.0.32 |
| `waveStepCode` | Wave step code from wave processing method (for example, replenishment). | 10.0.32 |
| `waveProcessingId` | Wave processing ID. | 10.0.31 |
| `workCompleted` | Result of the work creation. Currently used to indicate that kanban work was fully created. Can have a value of "true" or "false". | 10.0.32 |
| `workCreationLogFailed` | Indicates whether work creation failed (can have a value of "true" or "false"). | 10.0.31 |
| `workCreationLogMessage` | Message logged during a processes (such as work creation or wave allocation). | 10.0.31 |
| `workCreationLogTransactionTime` | Timestamp for when the work creation log was created. | 10.0.31 |
| `workCreationNumber` | Work creation number used for the work creation process. | 10.0.31 |
| `WorkExecuteMode` | Work processing mode for the Warehouse Management mobile device app flow. | 10.0.31 |
| `WorkExecuteStep` | Work processing step for the Warehouse Management mobile device app flow. | 10.0.31 |
| `WorkId` | Work ID that was processed. | 10.0.32 |
| `workOrderType` | Work order type that was processed. | 10.0.31 |
| `worksCreated` | Number of work records that were created during the work creation process. | 10.0.32 |
| `workTemplateCode` | Work template code used in the work creation process. | 10.0.32 |
| `workType` | The work type for the work line used during the work creation process (for example, "pick" or "put"). | 10.0.31 |

## Available telemetry for the Warehouse Management mobile app

In Application Insights, telemetry from the Warehouse Management mobile app is logged as custom events on each server call. The following table lists the events that are currently available.

| Event ID | Area | Name | Supply Chain Management version |
|---|---|---|---|
| WHS000006 | Mobile application frontend | Warehouse.MobileApp.ClientRoundTrip | 10.0.29 |

The following table lists the telemetry data that is logged as custom dimensions on each event.

| Name | Description | Supply Chain Management version |
|---|---|---|
| `activityId` | GUID of the server request activity ID. | 10.0.29 |
| `activityGraph` | A constant that provides information about the place of the call in the activity hierarchy. Will always log the value "Warehouse.MobileApp.Interaction". | 10.0.29 |
| `backendProcessingTime` | Information about the processing time of the request on the server. | 10.0.29 |
| `batteryLevel` | Information about the device's battery level. | 10.0.29 |
| `batterySession` | Information about the battery session of the device. If the device is charging, the telemetry logs it as such. Otherwise, a globally unique identifier (GUID) is logged that represents an on-battery session. Every time that the device charges, the GUID for the on-battery session is changed. | 10.0.29 |
| `batteryState` | Information about the charging status of the device. For more information, see [BatteryState Enum](/dotnet/api/xamarin.essentials.batterystate). | 10.0.29 |
| `deviceId` | GUID of the device that performs the call. | 10.0.29 |
| `eventid` | A constant that identifies the telemetry that is emitted by the Warehouse Management mobile app. This information helps you distinguish mobile app data from other warehousing telemetry events that are emitted from Supply Chain Management. | 10.0.29 |
| `isEnergySaverTurnedOn` | Information about the energy saver status of the device. | 10.0.29 |
| `powerSource` | Information about the power source of the device. For more information, see [BatteryPowerSource Enum](/dotnet/api/xamarin.essentials.batterypowersource). | 10.0.29 |
| `renderingDurationInMilliseconds` | Information about the time that the Warehouse Management mobile app takes to render page controls after it calls the server. | 10.0.29 |
| `roundTripLatencyDurationInMilliseconds` | Information about the total time of a server call, from the request to the response. | 10.0.29 |
| `serverAadTenantId` | The Azure Active Directory (Azure AD) tenant ID of the connected Supply Chain Management environment. | 10.0.29 |
| `serverEnvironmentId` | The environment ID of the connected Supply Chain Management environment. | 10.0.29 |

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
