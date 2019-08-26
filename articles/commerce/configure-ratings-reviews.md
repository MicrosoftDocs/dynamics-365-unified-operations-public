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

Ratings are displayed on product list pages, category list pages, search results pages, and other site pages. Ratings histograms and product reviews are displayed on product details pages, along with a **Write a review** button that enables customers to submit a rating and review on a product.

### Ratings and reviews modules displayed on product details pages 

There are three modules that display the ratings and reviews summary on a product details page.

 - Write review module
 - Product reviews list module
 - Ratings histogram module
 
The following screenshot shows how the ratings and reviews modules are displayed on a product details page.

![eCommerce site settings - Ratings and Reviews ](media/rnr-eCommerce-pdp-reviews-modules_design.png)

#### Write review module

The write review module displays a button that enables users to sign in, assign a rating, and write a review on a product. This module also enables users to edit a previously submitted rating or review. This module is typically placed above the rating histogram and reviews list modules on a product details page.

The following screenshot shows how a review submission looks when a customer clicks **Write a review**.

![e-Commerce site settings - Write review module ](media/rnr-eCommerce-write-review-module.png)

| Property name     | Values                                                       | Property Description                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Name             | Write review                                                   | This is name of the "Write review" module|


#### Ratings histogram module

The ratings histogram module displays a ratings histogram on a product detail page. This module is typically placed between the write review module and reviews list module.

The ratings histogram module requires no configuration apart from adding it within the reviews list module. 

The following screenshot shows how a PDP template looks with ratings and reviews modules configured for display on product details pages:

![eCommerce site settings - Ratings and Reviews ](media/rnr-eCommerce-pdp-reviews-modules.png)

#### Product reviews list module

The product reviews module displays a list of product reviews along with sort, filter, and pagination options. This module is typically placed after the ratings histogram module on a product details page.


| Property name     | Values                                                       | Property Description                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Reviews shown on each page             | 10                                                   | Number of reviews to be displayed on a product details page. Next and previous buttons are displayed to page through the reviews. |

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
1. Go to **Buy box container module settings**.
1. Under **Buy box**, select **Product ratings** , then check **Link the click to full reviews module**.

The following screenshot shows how is done in the product details template.

![eCommerce site settings - Ratings and Reviews ](media/rnr-eCommerce-buy-box-rating-summary.png)

## Configure the privacy and policy page link  

To configure the privacy and policy page link, do the following.

1. Go to **Home > Sites**.
1. Click on your site name. 
1. Go to **Site management > Extensibility**
1. Click the **Routes** tab. 
1. Under **RNR Privacy and Policy**, click **Add a link**. If a link is already entered and you want to replace it, click the link. 
1. In the Add a link dialog box, select the link for the privacy and policy page, then click **OK**. 
1. Click **Save and Publish**. 

The following screenshot shows how the ratings and review privacy and policy link is configured.

![eCommerce site settings - Privacy and policy link ](media/rnr-eCommerce-rnr-privacy-policy-link.png)

