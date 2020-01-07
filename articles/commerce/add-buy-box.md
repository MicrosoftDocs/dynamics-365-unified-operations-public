---
# required metadata

title: Buy box module
description: This topic covers buy box modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 11/11/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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

# Buy box module

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers buy box modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

The term *buy box* typically refers to the area of a product details page that is "above the fold," and that hosts all the most important information that is required to make a product purchase. (An area that is "above the fold" is visible when the page is first loaded, so that users don't have to scroll down to see it.)

A buy box module is special container that is used to host all the modules that are shown in the buy box area of a product details page.

The URL of a product details page includes the product ID. All the information that is required to render a buy box module is derived from this product ID. If a product ID isn't provided, the buy box module won't be rendered correctly on a page. Therefore, a buy box module can't be used on any page that doesn't have product context (for example, a home page or a marketing page) without additional customizations.

## Buy box module properties and slots 

On a product details page, a buy box is divided into two regions: a media region on the left and a content region on the right. By default, the ratio of media region column width to content region column width is 2:1. On mobile devices the two regions are stacked so that one region appears below the other region. Column widths and stacking rank can be customized using themes.

A buy box module renders the title, description, price, and ratings of a product. It also allows customers to select product variants with differing product attributes such as size, style, and color. When a product variant is selected, other properties in the buy box (for example, the product description and images) are updated to reflect the variant information. 

A quantity selector is provided to enter the quantity of items to purchase. The maximum quantity allowed for purchase can be defined in site settings.
 
From the buy box, customers can also perform actions such as adding a product to the cart, adding a product to their wishlist, and choosing a pick-up location. These actions can be performed on a product or a product variant. Adding a product to a wishlist requires the customer to be signed in.

Removing or changing the order of buy box product properties and action controls can be done using themes. 

## Module properties

- **Heading tag** - The heading tag property defines the heading tag for the product title. If the buy box is on top of the page, this should be set to a **h1** to meet accessibility standards. 

## Modules that can be used in a buy box module

- **Media gallery** – This module is used to showcase images of a product on a product details page. It can support one to many images. It also supports thumbnail images. The thumbnail images can be arranged either horizontally (as a row below the image) or vertically (as a column next to the image). The media gallery module can be added to the **Media** slot in the buy box module. It currently supports only images. 
- **Store selector** – This module shows a list of nearby stores where an item is available for pickup. The module allows the user to enter a location to find stores nearby. The store selector module is integrated with the Bing Maps Geocoding API to convert the location to a latitude and longitude. A Bing Maps API key is required and must be added to the Retail shared parameters page in Dynamics 365 Retail. This module supports two properties, **Search radius** and **Terms of service link**. The search radius property defines the search radius for stores in miles. It defaults to a 50 mile radius if a radius is not provided. If using Bings Maps or any external service, a terms of service link can be provided using the terms of service link property. A terms of service link is required for Bing Maps service. 

## Buy box module settings

Buy box modules have three settings that can be configured at **Site Settings \> Extensibility**:

- **Maximum quantity** – This specifies the maximum number of each item that can be added to the cart. For example, a retailer might decide that only 10 of each product can be sold in a single transaction.
- **Inventory check** – When the value is set to **True**, an item is added to the cart only after the buy box module makes sure that it's in stock. This inventory check is done both for scenarios where the item will be shipped and for scenarios where it will be picked up in the store. If the value is set to **False**, no inventory check is done before an item is added to the cart and the order is placed.
- **Inventory buffer** – This specifies a buffer number for inventory. Inventory is maintained in real time, and when many customers place orders, it can be difficult to maintain an accurate inventory count. When an inventory check is done, if the inventory is less than the buffer amount, the product is treated as out of stock. Therefore, when sales occur quickly through several channels and the inventory count isn't fully synced, there is less risk that an item that is out of stock will be sold.

## Retail server interaction

The buy box module retrieves product information using Retail Server APIs. The product ID from the product details page is used to retrieve all information.

## Add a buy box module to a page

To add a buy box module to a new page and set the required properties, follow these steps.

1. Create a fragment that is named **buy box fragment**, and add a buy box module to it.
1. In the **Media** slot of the buy box module, add a media gallery module.
1. In the **Store selector** slot of the buy box module, add a store selector module.
1. Check in the page, and publish it.
1. Create a template for a product details page, and name it **PDP template**.
1. Add a default page.
1. In the **Main** slot of the default page, add a buy box fragment.
1. Save the template, Finish editing and publish it.
1. Use the template that you just created to create a page that is named **PDP page**.
1. In the **Main** slot of the new page, add a buy box fragment.
1. Save and preview the page. Add the **?productid=&lt;product id&gt;** query string parameter to the URL of the preview page. In that way, the product context is used to load and render the preview page.
1. Finish editing the page, save it, and publish it. A buy box should appear on the product details page.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
