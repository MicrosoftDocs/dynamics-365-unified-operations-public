---
# required metadata

title: Configure ratings and reviews
description: This topic describes how to configure your e-Commerce site to display customer ratings and reviews.
author: gvrmohanreddy
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
ms.author: gmohanv
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Configure ratings and reviews

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to configure your e-Commerce site to display customer ratings and reviews.

## Overview

Ratings and reviews on e-Commerce websites help inform customers about a product before they make a purchase decision by showing them what other customers think of that product. For e-Commerce websites, they are also a source for collecting customer feedback about a product. 

This document explains how to configure your e-Commerce website and pages to show ratings and reviews as follows:

1. E-Commerce site configuration.
2. Product details page - buy box configuration.
3. Ratings histogram and reviews list on product details page (PDP). 
4. Privacy and policy link configuration.

## Configure a site to display ratings and reviews  

Ratings and reviews configuration values such as tenant ID, review text length, and review title length are configured at the site level. 

To configure a site to display ratings and reviews, do the following. 

1. Go to **Home > Sites**.
1. Click on your site name. 
1. Go to **Site management > Extensibility**. 
1. In the **Ratings/Reviews tenant id** box, enter your tenant ID (for example, d247ff89-1bb8-42bf-955e-a731fbc57c75). You can find the tenant ID in your Dynamics 365 Lifecycle Services settings. 
1. In the **reviewTextMaxLength** box, enter the review text maximum length value (maximum 1000 characters). 
1. In the **reviewTitleMaxLength** box, enter the review title maximum length value (maximum 55 characters). 
1. Click **Save and Publish**. 

Refer to the below screenshot for more details:

![eCommerce site settings - Ratings and Reviews ](media/rnr-eCommerce-site-appsettings.png)

## Link a rating to the reviews section of a product details page 

On a product details page, a rating is shown below the product title at the top of page. The rating can be configured to link to the reviews section of the same product details page. 

To link the rating to the reviews section of the product detail page, do the following.  

1. Open the product details page template. 
2. Go to **Buy box container module settings**.
3. Under **Buy box**, select **Product ratings** , then check **Link the click to full reviews module**.

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

## Configure the privacy and policy link  

Refer to the below screenshot for more details on how to configure Ratings and review "Privacy and policy" link that is showed on "Write review" module:

1. Go to **Home > Sites**.
1. Click on your site name. 
1. Go to **Site management > Extensibility**
4. Click the **Routes** tab. 
5. Under **RNR Privacy and Policy**, click **Add a link**. If a link is already entered and you want to replace it, click the link. 
1. In the Add a link dialog box, select the link for the privacy and policy page, then click **OK**. 
6. Click **Save and Publish**. 

![eCommerce site settings - Privacy and policy link ](media/rnr-eCommerce-rnr-privacy-policy-link.png)

