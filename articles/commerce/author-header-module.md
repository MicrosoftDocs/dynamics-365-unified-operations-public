--
# required metadata

title: Header module
description: This topic covers header modules and describes how to create page headers in Microsoft Dynamics 365 Commerce.
author: anupamar
manager: annbe
ms.date: 10/31/2019
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

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers header modules and describes how to create page headers in Microsoft Dynamics 365 Commerce.

## Overview

In Dynamics 365 Commerce, a page header comprises multiple modules such as the header, navigation menu, search, promo banner, and cookie consent modules. 

The header module includes a site logo, links to the navigation hierarchy, links to other pages on the site, a cart icon, a wishlist icon, sign-in options, and the search bar. A header module is automatically optimized for the device that the site is being viewed on (in other words, a desktop device or a mobile device). For example, on a mobile device, the navigation bar is collapsed into a **Menu** button (which is sometimes referred to as a *hamburger menu*).

## Properties of a header module

A header module supports **Logo image**, **Logo link**, and **My account links** properties. 

The **Logo image** and **Logo link** properties are used to define a logo on the page. See [Add a logo](add-a-logo.md) for more details. 

The **My account links** property can be used to define account pages that the site owner wants to show quick links for in the header.

## Modules that are available in a header module

The following modules can be used in a header module:

- **Navigation menu** – The navigation menu represents the channel navigation hierarchy and other static navigation links. The channel navigation hierarchy can be configured in Dynamics 365 Commerce Retail. The navigation menu has a **Navigation Source** property that specifies retail server navigation menu and static menu items. If static menu items are specified as a source, relative links to other pages on the site can be provided. Configured items then appear as header navigation. 

- **Search** – The search module enables users to enter search terms to search for products. The default search page URL and search query parameters must be provided in **Site Settings \> Extensions**. The search module has properties that allow you to suppress the search button or label as needed. The search module also supports auto-suggest options such as product, keyword, and category search results. 

## Create a header module for a page

To create a header module, follow these steps.

1. Create a page fragment and add a container, set Width to Fill Container.
2. To the container, add Promo banner and Cookie consent module.
3. Add another container, set Width to Fill Container.
4. To the second container, add Header module.
5. Select the Header module, Navigation menu slot and add Navigation menu module. Configure the properties of navigation menu
6. Select the Header module, Search slot and add the Search module. Configure the properties of Search module. 
7. Save and Finish editing the page fragment. 
8. Publish it.

To help guarantee that a header appears on every page, follow these steps on every page template that is created for the site.

1. On the default page, add the Header page fragment containing the header module to the header in the main slot.
1. Save the template. 
1. Finish editing the template, and publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
