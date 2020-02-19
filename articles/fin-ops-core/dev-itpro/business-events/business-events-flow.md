---
# required metadata

title: Business events in Microsoft Power Automate
description: This topics provides information abou the business events that are available for consumption in Microsoft Power Automate via the application connector.
author: Sunil-Garg
manager: AnnBe
ms.date: 02/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Business events in Microsoft Power Automate

[!include[banner](../includes/banner.md)]

Business events can be consumed in Microsoft Power Automate via the application connector. The connector has a trigger that is named **when a business event occurs**. This trigger can be used to subscribe to any of the business events that are available in the target instance of the application.

## Prerequisite

It's important that you understand business events. For more information, see the [Business events](home-page.md) documentation.

> [!IMPORTANT]
> The **when a business event happens** trigger works only with application instances that run Platform update 24 or later, because business events aren't available in earlier platform releases.

## Subscribing to business events and unsubscribing from them

After the **when a business event happens** trigger is added to a flow, the following information must be provided:

- **Instance** – Specify the host name of the instance where business events occur. Environment instances should be available in the provided drop-down menu, but if an environment is not listed it can be entered as a custom value.
- **Category** – Select the category of business events. The **Business event** field then shows the business events in that category.
- **Business event** – The available business events in the selected category.
- **Legal entity** – Specify the legal entity where the business event is being subscribed to. The flow will be triggered when the business event occurs in that legal entity. By default, this field is blank and the business event is subscribed to in **all** legal entities.

When the flow is saved, a subscription to the selected business event is added into the environment instance. As part of the subscription process, the required endpoint is set up, and the corresponding business event is activated.

If the trigger is deleted or the flow is turned off, then the business event endpoint will be automatically deleted.

Multiple flows can subscribe to the same business event in different legal entities or in the same legal entity. Note that the default endpoint limit per event is ten. If needed, adjust the **Endpoints allowed per event** on the **Business event parameters** page.

> [!NOTE]
> The Power Automate endpoint must not be configured manually. The endpoint will automatically get created from Power Automate as explained above.

For how-to information about using business events in Microsoft Flow, see [Consume business events in Microsoft Flow](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/business-events/how-to/how-to-flow). 

## Other ways to consume business events in Power Automate

The previous section explains how you can subscribe to business events directly from Power Automate by using the trigger in the connector. However, you can also consume business events in Microsoft Power Automate from Microsoft Azure Event Grid, by using the [Event Grid connector for Microsoft Power Automate](https://docs.microsoft.com/connectors/azureeventgrid/).

Event Grid might be a viable approach for consuming business events in Power Automate if it's already being used for other integrations in an implementation. If a business event in the same legal entity must trigger multiple flows, you should consider consuming the business event from Event Grid.

This approach is applicable to any messaging or event platform that is used as an endpoint for business events, provided that a connector is available for it in Power Automate.
