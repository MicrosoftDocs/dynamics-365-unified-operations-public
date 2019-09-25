---
# required metadata

title: Product placement module overview
description: This topic covers product placement modules in Dynamics 365 Commerce.
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

# Product placement module overview  

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers product placement modules in Dynamics 365 Commerce.

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

## Add category browse and search results modules to a category page

> [!NOTE]
> This is a generic setup for a list page, which currently encompasses both Category and Search pages. They can be created using the same template, or using different templates both based on the "Category Page" module, depending on desired enrichment experience. 

To add category browse and search results modules to a category page, do the following.


1. Go to your site and create a new template 
![start defining category template](./media/Category_template.png)

1. Go to the Template Editor for your template 

1. Add a new **Category Page Summary** module to the **HTML Head slot** of the template. 
  ![Category page summary](./media/Category_template_definition.png)
1. Add a new **Category page** module to the body slot of the template. 
  ![Category page body slot](./media/Category_page_bodySlot.png)
For all the slots within the Category Page fill out the modules you’d like your template to have as appropriate. Some general guidance: 
> **Note**: For each module added to each slot below that's expected to be readily available with your template-based configuration on during actual page configuration, make sure to mark 'Min Occurs = 1' 
   1. *Header/Footer slot* will likely contain already created header/footer fragments as used across rest of site 
   1. *Sub Head/Sub Footer slots* are designated enrichment slots, so they should be configured as appropriate for desired enrichment experience 
   1. *Collection Filters Slot* is where "Refine Menu module (refine by collection)" will exist, and is required and the following configurations can be made for the refiners
      1. Style of glyph for selection of the refiner values
      1. Style of glyph to show on expansion & collapsing of the refiner values
      1. Control expansion of the refiner values
   1. *Collection Header* contains the following modules, which are not required, but are recommended 
      1. *Category Hierarchy* provides breadcrumbs for category pages. Provides a hierarchy of the current page with relation to its parent categories.
      1. *Collection Choice Summary* provides easy UI for managing active refiners. Choice summary by collection shows choices in a summary format for a product collection and refined by choices in a refine menu.
      1. *Collection Title* allows author to provide a contextual title for list page.
   1. *Sorting Modules Slot* contains the sorting dropdown (sort-by-collection module)  
   1. *Products Slot* contains the product list module (product-search-result). And user can control following properties for look and feel of the product tiles 
      1. Size of the heading 
      1. View products as cards or plain using 'Card layout of the module' settings
      1. Number of items to be displayed per page
      1. Show/hide product description, product price, product ratings
      1. Image quality 
   ![Product slot - product search result - Category and search results](./media/Category_page_body_productsSlot_searchresults.png) 
   
> [!NOTE]
> All of the aforementioned modules should be authorable by following supporting self-explanatory tooltips for every configuration in the tools.  

Once you are happy with the template, Check-in and publish the template. Then we have to create both a Search Page and a Category Page based on these templates. 

> [!NOTE]
> These pages will work in a contextual manner, as for category page there will be no default category to use, and for search page there will be no search query. 
 
1. Go to your site and create a new page  - choose the template you may have created in the above steps. 

2. Go to the Page editor for your page & observe the Page Outline on the left
>*Notice only modules (with MinOccurs =1) that were associated with slots as part of template definition, found under the category page, are readily available with template-based configurations.* 

3. Once the pages have been authored and checked in/published, you should create the appropriate URLs for the pages: 
  +.*Search Page: should have a URL path of '/search'*
       +. Go to URLs > Create a new URL and associate your search page
       ![searchPageToURLAssociation](./media/SearchURL_page_association.png)
  +.*Category Page: should have an alias of 'category-default'. By using the category-default alias, you should now be able to select a category to populate the page for WYSIWYG page editing.* 
       +. Go to URLs > Create a new Alias and associate your category page
       ![category-default-alias](./media/CategoryDefaultAlias.png)
 
 
## Add a product collection module to a category page

To add a product collection module to a category page, do the following.

1. Go to sites, create a new page and choose the template same as your default category page
1. From the page editor (assuming you are able to check out the page). From Page Outline, select 'Sub footer slot' and 'Add container'
1. Upon adding container - choose to 'Add module'
1. Next, choose 'Product collection' module
1. Configure settings to choose appropriate data source and inputs for product collection
   1. From Product Collection module settings - click on '+ Add a product list'
   1. From Type you may be able to select the following 
   
| Type                       | Description                                                                                                                                                                                                                                     | General practice                                                 | Context derivable from page context | Context author can override over page context | Sample                                                             |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|-------------------------------------|-----------------------------------------------|--------------------------------------------------------------------|
| Products by Category       | This will list products categorized into a given category, that is determined either from the page-context or author provided context, so that the products can be browsed by end-consumer during their shopping experiences.                   | Enrich category, Home-page, Check out & Cart, Product pages      | Category                            | Exclusively chosen category                   | [Category](./media/PC_Category.png)                                |
| Related Products           | This list shows products configured as related products in the back office by a Merchandising manager for the relation type chosen by the author.                                                                                               | Product pages, Check-out & cart, Wishlist, Customer Account page | Product, Relation type [Mandatory]  | Product, Relation type                        | [Related Products](./media/PC_RelatedProducts.png)                 |
| Curated                    | Here are the custom lists created in the back office by merchandizers and editors.                                                                                                                                                              | Enrich category, Home-page, Check out & Cart, Product pages      | NA                                  | List picker                                   | [Curated List](./media/CuratedList.png)                            |
| Algorithmic                | New - This list shows the newest products assorted to channels and catalogs. Best-selling - This list shows products ranked by the highest number of sales. Trending - This list shows the highest performing products for a given time period. | Home-page, Enrich category page, Check out & Cart                | Category                            | Exclusively chosen category                   | [Algorithmic](./media/New_BestSelling_Trending_CategoryPicker.png) |
| Frequently bought together | This list uses machine learning to analyze consumer purchase patterns to recommend related items that are commonly purchased for a set of seed items.                                                                                           | Product pages, Check out & Cart                                  | Product, Cart                       | Include cart                                  | [FBT](./media/FBT_IncludeCart.png)                                 |
| People also like           | This list uses machine learning to analyze consumer purchase patterns to recommend related items for a given seed item.                                                                                                                         | Product pages, Check out & Cart                                  | Product, Cart                       | NA                                            | [PAL](./media/PAL_COllection.png)                                  |


> Related Articles:
>  -	Learn here more about [Omni-channel Product Recommendations Overview](product-recommendations-overview.md)
>  -	Learn here how to [Create curated product lists]( create-editorial-recommendation-lists.md)
>  -	If you're having issues with Algorithmic lists or AI/ML based lists use this link [Product recommendations FAQ]( faq-recommendations.md) 
