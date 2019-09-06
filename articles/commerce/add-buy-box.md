---
# required metadata

title: Add a buy box to a page
description: This topic covers buy box modules and how to add them to site pages in Dynamics 365 Commerce.
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

This topic covers buy box modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

"Buy box" typically refers to the area of a product details page that is above the fold and hosts all the critical information for making a product purchase. A buy box module is special container that is used for hosting all the modules that are displayed in the buy box area of a product details page.  

On a product details page, the product ID is in the URL. A buy box module derives all the information it needs to render from this product ID. In the absence of a product ID, a buy box module will not render correctly on a page. This means that a buy box module cannot be used on a page that does not have product context (for example, a home page or marketing page). 

## Buy box module properties and slots 

As a container, a buy box module controls some basic properties such as "width," which allows the modules inside the container to fit within the container or fill the screen.  

On a product details page, a buy box is divided into two regions, with a media region on the left and a content region on the right. By default, a buy box has a 2:1 column width but this can be overriden by the theme. These two regions are represented by slots in the buy box module. Each slot is preconfigured to only accept specific modules that are supported by the slot. For example, a media slot will only support the media gallery module.

On mobile view ports, media and content slots will stack one below the other.  

## Modules available for use in a buy box module

**Media Gallery:** The media gallery module is used for showcasing images of a product on a product details page. It can support one to many images. It also supports thumbnails which can be arranged horizontally (below the image as a row) or vertically (next to the image as a column). The media gallery module can be added to media slot in the buy box container. The media gallery module only supports  images, videos and other formats are currently not supported. 

**Product title:** The product title module displays the title of a product on a product details page. It has a default heading tag of H1 but can be changed as needed. 
                  
**Product rating:** The product rating module displays star ratings based on customer ratings for a product. The buy box module retrieves the product ratings for each product from the ratings service.

**Product price:** The product price module displays the price of the product, including strikethrough prices and discounts.  

**Product description:** The product description module displays the description of the product. 

**Product configure:** The product configure module displays size, style, and dimensions of a product. It supports two configurations: dimension selectors can be stacked one below another, or side-by-side. When a product variant is selected, other properties in the buy box refresh to reflect the variant information (for example, product description, images, etc.). 

**Product quantity:** The product quantity module is used to configure the quantity of the product. The maximum quantity of a product or variant that can be added to cart is restricted by a setting.

**Add to cart:** The add to cart module is used to perform the add to the cart action. Only a product or a variant can be added to cart. In other words, a master product cannot be added to cart. There is a "Navigate to cart" setting on the module which when set to true navigates the user to the cart page each time an add to cart action is triggered. It can be set to false if the site author prefers to keep the customer browsing on the product details page after items are added to cart.  

**Add to wish list:** The add to wish list module is used to add an item to the customer's wish list. Only a product or a variant can be added to a wish list. The add to wish list action can only be completed if the customer is a signed in to the site, and there is error-handling logic in the module to make sure these conditions are met.  

**Find in store:** The find in store module triggers the "buy online, pick up in store" flow. 

**Pick up in store:** The pick up in store module shows the list of nearby stores where an item is available for pickup. When this module is invoked, by default it shows the stores available within a 50 mile radius of the customer's location, although the search radius can be customized in the module. For each store, if inventory check is enabled, the inventory check is done and an appropriate in-stock or out-of-stock message is shown. 

**Store search by Bing Maps:** This store search module enables a customer to input a location to search for a stores, and is available for use inside the pick up in store module. This module uses the Bing Maps geocoding APIs to convert the customer-inputted location to a latitude and longitude. In the absence of this module, only stores in the customer's current location will be listed and the customer cannot search for another location.  

**Content rich block:** The content rich block module can display a CMS-driven message that the site author or retailer wants to promote in the buy box, for example "For issues with order, contact 1-800-FABRIKAM" or "Free shipping on orders over $100."  

## Buy box module settings 

Buy box modules have three configurable settings, as follows.

- **Maximum quantity:** This is the maximum number of items that can be added to the cart per item. For example, a retailer may decide to allow only 10 of each product to be sold in a single transaction.  
- **Inventory check:**  When this is set to True, the buy box module will ensure that the item is in stock before adding it to the cart (for both the ship to home or pick up in store scenarios). If set to False, an inventory check will not be done before adding a product to the cart and placing an order. 
- **Inventory buffer:** Inventory is maintained in real time, and with many customers making orders it's difficult to maintain an accurate inventory count. For this reason, a buffer can be defined for inventory. When doing an inventory check, if the inventory is less than the buffer amount, the product is treated as out-of-stock. This reduces the chances of selling an item when it is out of stock but inventory count has not fully synchronized due to fast sales through several channels.  

## Retail server interaction 

The buy box module retrieves product information using retail server APIs. All information is retrieved using the product detail page's product ID. 

## Add a buy box module to a page 

To add a buy box module to a new page and set the required properties, do the following.  

1. Create a new fragment named "buy box fragment" and add a buy box module to it.

1. In the **Media** slot of the buy box module, add **Media Gallery**. 

1. In the **Content** slot of the buy box module, add the following modules: **Product Name**, **Product Ratings**, **Product Price**, **Product Description**, **Product Configure**, **Add to Cart**, **Add to Wishlist**, and **Find in store**. The modules in the content slot can be rearranged to achieve the desired layout.  

1. Select the **Find in Store** module. In the slot inside this module, add **Pick up in Store**.  

1. In the slot inside the Pick up in store module, add **Store search by Bing Maps**.  

1. Check in and publish the page.

1. Create a template for a product details page named "PDP template."

1. Add a default page. In the **Main** slot of the default page, add a **Buy box fragment**.

1. Save, check in, and publish the template.

1. Create a page named "PDP page" using the PDP template you created. 

1. In the **Main** slot of the default page, add a **Buy box fragment**.

1. Save the page. To preview the page, add **?productid=&lt;*product id*&gt;** to the preview page URL. This will load and render the preview page with the product context. 

1. Check in and publish the page. A buy box should appear on the product details page.  
 

