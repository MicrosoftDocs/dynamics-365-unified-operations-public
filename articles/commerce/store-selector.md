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

Customers can use the store selector module to pick up a product in a selected store after an online purchase. In Commerce version 10.0.13, the store selector module also includes additional capabilities that can showcase a **Find a Store** page that shows nearby stores.

The store selector module lets users enter a location (city, state, address, and so on) to search for stores within a search radius. When the module is first opened, it uses the customer's browser location to find stores (if consent is provided).

## Store selector module usage in e-Commerce

- A store selector module can be used on a product details page (PDP) to select a store for pickup.
- A store selector module can be used on a cart page to select a store for pickup.
- A store selector module can be used on a standalone page that shows all available stores.

## Bing Maps integration

The store selector module is integrated with the [Bing Maps REST application programming interfaces (APIs)](https://docs.microsoft.com/bingmaps/rest-services/) to use Bing's Geocoding and Autosuggest features. A Bing Maps API key is required and must be added to the shared parameters page in Commerce headquarters. The Geocoding API is used to convert a location to latitude and longitude values. The integration with the Autosuggest API is used to show search suggestions when users enter locations in the search field.

For the Autosuggest REST API, you must ensure that the following URLs are allowed (also known as "whitelisted") per your site's content security policy (CSP). This setup is done in Commerce site builder, by adding allowed URLs to various CSP directives for the site (for example, **img-src**). For more information, see [Content security policy](manage-csp.md). 

- To the **connect-src** directive, add **&#42;.bing.com**.
- To the **img-src** directive, add **&#42;.virtualearth.net**.
- To the **script-src** directive, **add &#42;.bing.com, &#42;.virtualearth.net**.
- To the **script style-src** directive, add **&#42;.bing.com**.
 
## Pickup in store mode

The store selector module supports a **Pick up in store** mode that shows a list of stores where a product is available for pickup. It also shows store hours and product inventory for each store in the list. The store selector module requires the context of a product to render product availability and to let the user add the product to the cart, if the product's delivery mode is set to **pickup** at the selected store. For more information, see [Inventory settings](inventory-settings.md). 

The store selector module can be added to a buy box module on a PDP to show stores where a product is available for pickup. It can also be added to a cart module. In this case, the store selector module shows pickup options for each line item in the cart. The store selector module can also be added to other pages or modules via extensions and customizations.

For this scenario to work, products should be configured so that the **pickup** delivery mode is used. Otherwise, the module won't be shown on the product pages. For more information about how to configure the delivery mode, see [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

The following image shows an example of a store selector module used on a PDP.

![Example of a store selector module](./media/BOPIS.PNG)

## Find stores mode

The store selector module also supports a **Find stores** mode. This mode can be used to create a store locations page that shows available stores and their information. In this mode, the store selector module works without product context and can be used as a standalone module on any site page. In addition, if the relevant settings are turned on for the module, users can select a store as their preferred store. When a store is selected as a user's preferred store, the store ID is maintained in the browser cookie. Therefore, the user must accept a cookie consent message.

The following illustration shows an example of a store selector module that is used together with a map module on a store locations page.

![Example of a store selector module](./media/ecommerce-Storelocator.PNG)

## Render a map

The store selector module can be used together with the map module to show the store locations on a map. For more information about the map module, see [Map module](map-module.md)

## Store selector module properties

| Property name | Value | Description |
|---------------|-------|-------------|
| Heading | Text | The heading for the module. |
| Mode | **Find stores** or **Pick up in store** | **Find stores** mode shows available stores. **Pick up in store** mode lets users select a store for pickup. |
| Style | **Dialog** or **Inline** | The module can be rendered either inline or in a dialog box. |
| Set as preferred store | **True** or **False** | When this property is set to **True**, users can set a preferred store. This feature requires that users accept a cookie consent message. |
| Show all stores | **True** or **False** | When this property is set to **True**, users can bypass the **Search radius** property and view all stores. |
| Autosuggest options: Max results | Number | This property defines the maximum number of autosuggest results that can be shown via the Bing Autosuggest API. |
| Search radius | Number | This property defines the search radius for stores, in miles. If no value is specified, the default search radius of 50 miles is used. |
| Terms of service | URL |  This property specifies the terms of service URL that is required to use the Bing Maps service. |

## Add a store selector module to a page

For **Pickup in store** mode, the module can be used only on PDPs and cart pages. You must set the mode to **Pickup in store** in the module's property pane.

- For information on how to add a store selector module to a buy box module, see [Buy box module](add-buy-box.md). 
- For information on how to add a store selector module to a cart module, see [Cart module](add-cart-module.md)

To configure the store selector module to show available stores for a store locations page, as in the illustration that appears earlier in this topic, follow these steps.

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
1. Set the **Search radius** value in miles.
1. Set other properties, such as **Set as preferred store**, **Show all stores**, and **Enable auto suggestion**, as you require.
1. In the **Container with 2 columns** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Map** module, and then select **OK**.
1. In the module's properties pane, set any additional properties as you require.
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

[Maps module](map-module.md)
