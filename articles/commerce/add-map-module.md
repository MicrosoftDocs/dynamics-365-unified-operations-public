---

# required metadata

title: Map module
description: This topic covers map modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
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

This topic covers map modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A map module visually displays the location of stores on an interactive map, and uses the [Bing Maps V8 Web Control](https://docs.microsoft.com/bingmaps/v8-web-control/) to render maps. A Bing Maps API key is required and must be added to the Commerce shared parameters page in Dynamics 365 Commerce. The map module provides different views such as Road, Aerial, and Streetside that users can select to view map locations, and also allows interactions such as zooming and user location.

A map module works in conjunction with the store selector module to determine the geographic locations where stores need to be rendered on a map. Store selector and map modules interact with each other when a user selects a store on either of these modules. Map modules can be extended for other scenarios outside of store selector interaction but will require customization.

This module was introduced in Commerce version 10.0.13.

The following image shows an example of a map module used on a store locations page.

![Example of a store selector module](./media/ecommerce-Storelocator.PNG)


## Module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading| Text| Heading for the module|
|Pushpin options - Default icon|image | The icon to use for stores shown on the map|
|Pushpin options - Active icon|image | The icon to use for a store that is selected on the map|
|Pushpin options - Default icon color|string  |Text of HEX value for the color of the Active selected pushpin |
|Pushpin options - Active icon color|string | Text or HEX value for the color of the Active selected pushpin|
|Show index|True or false  | If true, the pushpins that indicate a store have an index that matches the index on the list view displayed by Store selector module|

## Content security policy

For the maps module to interact with the Bing Maps, you must ensure that the following URLs are allowed (otherwise known as whitelisted) per your site's [Content security policy](manage-csp.md). 

- To connect-src add &#42;.bing.com
- To img-src add &#42;.virtualearth.net
- To script-src add &#42;.bing.com, &#42;.virtualearth.net
- To script style-src add &#42;.bing.com

## Add a map module to a page

For details on how to configure a map module on a page, see [Store selector module](store-selector.md). 
 
## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Store selector module](store-selector.md)

[Manage Bing Maps for your organization](./dev-itpro/manage-bing-maps.md)

[Bing Maps V8 Web Control](https://docs.microsoft.com/bingmaps/v8-web-control/)



