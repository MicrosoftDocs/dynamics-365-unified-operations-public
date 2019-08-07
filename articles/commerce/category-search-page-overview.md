---
# required metadata

title: Quick tour of default category landing page and search results
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

# Quick tour of default category landing page and search results

This topic provides an overview of the deault category landing page and search results in Dynamics 365 for Commerce e-Commerce.

## Default category landing page

The default category landing page is the page that a website visitor generally lands on when selecting a category from the navigation hierarchy, It's part of the universal header-footer. The category page enables browsing, and sorting and refining the categorized products. 

  ![Default category landing view](./media/SimpleCategoryLandingDressCategory.png)

The top of the page has a header that shows all the product categories and other pages that have been configured by the merchandising manager. Configuration is done as part of the channel navigation hierarchy configuration. On the bottom of the page is a footer with quick links to various topics that a shopper may be interested in. 

The following components are essential for a category. 

- **Product placement** tiles are for the products that have been defined in this category by the merchandising manager as part of the navigation hierarchy configuration.
- **Refiners and choice summary** are filters with counts that can be used to refine items. They are configured by the merchandising manager as part of the configuration of the "channel categories and product attributes" metadata. 
- **Sorting options** are used by a website visitor to sort the products. By default, the following sorting options are available.
	- Price low to high.
	- Price high to low.
	- Product name [A-Z].
	- Product name [Z-A].
	- Ratings low to high.
	- Ratings high to low.
- **Pagination** makes it posible for a website visitor to navigate from one page of categorized product results to another. 
- **Total count** provides the total number of products that are defined in a particular category. 


## Enriching a category landing page

If you want a category landing page to have a more tailored experience for a specific category, you can choose to enrich the category landing page for that category. For example, if you might choose to add a marketing video and some category storytelling to get the shoppers attention. This can be done via enriching the page for this category. Refer to [Enriching a category landing page](./articles/commerce/enrich-a-category.md) for more details.

 ![Enriched category landing view](./media/CategoryLandingPages.png)

## Auto-suggest & search results page

Journey of product discovery for a website visitor begins with either navigating to a category from the navigation hierarchy or by typing the search term in the search-bar. 

As soon as website visitor starts typing in the search bar they encounter the **immersive auto-suggest**. 

With new enhancements, here are the following kind of suggestions that a website visitor may discover as part of the immersive auto-suggest - 

+ **Keywords** search for keywords across all products assorted to the channel
+ **Products** directly navigable to product details page
+ **Scoped category search suggestions** support for "keywords" match in various categories, which enables users to trigger the search for the keyword for that category.
 
![Immersive auto-suggest](./media/ImmersiveAutoSuggestUX.png)

Now, if a website visitor would've clicked on the "Keywords" or "Scoped category search suggestions" or "entered triggered the search for no-known suggestions" then they are navigated to the search results page. 

**Search results page** allows a website visitor to be able to browse, sort and refine the search results for their intended action.

 ![Search landing](./media/SearchLanding.png)

Apart from the Universal header footer section on the search page these are the following components that are considered to be essential for browsing of search results - 

1. **Product placement** - these are the product tiles of the products that are sorted (by default) based on the cloud-powered search relevancy score for the user-triggered search interaction.
1. **Refiners & Choice summary** - these are the filters with counts that are marked to be available as an option to refine by  a Merchandising manager as part of the 'Channel categories & product attributes' metadata configuration in the back-office. 
1. **Sorting options** - these are the options a website visitor can sort these search results. By default, sorting options that shall be available are the following 
	- Price low to high
	- Price high to low
	- Product name [A-Z]
	- Product name [Z-A]
	- Ratings low to high
	- Ratings high to low
	- Default
1. **Pagination** - Allowing a website visitor to be able to navigate from one page results to another page of search results. 
1. **Total count** - Providing hint to a website visitor about number of products that are in total matching their search criteria. 

