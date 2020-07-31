---

# required metadata

title: Payment module
description: This topic describes covers the payment module and how to configure it in Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 07/31/2020
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
[!include [banner](includes/preview-banner.md)]

This topic describes covers the payment module and how to configure it in Dynamics 365 Commerce.

## Overview

The payment module allows customers to pay for orders using credit or debit cards. Payment integration for this module is provided by the Dynamics 365 Payment Connector for Adyen. For more information about how to set up and configure the payment connector, see [Dynamics 365 Payment Connector for Adyen](dev-itpro/adyen-connector.md). 

The payment module hosts the payment information that is served via Adyen in an HTML inline frame (iframe). The payment module interacts with the Commerce Scale Unit to retrieve the Adyen payment information. As part of the Commerce Scale Unit interaction, the payment module can allow billing address information to be served within the iframe or as a separate module. In the Fabrikam theme, the billing address is displayed in a separate module since this allows for more formatting flexibility to render the address lines to look like those for the shipping address. 

The payment module also allows a signed-in customer to save their payment information. The payment information and billing address are saved and managed via the Dynamics 365 Payment Connector for Adyen.

The payment module covers any order charges that are not already covered by loyalty points or a gift card. If an order total is fully covered by loyalty points or gift card credits, the payment module will be hidden and the customer will be able to proceed to place the order without it.

The Adyen payment connector also supports strong customer authentication (SCA). Part of the EU Payment Services Directive 2.0 (PSD2.0) requires online shoppers to be authenticated outside of their online shopping experience when paying with an electronic payment method. During the checkout flow, the customer is redirected to their banking site, and then after authentication is redirected back to the Commerce checkout flow. During this redirection, the information that was entered by the customer in the checkout flow such as shipping address, delivery options, gift card information, and loyalty information will persist. To turn on this feature, the payment connector must be configured for SCA in Commerce headquarters. For more information, see [Strong Customer Authentication using Adyen](adyen_redirect.md).

The following image shows an example of gift card, loyalty, and payment modules on a checkout page.

![Example of gift card, loyalty, and payment modules on a checkout page](./media/ecommerce-payments.PNG))

## Payment module properties

| Property name             | Values                 | Description |
|---------------------------|-----------------------|-------------|
| Heading                  | Heading| Displays an optional heading for the payment module. |
| Height of the iframe | Pixels   | The iframe height in pixels that can be adjusted as needed. |
| Show billing address       | True, False | If true, the billing address is served by Adyen inside the payment module iframe. If false, the billing address will not be served by Adyen and will require a Commerce user to configure a module to display the billing address on the checkout page.  |
| Payment style override  |  CSS code | Since the payment module is hosted within an iframe, there is limited limited styling capability. Some styling can be achieved using this property. The CSS code must be pasted into this property value to override site styles. Site builder CSS overrides and styles do not apply to this module. |

## Billing address

The payment module lets a customer provide a billing address for their payment information, and also allows customers to use their shipping address as the billing address to make checkout flow easier and faster. The payment module should be configured on the checkout page if the **Show billing address** property is set to false. 

## Add a payment module to a checkout page and set the required properties

A payment module can only be added to a checkout module. For more information on configuring a payment module for a checkout page, see [Checkout module](add-checkout-module.md).

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)

[Dynamics 365 Payment Connector for Adyen](dev-itpro/adyen-connector.md)

[Strong Customer Authentication using Adyen](adyen_redirect.md)
