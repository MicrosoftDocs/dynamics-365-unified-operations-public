---
title: Order checkouts with inventory availability
description: This article describes how do order checkouts work with inventory availability in Dynamics 365 Commerce.
author: wenxyang
ms.date: 09/10/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: wenxyang
ms.search.validFrom: 2023-01-01

---

# Order checkouts with inventory availability

[!include [banner](includes/banner.md)]

This article describes how do order checkouts work with inventory availability in Dynamics 365 Commerce.

Some customers will require the inventory availability check in the carting and order checkouts to avoid overselling. However, we also see many retailers will want to oversell products. So, today the order checkout experience with inventory availability is different on eCommerce and POS.

## Order checkouts on eCommerce

On eCommerce, when "Enable stock check in app" is turned on via [Apply inventory settings](inventory-settings.md), we will perform inventory availability check before adding a product to the cart, only available products are allowed. Before the order checkouts, we will also perform the inventory availability check.

When "Enable stock check in app" is turned off, we will not perform inventory availability check in either adding to cart or order checkouts.

# Order checkouts on POS

On POS, there is no inventory availability check when adding a product to the cart or order checkout. The store employees can use [POS inventory lookup](pos-inventory-lookup-operation.md) operation to check the availability before the order checkouts.

If your business require automatic inventory availability check from the system on POS, it's recommended to build your own customizations.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
