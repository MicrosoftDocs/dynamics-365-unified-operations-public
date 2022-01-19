---
# required metadata

title: Core data actions
description: This topic covers the list of core data actions that are included with the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
ms.date: 01/19/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Core data actions

[!include [banner](../includes/banner.md)]

This topic covers the list of core data actions that are included with the Microsoft Dynamics 365 Commerce online software development kit (SDK). 

You can find most of the core data actions in the **\\node\_modules\\@msdyn365-commerce-modules** and **\\node\_modules\\@msdyn365-commerce** directories. Many core data actions can be found under the **\\node\_modules\\@msdyn365-commerce-modules\\retail-actions\\dist\\lib** directory, and some core data actions can be found within specific related subdirectories, like for example the cart state data actions which can be found under the **\\node\_modules\\@msdyn365-commerce\\global-state\\src\\cart-state** directory.

> [!NOTE] 
> All core data actions are observable data actions that are wrapped in an **AsyncResult** class.

Data action| Description
--- | --- 
add-address | Add a new address to an existing customer.
checkout | Initiate checkout for an order.
delete-address | Delete an existing customer address.
generic-data-action | A sample data action.
get-active-cart | Get the active cart, or create an active cart if none exists.
get-address | Return a list of customer addresses.
get-card-payment-accept-point | Return card payment information.
get-categories | Return a list of product categories.
get-categories-hierarchy | Return a list of product categories as a hierarchy.
get-checkout-cart | Return information about the current checkout cart.
get-current-category | Return a category hierarchy for a given category ID.
get-customer | Return customer information for a given customer account number.
get-customer-loyalty-cards | Return a list of loyalty cards for a given customer.
get-dimensions-for-selected-variant | Return a list of available product dimensions for a given product variant.
get-full-products | Get detailed product information, including prices and ratings, for a product.
get-full-products-by-category | Get detailed product information for the products in a specific category.
get-full-products-by-refine-search-category | Get detailed product information for a category when refiners are applied.
get-full-products-by-refine-search-text | Get detailed product information, based on a given search term, when refiners are applied.
get-full-products-search-by-text | Get detailed product information, based on a given search term.
get-list | Return a list of products.
get-order-history | Return a list of past orders for a customer.
get-org-unit-configuration | Return organizational unit information.
get-products-by-category | Return a list of products for a specific category.
get-recommendations | Return a list of product recommendations.
get-refiners-by-category | Return a list of applicable refiners for a given category.
get-refiners-by-text | Return a list of applicable refiners for a given text search term.
get-related-products | Return a list of related products.
get-selected-variant | Return a specific variant for a given product.
get-simple-products | Return a list of products together with basic information for a list of product IDs.
get-wishlist-by-customer-id | Return a customer's wish list.
refine-search-by-category | Return a list of products, based on the selected category.
search-org-unit-locations | Return a list of store locations.
update-address | Update an existing customer address.
update-line-delivery-specifications | Update delivery information for line items in the cart.
update-primary-address | Update a customer's primary address.

## Additional resources

[Data actions overview](data-actions.md)

[Data action cache options](data-action-cache.md)

[Test data actions with mocks](test-data-action-mocks.md)

[Page load data actions](page-load-data-action.md)

[Event-based data actions](event-based-data-actions.md)

[Call Retail Server APIs](call-retail-server-apis.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
