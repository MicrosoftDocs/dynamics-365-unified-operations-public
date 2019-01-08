---
# required metadata

title: Business events in Microsoft Flow
description: Business events are available for consumption in Microsoft Flow via the Finance and Operations connector.
author: Sunil-Garg
manager: AnnBe
ms.date: 01/08/2019
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

# Business events in Microsoft Flow

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

Business events are available for consumption in Microsoft Flow via the Finance and Operations connector. The Finance and Operations connector has a trigger called **when a business event happens** which can be used to subscribe to any of the business events available in the target Finance and Operations instance.

## Prerequisite

Understanding of business events is important which is explained in the [Business events](home-page.md) documentation.

> [!Important]

> -   The Finance and Operations connector for Flow is in preview.
>
> -   The trigger **when a business event happens** will only work with Finance and Operations instances that are running platform update 24 or later since business events are not available prior to that platform release.

## Subscribing and un-subscribing a business event
Once the trigger **when a business event happens** is added to the Flow, the following information must be provided.

-   **Instance** – This is the URL of the Finance and Operations instance where business events happen.

-   **Category** – This is the category of business events. Selecting a category will show business events from the chosen category in the following field.

-   **Business event** – This shows the catalog of business events in the chosen category.

-   **Legal entity** – This can be used to specify a legal entity in which the business event is being subscribed. By default, there is no selection which implies **all** legal entities. Subscribing to a business event in all legal entities will trigger the Flow when the business event happens in any of the legal entities in Finance and Operations.

When the Flow is saved, the Flow is automatically subscribed to the selected business event. The required endpoint set up and the activation of the corresponding business event is completed as part of the subscription.

When the trigger is deleted or the Flow is deleted, the business event is automatically unsubscribed.

Multiple Flows can subscribe to the same business event in different legal entities.

## Alternate ways to consume business events in Flow
In addition to directly subscribing to business events from Flow using the trigger in the Finance and Operations connector, one can also consume business events from Azure event grid in Flow using the [event grid connector for Flow](https://docs.microsoft.com/en-us/connectors/azureeventgrid/).

If Azure event grid is already in use for other integrations in an implementation, then using event grid to also consume business events in Flow could be a viable option. If a business event in the same legal entity needs to trigger multiple Flows then, consuming the business event from Azure event grid is an approach to consider.

This approach is applicable to any messaging/event platform used as an endpoint for business events provided it has a connector available in Flow.
