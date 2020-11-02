---
# required metadata

title: Purchasing a digital gift card
description: This topic covers purchasing gift card in e-commerce
author: anupamar-ms
manager: annbe
ms.date: 10/20/2020
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
ms.dyn365.ops.version: Release 10.0.15

---

# Purhcasing a Gift card on e-commerce

[!include [banner](includes/banner.md)]

This topic covers purchasing a gift card on e-commerce.

## Overview
In Dynamics 365 Commerce 10.0.16 release, we support purchase of digital gift cards via e-commerce. 

## Configuring a digital gift card in Headquarters
A gift card product should be configured in headquarters similar to other products. Here are the important steps for configuring a gift card for e-commerce purchase.

- If the product is a digital gift card set **Item Type= Service item** when configuring the product. If a product is of type Service item it will not be checked for available inventory before placing an order. For more details refer to [Creating a product](create-new-product-commerce.md)
- If the gift card needs to support multiple pre-defined values such as $25, $50 etc. This should be setup using the Size dimension and each pre-determined amount will be a variant. For more details refer to [Product dimensions](product-dimensions.md)
- If the gift card allows a custom amount, it should have xyz = Key in Price. This ensures a price can be entered by the customer when browsing the product on the product details page.
- Set the delivery mode for gift cards to be of type Electronic. For more details refer to [Setup up modes of delivery](./appuser-itpro/set-up-modes-of-delivery.md)
- Add product image(s) for the gift card product in Site Builder's Digital Asset Management. The gift card image file name(s) should follow the same pattern as defined in the Media template. 
- Please ensure you have an **Online Functionality Profile** created and associated to your **Online store** in Headquarters. In the functionality profile set cart aggreation to **True**. This will ensure all items except gift card are aggregated. For details refer to [Online Functionality Profile](online-functionality-profile.md)
- The product needs to be configured to be of type Gift card.  For details refer to [External gift card setup](./dev-itpro/gift-card.md)
- Set up the email template for "Issue Giftcard" action so the customer receives an email once the gift card is invoiced. For more details refer to [Setup email notification](email-notification-profiles.md)


## Enabling Gift card feature in Headquarters
**Purchasing gift card on e-commerce feature** feature flag must be enabled in headquarters for gift card purchase flow to work on e-commerce. 

## Gift card experience in e-commerce Experience
On e-commerce, the gift card purchase flow goes through the same flow as other products in the sytem and does not require any additional modules to be configured.

If the product is configured to allow a custom amount, this needs to also enabled on the **BuyBox** module. The Buybox module supports module configuration to **Enable custom price** which must be set to True. In addition, you can define a **Minimum** and **Maximum** amount allowed on the custom price as well.

If the product is setup as a Service item, it will not be checked for inventory.

When multiple gift cards are added to cart, the items will not be aggregated in the cart line. This is required as each sales line will be invoiced with a separate gift card number. 


## Additional resources

[Buybox module](add-buy-box.md)

[Checkout module](add-checkout-module.md)

[Cart module](add-cart-module.md)

[Creating a product](create-new-product-commerce.md)

[Setup up modes of delivery](./appuser-itpro/set-up-modes-of-delivery.md)

[Product dimensions](product-dimensions.md)

[Setup email notification](email-notification-profiles.md)

[Online Functionality Profile](online-functionality-profile.md)

[External gift card setup](./dev-itpro/gift-card.md)
