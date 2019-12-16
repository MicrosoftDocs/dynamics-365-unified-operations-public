--
# required metadata

title: Header module
description: This topic covers header modules and describes how to create them in Microsoft Dynamics 365 Commerce.
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

This topic covers header and describes how to create a header in Microsoft Dynamics 365 Commerce.

## Overview

A page header is comprised of multiple modules - Header, Navigation Menu, Search, Promo banner, Cookie consent etc. 

A header module in particular includes a site logo, links to the navigation hierarchy, links to other pages on the site, cart icon, wishlist icon, sign-in optins and the search bar. A header module is automatically optimized for the device that the site is being viewed on (that is, a desktop device or a mobile device). For example, on a mobile device, the navigation bar is collapsed into a **Menu** button (which is sometimes referred to as a *hamburger menu*).

In addition to a header module, a page header typically includes a cookie consent and promo banner. These additional modules can be added to the page header if needed.

## Properties of a header

A header module supports a **Logo image**, **Logo link** and **My account links**. 

Logo image and Logo link are used to define a logo on the page. See [Adding a logo](add-a-logo.md) for more details on adding a logo. 

My account links can be used to define the account pages that the site owner wants to show quick links on the header.

## Modules that are available in a header module

The following modules can be used in a header module:

- **Navigation menu** – The navigation menu represents the channel navigation hierarchy and other static navigation links. The channel navigation hierarchy can be configured in Dynamics 365 Commerce back office. The navigation menu has a **Navigation Source** property that allows retail server navigation menu and static menu items. If static menu items are allowed as a source, relative links to other pages on the site can be provided. Configured items then appear as header navigation. See [Navigation menu](Add-navigation-menu.md)for more details

- **Search** – The search module lets users enter search terms so that they can search for products. It also shows auto-suggest options when the user searches for a term. See [Search](Add-Search.md) for more details on this module

## Create a header for a page

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
