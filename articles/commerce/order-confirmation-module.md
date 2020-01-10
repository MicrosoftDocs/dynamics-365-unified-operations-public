---
# required metadata

title: Order details module
description: This topic covers order details modules and describes how to use them in Microsoft Dynamics 365 Commerce.
author: anupamar
manager: annbe
ms.date: 10/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations

# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar-ms
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Order details module

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers order details modules and describes how to use them in Microsoft Dynamics 365 Commerce.

## Overview

The order details module is used to display order confirmation details after the placement of an order. It shows the order confirmation ID, order contact information, and other order details such as items purchased, payment information, and shipping method.


## Order confirmation module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Heading       | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | The order confirmation module can have a heading. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |
|Contact number| Text| A contact number can be provided for order-related questions.|

## Modules that can be used on an order details page  

When creating an order details page, in addition to the order details module you can add other relevant modules to the page such as the following.

- **Recommendations module** – The recommendations module can be added to the order details page to suggest other products to the customer.
- **Marketing modules** – Any marketing module can be added to to the order details page to display marketing content.

## Create an order details page module

1. Create a page template that is named **Order details template**.
1. In the **Main** slot of the default page, add an order details module.
1. In the order details module, add a recommendations module.
1. Save and preview the template. The order details module will not be rendered, because it requires the context of the order confirmation number.
1. Check in the template, and publish it.
1. Use the order details template that you just created to create a page that is named **order details page**.
1. Add the default page to the page outline.
1. In the **Header** slot, add a header fragment.
1. In the **Footer** slot, add a footer fragment.
1. In the **Main** slot, add an order details module.
1. In the property pane of the order details module, add the heading **Order details**.
1. Below the order details module, add a recommendations module, and configure it so that it uses the **New** and **Best Selling** settings.
1. Save and preview the page, check it in, and publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
