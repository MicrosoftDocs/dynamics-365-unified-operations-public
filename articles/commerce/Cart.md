---
# required metadata

title: Cart
description: This topic reviews setting up a Cart module in a Dynamics 365 e-Commerce page.
author: anupamar-ms
manager: BrendanSullivanMSFT
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---

# Cart 

Cart module is container that is used for hosting all the necessary modules that are needed to showcase the items in the Cart. For instance, it includes all the items added to the cart, order summary, promo codes etc.  

Cart module renders data based on the Cart id which is a browser cookie that is available throughout the site. 

## Properties of Cart 

As a container, Cart provides some basic properties such as Heading and Width. Heading is typically “Shopping bag” “Your cart” “Items in your cart” etc.  Width allows the modules inside this container to fit within or full screen. See container for more details on Width property.  

Cart is divided into multiple regions – Cart line items, Order summary and checkout, Find in Store. Each region maps to a slot. Every slot has a predefined set of modules that it accepts as input.  

## Modules available in Cart 

**Cart line items**: It displays a summary of each item added to cart. This includes product title, dimensions selected, price, quantity, discounts etc. It also supports actions such as Remove from cart and Add to wishlist. On each line item, there is an option to ship or pick up from store but this has to be configured separately see below 

**Order summary:** This represents the order summary in terms of Subtotal, Shipping, Taxes, Savings etc. A heading can be configured for this module. 

**Promo code:** This module allows the user to redeem promo codes. The promo code can be applied or removed.  

**Checkout**: This initiates the checkout action and redirects the user to the checkout page. There are 3 links that need to be configured for this module - Checkout link, Guest Checkout link, Back to Shopping link. Checkout link enforces sign-in if the user is not already signed-in. Guest Checkout link allows anonymous user to place an order and is shown only when the user is not signed in. Back to Shopping link allows the user to navigate to home page or any other page to continue the shopping journey. 

**Content rich block:** Cart container allows content rich block to support custom CMS driven messaging.  Any message can be added. For Cart, an example “For issues with the order, contact 1-800-Fabrikam”.    

**Pick up in store:** This module shows the list of nearby stores where an item is available for pickup. When this module is invoked, it shows the stores available within 50 mile radius of the user’s location. This search radius is configurable in the module as part of the site authoring. For each store, if inventory check is enabled, the inventory check is done and an appropriate in-stock or out-of-stock message is shown. 

**Store search by Bing Maps:** This is store search module that is available inside the Pick up in Store module. It allows user to input a location to search for stores. This module uses the Bing Maps Geocoding APIs to convert the user inputted location to a latitude/longitude. In the absence of this module, only stores in the user’s current location will be listed and the user cannot search for another location.  

## Retail Server interaction 

Cart retrieves product information using Retail Server APIs. Using the cart id from the browser cookie all the information is retrieved from Retail server.

## AppSettings 

Cart uses three settings that are defined in the App Settings 

- Maximum quantity: This is the maximum number of items that can be added to the cart per item. E.g. a retailer may decide to support only 10 of each product to be sold in a single transaction. Cart line module allows a shopper to modify the quantity of items inline. This quantity should respect the maximum quantity setting.   
- Inventory check:  When this is true, every time the Cart module is loaded, all items in Cart have to be checked to make sure they are in stock. Alternatively, it can be set to false if the retailer does not want to do inventory check before placing an order 

- Inventory buffer: Inventory is real-time and with many people making orders via multiple channels its hard to stay accurate. When doing inventory check, if the inventory is less than the buffer its treated as out-of-stock. This done to reduce the chances of selling an item when its out of stock but inventory count has not fully updated due to fast sales through several channels.  

## Authoring a Cart 

This section explains how to add a cart module to a new page and set the required properties.  

1. In tooling, create a new fragment “Cart fragment”.  

2. Add Cart module
3. In the Cart line items slot, add Cart line items module 
4. In the Order summary and promo code module, add promo code and order summary module 

5. In the Checkout slot, add the Checkout module. [TBD Checkout configuration] 

6. In the Find in Store slot, add the Pick up in Store module 

7. In the Pick up in Store module, select the store search slot and add the Store search by Bing Maps module 

8. Check-in and Publish.  

9. Now create a new template and add the Cart fragment to it

10. Create a page with the newly added template




