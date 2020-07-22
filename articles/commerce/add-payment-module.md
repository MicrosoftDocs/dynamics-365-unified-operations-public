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
ms.dyn365.ops.version: Release 10.0.5

---

# Payment module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes covers the payment module and how to configure it in Dynamics 365 Commerce.

## Overview

The payment module allows customers to pay for orders using credit or debit cards. Payment integration for this module is provided by the Dynamics 365 Payment Connector for Adyen. For more information about how to use setup and configure the payment connector, see [Dynamics 365 Payment Connector for Adyen](dev-itpro/adyen-connector.md). 

The payment module hosts the payment information that is served via Adyen in an HTML inline frame (iframe). The module interacts with the Commerce Scale Unit and retrieves the Adyen information which is then hosted within the iframe. As part of the Commerce Scale Unit interaction, it can allow billing address to be served within the Adyen iframe or as a separate module. In the Fabrikam theme, the billing address is represented as a separate module since it allows for more flexibility to format the address lines to look similar to those for the shipping address. 

The payment module also allows a signed-in customer to save their payment information. The payment information and billing address are saved and managed via the Dynamics 365 Payment Connector for Adyen.

THe payment module covers any order charges that are not already covered by loyalty points or a gift card. If an order total is fully covered by loyalty points or gift card credits, the payment module will be hidden and the customer will be able to proceed to place the order.

The Adyen payment connector also supports strong customer authentication (SCA). Part of the EU Payment Services Directive 2.0 (PSD2.0) requires online shoppers to be authenticated outside of their online shopping experience when paying with an electronic payment method. During the checkout flow, the customer is redirected to their banking site and after authentication will be redirected back to the e-Commerce checkout flow. During this redirection, the information that was entered by the customer in the checkout flow such as shipping address, delivery options, gift card and loyalty information will persist. To turn on this feature, the payment connector must be configured for SCA in Commerce headquarters. FOr more information, see [Strong Customer Authentication using Adyen](adyen_redirect.md). The support for SCA via payment module was been added in Commerce version 10.0.12. 

The following image shows an example of a checkout page with a payment module along with gift card and loyalty modules.

![Example of gift card, loyalty, payment, and billing address modules](./media/ecommerce-payments.PNG))

## Payment module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading                  | Heading| An optional heading can be provided for the module. |
| Height of the iframe | pixels   | The iframe height can be adjusted as needed. |
| Show billing address       | **True** or **False** | If true, billing address is served by Adyen inside the payment module iframe. If false, the billing address will not be served by Adyen and will require a Commerce user to configure a billing address module on the checkout page.  |
| Payment style override  |  CSS input | Since the payment module within an iframe it provides limited capabilty to style. Some styling can be achieved via this field. A Commerce user must copy and paste the entire CSS for this module along with additional changes in this property to override the styles. Site builder CSS overrides and styles do not apply to this module. |

## Billing address

This module lets a customer provide a billing address for their payment information. As mentioned earlier, this module should be configured on the checkout page if the **Show billing address** property on Payment module is set to false. This module also allows the customers to use their shipping address as the billing address to make the checkout flow easy and faster. 

## Add a payment module to a checkout page and set the required properties

A payment module can only be added to a checkout module. For more information on configuring a payment module for a checkout page, see [Checkout module](add-checkout-module.md].

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
