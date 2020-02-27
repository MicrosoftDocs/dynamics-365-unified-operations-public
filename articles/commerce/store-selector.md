---

# required metadata

title: Store selector module
description: This topic covers the store selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 02/27/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology:

# optional metadata
# ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt\_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
ms.search.industry:
ms.author: anupamar
ms.search.validFrom: 2020-02-10
ms.dyn365.ops.version:

---

# Store selector module

[!include [banner](includes/banner.md)]

This topic covers the store selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A store selector module is used for the "buy online, pick up in store"" (BOPIS) customer scenario. It displays a list of stores where a product is available for pickup, as well as store hours and product inventory for each store.

The store selector module requires the context of a product and a search location to find stores. In the absence of a search location, it defaults to the customer's browser location, provided that the customer gives consent. The module has an input box which allows the customer to enter a location (zipcode, or city and state) to find stores that are nearby.

The store selector module is integrated with the Bing Maps Geocoding application programming interface (API) to convert the location to a latitude and longitude. A Bing Maps API key is required and must be added to the Commerce shared parameters page in Dynamics 365 Commerce.

The store selector module can be added to a buy box module on the product details page (PDP) to display stores where a product is available for pickup. It can also be added to a cart module. When added to a cart module, the store selector module displays pickup options for each cart line item. In addition, with custom coding this module can be added to other pages or modules via extensions and customizations.

For the BOPIS scenario to work, products should be configured with the "customer pickup" delivery mode. Otherwise, the module will not be shown on the respective pages. For details on how to configure the delivery mode, see [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

The following image shows an example of a store selector module used on a PDP.

![Example of a store selector module](./media/BOPIS.PNG)

## Store selector module usage in e-Commerce

- A store selector module can be used on a product details page (PDP) to find nearby stores where a product is available for pickup.
- A store selector module can be used on a cart page to find nearby stores where a product in the cart is available for pickup.

## Store selector module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Search radius | Number | Defines the search radius for stores, in miles. If no value is specified, the default search radius of 50 miles is used.|
|Terms of Service | URL    |  The terms of service URL that is required for the Bing Maps service. |

## Add a store selector module to a page

To add a store selector module to a page, follow these steps.

1.
1.
1.
1.
1.
1.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buybox.md)

[Cart module](add-cart.md)

[Quick tour of PDP](quick-tour-pdp.md)

[Quick tour of Cart and checkout](quick-tour-cart-checkout.md)

[Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)
