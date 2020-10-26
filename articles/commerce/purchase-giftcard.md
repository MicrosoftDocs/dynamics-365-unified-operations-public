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
In Dynamics 365 Commerce 10.0.15 release, we support purchase of digital gift cards via e-commerce. 

## Configuring a digital gift card in Headquarters
A gift card product should be configured in headquarters similar to other products. Here are the important steps for configuring a gift card for e-commerce purchase.

- If the product is a digital gift card set Item Type= Service item when configuring the product. If a product is of type Service item it will not be checked for available inventory before placing an order.
- If the gift card has multiple pre-defined values such as $25, $50 etc. This has to be setup using the Size dimension and each predetermined amount will be a variant.
- If the gift card allows a custom amount, it should have xyz = Key in Price. This ensures a price can be entered by the customer when browsing the product on the product details page.
- Set the delivery mode for gift cards to be of type Electronic
- Add a product image for the gift card product in Site Builder's Digital Asset Management. The gift card image file name(s) should follow the same pattern as defined in the Media template. 
- The product needs to be configured to be of type Gift card. 
Set up the email template for "Issue Giftcard" action so the customer receives an email once the gift card is invoiced

## Enabling Gift card feature in Headquarters
**xx** feature flag must be enabled in headquarters for gift card purchase flow.

## e-commerce Experience
On e-commerce, the gift card purchase flow goes through the same flow as other products in the sytem and does not require any additional modules to be configured.

If the product is configured to allow a custom amount, this needs to also enabled on the **BuyBox** module. The Buybox module supports module configuration to **Enable custom price** which must be set to True. In addition, you can define a **Minimum** and **Maximum** amount allowed on the custom price as well.

## Additional resources

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)

[Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)

[Create an online functionality profile](online-functionality-profile.md)
