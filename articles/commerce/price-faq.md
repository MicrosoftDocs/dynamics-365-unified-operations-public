---
title: Price FAQ
description: This article provides answers to frequently asked questions about pricing and discounts in Microsoft Dynamics 365 Commerce.
author: zhizhen
ms.date: 01/27/2026
ms.topic: faq
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: zhizhen
ms.search.validFrom: 10/20/2022
ms.custom: 
  - bap-template
---

# Price FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about pricing and discounts in Microsoft Dynamics 365 Commerce.

### What pricing calculation scenarios does the Commerce pricing engine support?

- **In Commerce headquarters:** Call center sales order and Price simulator.
- **In Point of Sale (POS):** All operations.
- **In E-commerce:** All operations.

### How can I extend the Commerce pricing engine?

Check out the latest Commerce software development kit (SDK) samples in the `src/PricingEngine` folder of [microsoft/Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/).

### Why do I see the wrong price?

To diagnose your price and discount configurations, follow these steps:

1. Go to **Retail and Commerce** \> **Pricing and discounts** \> **Price simulator**.
1. Set your price calculation context, including the channel, the customer (if there's one), and sales lines.
1. If you see the expected prices in Price simulator, your price and discount configurations are likely correct. To confirm that you successfully synchronized your data to the Commerce Scale Unit, follow [Commerce Data Exchange best practices](dev-itpro/cdx-best-practices.md).

    If you **don't** see the expected prices in Price simulator, reevaluate your price and discount configurations, including price groups, loyalty, affiliation, and discounts.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
