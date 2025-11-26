---
title: Business events and Microsoft Forms Pro
description: Learn about business events and Microsoft Forms Pro through a scenario where a survey is sent to users when a product is shipped.
author: johnmichalak
ms.author: johnmichalak
ms.topic: upgrade-and-migration-article
ms.date: 10/29/2025
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global for most topics. Set Country/Region name for localizations
ms.search.validFrom: Platform update 27
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 2019-6-30 

---

# Business events and Microsoft Forms Pro

[!include[banner](../../includes/banner.md)]

This article goes through a scenario where Microsoft Forms Pro is used to create a survey that you can use with business events. Specifically, in the scenario described here, a survey is sent to customers when a product is shipped. The survey information is gathered by using Forms Pro.

## Prerequisites

If you haven't used Forms Pro before, first read the [Forms Pro documentation](/forms-pro/) to learn how to use it.

## Scenario

1. Create a survey. Based on the title that you enter for the survey, Forms Pro suggests survey questions.

    :::image type="content" source="../../media/Forms_Pro1.png" alt-text="Screenshot of suggested survey questions in Forms Pro.":::

1. The sales order tracks the shipment. When the product is shipped, the status of the sales order is changed to **Delivered**.

    :::image type="content" source="../../media/SalesOrder1.png" alt-text="Screenshot of sales order that has a status of Delivered.":::

    Therefore, configure an alert on the sales order, so that an alert is created whenever the value of the **Status** field is changed. Be sure to set the **Send externally** option to **Yes**, so that the alert is sent out as a business event.

    :::image type="content" source="../../media/Alerts1.png" alt-text="Screenshot of alert configuration.":::

1. Set up the flow that is triggered by the business event whenever the status of the sales order is updated (see the illustration in the next step). After it's triggered, the flow will use the Forms connector to send the survey to the customer email address that is registered on the sales order.

    The customer email address and other information that is required for the scenario must be in the payload of the business event. If the payload doesn't have this data, it can be extended so that it includes the appropriate fields. For more information, see the [Business events developer documentation](../business-events-dev-doc.md).

1. Because Microsoft Power Automate is used to orchestrate this scenario, don't activate the **When a change based alert occurs** business event in the application. Instead, set up Power Automate so that it subscribes directly to the business event.

    :::image type="content" source="../../media/Flow1.png" alt-text="Screenshot of flow configuration.":::

1. After you finish setting up the flow, it will be triggered and send out the survey whenever the sales order's status is updated.

    :::image type="content" source="../../media/Survey1.png" alt-text="Screenshot of survey interface.":::

    As users fill in the survey and submit it, Forms Pro shows some analytics.

    :::image type="content" source="../../media/Forms_Pro2.png" alt-text="Screenshot of survey analytics in Forms Pro.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
