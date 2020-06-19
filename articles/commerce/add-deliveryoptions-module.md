---
# required metadata

title: Delivery options module
description: This topic describes how to add a Delivery options module to a checkout page and set the required properties.
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

# Delivery options module


[!include [banner](includes/banner.md)]

This topic describes how to add a Delivery options  module to a checkout page and set the required properties.

## Overview

Delivery options module lets a customer select a mode of delivery for their order. 

To configure modes of delviery, See [Online channel setup](channel-setup-online.md). In addition, each delivery mode can have an associated shipping charge. Refer to [Omni-channel Advanced auto-charges](omni-auto-charges.md) to learn more about configuring charges for the online store. The Fabrikam theme, supports a mixed mode of delivery where some items can be shipping and some can be pickup. For a mixed mode of delivery to work, its required to configure **Header Charges with proration** see [Prorate header chanrges to match sales lines](pro-rate-charges-matching-lines.md) for more details on this configuration.  

In 10.0.13, the Delivery Options module will also work for **Header charges without proration** assuming the workflow doesnt support a mixed mode of delivery in the cart.  This requires "XYZ" flag in backoffice to be turned on. 

If a shipping charge is configured as a Line charge, it will automatically appear on the cart line for each item.

Delivery options module requires a shipping address to determine the modes of delivery. If the shipping address is changed, the delivery options must be retrieved again. If the order includes only items that will be picked up in the store, this module is automatically hidden. 
     The following image shows an example of a delivery options module on a checkout page.
    ![Example of a delivery options module](./media/ecommerce-deliveryoptions.PNG)

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
