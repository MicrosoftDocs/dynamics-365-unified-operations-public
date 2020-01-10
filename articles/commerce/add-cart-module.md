---
# required metadata

title: Cart module
description: This topic covers cart modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/31/2019
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

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers cart modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A cart module is used to display items that are added to the cart before a customer proceeds to checkout. For example, it includes all the items that have been added to the cart and an order summary. It also allows the customer to apply or remove promotional codes.

The cart module supports signed-in checkout and guest checkout, as well as a "Back to shopping" link. The route for the "Back to shopping" link can be configured in **Site Settings \> Extensions \> Routes**.

The cart module renders data based on the cart ID. The cart ID is a browser cookie that is available throughout the site.

## Cart module properties and slots

The cart module has a **Heading** property, which for example can be set to "Shopping bag," "Items in your cart," etc. 

## Modules that can be used in a cart module

- **Text block** – This module supports custom messaging in the cart module. The messages are driven by the content management system (CMS). Any message can be added, such as "For issues with the order, contact 1-800-Fabrikam."
- **Store selector** – This module shows a list of nearby stores where an item is available for pickup. The module allows the user to enter a location to find stores nearby. The store selector module is integrated with the Bing Maps Geocoding API to convert the location to a latitude and longitude. A Bing Maps API key is required and must be added to the Retail shared parameters page in Dynamics 365 Retail. This module supports two properties, **Search radius** and **Terms of service link**. The search radius property defines the search radius for stores in miles. It defaults to a 50 mile radius if a radius is not provided. If using Bings Maps or any external service, a terms of service link can be provided using the terms of service link property. A terms of service link is required for Bing Maps service.

## Cart module settings

Cart modules have the following settings that can be configured at **Site Settings \> Extensions**:

- **Maximum quantity** – This specifies the maximum number of each item that can be added to the cart. For example, a retailer might decide that only 10 of each product can be sold in a single transaction.
- **Inventory check** – When the value is set to **True**, an item is added to the cart only after the buy box module makes sure that it's in stock. This inventory check is done both for scenarios where the item will be shipped and for scenarios where it will be picked up in the store. If the value is set to **False**, no inventory check is done before an item is added to the cart and the order is placed.
- **Inventory buffer** – This specifies a buffer number for inventory. Inventory is maintained in real time, and when many customers place orders, it can be difficult to maintain an accurate inventory count. When an inventory check is done, if the inventory is less than the buffer amount, the product is treated as out of stock. Therefore, when sales occur quickly through several channels and the inventory count isn't fully synced, there is less risk that an item that is out of stock will be sold.
**Back to shopping** - The back to shopping route can be configured at the site level. This configuration allows retailers to take the customer back to the home page or any other page of the site.

## Retail Server interaction

The cart module retrieves product information by using Retail Server APIs. The cart ID from the browser cookie is used to retrieve all the product information from Retail Server.

## Add a cart module to a page

To add a cart module to a new page and set the required properties, follow these steps.

1. Create a fragment that is named **Cart fragment**, and add a cart module to it.
2. Add a heading to the cart module.
3. Add a **Store selector** module to the cart module.
4. Finish editing, save, and publish the fragment.
5. Create a template that is named **Cart template**, and add the cart fragment that you just created to it.
6. Save the template, check it in, and publish it.
7. Create a page that uses the new template.
8. Save and preview the page.
9. Check in the page, and publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
