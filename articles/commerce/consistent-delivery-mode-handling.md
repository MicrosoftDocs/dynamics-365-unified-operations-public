---
title: Enable consistent delivery mode handling in e-commerce channels
description: Learn about the "Enable consistent delivery mode handling in channel" feature in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2022-02-10

---

# Enable consistent delivery mode handling in e-commerce channels

[!include [banner](includes/banner.md)]

This article describes the **Enable consistent delivery mode handling in channel** feature in Microsoft Dynamics 365 Commerce, and some of the recommended tests that organizations should run to ensure that system behavior meets expectations.

> [!NOTE]
> The **Enable consistent delivery mode handling in channel** feature is mandatory starting with Commerce version 10.0.31.

The **Enable consistent delivery mode handling in channel** feature resolves problems with charge calculations on e-commerce channels. For example, without this feature, users can experience one or both of the following problems in e-commerce channels:
- Nonprorated header-level charges don't appear.
- Charges for delivery modes aren't consistent between the mode of delivery selection and the checkout order summary.

This feature also unifies the logic for handling the pickup and ship delivery modes for a customer order. When you enable this feature, the pickup order lines use the selected store's main warehouse, while the ship order lines use the store's shipping warehouse. Microsoft recommends that you perform the following e-commerce and point of sale (POS) tests to validate that the system behavior meets expectations.

## E-commerce tests

- Create an e-commerce shipping order and validate the warehouse at the header and lines.
- Create an e-commerce pickup order for a store and validate the warehouse at the header and lines. 
- Create an e-commerce order that contains both ship and pickup lines and confirm that the order lines appear on the correct store selected for shipping and pickup. For such orders, the header warehouse isn't relevant because the lines are fulfilled from different warehouses.

## POS tests

- Create a customer order on POS and select "ship all" from a different store that uses different warehouses for shipping and pickup. Validate the warehouse at the header and lines.
- Create a customer order on POS and select "pick up all" from a different store that uses different warehouses for shipping and pickup. Validate the warehouse at the order header and lines.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
