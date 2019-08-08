---
# required metadata

title: Quick tour of default category landing page and search results page
description: This topic provides an overview of the deault category landing page and search results in Dynamics 365 for Commerce e-Commerce.
author: josaw1
manager: annbe
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: asharchw
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 
---

# Quick tour of default category landing page and search results pages

This topic provides an overview of the default category landing page and search results page in Dynamics 365 for Commerce e-Commerce.

## Default category landing page

The default category landing page is the page that a website user generally lands on when selecting a category from the navigation hierarchy, It's part of the universal header-footer. The category page enables browsing, and sorting and refining the categorized products. 

  ![Default category landing view](./media/SimpleCategoryLandingDressCategory.png)

The top of the page has a header that shows all the product categories and other pages that have been configured by the merchandising manager. Configuration is done as part of the channel navigation hierarchy configuration. On the bottom of the page is a footer with quick links to various topics that a shopper may be interested in. 

The following components are essential for a category. 

- **Product placement** tiles are for the products that have been defined in this category by the merchandising manager as part of the navigation hierarchy configuration.
- **Refiners and choice summary** are filters with counts that can be used to refine items. They are configured by the merchandising manager as part of the configuration of the "channel categories and product attributes" metadata. 
- **Sorting options** are used by a website visitor to sort the products. By default, the following sorting options are available.
	- Price - low to high.
	- Price - high to low.
	- Product name - [A-Z].
	- Product name - [Z-A].
	- Ratings - low to high.
	- Ratings - high to low.
- **Pagination** makes it posible for a website visitor to navigate from one page of categorized product results to another. 
- **Total count** provides the total number of products that are defined in a particular category. 


## Enrich a category landing page

If you want a category landing page to have a more tailored experience for a specific category, you can choose to enrich the category landing page for that category. For example, if you might choose to add a marketing video and some category storytelling to get the shoppers' attention. Refer to [Enriching a category landing page](./articles/commerce/enrich-a-category.md) for more details.

 ![Enriched category landing view](./media/CategoryLandingPages.png)

## Auto-suggest and search results pages

A website user may choose to explore a site by either navigating to a category from the navigation hierarchy or by typing a search term in the search bar. 

As soon as the user starts typing in the search bar, they will encounter the immersive auto-suggest functionality, which provides  suggested search terms. 

The following are some of the types of suggestions that mmay come up. 

- **Keywords** are used by search to find items across all products assorted to the channel.
- **Products** provide direct links to the product details page.
- **Scoped category search suggestions** list various categories and enable users to search for the keyword for that category.
 
![Immersive auto-suggest](./media/ImmersiveAutoSuggestUX.png)

When a user clicks a keyword or scoped category search suggestion, or enters a search with no-known suggestions, the search results page comes up. 

The search results page provides a list of search results that the user can browse, sort, and refine to find their desired item.

 ![Search landing](./media/SearchLanding.png)

In addition to the universal header and footer section, the following components are essential for a search results page.

- **Product placement** tiles are for the products that are sorted (by default) based on the cloud-powered search relevancy score for the user search.
- **Refiners and choice summary** are filters with counts that can be used to refine items. They are configured by the merchandising manager as part of the configuration of the "channel categories and product attributes" metadata. 
- **Sorting options** are used by a website visitor to sort the products. By default, the following sorting options are available.
	- Price - low to high.
	- Price - high to low.
	- Product name - [A-Z].
	- Product name - [Z-A].
	- Ratings - low to high.
	- Ratings - high to low.
	- Default
 **Pagination** makes it posible for a website visitor to navigate from one page of categorized product results to another. 
- **Total count** provides the total number of products that are defined in a particular category that match the search criteria. 
