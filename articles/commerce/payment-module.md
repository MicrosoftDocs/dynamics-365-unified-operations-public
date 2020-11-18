---
# required metadata

title: Payment module
description: This topic covers the payment module and explains how to configure it in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.13

---

# Payment module

[!include [banner](includes/banner.md)]

This topic covers the payment module and explains how to configure it in Microsoft Dynamics 365 Commerce.

## Overview

The payment module lets customers pay for orders by using credit or debit cards. Payment integration for this module is provided by the Dynamics 365 Payment Connector for Adyen. For more information about how to set up and configure the payment connector, see [Dynamics 365 Payment Connector for Adyen](dev-itpro/adyen-connector.md).

The payment module hosts the payment information that is served via Adyen in an HTML inline frame (iframe). The payment module interacts with the Commerce Scale Unit to retrieve the Adyen payment information. As part of the Commerce Scale Unit interaction, the payment module can allow billing address information to be served either in the iframe or as a separate module. In the Fabrikam theme, the billing address is shown in a separate module. This approach allows for more formatting flexibility, because the address lines can be rendered so that they resemble the lines of the shipping address.

The payment module also lets signed-in customers save their payment information. The payment information and billing address are saved and managed via the Adyen payment connector.

The payment module covers any order charges that aren't already covered by loyalty points or a gift card. If the total for an order is fully covered by loyalty points or gift card credits, the payment module will be hidden, and the customer will be able to place the order without it.

The Adyen payment connector also supports strong customer authentication (SCA). Part of the European Union (EU) Payment Services Directive 2.0 (PSD2.0) requires that online shoppers be authenticated outside their online shopping experience when they use an electronic payment method. During the checkout flow,  customers are redirected to their banking site. Then, after authentication, they are redirected back to the Commerce checkout flow. During this redirection, the information that a customer entered in the checkout flow (for example, the shipping address, delivery options, gift card information, and loyalty information) will persist. Before you can turn on this feature, the payment connector must be configured for SCA in Commerce headquarters. For more information, see [Strong Customer Authentication using Adyen](adyen_redirect.md).

> [!NOTE]
> For the Adyen payment connector, the iframe module in the payment module can be rendered only if you add the Adyen URL to your site's allow list. To complete this step, add **\*.adyen.com** to the **child-src**, **connect-src**, **img-src**, **script-src**, and **style-src** directives of your site's content security policy. For more information, see [Manage Content Security Policy](manage-csp.md). 

The following illustration shows an example of gift card, loyalty, and payment modules on a checkout page.

![Example of gift card, loyalty, and payment modules on a checkout page](./media/ecommerce-payments.PNG)

## Payment module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Heading | Heading text | An optional heading for the payment module. |
| Height of the iframe | Pixels | The iframe height, in pixels. The height can be adjusted as required. |
| Show billing address | **True** or **False** | If this property is set to **True**, the billing address will be served by Adyen inside the payment module iframe. If it's set to **False**, the billing address won't be served by Adyen, and a Commerce user will have to configure a module to show the billing address on the checkout page. |
| Payment style override | Cascading Style Sheets (CSS) code | Because the payment module is hosted in an iframe, there is limited styling capability. You can achieve some styling by using this property. To override site styles, you must paste the CSS code as the value of this property. Site builder CSS overrides and styles don't apply to this module. |

## Billing address

The payment module lets customers provide a billing address for their payment information. It also lets them  use their shipping address as the billing address, to make the checkout flow easier and faster. If the **Show billing address** property is set to **False**, the payment module should be configured on the checkout page.

## Add a payment module to a checkout page and set the required properties

A payment module can be added only to a checkout module. For more information about how to configure a payment module for a checkout page, see [Checkout module](add-checkout-module.md).

## Additional resources

[Cart module](add-cart-module.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Pickup information module](pickup-info-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)

[Dynamics 365 Payment Connector for Adyen](dev-itpro/adyen-connector.md)

[Strong Customer Authentication using Adyen](adyen_redirect.md)
