---

# required metadata

title: Map module
description: This topic covers map modules and describes how to configure them in Microsoft Dynamics 365 Commerce.
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

# Map module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers map modules and describes how to configure them in Microsoft Dynamics 365 Commerce.

## Overview

A map module visually displays the location of stores on an interactive map, using the [Bing Maps V8 Web Control](https://docs.microsoft.com/bingmaps/v8-web-control/) to render maps. A Bing Maps API key is required and must be added to the shared parameters page in Commerce headquarters. Map modules provide different views such as Road, Aerial, and Streetside that users can select to view map locations, and also allows interactions such as zooming and user location.

A map module works in conjunction with the store selector module to determine the geographic locations of stores that need to be rendered on a map. Store selector and map modules interact with each other when a user selects a store in either of these modules on a site page. Map modules can be extended for other scenarios outside of store selector interaction but this requires module customization.

The map module was introduced in Commerce version 10.0.13.

The following image shows an example of a map module used on a store locations page.

![Example of a store selector module](./media/ecommerce-Storelocator.PNG)

## Module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading| Text| The heading for the module. |
| Pushpin options: Default icon | Image | The pushpin icon image to use for stores shown on a map. |
| Pushpin options: Active icon | Image | The pushpin icon image to use for a store that is selected on a map. |
| Pushpin options: Default icon color| Character string  |Text or hexadecimal value for the color of pushpin icons on a map. |
| Pushpin options: Active icon color| Character string | Text or hexadecimal value for the color of selected pushpin icons on a map. |
| Show index | True/False  | If set to "True," pushpin icons that indicate a store will display an index that matches the index on the list view displayed by the store selector module. |

## Add allowed mapping URLS to site content security policy (CSP) directives

For the maps module to interact with the Bing Maps, you must ensure that the following mapping URLs are allowed (otherwise known as "whitelisted") per your site's content security policy (CSP). This is done in Commerce site builder by adding allowed URLs to various site CSP directives (for example, **img-src**). For more information, see [Content security policy](manage-csp.md). 

- To the **connect-src** directive, add &#42;.bing.com.
- To the **img-src** directive, add &#42;.virtualearth.net.
- To the **script-src** directive, add &#42;.bing.com, &#42;.virtualearth.net.
- To the **script style-src** directive, add &#42;.bing.com.

## Add a map module to a page

For details on how to configure a map module on a page, see [Store selector module](store-selector.md). 
 
## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Store selector module](store-selector.md)

[Manage Bing Maps for your organization](./dev-itpro/manage-bing-maps.md)

[Bing Maps V8 Web Control](https://docs.microsoft.com/bingmaps/v8-web-control/)



