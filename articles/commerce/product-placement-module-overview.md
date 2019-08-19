---
# required metadata

title: Product placement module
description: 
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

# Product placement module 

Product placement represent physical products and services on the website. On interaction, the product placement typically navigates to a detail page for users to purchase, acquire, or learn more about the product or service. 

As retailers consider product discovery as a primary tool for customer interaction across their website. With this module, we aim to provide retailers a quick & intuitive visual interface for authoring the product collections & enable them to build compelling shopping experiences on their website.

Thumb-rule: Always use product placements to show a group of products of a similar type or theme. 

The source for the product groups or collection – could be – Category browse results, search results, editorial collections (manually defined in back-office as related products for a product, or product lists), smart-logic based grouped results like new, best-selling, trending etc & machine-learning based recommendations. 

  ![Product placement across various interactions on the site](./media/ProductCollectionsAcrossTheSiteUseProductPlacement.png)


| # | Product placement kind     | Description                                                                                                                                                                                                                   |
|---|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | Category                   | This will list products categorized into a given category, that is determined either from the page-context or author provided context, so that the products can be browsed by end-consumer during their shopping experiences. |
| 2 | Search                     | This will list products based on search term queried by the user to browse the search results during their shopping experiences.|
| 3 | Related products           | This list shows products configured as related products in the back office by a Merchandising manager for the relation type chosen by the author.|
| 4 | Editorial product lists    | Here are the custom lists created in the back office by merchandizers and editors.|
| 5 | New                        | This list shows the newest products assorted to channels and catalogs.|
| 6 | Best selling               | This list shows products ranked by the highest number of sales.                      |               
| 7 | Trending                   | This list shows the highest performing products for a given time period.|
| 8 | Frequently bought together | This list uses machine learning to analyze consumer purchase patterns to recommend related items that are commonly purchased for a given seed item.|
| 9 | People also like           | This list uses machine learning to analyze consumer purchase patterns to recommend related items for a given seed item.|


