---
# required metadata

title: Core data actions
description: This topic covers the list of core Data Actions included with the Dynamics 365 Commerce E-Commerce SDK. 
author: SamJarawan
manager: JeffBl
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
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Core data actions

This topic covers the list of core data actions included with the Dynamics 365 Commerce Online SDK.  All core data actions can be found in the `\node_modules\@msdyn365-commerce-modules\retail-actions\dist\lib` directory.

Note: All core data actions are Observable data actions, which return the result specified below, wrapped in an AsyncResult.

Data Action| Description
--- | --- 
add-address |  Adds a new address to an existing customer
checkout | Initiates a Retail order check out
delete-address | Deletes an existing customer address
generic-data-action | Sample data action
get-active-cart | Gets the active cart (or creates one if none exist)
get-address | Returns a list of customer addresses
get-card-payment-accept-point | Return card payment information
get-categories | Returns a list of Retail product categories
get-categories-hierarchy | Returns a list of Retail product categories as a hierarchy
get-checkout-cart | Returns the current checkout cart information
get-current-category | Returns a category hierarchy for a given category Id
get-customer | Returns customer information for a given customer account number
get-customer-loyalty-cards | Returns a list of loyalty cards for a given customer
get-dimensions-for-selected-variant | Returns a list of available product dimensions for given product variant
get-full-products | Get detailed product information for a product including prices and ratings
get-full-products-by-category | Get detailed product information for products in a specific category
get-full-products-by-refine-search-category | Get detailed product information for a category with refinements applied
get-full-products-by-refine-search-text | Get detailed product information back given a search term and refinements applied
get-full-products-search-by-text | Get detailed product information back given a search term
get-list | Returns a list of products
get-order-history | Returns a list of past orders for a customer
get-org-unit-configuration | Returns organization unit information
get-products-by-category | Returns a list of products for a specific category
get-recommendations | Returns a list of product recommendations
get-refiners-by-category | Returns a list of applicable refiners for a given category
get-refiners-by-text | Returns a list of applicable refiners for a given text search term
get-related-products | Returns a list of related products
get-selected-variant | Returns a specific variant for a given product
get-simple-products | Returns a list of products with basic information for a list of product Ids
get-wishlist-by-customer-id | Returns a customer's wish list
refine-search-by-category | Returns a list of products based on selected category
search-org-unit-locations | Returns a list of retail store locations
update-address | Update an existing customer address
update-line-delivery-specifications | Update delivery information for line items in the cart
update-primary-address | Update a customer's primary address
