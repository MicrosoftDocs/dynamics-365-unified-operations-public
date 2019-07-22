# Overview
Ratings and Reviews on eCommerce website helps consumers (C2) directly to understand how a product is perceived by fellow consumers and make a purchase decision. eCommerce website is also a primary source for receiving ratings and reviews on a product. This document explains how to configure your eCommerce website and pages to show ratings and reviews.

## Site configuration  

There are some values like Ratings and Reviews Service endpoint, review text length etc. are configured at site level. The following explains on how to configure those values. 

	1. Go to ….. Tool
	2. Got to Site Setting 
	3. Configure Ratings and Reviews Service endpoint as https://<tenanteID>.rnr.ms/
Configure Review text length value (maximum 1000 characters


##Ratings and review on product details page (PDP) 

Ratings summary is showed across the sites in the products placement lists, category lists, and search results etc. Ratings summary along with review list will be showed on product details page, also allows consumers to submit a rating and review on a product on product details pages.  There are multiple modules those needs to be configure to show ratings summary, write review, and reviews list on product details page as follows:

	1. Product reviews list module 
	2. Write review module 
	3. Ratings histogram  module 

## Product Reviews list module 
Product reviews module is used to display list of product’s reviews along with sort, filter, and pagination options. This module is typically placed on product details page.

-<Image to be placed>




| Property name     | Values                                                       | Property Description                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Image             | Image file                                                   | This is the image that will be used for marketing the product or   promotion. An image can uploaded to the image gallery or an existing   image can be used. |
| Heading           | Heading text<br />Heading tag = H1, H2, H3, H4, H5, H6       | A Feature has a heading. Heading supports heading tag which defaults   to H2 but can be changed to meet accessibility requirements. |
| Paragraph         | Paragraph text                                               | Feature supports paragraph in rich text format. Some basic rich text   functionality is supported such a Bold, Underline, Italics, hyperlinks etc. Some of these capabilities may be overridden by the page theme applied on the module. |
| Link              | Link text<br />Link url<br />Aria label<br />Open link in new tab | A Feature can have one or more call to   actions. E.g. “Shop Now” which redirects the shopper to the link. If a link   is added, link text, url and aria label must be provided.<br />Aria-label should be descriptive for   accessibilty.<br />If user wants to open the link in a new   tab, that can be configured. |


## Write review module 
Write review module allows users to sign-in, give a rating, and write a review on a product. The same module also allows users to edit the previously given rating and review.  This module is typically placed above the Product Reviews List and Ratings Histogram modules on product details page.

-<Image to be placed>




| Property name     | Values                                                       | Property Description                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Image             | Image file                                                   | This is the image that will be used for marketing the product or   promotion. An image can uploaded to the image gallery or an existing   image can be used. |
| Heading           | Heading text<br />Heading tag = H1, H2, H3, H4, H5, H6       | A Feature has a heading. Heading supports heading tag which defaults   to H2 but can be changed to meet accessibility requirements. |
| Paragraph         | Paragraph text                                               | Feature supports paragraph in rich text format. Some basic rich text   functionality is supported such a Bold, Underline, Italics, hyperlinks etc. Some of these capabilities may be overridden by the page theme applied on the module. |
| Link              | Link text<br />Link url<br />Aria label<br />Open link in new tab | A Feature can have one or more call to   actions. E.g. “Shop Now” which redirects the shopper to the link. If a link   is added, link text, url and aria label must be provided.<br />Aria-label should be descriptive for   accessibility.<br />If user wants to open the link in a new   tab, that can be configured. |


## Ratings histogram module 
Ratings histogram module shows ratings summary and histogram of a product’s rating. This module is typically placed above the Product Review List module on product details page.


-<Image to be placed>




| Property name     | Values                                                       | Property Description                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Image             | Image file                                                   | This is the image that will be used for marketing the product or   promotion. An image can uploaded to the image gallery or an existing   image can be used. |
| Heading           | Heading text<br />Heading tag = H1, H2, H3, H4, H5, H6       | A Feature has a heading. Heading supports heading tag which defaults   to H2 but can be changed to meet accessibility requirements. |
| Paragraph         | Paragraph text                                               | Feature supports paragraph in rich text format. Some basic rich text   functionality is supported such a Bold, Underline, Italics, hyperlinks etc. Some of these capabilities may be overridden by the page theme applied on the module. |
| Link              | Link text<br />Link url<br />Aria label<br />Open link in new tab | A Feature can have one or more call to   actions. E.g. “Shop Now” which redirects the shopper to the link. If a link   is added, link text, url and aria label must be provided.<br />Aria-label should be descriptive for   accessibilty.<br />If user wants to open the link in a new   tab, that can be configured. |

