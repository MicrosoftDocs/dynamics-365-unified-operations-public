---
# required metadata

title: Add a buy box to a page
description: This topic covers buy box modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Add a buy box to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers buy box modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

The term *buy box* typically refers to the area of a product details page that is "above the fold," and that hosts all the most important information that is required to make a product purchase. (An area that is "above the fold" is visible when the page is first loaded, so that users don't have to scroll down to see it.)

A buy box module is special container that is used to host all the modules that are shown in the buy box area of a product details page.

The URL of a product details page includes the product ID. All the information that is required to render a buy box module is derived from this product ID. If a product ID isn't provided, the buy box module won't be rendered correctly on a page. Therefore, a buy box module can't be used on any page that doesn't have product context (for example, a home page or a marketing page).

## Buy box module properties and slots 

As a container, a buy box module controls some basic properties, such as the width. The width setting determines whether the modules inside the container must fit within that container, or whether they can fill the screen.

On a product details page, a buy box is divided into two regions: a media region on the left and a content region on the right. These two regions are represented by slots in the buy box module. Each slot is preconfigured to accept only specific modules that are supported by the slot. For example, a **Media** slot supports only the media gallery module.

By default, the ratio of column widths for the media region and the content region is 2:1. However, the column widths can be overridden by the theme. In addition, on mobile devices, the two regions are stacked, so that one region appears below the other region.

## Modules that can be used in a buy box module

- **Media gallery** – This module is used to showcase images of a product on a product details page. It can support one to many images. It also supports thumbnail images. The thumbnail images can be arranged either horizontally (as a row below the image) or vertically (as a column next to the image). The media gallery module can be added to the **Media** slot in the buy box module. It currently supports only images and videos.
- **Product title** – This module shows the title of the product on a product details page. By default, the **H1** heading tag is used, but the heading tag can be changed as required.
- **Product rating** – This module shows star ratings, based on customer ratings for a product. The buy box module retrieves the product ratings for each product from the ratings service.
- **Product price** – This module shows the price of the product. The price includes strikethrough prices and discounts.
- **Product description** – This module shows the description of the product.
- **Product configure** – This module shows the size, style, and dimensions of the product. The dimension selectors can be stacked vertically, or they can appear side by side. When a product variant is selected, other properties in the buy box (for example, the product description and images) are updated to reflect the variant information.
- **Product quantity** – This module is used to configure the quantity of the product. A setting limits the quantity of a product or variant that can be added to the cart.
- **Add to cart** – This module is used to perform the "add to the cart" action. Only a product or a variant can be added to the cart. In other words, a master product can't be added to the cart. The module has a **Navigate to cart** property that the site author can set. When this property is set to **True**, the user is taken to the cart page every time that an "add to the cart" action is triggered. When it's set to **False**, the customer can continue to browse on the product details page after items are added to the cart.
- **Add to wish list** – This module is used to add an item to the customer's wish list. Only a product or a variant can be added to a wish list. Additionally, the customer must be signed in to the site. The module includes error handling logic to make sure that both these conditions are met.
- **Find in store** – This module triggers the "buy online, pick up in store" flow.
- **Pick up in store** – This module shows a list of nearby stores where an item is available for pickup. By default, this module shows stores that are within a 50-mile radius of the customer's location. However, the search radius can be customized in the module. For each store, an inventory check is done, if the inventory check functionality is turned on, and an appropriate in-stock or out-of-stock message is shown.
- **Store search by Bing Maps** – This module can be used inside the pick up in store module. It lets customers search for stores by entering a location. The Bing Maps geocoding application programming interface (API) is used to convert the specified location to a latitude and a longitude. If this module is used, only stores that are near the customer's current location are shown, and the customer can't search for a different location.
- **Content rich block** – This module can show a message that the site author or retailer wants to promote in the buy box, such as "For issues with order, contact 1-800-FABRIKAM" or "Free shipping on orders over $100." The messages are driven by the content management system (CMS).

## Buy box module settings

Buy box modules have three settings that can be configured:

- **Maximum quantity** – The maximum number of each item that can be added to the cart. For example, a retailer might decide that only 10 of each product can be sold in a single transaction.
- **Inventory check** – When the value is set to **True**, an item is added to the cart only after the buy box module makes sure that it's in stock. This inventory check is done both for scenarios where the item will be shipped and for scenarios where it will be picked up in the store. If the value is set to **False**, no inventory check is done before an item is added to the cart and the order is placed.
- **Inventory buffer** – Inventory is maintained in real time, and when many customers place orders, it can be difficult to maintain an accurate inventory count. Therefore, a buffer can be defined for inventory. When an inventory check is done, if the inventory is less than the buffer amount, the product is treated as out of stock. Therefore, when sales occur quickly through several channels, so that the inventory count isn't fully synced, there is less risk that an item that is out of stock will be sold.

## Retail server interaction

The buy box module retrieves product information using Retail Server APIs. The product ID from the product details page is used to retrieve all information.

## Add a buy box module to a page

To add a buy box module to a new page and set the required properties, follow these steps.

1. Create a fragment that is named **buy box fragment**, and add a buy box module to it.
1. In the **Media** slot of the buy box module, add a media gallery module.
1. In the **Content** slot of the buy box module, add the following modules: product title, product rating, product price, product description, product configure, add to cart, add to wish list, and find in store. You can rearrange the modules in the **Content** slot to achieve the desired layout.
1. Select the find in store module. In the slot inside this module, add a pick up in store module.
1. In the slot inside the pick up in store module, add a store search by Bing Maps module.
1. Check in the page, and publish it.
1. Create a template for a product details page, and name it **PDP template**.
1. Add a default page.
1. In the **Main** slot of the default page, add a buy box fragment.
1. Save the template, check it in, and publish it.
1. Use the template that you just created to create a page that is named **PDP page**.
1. In the **Main** slot of the new page, add a buy box fragment.
1. Save and preview the page. Add the **?productid=&lt;product id&gt;** query string parameter to the URL of the preview page. In that way, the product context is used to load and render the preview page.
1. Check in the page, and publish it. A buy box should appear on the product details page.
