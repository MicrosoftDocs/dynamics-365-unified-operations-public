---
title: Manage business event endpoints
description: Learn about how to manage endpoints for finance and operations apps business events, including a table that provides tutorials for various endpoint types.
author: jaredha
ms.author: riverma
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/11/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-11-03
ms.dyn365.ops.version: 10.0.22
---

# Manage business event endpoints

[!include[banner](../includes/banner.md)]

Endpoints let you manage the destinations that business events are sent to. Business events in finance and operations apps support the following endpoint types.

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

You can create endpoints for these messaging and event brokers. Some scenarios might require multiple endpoints for organized distribution of business events to consumers. You can create multiple endpoints to support these scenarios.

You must create the Microsoft Azure–based endpoints in your Azure subscription. For example, if you use Event Grid as an endpoint, you must create the endpoint in your Azure subscription.

A finance and operations app doesn't provision the endpoints. You must create and provide the endpoints to the app. The app then sends events to the endpoints that you provide. You might incur more costs if you use these endpoints in your Azure subscription.

## Subscribing to finance and operations apps events from Dataverse

> [!IMPORTANT]
> Before you subscribe to finance and operations apps business events and data events in Microsoft Dataverse, enable the Microsoft Power Platform integration. For information about how to enable the Microsoft Power Platform integration for a finance and operations apps environment, see [Enable the Microsoft Power Platform integration](../power-platform/enable-power-platform-integration.md).

After you enable the Microsoft Power Platform integration, you can subscribe to finance and operations apps business events and data events from Dataverse. Subscription enables the following capabilities:

- Consistent behavior across events from multiple applications in Dataverse
- Application Lifecycle Management (ALM) for the Dataverse solution to consistently consume events from finance and operations apps
- Registration of plug-ins and software development kit (SDK) steps on finance and operations apps events in Dataverse

When you enable the Microsoft Power Platform integration for a finance and operations apps environment, the linked Microsoft Power Platform environment syncs the created endpoints for business events for supported endpoint types in Dataverse. You can then use the endpoints in Microsoft Power Platform. When the endpoints are synced, business events that finance and operations apps send are proxied through Dataverse to the endpoint.

The following table shows the mapping between the finance and operations apps and Dataverse implementations of the endpoints.

| Finance and operations apps endpoint type | Dataverse service endpoint type    |
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
> If an endpoint type isn't supported in Dataverse, or if you don't enable the Microsoft Power Platform integration, the endpoint continues to send the event from finance and operations apps instead of sending it through Dataverse.

### Viewing or creating mapped endpoints in Dataverse

When you add a new endpoint in finance and operations apps, the app syncs it to Dataverse. The endpoint then appears in the **ServiceEndpoint** table for use in Dataverse. You can also create the endpoint directly in Dataverse in the **ServiceEndpoint** table. If you create the service endpoint by subscribing to a finance and operations apps event, the endpoint is automatically available to finance and operations apps. You can view it on the **Endpoints** tab of the **Business events** page. This behavior applies to the following mapped endpoint types:

- Azure Service Bus Queue
- Azure Service Bus Topic
- Azure Event Grid
- Azure Event Hub

For more information about the **ServiceEndpoint** table, see [ServiceEndpoint table/entity reference](/powerapps/developer/data-platform/reference/entities/serviceendpoint).

> [!NOTE]
> When you map endpoints in Dataverse, you must add Dataverse IP addresses to the allow list of firewall policies for business events and data events. For more information about the IP addresses required for the firewall policies, see [IP addresses required](/power-platform/admin/online-requirements#ip-addresses-required).

### Microsoft Power Automate endpoints

You can't set up the **Microsoft Power Automate** endpoint type directly in finance and operations apps. Use this endpoint type for subscriptions that are created and sent directly from a flow in Power Automate.

You create the endpoint on the **Endpoints** tab of the **Business events** page in finance and operations apps when you subscribe to a finance and operations apps business event or data event in Power Automate. For more information about how to subscribe to business events and data events in Power Automate, see [Business events in Microsoft Power Automate](business-events-flow.md).

### Microsoft Dataverse endpoints

The **Dataverse** endpoint type also isn't available for manual setup in finance and operations apps. The endpoint is created when you register a plug-in or an SDK step on a finance and operations apps business event or data event in Dataverse. When you register the step, it becomes visible as an endpoint in the list on the **Endpoints** tab of the **Business events** page in finance and operations apps.

:::image type="content" source="../media/businessevents_DataverseEndpoint.png" alt-text="Screenshot of the Endpoint of the Dataverse type on the Business events page in a finance and operations app.":::

The business event registration itself also appears on either the **Business event catalog** tab or the **Data event catalog** tab of the **Business events** page in finance and operations apps, depending on registration. In this way, finance and operations apps users can learn which business event or data event has a plug-in or SDK step registered in Dataverse. They can also learn the reason why the event is active in finance and operations apps.

You can subscribe to finance and operations apps events directly in Dataverse by using the tools in the Dataverse toolset, such as the Power Platform Tools extension for Visual Studio. For more information about this extension, see [Install Power Platform Tools](/powerapps/developer/data-platform/tools/devtools-install). These subscriptions appear on the **Business event catalog** tab of the **Business events** page in finance and operations apps.

You can update some attributes of service endpoints in Dataverse, such as the name and description. These updates also appear in finance and operations apps. However, updates that change the service endpoint type are prevented if the service endpoint is used with finance and operations apps events. These updates include a change from a Service Bus article to a Service Bus queue, which Dataverse usually allows. This behavior helps ensure design simplicity and consistency, because finance and operations apps don't allow these updates to endpoints after they're created.

After you create service endpoints, Dataverse doesn't allow you to delete them if they're being used. This limitation also applies to service endpoints that finance and operations apps events use. Any attempt to delete one of these endpoints causes an error, and deletion is prevented.

For more information about how to subscribe to finance and operations apps business events in Dataverse, see [Subscribe to events in Dataverse](how-to/how-to-dataverse-events.md).

### Application secret expiry notification and management

The business event endpoint configuration requires developers to create an application secret in Microsoft Entra ID. However, after completing the initial setup, developers often forget to update the endpoint when the secret expires. As a result, business events sent through that endpoint fail until the new secret is manually updated, which can lead to event loss.

To address this problem, the business event endpoint configuration page includes a new field, **SecretExpiryDate**. Developers can enter the secret's expiry date from Microsoft Entra ID when configuring the endpoint.

:::image type="content" source="media/business-events-azure-app-id-secret.png" alt-text="Business Event Endpoint configuration page showing the Secret Expiry Date field for managing application secrets.":::

Finance and operations apps use this information to proactively notify developers about upcoming secret expirations through a banner alert on the business event endpoint configuration page.

:::image type="content" source="media/business-events-error-info-warning.png" alt-text="Banner alert on the Business Event configuration page displaying a notification about upcoming secret expiration.":::

#### Banner classification

- Info – The secret expires within the next 30 days.
- Warning – The secret expires within the next 15 days.
- Error – The secret expires within one day or has already expired.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
