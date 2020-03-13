---
# required metadata

title: Giftcard module
description: This topic covers gift card module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 01/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Glift card module


[!include [banner](includes/banner.md)]

This topic covers Gift card module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Gift cards are a common form of tender. The gift card module can be used in checkout module as a form of tender. The gift card module supports Dynamics 365 gift cards, SVS and Givex gift cards. SVS and Givex gift cards are redeemed via Adyen payment provider.


## Gift card module properties

## Site settings for gift card

Gift card modules have the following settings that can be configured at **Site Settings \> Extensions**:

**Supported gift card type**: This setting supports 3 values
1. Dynamics 365 gift card - WHen this setting is applied the gift card module will only redeeming of Dynamics 365 gift cards
2. SVS and Givex gift cards
3. Dynamics 365, SVS and Givex gift card

## Add a cart module to a page

To add a cart module to a new page and set the required properties, follow these steps.

1. Create a fragment that is named **Cart fragment**, and add a cart module to it.
1. Add a heading to the cart module.
1. Add a store selector module to the cart module.
1. Save the fragment, finish editing it, and publish it.
1. Create a template that is named **Cart template**, and add the cart fragment that you just created to it.
1. Save the template, finish editing it, and publish it.
1. Create a page that uses the new template.
1. Save and preview the page.
1. Finish editing the page, and publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
