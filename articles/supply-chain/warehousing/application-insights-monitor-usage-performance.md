---
title: Monitor Warehouse Management usage and performance
description: The Supply Chain Management tenant and the Warehouse Management mobile app emit telemetry data, which lets you monitor and analyze the activities and general health of your system. You can use the information to diagnose issues and analyze operations that affect performance.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/30/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Monitor Warehouse Management usage and performance

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management emits telemetry data for various Warehouse Management activities and operations, including both the Supply Chain Management tenant and the Warehouse Management mobile app. Telemetry data helps provide insight into the activities and general health of your tenants and devices, so that you can diagnose problems and analyze operations that affect performance. Telemetry data is collected and processed by using [Application Insights](/azure/azure-monitor/app/app-insights-overview), an Azure service that's optimized for this purpose.

## Prerequisites

Before you can collect and analyze Warehouse Management telemetry data, the following prerequisites must be in place for your system:

- **Supply Chain Management version** – Telemetry with Application Insights requires Supply Chain Management version 10.0.29 or later. Additional telemetry features require later versions of Supply Chain Management. See the tables later in this article for details about which features require which versions of Supply Chain Management.
- **Warehouse Management mobile app version** – Telemetry with Application Insights requires Warehouse Management mobile app version 2.0.28 or later. Additional telemetry features require later versions of the app. See the tables later in this article for details about which features require which versions of Supply Chain Management and the Warehouse Management mobile app.
- **Application Insights** – You must have an Application Insights resource in Azure, and you must configure your Supply Chain Management environment to send telemetry data to it. For instructions, see [Enable warehousing telemetry with Application Insights](application-insights-warehousing.md).

## Available telemetry for Supply Chain Management tenants

In Application Insights, telemetry from Supply Chain Management tenants is logged as custom events. The following table lists the events that are currently available. It also shows the minimum version of Supply Chain Management that's required to generate each event.

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
| WHS000028 | Wave creation | Warehouse.WaveCreated | 10.0.33 |
| WHS000029 | Wave creation | Warehouse.WaveStatusChanged | 10.0.33 |

The following table lists the telemetry data that's logged as custom dimensions. (Not all this data is logged for all events.) The table also shows the minimum version of Supply Chain Management that's required to log each dimension.

| Name | Description | Supply Chain Management version |
|---|---|---|
| `aadTenantId` | The Azure Active Directory (Azure AD) tenant ID of the connected Supply Chain Management environment. | 10.0.31 |
| `activityId` | The activity ID of the session that the event was logged during. | 10.0.31 |
| `activityGraph` | A chart that represents the level of the telemetry event, based on the business process that was done. | 10.0.31 |
| `allocatedLoadLines` | The number of load lines that were allocated during wave processing. | 10.0.32 |
| `elapsedMilliseconds` | The amount of time (in milliseconds) that the event took from start to stop. | 10.0.31 |
| `environmentId` | The environment ID of the connected Supply Chain Management environment. | 10.0.31 |
| `eventId` | A constant that uniquely identifies the event. | 10.0.31 |
| `eventStatus` | The status of the event. The value can be "start" or "stop". | 10.0.31 |
| `foundInventoryQuantity` | The quantity (in inventory units) that was found at a location during the allocation process. | 10.0.31 |
| `foundLocationId` | The location ID of the location where the inventory was found during the allocation process. | 10.0.31 |
| `foundQuantity` | The quantity that was found at a location during the allocation process. The value is expressed in the unit that's specified by the `foundUnitOfMeasure` dimension. | 10.0.31 |
| `foundUnitOfMeasure` | The unit of measure of the `foundQuantity` dimension. | 10.0.31 |
| `immediateReplenishmentQuantity` | The requested quantity that was used during immediate replenishment. The value is expressed in the unit that's specified by the `immediateReplenishmentUnitOfMeasure` dimension. | 10.0.32 |
| `immediateReplenishmentTemplateId` | The ID of the replenishment template that was used for the immediate replenishment. | 10.0.32 |
| `immediateReplenishmentUnitOfMeasure` | The unit of measure of the `immediateReplenishmentQuantity` dimension. | 10.0.32 |
| `itemId` | The item ID that was processed. | 10.0.31 |
| `itemRecordId` | The item record ID that was processed. | 10.0.31 |
| `loadConsolidated` | A value that indicates whether a load was consolidated when it was created from a shipment during wave processing. | 10.0.32 |
| `loadPostMethodName` | The name of the load posting method that was processed. | 10.0.32 |
| `loadId` | The load ID that was processed. | 10.0.31 |
| `locationsEvaluated` | The number of locations that were evaluated by the location directives. | 10.0.31 |
| `mobileDeviceId` | The globally unique identifier (GUID) of the device from which the Warehouse Management mobile app performed a call to the Supply Chain Management environment. | 10.0.31 |
| `mobileDeviceRequestActivityId` | The GUID of the server request activity that was performed by the Warehouse Management mobile app. | 10.0.31 |
| `mobileDeviceRequestImageDetails` | A value that identifies an image that was requested by the Warehouse Management mobile app. | 10.0.31 |
| `mobileDeviceRequestImageIsThumbnail` | A value that indicates whether an image that was requested by the Warehouse mobile app was a thumbnail. | 10.0.31 |
| `orderNumber` | The source document order number (such as a sales order number or purchase order number). | 10.0.31 |
| `releaseToWarehouseId` | The release to warehouse ID that was used to process a wave. | 10.0.32 |
| `replenishmentTemplateId` | The replenishment template ID that was used during replenishment. | 10.0.32 |
| `requestedInventoryQuantity` | The quantity (in inventory units) that was requested when a location was being found during processing of a location directive. | 10.0.31 |
| `shipmentId` | The shipment ID that was processed. | 10.0.31 |
| `shipmentsCreated` | The number of shipments that were created during processing. | 10.0.32 |
| `validateWaveSuccess` | The result of the wave validation. The value can be "true" or "false". | 10.0.32 |
| `warehouseId` | The warehouse ID of the warehouse where the processing was done. | 10.0.32 |
| `waveId` | The wave ID that was processed. | 10.0.31 |
| `waveMethodsProcessed` | The number of wave processing methods that had been processed so far. | 10.0.32 |
| `waveStepCode` | The wave step code from the wave processing method (for example, replenishment). | 10.0.32 |
| `waveProcessingId` | The wave processing ID. | 10.0.31 |
| `workCompleted` | The result of the work creation. This dimension is currently used to indicate that kanban work was fully created. The value can be "true" or "false". | 10.0.32 |
| `workCreationLogFailed` | A value that indicates whether work creation failed. The value can be "true" or "false". | 10.0.31 |
| `workCreationLogMessage` | The message that was logged during a process (such as work creation or wave allocation). | 10.0.31 |
| `workCreationLogTransactionTime` | A timestamp that indicates when the work creation log was created. | 10.0.31 |
| `workCreationNumber` | The work creation number that was used for the work creation process. | 10.0.31 |
| `WaveStatusCurrent` | The status of the current wave. | 10.0.33 |
| `waveStatusPrevious` | The status of the previous wave. | 10.0.33 |
| `WorkExecuteMode` | The work processing mode for the Warehouse Management mobile device app flow. | 10.0.31 |
| `WorkExecuteStep` | The work processing step for the Warehouse Management mobile device app flow. | 10.0.31 |
| `WorkId` | The work ID that was processed. | 10.0.32 |
| `workOrderType` | The work order type that was processed. | 10.0.31 |
| `worksCreated` | The number of work records that were created during the work creation process. | 10.0.32 |
| `workTemplateCode` | The work template code that was used in the work creation process. | 10.0.32 |
| `workType` | The work type of the work line that was used during the work creation process (for example, "pick" or "put"). | 10.0.31 |

## Available telemetry for the Warehouse Management mobile app

In Application Insights, telemetry from the Warehouse Management mobile app is logged as custom events on each server call. The following table lists the events that are currently available. It also shows the minimum versions of Supply Chain Management and the Warehouse Management mobile app required to generate each event.

| Event ID | Area | Name | Supply Chain Management version | Mobile app version |
|---|---|---|---|---|
| WHS000006 | Mobile application frontend | Warehouse.MobileApp.ClientRoundTrip | 10.0.29 | 2.0.28 |
| WHS000030 | Mobile application frontend | Warehouse.MobileApp.FailedServerInvoke | 10.0.29 | 2.1.14 |
| WHS000031 | Mobile application frontend | Warehouse.MobileApp.ServiceInvokeException | 10.0.29 | 2.1.14 |


The following table lists the telemetry data that's logged as custom dimensions on each event. (Not all this data is logged for all events.) It also shows the minimum versions of Supply Chain Management and the Warehouse Management mobile app that are required to generate each dimension.

| Name | Description | Supply Chain Management version | Mobile app version |
|---|---|---|---|
| `activityId` | The GUID of the server request activity ID. | 10.0.29 | 2.0.35 |
| `activityGraph` | A constant that provides information about the place of the call in the activity hierarchy. The value "Warehouse.MobileApp.Interaction" will always be logged. | 10.0.29 | 2.0.35 |
| `appVersion` | The version of the app that performs the call. | 10.0.33 | 2.0.43 |
| `backendProcessingTime` | Information about the processing time of the request on the server. | 10.0.29 | 2.0.28 |
| `batteryLevel` | Information about the device's battery level. | 10.0.29 | 2.0.28 |
| `batterySession` | Information about the battery session of the device. If the device is charging, the telemetry logs it as such. Otherwise, it logs a GUID that represents an on-battery session. Every time that the device charges, the GUID for the on-battery session is changed. | 10.0.29 | 2.0.28 |
| `batteryState` | Information about the charging status of the device. For more information, see [BatteryState Enum](/dotnet/api/xamarin.essentials.batterystate). | 10.0.29 | 2.0.28 |
| `deviceId` | The GUID of the device that performs the call. | 10.0.29 | 2.0.28 |
| `deviceBrand` | The brand of the device that performs the call. | 10.0.33 | 2.0.43 |
| `deviceModel` | The model of the device that performs the call. | 10.0.33 | 2.0.43 |
| `devicePlatform` | The computing platform of the device that performs the call. | 10.0.33 | 2.0.43 |
| `eventid` | A constant that identifies the telemetry that's emitted by the Warehouse Management mobile app. This information helps you distinguish mobile app data from other warehousing telemetry events that are emitted from Supply Chain Management. | 10.0.29 | 2.0.33 |
| `isEnergySaverTurnedOn` | Information about the energy saver status of the device. | 10.0.29 | 2.0.28 |
| `powerSource` | Information about the power source of the device. For more information, see [BatteryPowerSource Enum](/dotnet/api/xamarin.essentials.batterypowersource). | 10.0.29 | 2.0.28 |
| `renderingDurationInMilliseconds` | Information about the time that the Warehouse Management mobile app takes to render page controls after it calls the server. | 10.0.29 | 2.0.28 |
| `roundTripLatencyDurationInMilliseconds` | Information about the total time of a server call, from the request to the response. | 10.0.29 | 2.0.28 |
| `serverAadTenantId` | The Azure AD tenant ID of the connected Supply Chain Management environment. | 10.0.29 | 2.0.33 |
| `serverEnvironmentId` | The environment ID of the connected Supply Chain Management environment. | 10.0.29 | 2.0.33 |
| `lastKnownWMSLocation` | The last WMSLocation captured in the mobile app flows. | 10.0.29 | 2.1.14 |
| `requestNextPageTimeInMilliseconds` | Information about the total time taken to request the neext page from the server.  | 10.0.29 | 2.1.14 |
| `serverInvokeErrorMessage` | Contains the exception message when a generic exception is thrown.  | 10.0.29 | 2.1.14 |
| `serviceInvokeExceptionCategory` | Contains information about the type of an exception thrown by the server.  | 10.0.29 | 2.1.14 |
| `numberOfRetries` | The number of times the mobile app tried to request the next page after an exception occured.  | 10.0.29 | 2.1.14 |
| `connectionType` | The number of times the mobile app tried to request the next page after an exception occured.  | 10.0.29 | 2.1.14 |


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
