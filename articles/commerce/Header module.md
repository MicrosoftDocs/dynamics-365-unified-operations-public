---
# required metadata
 
title: Header module
description:  
author: AnupamaR
manager: brendans
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 
 
# optional metadata
 
# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: AnupamaR
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 
 
---


The **Header module** is special container that is used for hosting all the modules that will be displayed on the page header. For instance, it includes your site logo, links to the navigation hierarchy, links to other pages on ecommerce, search bar etc. 

The Header module has an optimized design based on the viewport – Desktop vs Mobile.  For instance, the navigation bar collapses to a hamburger menu in Mobile view port.

## Properties of Header

Header supports Heading and Width property, similar to generic containers. 

The Header container has multiple slots – Informational message, Navigation menu, Logo, Search bar, Cart icon, Wishlist icon and Account information.  Each slot supports a specific set of modules.

## Modules available in Header

**Navigation menu** - Navigation menu items represent the channel navigation hierarchy and other static navigation links. The channel navigation hierarchy can be configured in HQ. The configured items appear as a header navigation. In addition, static navigation links can be configured and relative links to other pages on the ecommerce site can be provided. The header itself can be aligned – left, right or center. 

**Cart icon**. The Cart icon is an icon for Cart shown on the header to indicate the number of items in cart. The link to the cart page should be provided so the user can be redirected to the page when they interact with this icon.

**Wishlist icon**. The Wishlist icon is an icon shown on the header to indicate the number of items a customer has added to their Wishlist. The link to the Wishlist page should be provided so the user can be redirected to the page when they interact with this icon.

**Sign-in module**. The Sign-in module is shown on the header to allow the user to sign-in or sign-up for an account. If the user is already signed-in, this module can be configured to show links to the Account page, Order history etc.

**Logo module**. This module shows the logo that represents the retailer/brand. It is an image with a link. Link is typically programmed to redirect to Home page so the user can have a quick way to navigate back to home page from any page on the site.

**Alert** - Alert is used to show an inline message on the header that applies to all pages on the site. E.g. “Annual sale ends in 2 days”. See the Alert module help topic for details

**Search bar**. The Search bar allows the user to enter search terms to search for products. The module must be configured with the Search page URL which is the URL to the search results page. The query string parameter should be provided, the default is “q”. It has an auto-suggest slot where the auto-suggest module should be added. 

**Auto suggest**. The Auto suggest module shows the auto suggest results. The results can be textual or immersive. Textual shows the list of matching product names only. For Immersive, product name, price and image are shown in-line for matching products. In addition, the number of results to be shown in auto suggest can be configured.

## Authoring a Header Module

1. Create a page fragment with a Header module

2. Populate the Header module slots with the respective modules

3. Update the settings for each module

4. Save the page fragment. 
5. Check in and Publish

On every page template created for the site, 

1. add the Header fragment to the Header in the Main Slot of the Default Page

2. Save the template. 
3. Check in and Publish

This will ensure every page renders the header
