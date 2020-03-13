---
# required metadata

title: Header module
description: This topic covers header modules and describes how to create page headers in Microsoft Dynamics 365 Commerce.
author: anupamar
manager: annbe
ms.date: 01/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar-ms
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Header module


[!include [banner](includes/banner.md)]

This topic covers header modules and describes how to create page headers in Microsoft Dynamics 365 Commerce.

## Overview

In Dynamics 365 Commerce, a page header comprises multiple modules, such as the header, navigation menu, search, promo banner, and cookie consent modules. 

The header module includes a site logo, links to the navigation hierarchy, links to other pages on the site, a cart symbol, a wishlist symbol, sign-in options, and the search bar. A header module is automatically optimized for the device that the site is being viewed on (in other words, for a desktop device or a mobile device). For example, on a mobile device, the navigation bar is collapsed into a **Menu** button (which is sometimes referred to as a *hamburger menu*).

## Properties of a header module

A header module supports **Logo image**, **Logo link**, and **My account links** properties. 

The **Logo image** and **Logo link** properties are used to define a logo on the page. For more information, see [Add a logo](add-logo.md). 

The **My account links** property can be used to define account pages that the site owner wants to show quick links for in the header.

## Modules that are available in a header module

The following modules can be used in a header module:

- **Navigation menu** – The navigation menu represents the channel navigation hierarchy and other static navigation links. The channel navigation hierarchy can be configured in Dynamics 365 Commerce. The navigation menu has a **Navigation Source** property that is used to specify Retail Server navigation menu items and static menu items as a source. If static menu items are specified as a source, relative links to other pages on the site can be provided. Configured items then appear as header navigation. 
- **Search** – The search module lets users enter search terms to search for products. The URL of the default search page and the search query parameters must be provided at **Site Settings \> Extensions**. The search module has properties that let you suppress the search button or label as you require. The search module also supports auto-suggest options, such as product, keyword, and category search results.
-**Cart icon** - The cart icon represents the cart icon which shows number of items in the cart at any given time. See [Cart icon module](add-carticon-module.md)

## Create a header module for a page

To create a header module, follow these steps.

1. Create a fragment that is named **Header fragment**, and add a container module to it.
1. In the property pane for the container module, set the **Width** property to **Fill container**.
1. Add promo banner and cookie consent modules to the container module.
1. Add another container module to the fragment, and set the **Width** property to **Fill container**.
1. Add a header module to the second container module.
1. In the **Navigation menu** slot of the header module, add a navigation menu module. 
1. In the property pane for the navigation menu module, configure the properties of the navigation menu module.
1. In the **Search** slot of the header module, add a search module. 
1. In the property pane for the search module, configure the properties of the search module. 
1. Save the page fragment, finish editing it, and publish it. 

To help guarantee that a header appears on every page, follow these steps on every page template that is created for the site.

1. In the **Main** slot of the default page, add the header page fragment that contains the header module to the header.
1. Save the template, finish editing it, and publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
