---
# required metadata

title: Checkout module
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

This module lets a customer pay for an order by using credit or debit card. If the total amount in the cart is covered by loyalty points or a gift card, or if it's 0 (zero), this module is automatically hidden. The payment integration is provided by the Adyen payment connector for this module. For more information about how to use setup and configure this connector to use on e-commerce, see [Dynamics 365 Payment Connector for Adyen](dev-itpro/adyen-connector.md). The Adyen payment connector also supports Strong Customer Authentication. Part of the EU Payment Services Directive 2.0 (PSD2.0) requires online shoppers to be authenticated outside of their online shopping experience when paying with an electronic payment method. For more details refer to [Strong Customer Authentication using Adyen](adyen_redirect.md). 


The following is an example of the checkout page with Payment module along with Gift card and Loyalty
![Example of gift card, loyalty points, payment, and billing address modules](./media/ecommerce-payments.PNG))

## Add a payment module to a checkout page and set the required properties

A payment module can only be added to a Checkout container. See [Checkout module](add-checkout-module.md] for details on configuring the module to a page
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
