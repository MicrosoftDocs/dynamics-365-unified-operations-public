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

Product discovery is a primary tool for retailers to engage with their shoppers across their website. With this module, we aim to provide retailers a quick & intuitive visual interface for authoring the product collections & enable them to build compelling shopping experiences on their website.

Product collection modules represent physical products and services on the website. On interaction, the product collection typically navigates to a detail page for users to purchase, acquire, or learn more about the product or service. 

The source for the product groups or collection – could be an editorial collections (manually defined in back-office as related products for a product, or product lists), algorithmic lists like new, best-selling, trending or machine-learning based recommendations. 

![product collection across various interactions on the site](./media/ProductCollectionsAcrossTheSiteUseProductPlacement.png)

> [!NOTE]
> Always use product collection modules to show a group of products of a similar type or theme other than the search results. And for default categorized products & search results use 'Category page summary > Category page > Product Slot > Product search result'.

The following table shows product collection modules and their types and descriptions.

| Product collection module     | Type | Description                                                                                                                                                                                                                   |
|----------------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Category browse           | Editorial | Retailers create a retail channel navigation category hierarchy to set up a category structure for products that they offer through their online. |
| Search results           | Search-query | This list shows products that best-match the search query by the shopper.|
| Related products           | Editorial | This list shows products configured as related products in the back office by a Merchandising manager for the relation type chosen by the author.|
| Curated product lists    | Editorial | Here are the custom lists created in the back office by merchandizers and editors.|
| New                        | Algorithmic | This list shows the newest products assorted to channels and catalogs.|
| Best selling               | Algorithmic | This list shows products ranked by the highest number of sales.                      |               
| Trending                   | Algorithmic | This list shows the highest performing products for a given time period.|
| Frequently bought together | AI / ML  | This list uses machine learning to analyze consumer purchase patterns to recommend related items that are commonly purchased for a given seed item.|
| People also like           | AI / ML | This list uses machine learning to analyze consumer purchase patterns to recommend related items for a given seed item.|

