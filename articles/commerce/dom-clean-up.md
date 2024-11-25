---
title: Clean up DOM fulfillment plans and logs
description: This article describes how to clean up distributed order management (DOM) fulfillment plans and logs in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/17/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-11-07
---

# Clean up DOM fulfillment plans and logs

[!include [banner](includes/banner.md)]

This article describes how to clean up distributed order management (DOM) fulfillment plans and logs in Microsoft Dynamics 365 Commerce.

When DOM processing is run, fulfillment plans and DOM logs are created. Over time, the system keeps numerous fulfillment plans and DOM logs. To manage the number of fulfillment plans that the system keeps, you can configure a batch job that deletes older fulfillment plans, based on the **Fulfillment data retention period (in days)** and **DOM logs retention period (in days)** values of the DOM parameters in Commerce headquarters.

To configure a batch job that deletes older fulfillment plans, follow these steps.

1. In headquarters, go to **Retail and Commerce \> Distributed order management \> Batch processing \> DOM fulfillment data deletion job setup**.
1. For **Batch group**, select a configured batch group.
1. Select **Recurrence**, and then define the recurrence of the batch job.
1. Select **OK**.

## Additional resources

[DOM overview](dom.md)

[Set up DOM](dom-set-up.md)

[DOM rules](dom-rules.md)

[DOM cost configuration](dom-costs.md)

[DOM processing](dom-processing.md)

[Results of DOM runs](dom-runs-results.md)

[DOM extensibility](dom-extensibility.md)

[DOM limitations](dom-limitations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
