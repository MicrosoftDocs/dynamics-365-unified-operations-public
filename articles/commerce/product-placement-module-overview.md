# Product discovery via category browse, search results & product collection modules  

Product discovery is a primary tool for retailers to engage with their shoppers across their website. With this module, we aim to provide retailers a quick & intuitive visual interface for authoring the product collections & enable them to build compelling shopping experiences on their website.

Product collection represent physical products and services on the website. On interaction, the product collection typically navigates to a detail page for users to purchase, acquire, or learn more about the product or service. 

The source for the product groups or collection – could be an editorial collections (manually defined in back-office as related products for a product, or product lists), algorithmic lists like new, best-selling, trending or machine-learning based recommendations. 

  ![product collection across various interactions on the site](./media/ProductCollectionsAcrossTheSiteUseProductPlacement.png)

> **Note** Always use product collection to show a group of products of a similar type or theme other than the search results. And for default categorized products & search results use 'Category page summary > Category page > Product Slot > Product search result'.

| # | Product collection kind     | Type | Description                                                                                                                                                                                                                   |
|---|----------------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | Category browse           | Editorial | Retailers create a retail channel navigation category hierarchy to set up a category structure for products that they offer through their online. |
| 1 | Search results           | Search-query | This list shows products that best-match the search query by the shopper.|
| 1 | Related products           | Editorial | This list shows products configured as related products in the back office by a Merchandising manager for the relation type chosen by the author.|
| 1 | Curated product lists    | Editorial | Here are the custom lists created in the back office by merchandizers and editors.|
| 3 | New                        | Algorithmic | This list shows the newest products assorted to channels and catalogs.|
| 4 | Best selling               | Algorithmic | This list shows products ranked by the highest number of sales.                      |               
| 5 | Trending                   | Algorithmic | This list shows the highest performing products for a given time period.|
| 6 | Frequently bought together | AI / ML  | This list uses machine learning to analyze consumer purchase patterns to recommend related items that are commonly purchased for a given seed item.|
| 7 | People also like           | AI / ML | This list uses machine learning to analyze consumer purchase patterns to recommend related items for a given seed item.|

# How to add a category/search to your website pages

> **Note**: This is a generic setup for a list page, which currently encompasses both Category and Search pages. They can be created using the same template, or using different templates both based on the "Category Page" module, depending on desired enrichment experience. 

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
   
   > **Note**: All of the aforementioned modules should be authorable by following supporting self-explanatory tooltips for every configuration in the tools.  

Once you are happy with the template, Check-in and publish the template. Then we have to create both a Search Page and a Category Page based on these templates. 

 > **Note** : These pages will work in a contextual manner, as for category page there will be no default category to use, and for search page there will be no search query. 
 
1. Go to your site and create a new page  - choose the template you may have created in the above steps. 

1. Go to the Page editor for your page & observe the Page Outline on the left
>*Notice only modules (with MinOccurs =1) that were associated with slots as part of template definition, found under the category page, are readily available with template-based configurations.* 
1. Once the pages have been authored and checked in/published, you should create the appropriate URLs for the pages: 
   1.*Search Page: should have a URL path of '/search'*
       1. Go to URLs > Create a new URL and associate your search page
       ![searchPageToURLAssociation](./media/SearchURL_page_association.png)
   1.*Category Page: should have an alias of 'category-default'. By using the category-default alias, you should now be able to select a category to populate the page for WYSIWYG page editing.* 
       1. Go to URLs > Create a new Alias and associate your category page
       ![category-default-alias](./media/CategoryDefaultAlias.png)
 
 
# How to add a product collection to a category page and make an enriched category page

1. Go to sites, create a new page and choose the template same as your default category page
1. From the page editor (assuming you are able to check out the page). From Page Outline, select 'Sub footer slot' and 'Add container'
1. Upon adding container - choose to 'Add module'
1. Next, choose 'Product collection' module
1. Configure settings to choose appropriate data source and inputs for product collection
   1. From Product Collection module settings - click on '+ Add a product list'
   1. From Type you may be able to select the following 



> Related Articles:
>  -	Learn here more about [Omni-channel Product Recommendations Overview](product-recommendations-overview.md)
>  -	Learn here how to [Create curated product lists]( create-editorial-recommendation-lists.md)
>  -	If you're having issues with Algorithmic lists or AI/ML based lists use this link [Product recommendations FAQ]( faq-recommendations.md) 
