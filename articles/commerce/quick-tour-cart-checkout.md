---
# required metadata

title: Quick tour of cart and checkout
description: This topic provides a quick tour of cart and checkout in Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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

# Quick tour of cart and checkout

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic provides a quick tour of cart and checkout in Dynamics 365 Commerce.

## Overview

## Cart

The **Cart page** serves as the shopping bag which includes all the items added to the Cart. Here is a screenshot of the Cart page built with web starter kit and Fabrikam theme.

![Cart page](./media/cart2.PNG)

The top of the page has a Header which shows all the product categories and other pages that retailer wants the shopper to browse. On the bottom of the page is a Footer with quick links to various topics that a shopper may be interested. Refer to Header and Footer for more details.

The main body of the Cart page shows all the items added to the Cart by the shopper. On the Cart, all applicable discounts including complex discounts will be showcased (e.g. Buy 3 items and get 10% off, Buy a bottle and a backpack to get 10% off, etc.) There is a promo code module which also allows the user to apply or remove promo codes.

The Order summary module shows the amount due after discounts, shipping, taxes etc. A shopper can shop anonymously or as a signed-in user. If a user is signed-in, items in their cart are preserved. This allows them to continue their shopping journey from multiple devices.

From the Cart, a shopper can proceed to checkout. Checkout can be initiated as a guest user or as a signed-in user. See Cart topic for authoring a cart page. 

## Checkout

The Checkout page is where your customers enter the information needed to place an order. Here is a screenshot of the Cart page built with web starter kit and Fabrikam theme.

![Checkout page](./media/Checkout.PNG)

The top of the page has a Header which shows all the product categories and other pages that retailer wants the shopper to browse. On the bottom of the page is a Footer with quick links to various topics that a shopper may be interested. Refer to Header and Footer for more details.

The main body of the Checkout page is where all order information is collected. This includes shipping address, delivery options, payment etc. Checkout has a step by step flow as the workflow requires information to be entered in a certain order to be processed (e.g. shipping address must be entered before shipping costs can be calculated and so that payment can be authorized.)

Shipping address is required if items need to be shipped to an address. The shipping address format can be configured in HQ for each locale (e.g. if the country selected is United States, shipping address will require street Address, state, zip code etc.) There is some basic input validation that is done for shipping address fields – alphanumeric, maximum length, number etc. The address itself is not verified for validity; this can be done via third party services as a customization. 

Shipping address is applied to all items in the cart that have the ship option selected. It is not possible to ship individual cart items to separate when using the starter kit checkout flow. If this capability is required, it can be accomplished through customization of the checkout modules. 

Once the shipping address is provided, shipping methods that are applicable to the Dynamics 365 online store the customer is shopping in will be shown. The shipping methods and the addresses they support can be configured in HQ.  

The next step in the checkout flow is payment. In e-commerce, orders can be placed using multiple forms of payment – credit card, gift card and loyalty points.  A combination of these payment methods can be used to place the order. Depending on which payment methods are used, additional information is required. For example, credit card payment requires a billing address. 

Credit card payments are processed via Adyen Payment connector. For additional details on this Payment connector see the help topic that covers payment providers.

Loyalty points can be used to redeem for an order. However, the user must be a loyalty member to be able to redeem the points. This module is shown only if the user has an existing loyalty membership. For non-members and guest users, this module will be hidden.

In starter kit, we support redeeming internal gift cards to place an order. Currently user must be signed-in to apply the internal gift card. Its recommended to customize the flow using a PIN on internal gift cards for additional security.

The checkout process can be completed as a guest user or a signed-in user. If the user is signed-in, account information such as saved shipping address, saved credit card details will be automatically retrieved. 

Checkout also shows a summary of the line items in the cart for the shopper to verify before making the purchase. The line items cannot be edited in checkout flow. There is a quick link to the Cart for the user to go back and edit the line items.

Once shipping and billing information is provided, the order summary will reflect the amount due after loyalty, gift card and other payments have been applied.

When an order is placed, a confirmation number is provided to the shopper. At the time the order is placed, the payment is authorized, but not charged. When the order is fulfilled (either shipped or picked up,) payment will be charged. 

Once an order is created, an order confirmation email is sent to the customer to confirm that the order was created.

For details on authoring a checkout page, see the Checkout help topic.
