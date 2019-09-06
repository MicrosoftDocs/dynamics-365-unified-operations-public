---
# required metadata

title: Add a cart module to a page
description: This topic covers cart modules and how to add them to site pages in Dynamics 365 Commerce.
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

This topic covers cart modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

A cart module is container that is used for hosting all the necessary modules that are needed to showcase items in the cart. For example, it includes all the items added to the cart, the order summary, and promo codes.  

The cart module renders data based on the cart ID which is a browser cookie that is available throughout the site. 

## Cart module properties and slots

As a container, a cart module controls some basic properties such as "heading" and "width." Heading values are typically text values such as "Shopping bag," "Your cart," or "Items in your cart." Width allows the modules inside the container to fit within the container or fill the screen.

The cart page is divided into multiple regions: cart line items, order summary and checkout, and "find in store" functionality. Each region maps to a slot in the cart module, and every slot has a predefined set of modules that it accepts as input.  

## Modules available for use in a cart module 

**Cart line items:** The cart line items module displays a summary of each item added to cart. This includes product title, dimensions selected, price, quantity, discounts, etc. It also supports actions such as "remove from cart" and "add to wish list." On each line item, there is an option to ship or pick up from store that must be configured separately in the pick up in store module below.

**Order summary:** The order summary module displays order summary such as subtotal, shipping, taxes, and savings. A heading can be configured for this module. 

**Promo code:** The promo code module enables the customer to redeem promo codes. The promo code can be applied or removed.  

**Checkout:** The checkout module initiates the checkout action and redirects the user to the checkout page. There are three links that need to be configured for this module: the checkout link, guest checkout link, and back to shopping link. The checkout link enforces sign in if the customer is not already signed in. The guest checkout link allows an anonymous customer to place an order and is shown only when a customer is not signed in. The back to shopping link allows the user to navigate to the home page or any other page to continue their shopping journey. 

**Content rich block:** The content rich block module supports custom CMS driven messaging in the cart module. Any message can be added, for example "For issues with the order, contact 1-800-Fabrikam."    

**Pick up in store:** The pick up in store module shows a list of nearby stores where an item is available for pickup. When this module is invoked, by default it shows the stores available within 50 mile radius of the customer's location, although the search radius can be customized in the module. For each store, if inventory check is enabled, the inventory check is done and an appropriate in-stock or out-of-stock message is shown. 

**Store search by Bing Maps:** This store search module enables a customer to input a location to search for a stores, and is available for use inside the pick up in store module. This module uses the Bing Maps geocoding APIs to convert the customer-inputted location to a latitude and longitude. In the absence of this module, only stores in the customer's current location will be listed and the customer cannot search for another location.

## Retail Server interaction 

The cart module retrieves product information using retail server APIs. Using the cart ID from the browser cookie, all the product information is retrieved from retail server.

## Cart module settings

Cart modules have three configurable settings, as follows. 

- **Maximum quantity:** This is the maximum number of items that can be added to the cart per item. For example, a retailer may decide to allow only 10 of each product to be sold in a single transaction.   
- **Inventory check:**  When this is set to True, the buy box module will ensure that the item is in stock before adding it to the cart (for both the ship to home or pick up in store scenarios). If set to False, an inventory check will not be done before adding a product to the cart and placing an order.
- **Inventory buffer:** Inventory is maintained in real time, and with many customers making orders it's difficult to maintain an accurate inventory count. For this reason, a buffer can be defined for inventory. When doing an inventory check, if the inventory is less than the buffer amount, the product is treated as out-of-stock. This reduces the chances of selling an item when it is out of stock but inventory count has not fully synchronized due to fast sales through several channels.  

## Add a cart module to a page 

To add a cart module to a new page and set the required properties, do the following.  

1. Create a new fragment named "cart fragment" and add a cart module to it. 
1. In the **Cart line items** slot of the cart module, add a cart line items module. 
1. In the **Order summary** slot, add an order summary module. 
1. In the **Promo code** slot, add a promo code module. 
1. In the **Checkout** slot, add a checkout module. 
1. In the **Find in Store** slot, add a pick up in store module. 
1. In the pick up in store module, select the store search slot and add the **Store search by Bing Maps** module. 
1. Check in and publish the fragment.  
1. Create a new template named "cart template" and add the cart fragment you created to it.
1. Save, check in, and publish the template.
1. Create a page using the new template.
1. Save and preview the page.
1. Check in and publish the page.
