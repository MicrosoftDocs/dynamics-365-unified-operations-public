---
# required metadata

title: Sell and return outside of assortments
description: Ability for retailers to sell and return products outside of assortments.
author: prabhu-padhi
manager: AnnBe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope:
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: prabhup
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: 

---

# Sell and return outside of assortment
One of the most common scenarios for any retailers is the ability to sell products to their customers or accept returns from their customers even if they don’t carry the products in their stores (that is, products are not assorted to the stores).

+ **Scenario-1:** Retailer doesn’t carry all its products in a specific store and the remaining are stored in the warehouse. The store associate can assist the customer by searching or browsing specific products from the warehouse, add them to the cart, and complete the checkout by selecting specific delivery methods (shipping to an address from the warehouse or letting the customer pick-up from the current store or from another store).
+ **Scenario-2:** Retailer doesn’t carry specific products in the store or do not have them in the stock, but they are available in other stores. The store associate can assist the customer by searching or browsing specific products from the other store, add them to the cart, and complete the checkout by selecting specific delivery methods (shipping to an address from the warehouse or letting the customer pick-up from the other store).
+ **Scenario-3:** Retailers who have many stores in and around specific cities/zip codes/etc. typically don’t want to force their customers to return specific products in a store that they purchased. Instead, they allow their customers to return products in any store independent of where they purchased the products.

This feature enables the following **capabilities**:
+ Search or Browse other store’s products
+ Search or Browse all products (aka released products)
+ Create cash-and-carry transaction or customer order
+ If customer order, then select delivery options (ship to an address from the warehouse, or pick-up from current store or another store)
+ Pick-up products from current store or another store
+ Cancel order in current store or another store
+ Return order (with or without receipt) in current store or another store
