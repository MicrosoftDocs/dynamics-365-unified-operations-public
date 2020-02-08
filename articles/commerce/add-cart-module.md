---
# required metadata

title: Cart module
description: This topic covers cart modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 01/23/2020
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
ms.dyn365.ops.version: Release 10.0.5

---

# Cart module


[!include [banner](includes/banner.md)]

This topic covers cart modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A cart module is used to show the items that have been added to the cart before the customer proceeds to checkout. For example, it includes all the items that have been added to the cart and an order summary. It also lets the customer apply or remove promotional codes.

The cart module supports signed-in checkout and guest checkout. It also supports a **Back to shopping** link. You can configure the route for this link at **Site Settings \> Extensions \> Routes**.

The cart module renders data based on the cart ID. The cart ID is a browser cookie that is available throughout the site.

## Cart module properties and slots

The cart module has a **Heading** property that can be set to values such as **Shopping bag** and **Items in your cart**. 

## Modules that can be used in a cart module

- **Text block** – This module supports custom messaging in the cart module. The messages are driven by the content management system (CMS). Any message can be added, such as "For issues with your order, contact 1-800-Fabrikam."
- **Store selector** – This module shows a list of nearby stores where an item is available for pickup. It lets users enter a location to find stores that are nearby. The store selector module is integrated with the Bing Maps Geocoding application programming interface (API) to convert the location to a latitude and longitude. A Bing Maps API key is required and must be added to the Retail shared parameters page in Dynamics 365 Retail. This module supports two properties, **Search radius** and **Terms of service link**. The **Search radius** property defines the search radius for stores, in miles. If no value is specified, the default search radius, 50 miles, is used. If Bings Maps or any external service is used, the **Terms of service link** property can be used to provide a link to the terms of service. A terms of service link is required for the Bing Maps service. 

## Cart module settings

Cart modules have the following settings that can be configured at **Site Settings \> Extensions**:

- **Maximum quantity** – This property is used to specify the maximum number of each item that can be added to the cart. For example, a retailer might decide that only 10 of each product can be sold in a single transaction.
- **Inventory check** – When the value is set to **True**, an item is added to the cart only after the buy box module makes sure that it's in stock. This inventory check is done both for scenarios where the item will be shipped and for scenarios where it will be picked up in the store. If the value is set to **False**, no inventory check is done before an item is added to the cart and the order is placed.
- **Inventory buffer** – This property is used to specify a buffer number for inventory. Inventory is maintained in real time, and when many customers place orders, it can be difficult to maintain an accurate inventory count. When an inventory check is done, if the inventory is less than the buffer amount, the product is treated as out of stock. Therefore, when sales occur quickly through several channels, and the inventory count isn't fully synced, there is less risk that an item that is out of stock will be sold.
- **Back to shopping** – This property is used to specify the route for the **Back to shopping** link. This route can be configured at the site level. This configuration lets retailers take the customer back to the home page or any other page on the site.

## Commerce Scale Unit interaction

The cart module retrieves product information by using Commerce Scale Unit APIs. The cart ID from the browser cookie is used to retrieve all the product information from Commerce Scale Unit.

## Add a cart module to a page

To add a cart module to a new page and set the required properties, follow these steps.

1. Create a fragment that is named **Cart fragment**, and add a cart module to it.
1. Add a heading to the cart module.
1. Add a store selector module to the cart module.
1. Save the fragment, finish editing it, and publish it.
1. Create a template that is named **Cart template**, and add the cart fragment that you just created to it.
1. Save the template, finish editing it, and publish it.
1. Create a page that uses the new template.
1. Save and preview the page.
1. Finish editing the page, and publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
