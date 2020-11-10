---
# required metadata

title: Configure digital gift cards
description: This topic describes how to configure digital gift cards in Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 11/16/2020
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

# Configure digital gift cards

[!include [banner](includes/banner.md)]

This topic describes how to configure digital gift cards in Dynamics 365 Commerce.

The purchase of digital gift cards is supported as of the Dynamics 365 Commerce 10.0.16 release. 

## The digital gift card experience in Dynamics 365 Commerce

In Dynamics 365 Commerce, a digital gift card purchase flow follows the same flow as other products in the system and does not require any additional modules to be configured.

If the product is setup as a **Service item**, it will not be checked for inventory.

When multiple gift cards are added to the cart, the items will not be aggregated in a single sales line. This is required because each sales line will be invoiced with a separate gift card number. 

## Enable the digital gift card feature in Commerce headquarters

The **Purchasing gift card on e-commerce feature** feature flag must be enabled in Commerce headquarters for gift card purchase flow to work in Dymamics 365 Commerce. 

## Configure a digital gift card in Commerce headquarters

Digital gift card products should be configured in Commerce headquarters similar to other products. Here are the important steps for configuring a gift card for purchase.

- If the product is a digital gift card, set **Item Type= Service item** when configuring the product. If a product is of type Service item it will not be checked for available inventory before placing an order. For more details refer to [Creating a product](create-new-product-commerce.md).

- If the gift card needs to support multiple pre-defined values such as $25, $50 etc. This should be setup using the Size dimension and each pre-determined amount will be a variant. For more details refer to [Product dimensions](https://docs.microsoft.com/dynamics365/supply-chain/pim/product-dimensions?toc=/dynamics365/retail/toc.json).

- If the gift card allows a custom amount, setup a variant that allows a custom amount and go to the product and set Key in Price = **Must key in price**. This ensures a price can be entered by the customer when browsing the product on the product details page. For this open the product from *Released Products in Category* and navigate down to *Commerce* section which should have this property.

- Set the delivery mode for gift cards to be of type Electronic. For more details refer to [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

- Add product image(s) for the gift card product in Site Builder's Digital Asset Management. The gift card image file name(s) should follow the same pattern as defined in the Media template. 

- Please ensure you have an **Online Functionality Profile** created and associated to your **Online store** in Headquarters. In the functionality profile set cart aggreation to **True**. This will ensure all items except gift card are aggregated. For details refer to [Online Functionality Profile](online-functionality-profile.md).

- The product needs to be configured to be of type Gift card.  For details refer to [External gift card setup](./dev-itpro/gift-card.md).

- Set up the email template for "Issue Giftcard" action so the customer receives an email once the gift card is invoiced. For more details refer to [Set up email notification](email-notification-profiles.md).

## Configure a custom amount for a digital gift card in Commerce site builder

If a digital gift card is configured to allow a custom amount, this must also enabled in the [Buy box module](add-buy-box.md) used on your site's product details pages (PDPs). The buy box module supports module configuration to allow custom prices. In addition, you can define a **Minimum** and **Maximum** amount allowed on the custom price.

To configure a custom amount for a digital gift card in Commerce site builder, follow these steps.

1. Navigate to the buy box module used on your site's PDPs. This might be implemented in a fragment, template, or page.
1. Select **Edit**. 
1. In the properties pane on the right, select the **Allow custom price** check box.
1. To optionally define minimum and maximum amounts for custom prices, enter prices for **Minimum price** and **Maximum price**.

## Additional resources

[Buybox module](add-buy-box.md)

[Checkout module](add-checkout-module.md)

[Cart module](add-cart-module.md)

[Creating a product](create-new-product-commerce.md)

[Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)

[Product dimensions](https://docs.microsoft.com/dynamics365/supply-chain/pim/product-dimensions?toc=/dynamics365/retail/toc.jso)

[Setup email notification](email-notification-profiles.md)

[Online Functionality Profile](online-functionality-profile.md)

[External gift card setup](./dev-itpro/gift-card.md)
