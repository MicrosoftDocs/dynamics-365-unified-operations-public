---
# required metadata

title: Add a product collection module to a category page
description: This topic describes how to add a product collection module to a category page in Microsoft Dynamics 365 Commerce.
author: v-chgri
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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

# Add a product collection module to a category page  

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes how to add a product collection module to a category page in Microsoft Dynamics 365 Commerce.

## Overview

Product collection modules help retailers build compelling shopping experiences by providing an intuitive visual interface that can be used to quickly author product collections. For more information, see [Product collection module overview](product-collection-module-overview.md).

## Add a product collection module to a category page

To add a product collection module to a category page, follow these steps.

1. In Dynamics 365 Commerce, go to your site, and create a page that uses the same template as your default category page.
1. In the page outline, select the **Sub footer** slot, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select **Container**, and then select **OK**.
1. In the container module, select the ellipsis button, and then select **Add Module**.
1. In the **Add Module** dialog box, select **Product collection**, and then select **OK**.
1. Configure settings by selecting an appropriate data source and inputs for the product collection.
1. In the properties pane for the product collection module, select **Add a product list**.
1. In the **Select product list configuration** dialog box, select the type of list, enter the number of items, and select any other options that are available for the list type. For more information about list types, see the table that follows. 
1. Select **OK**.
1. Save the page, and check it in.

The following table shows the list types that are available for selection in the **Select product list configuration** dialog box.
   
| Type                       | Description | General practice | Context that can be derived from the page context | Context that the author can override the page context with |
|----------------------------|-------------|------------------|-------------------------------------|-----------------------------------------------|
| Products by category       | A list of products that belong to a given category. This category is determined from either the page context or the context that the author provides. | Enrich category page, home page, checkout and cart pages, and product pages | Category | Category determined by author |
| Related products           | A list of products that a merchandising manager has configured as related products in Retail for the relation type. | Product pages, checkout and cart pages, wish list page, and customer account page | Product, Relation type (Mandatory)  | Product, Relation type |
| Curated                    | A custom list that merchandisers and editors have created in Retail. | Enrich category page, home page, checkout and cart pages, and product pages | Not applicable | List picker |
| Algorithmic                | <ul><li>**New** – A list of the newest products that have been assorted to channels and catalogs.</li><li>**Best-selling** – A list of products that are ranked by the highest number of sales.</li><li>**Trending** – A list of the highest-performing products for a given period.</li></ul> | Home page, enrich category page, and checkout and cart pages | Category | Category determined by author |
| Frequently bought together | A list that uses machine learning to analyze consumer purchase patterns and recommend related items that are frequently purchased together with a given product. | Product pages, and checkout and cart pages | Product, Cart | Include cart |
| People also like           | A list that uses machine learning to analyze consumer purchase patterns and recommend items that are related to a given product. | Product pages, and checkout and cart pages | Product, Cart | Not applicable |

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Product collection module overview](product-collection-module-overview.md)

[Add a carousel module to a page](add-carousel.md)

[Add a content rich block module to a page](add-content-rich-block.md)

[Add content placement modules to a page](add-content-placement-modules.md)

[Add a container module to a page](add-container-module.md)

[Add a buy box to a page](add-buy-box.md)
