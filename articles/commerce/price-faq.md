---
title: Price FAQ
description: This article answers frequently ask questions about pricing and discounts in Microsoft Dynamics 365 Commerce.
author: zhizhen
ms.date: 10/08/2023
ms.topic: article
ms.prod:
ms.technology:
audience: Application User
ms.reviewer:
ms.search.region: Global
ms.author:
ms.search.validFrom:
ms.dyn365.ops.version:
ms.assetid:

---

# Price FAQ

[!include [banner](../includes/banner.md)]

This article answers frequently ask questions about pricing and discounts in Microsoft Dynamics 365 Commerce.

### What pricing calculation scenarios are backed by the Commerce pricing engine?
- In headquarters: Call center sales order and Price simulator.
- In Point of Sales: All operations.
- In Ecommerce: All operations.

### How can I extend the Commerce pricing engine?
You can checkout the latest Commerce SDK samples in the folder `src/PricingEngine` of [microsoft\/Dynamics365Commerce\.Solutions\: Repository for hosting the Dynamics 365 Commerce end to end sample solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions/ "microsoft/Dynamics365Commerce.Solutions: Repository for hosting the Dynamics 365 Commerce end to end sample solutions")

### Why am I seeing a wrong price?
To diagnostic you price and discount configurations, you can follow below steps:
1. Go to **Retail and Commerce** > **Pricing and discounts** > **Price simualtor**. Set your price calculation context including the channel, customer(if any), sales lines, etc..
1. If you're seeing expected prices in **Price simulator**, your price and discount configurations are likely to be correct. You can follow [Commerce Data Exchange best practices \- Commerce \| Dynamics 365 \| Microsoft Learn](/dev-itpro/cdx-best-practices "Commerce Data Exchange best practices - Commerce | Dynamics 365 | Microsoft Learn") to double check if you have successfully synchronized your data to the Commerce Scale Unit.
1. If you're **not** seeing expected prices in **Price simulator**, you need to reevaluate your price and discount configurations including price groups, loyalty, affiliation, discounts, etc..

[!INCLUDE[footer-include](../includes/footer-banner.md)]
