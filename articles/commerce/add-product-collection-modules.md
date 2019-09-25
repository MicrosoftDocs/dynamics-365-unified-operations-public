---
# required metadata

title: Add product collection modules to a category page
description: This topic describes how to add product collection modules to a category page in Dynamics 365 Commerce.
author: asharchw
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Add product collection modules to a category page  

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to add product collection modules to a category page in Dynamics 365 Commerce.

## Overview

Product collection modules provide retailers with a quick and intuitive visual interface for authoring product collections and enable them to build compelling shopping experiences. For more information, see [Product collection module overview](product-collection-module-overview.md).

## Add a product collection module to a category page

To add a product collection module to a category page, do the following.

1. In your site in Commerce, create a new page using the same template as your default category page.
1. From the page outline, select **Sub footer slot**, click the ellipsis button (**...**), then select **Add Module**.
1. In the **Add Module** dialog box, select **Container**, then click **OK**.
1. In the **Container** module, click the ellipsis button (**...**), then select **Add Module**.
1. In the **Add Module** dialog box, select **Product collection**, then click **OK**.
1. Configure settings to choose appropriate data source and inputs for product collection
1. In the right-side properties pane of the product collection module, click **+Add a product list**. The **Select product list configuration** dialog box appears.
1. Select the type of list, enter the number of items, and select any other options available for the type of list. See the table below for more information on list types. 
1. Click **OK**.
1. Save and check in the page.

The following table shows the list types available to pick from in the **Select product list configuration** dialog box.
   
| Type                       | Description                                                                                                                                                                                                                                     | General practice                                                 | Context derivable from page context | Context author can override over page context |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|-------------------------------------|-----------------------------------------------|
| Products by Category       | Lists products categorized into a given category determined either from the page context or author-provided context                   | Enrich category, Home-page, Check out & Cart, Product pages      | Category                            | Exclusively chosen category                   |
| Related Products           | Lists products configured as related products in Retail by a merchandising manager for the relation type chosen by the author                                                                                               | Product pages, Check-out & cart, Wishlist, Customer Account page | Product, Relation type [Mandatory]  | Product, Relation type                        |
| Curated                    | Displays custom lists created in Retail by merchandizers and editors                                                                                                                                                              | Enrich category, Home-page, Check out & Cart, Product pages      | NA                                  | List picker                                   |
| Algorithmic                | **New** - Lists the newest products assorted to channels and catalogs</br>**Best-selling** - Lists products ranked by the highest number of sales</br>**Trending** - Lists the highest-performing products for a given time period | Home-page, Enrich category page, Check out & Cart                | Category                            | Exclusively chosen category                   |
| Frequently bought together | Uses machine learning to analyze consumer purchase patterns to recommend related items that are commonly purchased with a given product                                                                                           | Product pages, Check out & Cart                                  | Product, Cart                       | Include cart                                  |
| People also like           | Uses machine learning to analyze consumer purchase patterns to recommend items related to a given product                                                                                                                         | Product pages, Check out & Cart                                  | Product, Cart                       | NA                                            |


