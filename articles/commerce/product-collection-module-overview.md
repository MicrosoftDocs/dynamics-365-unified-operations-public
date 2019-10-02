---
# required metadata

title: Product collection module overview
description: This topic provides an overview of product collection modules in Microsoft Dynamics 365 Commerce.
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

# Product collection module overview  

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic provides an overview of product collection modules in Microsoft Dynamics 365 Commerce.

## Overview

Product discovery is a primary tool that retailers use to engage with their customers on an e-Commerce website. Product collection modules help retailers build compelling shopping experiences by providing an intuitive visual interface that can be used to quickly author product collections.

Product collection modules represent physical products and services on the website. A product collection module is typically linked to a details page where customers can purchase a product or service, or learn more about it. 

The sources for product collections can be lists of three types:

- Editorial lists of products that are manually defined in Dynamics 365 Retail as related products for a product, or product lists
- Algorithmic lists, such as lists of new, best-selling, or trending products
- Recommendation lists that are based on machine learning

The following illustration shows the different types of product collections being used on an e-Commerce site.

![Example of the different types of product collections on an e-Commerce site](./media/ProductCollectionsAcrossTheSiteUseProductPlacement.png)

> [!NOTE]
> Always use product collection modules to show a group of products of a similar type or theme.

## Product collection modules and types

The following table describes various types of product collection modules in Dynamics 365 Commerce.

| Product collection module  | Type | Description |
|----------------------------|------|-------------|
| Category browse            | Editorial | This type of product collection module uses the navigation category hierarchy that the retailer created for a retail channel to show a browsing flow for products that are offered in a specific site category. |
| Search results             | Search query | This type of product collection module shows a list of products that best match the search query that the customer entered. |
| Related products           | Editorial | This type of product collection module shows a list of products that a merchandising manager has configured as related products in Retail, for the relation type that the author selected. |
| Curated product lists      | Editorial | This type of product collection module shows custom lists that merchandisers and editors have created in Retail. |
| New                        | Algorithmic | This type of product collection module shows a list of the newest products that have been assorted to channels and catalogs. |
| Best selling               | Algorithmic | This type of product collection module shows a list of products that are ranked by the highest number of sales. |
| Trending                   | Algorithmic | This type of product collection module shows a list of the highest-performing products for a given period. |
| Frequently bought together | Artificial intelligence/Machine learning | This type of product collection module uses machine learning to analyze consumer purchase patterns and recommend related items that are frequently purchased together with a given product. |
| People also like           | Artificial intelligence/Machine learning | This type of product collection module uses machine learning to analyze consumer purchase patterns and recommend items that are related to a given product. |

For information about how to use product collection modules, see [Add a product collection module to a category page](add-product-collection-modules.md).
