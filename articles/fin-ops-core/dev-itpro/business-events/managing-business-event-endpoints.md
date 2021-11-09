---
# required metadata

title: Manage business event endpoints
description: This topic provides information about how to manage endpoints for Finance and Operations apps business events.
author: jaredha
ms.date: 11/09/2021
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

# Manage business event endpoints
[!include[banner](../includes/banner.md)]

Endpoints let you manage the destinations that business events are sent to. Business events in Finance and Operations apps support the following endpoint types.

| Endpoint type | Tutorial |
| ------------- | -------- |
| Azure Service Bus Queue | [Business events and Azure Service Bus](how-to/how-to-servicebus-queue.md) |
| Azure Service Bus Topic | [Business events and Azure Service Bus](how-to/how-to-servicebus.md) |
| Azure Event Grid | [Business events and Azure Event Grid](how-to/how-to-eventgrid.md) |
| Azure Event Hub | [Business events and Azure Event Hubs](how-to/event-hub.md) |
| Azure Blob Storage | Not applicable |
| HTTPS | Not applicable |
| Microsoft Power Automate | [Business events and Microsoft Power Automate](how-to/how-to-flow.md) |
| Dataverse | [Subscribe to events in Dataverse](how-to/how-to-dataverse-events.md) |

Endpoints can be created for these messaging and event brokers out of the box. Some scenarios might require multiple endpoints for organized distribution of business events to consumers. You can create multiple endpoints to support these scenarios.

The Microsoft Azure–based endpoints must be in the customer's Azure subscription. For example, if Event Grid is used as an endpoint, the endpoint must be in the customer's Azure subscription.

A Finance and Operations app doesn't provision the endpoints. The endpoints must be created separately and provided to the app. The app then sends events to the endpoints that are provided. Customers might incur additional costs if they use these endpoints in their Azure subscription.

## Subscribing to Finance and Operations apps events from Dataverse

> [!IMPORTANT]
> Before you subscribe to Finance and Operations apps business events and data events in Microsoft Dataverse, you must enable the Microsoft Power Platform integration. For information about how to enable the Microsoft Power Platform integration for a Finance and Operations apps environment, see [Enable the Microsoft Power Platform integration](../power-platform/enable-power-platform-integration.md).

After the Microsoft Power Platform integration is enabled, you can subscribe to Finance and Operations apps business events and data events from Dataverse. Subscription enables the following capabilities:

- Consistent behavior across events from multiple applications in Dataverse
- Application Lifecycle Management (ALM) for the Dataverse solution to consistently consume events from Finance and Operations apps
- Registration of plug-ins and software development kit (SDK) steps on Finance and Operations apps events in Dataverse

When the Microsoft Power Platform integration is enabled for a Finance and Operations apps environment, endpoints that are created for business events are synced with the linked Microsoft Power Platform environment for endpoint types that are supported in Dataverse. The endpoints can then be used in Microsoft Power Platform. When the endpoints are synced, business events that are sent from Finance and Operations apps are proxied through Dataverse to the endpoint.

The following table shows the mapping between the Finance and Operations apps and Dataverse implementations of the endpoints.

| Finance and Operations apps endpoint type | Dataverse service endpoint type    | 
| ----------------------------------------- | ---------------------------------- |
| Azure Service Bus Queue                   | Azure Service Bus of type Queue    | 
| Azure Service Bus Topic                   | Azure Service Bus of type Topic    |
| Azure Event Grid                          | Azure Event Grid                   |
| Azure Event Hub                           | Azure Event Hub                    |
| HTTPS                                     | Webhook                            |
| Azure Blob Storage                        | Not supported in Dataverse         |
| Microsoft Power Automate                  | Asynchronous callback registration |
| Dataverse                                 | Plug-in or SDK step registration   |

> [!NOTE]
> If an endpoint type isn't supported in Dataverse, or if the Microsoft Power Platform integration isn't enabled, the endpoint will continue to send the event from Finance and Operations apps instead of sending it through Dataverse.

### Viewing or creating mapped endpoints in Dataverse

When a new endpoint is added in Finance and Operations apps, it's synced to Dataverse. It's then available for use in Dataverse in the **ServiceEndpoint** table. You can also create the endpoint directly in Dataverse in the **ServiceEndpoint** table. If the service endpoint is created by subscribing to a Finance and Operations apps event, it will automatically be made available to Finance and Operations apps and can be viewed on the **Endpoints** tab of the **Business events** page. This behavior is applicable to the following mapped endpoint types:

- Azure Service Bus Queue
- Azure Service Bus Topic
- Azure Event Grid
- Azure Event Hub

For more information about the **ServiceEndpoint** table, see [ServiceEndpoint table/entity reference](/powerapps/developer/data-platform/reference/entities/serviceendpoint).

### Microsoft Power Automate endpoints

The **Microsoft Power Automate** endpoint type isn't made available for setup directly in Finance and Operations apps. This endpoint type is used for subscriptions that are created and sent directly from a flow in Power Automate. 

The endpoint is created on the **Endpoints** tab of the **Business events** page in Finance and Operations apps when you subscribe to a Finance and Operations apps business event or data event in Power Automate. For more information about how to subscribe to business events and data events in Power Automate, see [Business events in Microsoft Power Automate](business-events-flow.md).

### Microsoft Dataverse endpoints

The **Dataverse** endpoint type also isn't available for manual setup in Finance and Operations apps. The endpoint is created when a plug-in or an SDK step is registered on a Finance and Operations apps business event or data event in Dataverse. When the step is registered, it becomes visible as an endpoint in the list on the **Endpoints** tab of the **Business events** page in Finance and Operations apps. 

![Endpoint of the Dataverse type on the Business events page in a Finance and Operations app.](../media/businessevents_DataverseEndpoint.png)

The business event registration itself will also be listed on either the **Business event catalog** tab or the **Data event catalog** tab of the **Business events** page in Finance and Operations apps, depending on registration. In this way, Finance and Operations apps users can learn which business event or data event has a plug-in or SDK step registered in Dataverse. They can also learn the reason why the event is active in Finance and Operations apps.

Finance and Operations apps events can be subscribed to directly in Dataverse by using the tools in the Dataverse toolset, such as the Power Platform Tools extension for Visual Studio. For more information about this extension, see [Install Power Platform Tools](/powerapps/developer/data-platform/tools/devtools-install). These subscriptions will appear on the **Business event catalog** tab of the **Business events** page in Finance and Operations apps.

Some attributes of service endpoints in Dataverse, such as the name and description, can be updated. These updates will also be reflected in Finance and Operations apps. However, updates that change the service endpoint type will be prevented if the service endpoint is used with Finance and Operations apps events. These updates include a change from a Service Bus topic to a Service Bus queue, which Dataverse usually allows. This behavior helps ensure design simplicity and consistency, because Finance and Operations apps don't allow these updates to endpoints after they have been created.

After service endpoints are created, Dataverse doesn't allow them to be deleted if they are being used. This limitation also applies to service endpoints that are used by Finance and Operations apps events. Any attempt to delete one of these endpoints will cause an error, and deletion will be prevented. 

For more information about how to subscribe to Finance and Operations apps business events in Dataverse, see [Subscribe to events in Dataverse](how-to/how-to-dataverse-events.md).
