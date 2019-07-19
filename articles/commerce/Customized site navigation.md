This article discusses how you create an online navigation hierarchy to organize your products for browsing on your Dynamics 365 e-Commerce site.

Most online storefronts provide the ability for your customers to discover and browse for product by navigating through product categories. This capability is typically provided through tabs at the top of the page or through a left navigation bar. 

You create and manage the hierarchal structure of your category navigation and the products contained in those categories in back office. 

## Create a retail channel navigation hierarchy

1. Go to Retail > Products and categories > Category and product management
2. Click Category hierarchies.
3. Click New
4. Name the hierarchy
5. Click New category node and name the category. NOTE: the topmost category you create is your root category node and will not be displayed on your site. If you wish to create a category hierarchy that has a single top-level node on your site, create and name that category as a child of your root category. 
6. Continue creating sibling and child categories as needed.

You can now assign products to each category you created under the top-level category. 

## Customize the order of categories

By default, the categories you define will be displayed in alphabetical order on your site. However, You can also customize the display order of categories.

## Assign a category hierarchy type

1. Return to Category and product management and click on **Category hierarchies**
2. Click **Associate hierarchy type** below **SET UP** in the top menu
3. Click **New**
4. In the dropdown in the **Category hierarchy type** column, select **Retail channel navigation hierarchy**
5. In the dropdown in the **Category hierarchy** column, select the channel navigation hierarchy you just created.

 

## Publishing new or updated navigation hierarchies

To make your navigation hierarchy available to your online storefront, execute the following steps:

1. Go to **Retail** > **Channel setup** > **Channel categories and product** **attributes**
2. In the tree, select your online store
3. Click **Publish channel updates**
4. Go to Retail > Retail IT > Distribution schedule
5. In the list, find and select Job 1040
6. Click **Run now**
7. Repeat steps 6 and 7 for jobs 1070 and 1150

 

## Display categories on your site

To display your category hierarchy on your online storefront, you will add the Navigation menu module in the appropriate location within a template or fragment. See the [Creating templates](http://) and [Creating fragments](http://) help topics for more information. Provided that you have published your retail navigation hierarchy to the channel that your site is bound to, the Navigation menu module will display your navigation hierarchy. 

NOTE: The Navigation menu module that comes with the Store Starter Kit will only allow users to navigate to categories that do not have subcategories. If you would like your customers to be able to navigate to categories that contain subcategories, you will need to customize the Navigation menu module. 



## Customizing navigation options

You can also add navigation options to your navigation menu that aren't part of your product category hierarchy in HQ. For instance, you can add a Contact us menu item at the end of the list of product categories which can point to a specific page on your site that you have built for this purpose. 

To add custom navigation options to your navigation menu:

1. Select the navigation menu module within the template or fragment that you wish to customize
2. In the property panel, click on the Data tab
3. Click **+Add item** to create a new CMS nav item
4. Provide link text and a URL
5. Repeat steps 3 and 4 to add more custom menu items.

When finished, save the fragment and check it in. 

 

 

 

 

 