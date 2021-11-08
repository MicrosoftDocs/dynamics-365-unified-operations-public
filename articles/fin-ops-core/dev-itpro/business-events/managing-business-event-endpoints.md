---
# required metadata

title: Managing business event endpoints
description: This topic provides information on managing endpoints for Finance and Operations apps business events.
author: jaredha
ms.date: 11/08/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: jaredha
ms.search.validFrom: 2021-11-03
ms.dyn365.ops.version: 10.0.22
---

# Managing business event endpoints
[!include[banner](../includes/banner.md)]

## Overview
Endpoints let you manage the destinations to which business events are sent. Business events in Finance and Operations apps support the following endpoint types:

| Endpoint type | Tutorial |
| ------------- | -------- |
| Azure Service Bus Queue | [Business events and Azure Service Bus](how-to/how-to-servicebus-queue.md) |
| Azure Service Bus Topic | [Business events and Azure Service Bus](how-to/how-to-servicebus.md) |
| Azure Event Grid | [Business events and Azure Event Grid](how-to/how-to-eventgrid.md) |
| Azure Event Hub | [Business events and Azure Event Hubs](how-to/event-hub.md)  |
| Azure Blob Storage | Not applicable |
| HTTPS | Not applicable |
| Microsoft Power Automate | [Business events and Microsoft Power Automate](how-to/how-to-flow.md) |
| Dataverse | [Subscribing to events in Dataverse](how-to/how-to-dataverse-events.md) |

Endpoints can be created for these messsaging and event brokers out of the box. Some scenarios might require multiple endpoints for organized distribution of business events to consumers. You can create multiple endpoints to support these scenarios.

The Azure-based endpoints must be in the customer's Azure subscription. For example, if Event Grid is used as an endpoint, the endpoint must be in the customer's Azure subscription.

A Finance and Operations application doesn't provision the endpoints. The endpoints must be created separately and provided to the application. The application then sends events to the endpoints that are provided. Customers may incur additional costs if they use these endpoints in their Azure subscription.

## Subscribing to Finance and Operations events from Dataverse

> [!IMPORTANT]
> Enabling the Power Platform integration is prerequisite for subscribing to Finance and Operations business events and data events as outlined in this section. For more information on enabling the Power Platform integration for a Finance and Operations apps environment, see [Enabling the Power Platform integration](../power-platform/enable-power-platform-integration.md).

With the Power Platform integration enabled it is possible to subscribe to Finance and Operations business events and data events from Dataverse. This enables the following:

  - A consistent behavior across events from multiple applications in Dataverse.
  - Dataverse solution application lifecycle management (ALM) to consistently consume events from Finance and Operations apps.
  - Plug-ins and SDK steps to be registered on Finance and Operations apps events in Dataverse.

When the Power Platform integration is enabled for a Finance and Operations apps environment, endpoints created for business events are synchronized with the linked Power Platform environment for endpoint types that are supporteded in Dataverse, enabling the endpoint's use in the Power Platform. When the endpoints are synchronized, business events sent from Finance and Operations apps are proxied through Dataverse to the endpoint.

The following table provides the mapping between the Finance and Operations apps and Dataverse implementations of the endpoints.

| Finance and Operations apps endpoint type | Dataverse service endpoint type | 
| ----------------------------------------- | ------------------------------- |
| Azure Service Bus Queue                   | Azure Service Bus of type Queue | 
| Azure Service Bus Topic                   | Azure Service Bus of type Topic |
| Azure Event Grid                          | Azure Event Grid                |
| Azure Event Hub                           | Azure Event Hub                 |
| HTTPS                                     | Webhook                         |
| Azure Blob Storage                        | Not supported in Dataverse     |
| Microsoft Power Automate                  | Asynchronous callback registration |
| Dataverse                                 | Plug-in or SDK step registration |

> [!NOTE]
> For endpoint types that are not supported in Dataverse, or when the Power Platform integration is not enabled, the endpoint will continue to send the event from the Finance and Operations application rather than through Dataverse.

### Viewing or creating mapped endpoints in Dataverse

When a new endpoint is added in Finance and Operations, it is synchronized to Dataverse. It is then available for use in Dataverse in the **ServiceEndpoint** table. You can also create the endpoint directly in Dataverse in the **ServiceEndpoint** table. If the service endpoint is created subscribing to a Finance and Operations event, it will then automatically be made available to the Finance and Operations application and can be viewed on the **Endpoints** tab of the **Business events** page. This is applicable to the following mapped endpoint types:

- Azure Service Bus Queue
- Azure Service Bus Topic
- Azure Event Grid
- Azure Event Hub

See [ServiceEndpoint table/entity reference](/powerapps/developer/data-platform/reference/entities/serviceendpoint) for more information on the ServiceEndpoint table.

### Microsoft Power Automate endpoints

The **Microsoft Power Automate** endpoint type is not made available for setup directly in the Finance and Operations application. The endpoint type is used for subscriptions that are created and sent directly from a flow in Power Automate. 

The endpoint is created in the Finance and Operations application in the **Endpoints** tab of the **Business events** page when you subscribe to a Finance and Operations business event or data event in Power Automate. See [Business events in Microsoft Power Automate](business-events-flow.md) for more information on subscribing to business events and data events in Power Automate.

### Microsoft Dataverse endpoints

The **Dataverse** endpoint type is also not available for manual setup in the Finance and Operations application. The endpoint is created when a plug-in or an SDK step is registered on a Finance and Operations business event or data event in Dataverse. When the step is registered it becomes visible as an endpoint in the list on the **Endpoints** tab of the **Business events** page in the Finance and Operations application. 

![Business events Dataverse endpoint type in Finance and Operations](../media/businessevents_DataverseEndpoint.png)

The business event registration itself will also be listed in the **Business event catalog** or **Data event catalog** in the Finance and Operations application, depending on registration. This helps Finance and Operations apps users know which business event or data event has a plug-in or SDK step registered in Dataverse and the reason for the event being active in the Finance and Operations app.

Finance and Operations apps events can be subscribed to directly in Dataverse using the Dataverse tool set like the the **Power Platform Tools** extension for Visual Studio. See [Install Power Platform Tools](/powerapps/developer/data-platform/tools/devtools-install) for more information on the extension. These subscriptions will display in the **Business event catalog** in Finance and Operations apps.

Certain attributes of service endpoints in Dataverse, like name and description, can be updated. Such updates will reflect in Finance and Operations as well. However, updates that would change the service endpoint type, like changing from a service bus topic to a service bus queue, which Dataverse would normally allow, would be prevented if the service endpoint is used with Finance and Operations events. This is for design simplicity and consistency as Finance and Operations does not allow these updates to endpoints once created.

Once created, Dataverse does not allow deletion of service endpoints if it is being used. This is true, as well, for service endpoints used by Finance and Operations events. An attempt to delete the endpoint will result in an error, and deletion is prevented. 

For more information on subscribing to Finance and Operations business events in Dataverse, see [Subscribing to events in Dataverse](how-to/how-to-dataverse-events.md).
