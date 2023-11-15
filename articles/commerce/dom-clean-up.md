---
title: DOM fulfillment plans and logs clean-up
description: This article describes how to clean up distributed order management (DOM) fulfillment plans in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 11/15/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-11-07
---

# DOM fulfillment plans and logs clean-up

[!include [banner](includes/banner.md)]

This article describes how to clean up distributed order management (DOM) fulfillment plans in Microsoft Dynamics 365 Commerce.

When DOM processing is run, fulfillment plans and DOM logs are created. Over time, the system keeps numerous fulfillment plans and DOM logs. To manage the number of fulfillment plans that the system keeps, you can configure a batch job that deletes older fulfillment plans, based on the **Fulfillment data retention period (in days)** and **DOM logs retention period (in days)** values in the DOM parameters.

Configure a batch job that deletes older fulfillment plans, follow these steps.

1. Go to **Retail and Commerce \> Distributed order management \> Batch processing \> DOM fulfillment data deletion job setup**.
1. In the **Batch group** field, select a configured batch group.
1. Select **Recurrence**, and define the recurrence of the batch job.
1. Select **OK**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
