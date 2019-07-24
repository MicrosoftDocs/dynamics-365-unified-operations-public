---
# required metadata

title: Checkout
description: This topic reviews setting up a Checkout module in a Dynamics 365 e-Commerce page.
author: anupamar-ms
manager: BrendanSullivanMSFT
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---

# Checkout 

Checkout module is container that is used for hosting all the modules that are necessary to create an order. For instance, it includes Shipping address, Shipping methods, Billing information, Order summary etc. It presents a step-by-step flow for the user to enter all the relevant information to make a purchase.  

Checkout module renders data based on the Cart id which is derived from the page context. This means Checkout module cannot be used on a page that does not have the Cart context E.g. Marketing page or Home page. 

## Properties of Checkout 

Checkout has multiple steps such as Shipping address, Shipping methods etc. The section heading for each step can authored in the checkout container with a heading tag. A Width property is provided to indicate if items in container should fit to width or fill screen.  

Checkout container has multiple slots – Checkout information, Order summary, Place order. Each slot has a set of modules that are supported and will appear in a specific layout on the page. Checkout information slot has all modules that are needed to trigger a checkout e.g. shipping address, payment method etc. Order summary slot shows the order summary and place order action. Place order slot also supports place order action. To optimize placing order in various view ports, there are two slots where each Place order module can be defined.  

## Modules available in Checkout 

**Shipping address:** This module allows a user to add or select the shipping address for the order. If the user is signed-in, any address that was previously saved will be shown for the user to choose. In addition, the user can add a new address. The shipping address is for all items in the order that require shipping and cannot be customized on a line item basis. Shipping address formats are defined in HQ per country which is respected by the shipping address module.  The module does not provide address validation though it can be achieved via a customization. 

**Delivery options:** Delivery options allows the user to choose a delivery option for the order. Delivery options is based on the shipping address. If the shipping address is changed, the delivery options must retrieved again.  

**Checkout section container:** This is a container that allows multiple modules to be placed inside to create a section within the Checkout flow.  For example, all payment modules can be configured inside this container to make them appear as one section. This container is added only to control the layout of the flow. 

**Gift card:** Gift card allows the user to pay for the order using a gift card. This module supports Dynamics 365 Internal gift cards only. One or more gift cards can be applied to an order. If the gift card balance is not sufficient, it can be combined with another payment method.  

**Loyalty points:** Loyalty points allows the user to pay for the order using loyalty points. It provides a summary of available points and expiring points. It lets the user choose the amount they want to redeem using points. If the user is not signed-in or not a loyalty member this module will be hidden. 

**Credit card:** This module allows the user to pay for the order using credit card. Credit card integration is provided via Adyen payment connector.  See Adyen payment connector for more details on how to use this connector. 

**Billing address****:** This module allows the user to provide the billing information. This information is processed along with credit card by Adyen. It has an option to use Shipping address to Billing if the user prefers to do the same.  

**Contact information:** This module allows the user to add or change the contact information (email) for the order. 

**Place order**: This module allows the user to place the order. A link must be configured on the module to indicate the order confirmation page.  

**Content rich block**: A content rich block can be added in checkout container for any CMS driven messaging. E.g. “For issues with order contact 1-800-FABRIKAM” 

**Order summary**: Order summary is used to show the cost breakdown for the order 

**Order line items:** Order line items is used for showing a summary of the items that will be included in the order 

## Retail server interaction 

All the checkout information such as shipping address, shipping methods are stored in the Cart and processed as part of the order. The only exception is the credit card information. Credit card information is processed directly via Adyen Payment connector. The payment is authorized but not charged. 

## Authoring Checkout  

This section explains how to add a checkout module to a new page and set the required properties.

1. In tooling, create a new page template “Checkout template”.
2. In the Main slot of the template, add Checkout.
3. Check-in and Publish.
4. Now create a new page with the “Checkout template” and call it “Checkout page”.
5. On the page outline, add Default page.
6. To the Default page, add Checkout module.
7. Add a Heading for the page. Add a section heading for each section of the Checkout – Shipping address, Shipping Methods, Payment information, Contact information.
8. To the Checkout information slot, add Shipping address module.
9. To the Checkout information slot, add Delivery options module.
10. To the Checkout information slot, add Checkout section container module.
11. To the Checkout section container, add Gift Card, Loyalty and Credit card modules. This will ensure all payment methods appear within a section. 
12. To the Checkout information slot, add Contact information module.
13. In the above setup, there should be 4 sections on the Checkout information slot.
14. In the Order summary slot, add  order summary module and place order module.
15. In the order summary slot, add a content rich block with text “For questions on orders, contact 1-800-FABRIKAM”.
16. In the Place order slot, add place order module.
17. Save and Preview. Some modules may not render in preview as they don’t have a Cart context.
18. Check-in and Publish.
    

Checkout can be built as a Fragment <link> since there is only one instance of Checkout. 