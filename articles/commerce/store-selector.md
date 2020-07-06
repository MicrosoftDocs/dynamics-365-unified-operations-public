---

# required metadata

title: Store selector module
description: This topic covers the store selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 03/19/2020
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

A store selector module is used to "Pick-up" a product in a selected store. In 10.0.13, the module includes additional capabilities that allow it to showcase a "Find a Store" page to display available stores.  In this topic, we will discuss how the module can be used in both modes.

The Store selector module allows the user to input a location (city, state, address etc) to search for stores within a search radius. When the module is launched initially, it uses the customer's browser location (if consent is provided) as the initial location to find stores.

## Store selector module usage in e-Commerce

- A store selector module can be used on a product details page (PDP) to choose a store for pickup
- A store selector module can be used on a cart page to select a store for pickup
- A store selector module can be used on a stand-alone page that shows all available stores 

## Bing Maps integration
The store selector module is integrated with the [Bing Maps REST APIs](https://docs.microsoft.com/en-us/bingmaps/rest-services/) for Geocoding and Autosuggest. A Bing Maps API key is required and must be added to the Commerce shared parameters page in Dynamics 365 Commerce. Geocoding application programming interface (API) is used to convert the  location to a latitude and longitude. The Autosuggest API integration is used to show search suggestions as the user types a location on the input box.

For the Auto-suggest REST API, you need to ensure the following URLs are whitelisted per [Content security policy](manage-csp.md). 
1.To connect-src add *.bing.com
1. To img-src add *.virtualearth.net
1. To script-src add *.bing.com, *.virtualearth.net
1. To script style-src add *.bing.com


## Buy online pick-up in store
The Store selector supports a "Pick-up in store" mode. In this mode, it displays a list of stores where a product is available for pickup, as well as store hours and product inventory for each store in the pick-up mode. Here it requires the context of a product so it can render product availabilty and allow the user to add the product to cart with delivery mode set to pickup at the selected store. For more details on Inventory settings, refer to [Inventory settings](inventory-settings.md). 

The store selector module can be added to a buy box module on the product details page (PDP) to display stores where a product is available for pickup. It can also be added to a cart module. When added to a cart module, the store selector module displays pickup options for each cart line item. In addition, this module can be added to other pages or modules via extensions and customizations.

For this scenario to work, products should be configured with the "Pickup" delivery mode. Otherwise, the module will not be shown on the respective product pages. For details on how to configure the delivery mode, see [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).


The following image shows an example of a store selector module used on a PDP.

![Example of a store selector module](./media/BOPIS.PNG)

## Find a store
The Store selector module supports a "Find stores" mod which can be used to create a "Store locations" page. The page can  render available stores and their information. It operates without product context in this mode and can be used stand-alone on any page. In addition, a store can be selected as a preferred store if the relevant settings are turned on for the module.

The following image shows an example of a store selector module used on a Store locations page along with Map module [Maps module](add-maps-module.md).

![Example of a store selector module](./media/ecommerce-Storelocator.PNG)

## Showing a map
The module can be used with the Map module to render the store locations visually on a map. For more details on this module, refer to [Maps module](add-maps-module.md)


## Store selector module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading| Text| Heading for the module|
| Mode| Find stores, Pick up in store| Find stores, displays stores available. Pick up in store, allows user to select a store for pickup|
| Style| Dialog, Inline| The module can rendered inline or shown in a dialog|
| Set as preferred store| True or False| When true, it allows the user to set a store as a preferred store for their shopping experience|
| Show all stores | True or False| When true, it shows an option for the shopper to view all stores ignoring the search radius|
|Auto-suggest options - Max results| Number| It can be used to define the maximum number of auto-suggest results to render via Bing Auto-suggest API|
| Search radius | Number | Defines the search radius for stores, in miles. If no value is specified, the default search radius of 50 miles is used.|
|Terms of Service | URL    |  The terms of service URL that is required for the Bing Maps service. |


## Add a store selector module to a page

For pick-up in store, the module can be used only on PDP and Cart. In addtion, you must set the **Mode as Pick up in store** in the module property panel.
- For information on how to add a store selector module to a buy box module, see [Buy box module](add-buy-box.md). 
- For information on how to add a store selector module to a cart module, see [Cart module](add-cart-module.md)

To use the module to display available stores for a Store locations page, follow the below steps
 1. Go to **Templates**, and create a page template that is named **Marketing template**.
1. In the **Main** slot of the default page, dont add any modules.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Create a new page **Store locations** using the Marketing template.
1. Add a **Container with 2 columns** and set Width=Fill Container
1. To acheive the look shown in the example above, set the X-Small and Small view port to 100%, set the Medium and Large view ports to 33% 67% width on the container.
1. Add a Store selector module to the first column in container.
1. In module property panel, set Mode=Find stores and set Style=Inline
1. In module property panel, set other options "Set as preferred store" or "View all stores" or "Auto-suggest options" as needed
1. In module property panel, set Search radius in miles
1. Add a Maps module to the second column in  container.
1. In the Maps module property panel set any additional properties as needed.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
 
## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Quick tour of PDP](quick-tour-pdp.md)

[Quick tour of Cart and checkout](quick-tour-cart-checkout.md)

[Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)

[Manage Bing Maps for your organization](dev-itpro/manage-bing-maps.md)

[Bing Maps REST APIs](https://docs.microsoft.com/en-us/bingmaps/rest-services/)

[Maps module](add-maps-module.md)
