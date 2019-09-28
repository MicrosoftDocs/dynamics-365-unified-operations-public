---
# required metadata

title: Create a header module
description: This topic covers header modules and describes how to create them in Microsoft Dynamics 365 Commerce.
author: anupamar
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
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

# Create a header module

[!include [banner]../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers header modules and describes how to create them in Microsoft Dynamics 365 Commerce.

## Overview

A header module is a special container that is used to host all the modules that will be shown in a page's header. For example, it can include your site logo, links to the navigation hierarchy, links to other pages on the site, and the search bar.

A header module is automatically optimized for the device that the site is being viewed on (that is, a desktop device or a mobile device). For example, on a mobile device, the navigation bar is collapsed into a **Menu** button (which is sometimes referred to as a *hamburger menu*).

## Properties of a header

Like generic containers, a header module supports the **heading** and **width** properties.

A header module has multiple slots. For example, there are slots for an informational message, navigation menu, logo, search bar, cart icon, wish list icon, and account information. Each slot supports a specific set of modules.

## Modules that are available in a header module

The following modules can be used in a header module:

- **Navigation menu** – The navigation menu represents the channel navigation hierarchy and other static navigation links. The channel navigation hierarchy can be configured in Dynamics 365 Retail. Configured items then appear as header navigation. In addition, static navigation links can be configured, and relative links to other pages on the e-Commerce site can be provided. The header itself can be aligned left, right, or center.
- **Cart icon** – The cart icon is a special icon that represents the cart. It's shown in the header and indicates the number of items in the cart. A link to the cart page should accompany the cart icon, so that customers can be redirected to the cart page when they interact with the icon.
- **Wish list icon** – The wish list icon is shown in the header and indicates the number of items that have been added to the customer's wish list. A link to the wish list page should accompany this icon, so that customers can be redirected to the wish list page when they interact with the icon.
- **Sign-in module** – The sign-in module is shown in the header. It lets customers either sign in to their account or sign up for an account. If the customer is already signed in, the module can be configured to show links to the account page, order history page, or another page.
- **Logo module** – This module shows the logo that represents the retailer and brand. It's an image that has a link. The link is typically configured so that it has a redirect to the home page, Therefore, customers can quickly return to the home page from any page on the site.
- **Alert** – An alert appears in the header and is used to show an inline message that applies to all pages on the site. For example, an alert might show a message such as "Annual sale ends in 2 days."
- **Search bar** – The search bar lets users enter search terms so that they can search for products. The module must be configured with the URL of the search results page. The query string parameter can be configured (the default value is **"q"**). The search bar has an autosuggest slot where the autosuggest module should be added.
- **Autosuggest** – The autosuggest module shows automatically suggested results. These results can be keywords, products, or categories where the search term is found.

## Create a header module

To create a header module, follow these steps.

1. Create a page fragment that includes a header module.
1. Add modules to the slots in the header module.
1. Update the settings for each module.
1. Save the page fragment. 
1. Check in the page, and publish it.

To help guarantee that a header appears on every page, follow these steps on every page template that is created for the site.

1. On the default page, add the page fragment containing the header module to the header in the main slot.
1. Save the template. 
1. Check in the template, and publish it.
