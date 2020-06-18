---
# required metadata

title: Payment module
description: This topic describes how to add a payment module to a checkout page and set the required properties.
author: anupamar-ms
manager: annbe
ms.date: 05/28/2020
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

This topic describes how to add a payment  module to a checkout page and set the required properties.

## Overview

This module lets a customer pay for an order by using credit or debit card. Payment integration is provided by the Adyen payment connector for this module. For more information about how to use setup and configure this connector to use on e-commerce, see [Dynamics 365 Payment Connector for Adyen](dev-itpro/adyen-connector.md). 

The Adyen payment connector also supports Strong Customer Authentication. Part of the EU Payment Services Directive 2.0 (PSD2.0) requires online shoppers to be authenticated outside of their online shopping experience when paying with an electronic payment method. For more details refer to [Strong Customer Authentication using Adyen](adyen_redirect.md).  The support for Strong Customer Authentication via payment module has been added in 10.0.12. 

The Payment module hosts the payment information that is served via Adyen in an iframe. The module interacts with the Commerce Scale Unit and retrieves the Adyen information which is then hosted within the iframe. As part of the Commerce Scale Unit interaction, it can allow Billing address to be served within the Adyen iframe or as a separate module. In Fabirkam theme, Billing Address is represented as a separate module as it allows more flexibilty to style the address lines similar to Shipping Address. 

The module also allows a signed-in user (C2) to persist their payment information. The payment information and billing address are saved and managend via Adyen

THe Payment module covers the order charges that are not already covered by loyalty points or a gift card. If the order total is fully covered via Loyalty points or gift card, the payment module will be hidden and the user can proceed to place the order.

The following is an example of the checkout page with Payment module along with Gift card and Loyalty
![Example of gift card, loyalty points, payment, and billing address modules](./media/ecommerce-payments.PNG))


## Payment module properties
| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading                  | Heading| An optional heading can be provided to the module|
| Height of the iframe | pixels   | The iframe height can be adjusted as needed |
| Show billing address       | **True** or **False** | If True, Billing address is served  by Adyen inside the Payment iframe. If false, the billing address will not be served by Adyen and will require a C1 to configure a **Billing address module** to the checkout page  |
| Payment style override    |  CSS input | Since the payment module within an iframe it provides limited capabilty to style. Some styling can be achieved via this field. Its required for a C1 to copy/paste the entire CSS for this module along with additional changes in this property to override the styles. Site builder CSS overrides and styles do not apply to this module.|

## Billing address
This module lets a customer provide a billing address for their payment information. As mentioned earlier, this module should be configured on the checkout page if the **Show billing address** property on Payment module is set to false. This module also allows the customers to use their shipping address as the billing address to make the checkout flow easy and faster. 

## Add a payment module to a checkout page and set the required properties

A payment module can only be added to a Checkout container. See [Checkout module](add-checkout-module.md] for details on configuring the module to a page.

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
