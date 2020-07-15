---

# required metadata

title: Store selector module
description: This topic covers the store selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 07/31/2020
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
[!include [banner](includes/preview-banner.md)]

This topic covers the store selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A store selector module is used to by customers to "pick up" a product in a selected store after an online purchase. In Commerce version 10.0.13, the store selector module also includes additional capabilities that can showcase a "Find a Store" page that displays nearby stores.

The store selector module allows users to enter a location (city, state, address, etc.) to search for stores within a search radius. When the module is initially launched, it uses the customer's browser location (if consent is provided) as the initial location to find stores.

## Store selector module usage in e-Commerce

- A store selector module can be used on a product details page (PDP) to select a store for pickup.
- A store selector module can be used on a cart page to select a store for pickup.
- A store selector module can be used on a standalone page that shows all available stores.

## Bing Maps integration

The store selector module is integrated with the [Bing Maps REST APIs](https://docs.microsoft.com/bingmaps/rest-services/) to use Bing's Geocoding and Autosuggest features. A Bing Maps application programming interface (API) key is required and must be added to the shared parameters page in Commerce headquarters. The Geocoding API is used to convert a location to latitude and longitude. The Autosuggest API integration is used to show search suggestions when users enter locations into the search box.

For the Autosuggest REST API, you must ensure that the following URLs are allowed (also know as "whitelisted") per your site's content security policy (CSP). This is done in Commerce site builder by adding allowed URLs to various site CSP directives (for example, **img-src**). For more information, see [Content security policy](manage-csp.md). 

- To the **connect-src** directive, add &#42;.bing.com.
- To the **img-src** directive, add &#42;.virtualearth.net.
- To the **script-src** directive, add &#42;.bing.com, &#42;.virtualearth.net.
- To the **script style-src** directive, add &#42;.bing.com.
 
## "Pickup in store" mode

The store selector module supports a "Pick up in store" mode that displays a list of stores where a product is available for pickup, as well as store hours and product inventory for each store. The store selector module requires the context of a product so it can render product availability and allow the user to add the product to the cart with the delivery mode set to "pickup" at the selected store. For more information, see [Inventory settings](inventory-settings.md). 

The store selector module can be added to a buy box module on a PDP to display stores where a product is available for pickup. It can also be added to a cart module, where the store selector module displays pickup options for each cart line item. The store selector can also be added to other pages or modules via extensions and customizations.

For this scenario to work, products should be configured with the "pickup" delivery mode. Otherwise, the module will not be shown on the respective product pages. For more information on how to configure the delivery mode, see [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

The following image shows an example of a store selector module used on a PDP.

![Example of a store selector module](./media/BOPIS.PNG)

## "Find stores" mode

The store selector module also supports a "Find stores" mode which can be used to create a store locations page that can render available stores and their information. It operates without product context in this mode and can be used as a standalone module on any site page. In addition, a store can be selected as a preferred store if the relevant settings are turned on for the module. When a store is selected as the preferred store, the store ID is maintained in the browser cookie and requires the user to accept the cookie consent message.

The following image shows an example of a store selector module used on a store locations page along with a map module.

![Example of a store selector module](./media/ecommerce-Storelocator.PNG)

## Render a map

The module can be used with the map module to render the store locations visually on a map. For more information on the map module, see [Map module](add-map-module.md)

## Store selector module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading| Text | Heading for the module |
| Mode | Find stores, Pick up in store.| "Find stores" mode displays available stores. "Pick up in store" mode allows users to select a store for pickup. |
| Style | Dialog, Inline| The module can rendered either inline or in a dialog box.|
| Set as preferred store | True, False | When set to "True," this property allows users to set a preferred store. This feature requires the user to accept the cookie consent messaging. |
| Show all stores | True, False | When set to "True," this property shows an option for the shopper to bypass the search radius property and view all stores. |
| Autosuggest options: Max results | Number| Defines the maximum number of autosuggest results to render via the Bing Autosuggest API. |
| Search radius | Number | Defines the search radius for stores, in miles. If no value is specified, the default search radius of 50 miles is used.|
| Terms of service | URL |  This property specifies the terms of service URL that is required to use the Bing Maps service. |

## Add a store selector module to a page

For "pick up in store" mode, the module can only be used on PDP and cart pages. In addition, you must set the **Mode as Pick up in store** in the module's property pane.
- For information on how to add a store selector module to a buy box module, see [Buy box module](add-buy-box.md). 
- For information on how to add a store selector module to a cart module, see [Cart module](add-cart-module.md)

To configure the store selector module to display available stores for a store locations page as in the example image above, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New Template** dialog box, under **Template name**, enter **Marketing template**, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select the **Marketing template** template. Under **Page name**, enter **Store locations**, and then select **OK**.
1. In the **Main** slot of the new page, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container with 2 columns** module, and then select **OK**.
1. In the module's properties pane, set the **Width** value to **Fill Container**.
1. Set the **X-Small view port column configuration** value to **100%**.
1. Set the **Small view port column configuration** value to **100%**.
1. Set the **Medium view port column configuration** value to **33% 67%**.
1. Set the **Large view port column configuration** value to **33% 67%**.
1. In the **Container with 2 columns** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Store selector** module, and then select **OK**.
1. In the module's properties pane, set the **Mode** value to **Find stores**.
1. In the module's properties pane, set the **Search radius** value in miles.
1. In the module's properties pane, set other properties such as **Set as preferred store**, **View all stores**, and **Autosuggest options** as needed.
1. In the **Container with 2 columns** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Map** module, and then select **OK**.
1. In the module's properties pane, set any additional properties as needed.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
 
## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Quick tour of PDP](quick-tour-pdp.md)

[Quick tour of cart and checkout](quick-tour-cart-checkout.md)

[Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)

[Manage Bing Maps for your organization](dev-itpro/manage-bing-maps.md)

[Bing Maps REST APIs](https://docs.microsoft.com/bingmaps/rest-services/)

[Maps module](add-map-module.md)
