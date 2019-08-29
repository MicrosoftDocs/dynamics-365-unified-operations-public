---
# required metadata

title: Buy Box
description: This topic reviews setting up a Buy Box module in a Dynamics 365 e-Commerce page.
author: anupamar-ms
manager: BrendanSullivanMSFT
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
ms.author: anupamar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---

# Buy box 

Buy box typically refers to the region of the product details page that is above the fold and hosts all the critical information for making a product purchase. Buy box module is special container that is used for hosting all the modules that are shown in the product details page buy box region.  

On a product details page, the page context has the product id information from the URL. A buy box derives all the information from this product id. In the absence of a product id, buy box will not render correctly on the page. This means the buy box cannot be used on a page that does not have product context - E.g. Home page or Marketing page. 

## Properties of Buy Box 

As a container, Buy box provides some basic properties such as Width which allows the modules inside this container to fit within or fill screen.  

Buy Box is divided into two regions – Media region on the left and Content region on the right. By default they have a 2:1 column width but this can be overriden by theme. These two regions are represented as slots in the buy box module. Each slot is pre-configured to only accept specific modules that are supported by the slot. E.g. Media slot will only support Media gallery module.

On Mobile view port, Media and Content slots will stack one below the other.  

## Modules available in Buy Box 

**Media Gallery:** Media gallery is used for showcasing images of a product in a product details page. It can support one to many images. It also supports thumbnails which can be arranged horizontally (below the image as a row) or vertically (next to the image as a column). Media gallery can be added to Media slot in the buy box container. Media gallery supports only images. Videos and other formats are currently not supported. 

**Product title:** Product title is used for displaying title of a product in a product details page. It has a default heading tag of H1 but can be changed as needed. 
                  
**Product rating:** Product rating is used to display star ratings based on user rating for the product. The buy box integrates with the Ratings service to retrieve the product ratings for each product. See Ratings service for more details. 

**Product price:** Product price is used to display the price of the product including strikethrough price and discounts.  

**Product description****:** Product description is used to display the description of the product. 

**Product configure****:** The product dimensions defined for the product are shown in this module. Product configure module is used to configure size, style and other dimensions of the product. It supports two configurations – Dimension selectors can be stacked one below another or side-by-side. When a product variant is selected, other properties in the buy box update E.g. Product description, Images etc to reflect the variant information. 

**Product quantity****:** Product quantity is used to configure the quantity of the product. The maximum quantity of a product or variant that can be added to cart is restricted by a setting. This setting resides in the App settings <link>. 

**Add to cart**: Add to cart is used to perform the add to the cart action. Only a product or a variant can be added to cart. In other words a master product cannot be added to cart. There is a setting on the module “Navigate to cart” which when true navigate the user to Cart page each time an Add to cart action is triggered. It can be set to false if the site author prefers to keep the user browsing on the product details page after items are added to cart.  

**Add to wishlist****:** Add to wishlist is used to add an item to Wishlist. Only a product or a variant can be added to wishlist. In addition, add to wishlist can be completed only if the user invoking this action is a signed-in user. There is error-handling logic in the module to make sure these conditions are met.  

**Find in store****:** This is the action shown on the buy box that triggers the buy online pick up in store flow 

**Pick up in store****:** This module shows the list of nearby stores where an item is available for pickup. When this module is invoked, it shows the stores available within 50 mile radius of the user’s location. This search radius is configurable in the module as part of the site authoring. For each store, if inventory check is enabled, the inventory check is done and an appropriate in-stock or out-of-stock message is shown. 

**Store search by Bing Maps****:** This is store search module that is available inside the Pick up in Store module. It allows user to input a location to search for stores. This module uses the Bing Maps Geocoding APIs to convert the user inputted location to a latitude/longitude. In the absence of this module, only stores in the user’s current location will be listed and the user cannot search for another location.  

**Content rich block:** Buy box supports content rich block. This is for any CMS driven message that the site author or retailer wants to promote on the buy box. E.g. “For issues with order, contact 1-800-FABRIKAM” “Free shipping on orders over $100”.  

## AppSettings 

Buy box uses three settings that are defined in the App Settings 

- Maximum quantity: This is the maximum number of items that can be added to the cart per item. E.g. a retailer may decide to support only 10 of each product to be sold in a single transaction.  
- Inventory check:  When this is true, buy box will make sure the item is available in stock before adding it to cart (ship to home or pick up in store scenario). Alternatively, it can be set to false if the retailer does not want to do inventory check before placing an order 
- Inventory buffer: Inventory is real-time and with many people making orders via multiple channels it’s hard to stay accurate. For these reasons we have a buffer defined for inventory. When doing inventory check, if the inventory is less than the buffer its treated as out-of-stock. This reduces the chances of selling an item when it’s out of stock but inventory count has not fully sync’d due to fast sales through several channels.  

## Retail server interaction 

Buy box retrieves product information using Retail Server APIs. Using the product id from the page context all information is retrieved. [TBD more details] 

## Authoring a Buy Box 

This section explains how to add a buy box module to a new page and set the required properties.  

1. In tooling, create a new page template “Buy Box template”.  

1. In the Main slot of the template, add Buy Box. 

1. Check-in and Publish.  

1. Now create a new page with the “Buy Box template” and call it “Buy box page” 

1. On the page outline, add Default page 

1. To the Default page, add Buy Box module 

1. In the Media slot of the Buy Box module, add Media Gallery 

1. In the Content slot of the Buy Box module, add the modules– Product Name, Product Ratings, Product Price, Product Description, Product Configure, Add to Cart, Add to Wishlist and Find in store. 

1. The modules in Content slot can be rearranged as needed to achieve the layout needed 

1. Select the Find in Store module. To the slot inside this module, add Pick up in Store.  

1. To the slot inside Pick up in store module, add Store search by Bing Maps.  

1. Save and Preview. Some modules may not render as they don’t have a product context. To the Preview URL add *?productid=<insert product id>*. This will load the Preview page with the product context and will render the page in preview correctly. 

1. Check-in and Publish 

 

A buy box appears on the product details page.  See Quick Tour of Product Details page for additional modules that can be added below the buy box to make this page a fully functional product details page.  

If specific products need a more enriched or specialized product details page, see Enrich a product details page for details <link>. 

Buy box can be built as a Fragment since it does not change from page to page. The Pickup in Store module can also be built as a Fragment<link> as it will be used in both Cart and Buy Box. 
