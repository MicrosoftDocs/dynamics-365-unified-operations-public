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
[!include [banner](includes/preview-banner.md)]

This topic describes how to configure digital gift cards in Dynamics 365 Commerce.

The purchase of digital gift cards is supported as of the Dynamics 365 Commerce 10.0.16 release. 

## Digital gift cards in Dynamics 365 Commerce

In Dynamics 365 Commerce, the digital gift card purchase flow follows the same flow as other products in the system and does not require any additional modules to be configured.

When multiple gift cards are added to the cart, the items will not be aggregated in a single sales line. This is required because each sales line will be invoiced with a separate gift card number. 

## Enable the digital gift card feature in Commerce headquarters

The **Purchasing gift card on e-commerce feature** feature flag must be enabled in Commerce headquarters for gift card purchase flow to work in Dymamics 365 Commerce. 

## Configure a digital gift card in Commerce headquarters

Digital gift card products should be configured in Commerce headquarters similar to other products. For more information on creating and configuring products, see [Create a new product in Commerce](create-new-product-commerce.md).

Here are important steps specific to configuring a gift card for purchase in Commerce headquarters.

- If the product is a digital gift card, set the **Product type** to **Service item** when configuring the product. If a product is of type **Service item**, it will not be checked for available inventory before placing an order. For more information, see [Create a new product](create-new-product-commerce.md#create-a-new-product).
- If the gift card needs to support multiple predefined values (for example, $25, $50, $100), this should be set up using the **Size** dimension. Each predetermined amount will be a variant. For more information, see [Product dimensions](https://docs.microsoft.com/dynamics365/supply-chain/pim/product-dimensions?toc=/dynamics365/retail/toc.json).
- If the gift card needs to allow a custom amount, set up a variant that allows a custom amount, then and go to the product and set **Key in Price** to **Must key in price**. This ensures that a price can be entered by the customer when browsing the product on the product details page. For this open the product from **Released Products in Category** and navigate down to **Commerce** section which should have this property.
- Set the delivery mode for gift cards to be of type **Electronic**. For more information, see [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).
- Add product image(s) for the gift card product to the Commerce site builder **Media library**. The gift card image file name(s) should follow the same pattern as defined in the media template. 
- Ensure you have an online functionality profile created and associated with your online store in Commerce headquarters. In the functionality profile, set the **Aggregate products** to **Yes**. This will ensure that all items except gift cards are aggregated. For more information, see [Create an online functionality profile](online-functionality-profile.md).
- The product needs to be configured to be of type **Gift card**. For more information, see [Support for external gift cards](./dev-itpro/gift-card.md).

- Set up the email template **Email notification type** to **Issue Giftcard** so the customer receives an email once the gift card is invoiced. For more information, see [Set up an email notification profile](email-notification-profiles.md).

## Configure a custom amount for a digital gift card in Commerce site builder

If a digital gift card is configured to allow a custom amount, this must also enabled in the [Buy box module](add-buy-box.md) used on your site's product details pages (PDPs). The buy box module supports module configuration to allow custom prices. In addition, you can define a **Minimum** and **Maximum** amount allowed on the custom price.

To configure a custom amount for a digital gift card in Commerce site builder, follow these steps.

1. Navigate to the buy box module used on your site's PDPs. This might be implemented in a fragment, template, or page.
1. Select **Edit**. 
1. In the properties pane on the right, select the **Allow custom price** check box.
1. To optionally define minimum and maximum amounts for custom prices, enter prices for **Minimum price** and **Maximum price**.

## Additional resources

[Buy box module](add-buy-box.md)

[Checkout module](add-checkout-module.md)

[Cart module](add-cart-module.md)

[Create a new product in Commerce](create-new-product-commerce.md)

[Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)

[Product dimensions](https://docs.microsoft.com/dynamics365/supply-chain/pim/product-dimensions?toc=/dynamics365/retail/toc.json)

[Set up an email notification profile](email-notification-profiles.md)

[Create an online functionality profile](online-functionality-profile.md)

[Support for external gift cards](./dev-itpro/gift-card.md)
