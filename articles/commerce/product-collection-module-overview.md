---
# required metadata

title: Product collection module overview
description: This topic provides an overview of product collection modules in Dynamics 365 Commerce.
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

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic provides an overview of product collection modules in Dynamics 365 Commerce.

## Overview

Product discovery is a primary tool for retailers to engage with their customers on an e-Commerce website. Product collection modules provide retailers with a quick and intuitive visual interface for authoring product collections and enable them to build compelling shopping experiences.

Product collection modules represent physical products and services on the website. On interaction, a product collection module typically links to a detail page where customers can purchase or learn more about a product or service. 

The sources for product collections can be editorial lists (manually defined in Dynamics 365 Retail as related products for a product, or product lists), algorithmic lists (such as "new," "best-selling," or "trending"), or machine learning-based recommendations. 

The following diagram shows the different types of product collections used on an e-Commerce site.

![A diagram showing the different types of product collections used on an e-Commerce site](./media/ProductCollectionsAcrossTheSiteUseProductPlacement.png)

> [!NOTE]
> Always use product collection modules to show a group of products of a similar type or theme other than the search results. 

## Product collection modules, types, and descriptions

The following table lists various types of Commerce product collection modules and their descriptions.

| Product collection module     | Type | Description                                                                                                                                                                                                                   |
|----------------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Category browse           | Editorial | Uses a retail channel navigation category hierarchy created by retailers to a display a browsing flow for products offered in a site category|
| Search results           | Search query | Displays a list of products that best match the search query entered by the customer|
| Related products           | Editorial | Displays a list of products configured as related products in Retail by a merchandising manager for the relation type chosen by the author|
| Curated product lists    | Editorial | Displays custom lists created in Retail by merchandizers and editors|
| New                        | Algorithmic | Displays a list of the newest products assorted to channels and catalogs|
| Best selling               | Algorithmic | Displays a list of products ranked by the highest number of sales                      |               
| Trending                   | Algorithmic | Displays a list of the highest performing products for a given time period|
| Frequently bought together | Artificial intelligence / Machine learning  | Uses machine learning to analyze consumer purchase patterns to recommend related items that are commonly purchased with a given product|
| People also like           | Artificial intelligence / Machine learning | Uses machine learning to analyze consumer purchase patterns to recommend items related to a given product|

For information on using product collection modules, see [Add collection modules to a category page](add-product-collection-modules.md).

