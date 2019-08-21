# Overview
Ratings and Reviews on e-Commerce website helps consumers (C2) directly to understand how a product is perceived by fellow consumers and make a purchase decision. E-Commerce website is also a primary source for receiving feedback from end users in the form of ratings and reviews on a product. This document explains how to configure your e-Commerce website and pages to show ratings and reviews as follows:

1. E-Commerce site configuration.
2. Product details page - buy box configuration.
3. Ratings histogram and reviews list on product details page (PDP). 
4. Privacy and policy link configuration.


## E-Commerce site configuration  

Ratings and reviews configuration values like tenantId, review text length etc. are configured at site level. The following steps explains on how to configure those values. 

1. Go to e-Commerce authoring tool.
2. On the home page, under sites list, click on your site name. 
3. On the left navigation menu, click on Site management, and then click on Extensibility in the left navigation. 
4. Configure tenantID e.g. d247ff89-1bb8-42bf-955e-a731fbc57c75, which you can find in your D365 LCS settings. 
5. Configure Review text length value (maximum 1000 characters). 
6. Configure Review Title max length (maximum 55 characters). 
7. Click "Save and Publish" link at the top to publish your site configurations. 


Refer to the below screenshot for more details:

![eCommerce site settings - Ratings and Reviews ](media/rnr-eCommerce-site-appsettings.png)



## Product details page - buy box configuration  

On product details page, rating summary is showed below the product title at the top of page. Rating summary also can be a link to reviews section on the product details page. To make rating summary as a link to reviews list, use the following steps:  

1. Go to product details page template that you have created for your e-Commerce website. 
2. Go to Buy box container module settings
3. Choose Product ratings module under Buy box, then check "Link the click to full reviews module"


Refer to the below screenshot for more details:
![eCommerce site settings - Ratings and Reviews ](media/rnr-eCommerce-buy-box-rating-summary.png)

## Ratings histogram and reviews list on product details page (PDP) 

Ratings summary is showed across the sites in the products placement lists, category lists, and search results etc. Ratings summary along with review list will be showed on product details page, also allows consumers to submit a rating and review on a product on product details pages.  There are multiple modules those needs to be configure to show ratings summary, write review, and reviews list on product details page as follows:

1. Write review module. 
2. Product reviews list module. 
3. Ratings histogram module.

Refer to the below screenshot for more details on how the ratings and reviews modules are structured on product details page :

![eCommerce site settings - Ratings and Reviews ](media/rnr-eCommerce-pdp-reviews-modules_design.png)

### Write review module 
Write review module allows users to sign-in, give a rating, and write a review on a product. The same module also allows users to edit the previously given rating and review.  This module is typically placed above the Reviews list and Rating histogram modules on product details page.

Below screenshot shows how review submission module would look like when use clicks on "Write a review"
![e-Commerce site settings - Write review module ](media/rnr-eCommerce-write-review-module.png)

| Property name     | Values                                                       | Property Description                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Name             | Write review                                                   | This is name of the "Write review" module|


### Product Reviews list module 
Product reviews module is used to display list of product’s reviews along with sort, filter, and pagination options. This module is typically placed on product details page.



| Property name     | Values                                                       | Property Description                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| reviews shown on each page             | 10                                                   | Count of reviews to be showed in a pagination model. User will see next and previous buttons to paginate through the reviews. |




### Ratings histogram module 
Ratings histogram module shows ratings summary and histogram of a product’s rating. This module is typically placed above the Product Review List module on product details page.

This module has no additional configurations required, apart from adding it within the Reviews list module. 


Refer to the below screenshot for more details on how PDP template would look like with ratings and reviews modules on product details page:

![eCommerce site settings - Ratings and Reviews ](media/rnr-eCommerce-pdp-reviews-modules.png)



## Privacy and policy link configuration  

Refer to the below screenshot for more details on how to configure Ratings and review "Privacy and policy" link that is showed on "Write review" module:

1. Go to e-Commerce authoring tool.
2. On the home page, under sites list, click on your site name. 
3. On the left navigation menu, click on Site management, and then click on Extensibility in the left navigation. 
4. Click on "Routes" tab at the top of "Extensibility" section. 
5. Find RNR Privacy and Policy link section, and choose the page with Privacy and policy terms you have created for you site. 
6. Click "Save and Publish" link at the top to publish your site configurations. 


![eCommerce site settings - Privacy and policy link ](media/rnr-eCommerce-rnr-privacy-policy-link.png)

