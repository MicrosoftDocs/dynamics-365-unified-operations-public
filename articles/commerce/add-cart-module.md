---
# required metadata

title: Add a cart module to a page
description: This topic covers cart modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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

# Add a cart module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers cart modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A cart module is container that is used to host all the modules that are required to showcase items that are in the cart. For example, it includes all the items that have been added to the cart, the order summary, and promotional codes.

The cart module renders data based on the cart ID. The cart ID is a browser cookie that is available throughout the site.

## Cart module properties and slots

As a container, a cart module controls some basic properties, such as the heading and the width. The heading is typically text such as **Shopping bag**, **Your cart**, or **Items in your cart**. The width setting determines whether the modules inside the container must fit within that container, or whether they can fill the screen.

The cart page is divided into multiple regions: cart line items, order summary and checkout, and "find in store" functionality. Each region is mapped to a slot in the cart module, and every slot accepts a predefined set of modules.

## Modules that can be used in a cart module

- **Cart line items** – This module shows a summary of every item that has been added to the cart. The information includes the product title, selected dimensions, price, quantity, and discounts. This module also supports actions such as "remove from cart" and "add to wish list." For each line item, there is an option to ship the item or pick it up from the store. This option must be configured separately in the pick up in store module.
- **Order summary** – This module shows an order summary. The information includes the subtotal, shipping, taxes, and savings. A heading can be configured for this module.
- **Promo code** – This module lets the customer redeem promotional codes. A promotional code can be applied or removed.
- **Checkout** – This module initiates the checkout action and redirects the user to the checkout page. Three links must be configured for this module:

    - **Checkout** – This link forces customers to sign in if they aren't already signed in.
    - **Guest checkout** – This link lets anonymous customers place orders. It's shown only when customers aren't signed in.
    - **Back to shopping** – This link lets customers go to the home page or any other page, so that they can continue to shop.

- **Content rich block** – This module supports custom messaging in the cart module. The messages are driven by the content management system (CMS). Any message can be added, such as "For issues with the order, contact 1-800-Fabrikam."
- **Pick up in store** – This module shows a list of nearby stores where an item is available for pickup. By default, this module shows stores that are within a 50-mile radius of the customer's location. However, the search radius can be customized in the module. For each store, an inventory check is done, if the inventory check functionality is turned on, and an appropriate in-stock or out-of-stock message is shown.
- **Store search by Bing Maps** – This module can be used inside the pick up in store module. It lets customers search for stores by entering a location. The Bing Maps geocoding application programming interface (API) is used to convert the location that the customer entered to a latitude and a longitude. If this module isn't used, only stores that are near the customer's current location are shown, and the customer can't search for a different location.

## Cart module settings

Cart modules have three settings that can be configured:

- **Maximum quantity** – The maximum number of each item that can be added to the cart. For example, a retailer might decide that only 10 of each product can be sold in a single transaction.
- **Inventory check** – When the value is set to **True**, an item is added to the cart only after the buy box module makes sure that it's in stock. This inventory check is done both for scenarios where the item will be shipped and for scenarios where it will be picked up in the store. If the value is set to **False**, no inventory check is done before an item is added to the cart and the order is placed.
- **Inventory buffer** – Inventory is maintained in real time, and when many customers place orders, it can be difficult to maintain an accurate inventory count. Therefore, a buffer can be defined for inventory. When an inventory check is done, if the inventory is less than the buffer amount, the product is treated as out of stock. Therefore, when sales occur quickly through several channels, so that the inventory count isn't fully synced, there is less risk that an item that is out of stock will be sold.

## Retail Server interaction

The cart module retrieves product information by using Retail Server APIs. The cart ID from the browser cookie is used to retrieve all the product information from Retail Server.

## Add a cart module to a page

To add a cart module to a new page and set the required properties, follow these steps.

1. Create a fragment that is named **cart fragment**, and add a cart module to it.
1. In the **Cart line items** slot of the cart module, add a cart line items module.
1. In the **Order summary** slot, add an order summary module.
1. In the **Promo code** slot, add a promo code module.
1. In the **Checkout** slot, add a checkout module.
1. In the **Find in Store** slot, add a pick up in store module.
1. In the pick up in store module, select the **Store search** slot, and add a store search by Bing Maps module.
1. Check in the fragment, and publish it.
1. Create a template that is named **cart template**, and add the cart fragment that you just created to it.
1. Save the template, check it in, and publish it.
1. Create a page that uses the new template.
1. Save and preview the page.
1. Check in the page, and publish it.
