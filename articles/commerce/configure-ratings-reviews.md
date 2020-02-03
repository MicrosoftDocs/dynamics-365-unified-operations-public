---
# required metadata

title: Configure ratings and reviews
description: This topic describes how to configure your e-Commerce site to show customer ratings and reviews in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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


[!include [banner](includes/banner.md)]

This topic describes how to configure your e-Commerce site to show customer ratings and reviews in Microsoft Dynamics 365 Commerce.

## Overview

Ratings and reviews on e-Commerce websites help customers learn about products before they make a purchase decision, by showing them what other customers think about those products. For e-Commerce websites, ratings and reviews are also a mechanism for collecting customer feedback about products. 

Ratings are shown on product list pages, category list pages, search results pages, and other site pages. Ratings histograms and product reviews are shown on product details pages (PDPs). A **Write a review** button lets customers submit ratings and reviews for a product.

## Ratings and reviews modules on PDPs 

Three modules show the ratings and reviews summary on PDPs:

- Write review module
- Product reviews list module
- Ratings histogram module
 
The following illustration shows what the ratings and reviews modules look like on a PDP.

![Ratings and reviews modules on a PDP](media/rnr-eCommerce-pdp-reviews-modules_design.png)

> [!TIP] 
> For information about how to optimize PDP templates and layouts so that you can share the configurations for ratings and reviews modules among multiple PDPs on your e-Commerce site, see [Templates and layouts overview](templates-layouts-overview.md).

The following illustration shows how the **Add module** dialog box presents ratings and reviews modules in Dynamics 365 Commerce.

![Add module dialog box](media/rnr-eCommerce-pdp-adding-rnr-modules.png)

### Write review module

The write review module includes a **Write a review** button that lets users sign in, assign a rating, and write a review of a product. This module also lets users edit a rating or review that they previously submitted. This module typically appears above the ratings histogram and product reviews list modules on a PDP.

The following illustration shows the **Write a review** dialog box that appears when a customer selects **Write a review**. The customer can use this dialog box to submit a rating and a review.

![Write a review dialog box](media/rnr-eCommerce-write-review-module.png)

The following table shows the write review module property that needs to be configured in the authoring tool.

| Property name | Value        | Property description                 |
|---------------|--------------|--------------------------------------|
| Name          | Write review | The name of the write review module. |

### Ratings histogram module

The ratings histogram module shows a ratings histogram. This module typically appears between the write review module and the product reviews list module on a PDP.

The ratings histogram module requires no configuration. You just have to add the module in the PDP template. 

The following illustrations shows what a PDP template looks like in Dynamics 365 Commerce when ratings and reviews modules are configured for display on PDPs.

![PDP template when ratings and reviews are configured for display on PDPs](media/rnr-eCommerce-pdp-reviews-modules.png)

### Product reviews list module

The product reviews list module shows a list of product reviews together with sort, filter, and pagination options. This module typically appears after the ratings histogram module on a PDP.

The following table shows the product reviews list module properties that need to be configured in the authoring tool.

| Property name              | Value | Property description |
|----------------------------|-------| ---------------------|
| Reviews shown on each page | 10    | The number of reviews that should be shown at a time on a PDP. **Next** and **Previous** buttons are included, so that users can move through the pages of reviews. |

#### Ratings histogram – Summary view

The product reviews list module includes a slot where you can add a ratings histogram module. The following illustration shows how you can add a ratings histogram module in the product reviews list module in Dynamics 365 Commerce.

![Adding a ratings histogram module in a product reviews list module](media/rnr-eCommerce-pdp-rating-histogram-summary.png)

## Configure a site to show ratings and reviews

Configuration values for ratings and reviews, such as the tenant ID, review text length, and review title length, are configured at the site level. 

To configure a site to show ratings and reviews, follow these steps. 

1. Go to **Home \> Sites**.
1. Select the name of your site. 
1. Go to **Site management \> Extensibility**. 
1. In the **Review Text Max Length** field, enter the maximum number of characters that review text can have (for example, **1000**). 
1. In the **Review Title Max Length** field, enter the maximum number of characters that review titles can have (for example, **55**). 
1. Select **Save and Publish**. 

The following illustration shows what this configuration looks like in Dynamics 365 Commerce.

![Configuring a site to show ratings and reviews](media/rnr-eCommerce-site-appsettings.png)

## Link a product rating to the Reviews section of a PDP

A product rating is shown below the product title at the top of PDP. The product rating can be configured so that it's linked to the **Reviews** section of the same PDP. 

To link a product rating to the **Reviews** section of the PDP, follow these steps.

1. Open the PDP template. 
1. Go to **Buy box container module settings**.
1. Under **Buy box**, select **Product ratings**, and then select the **Link the click to full reviews module** check box.

The following illustration shows what this configuration looks like in Dynamics 365 Commerce.

![Linking a product rating to the Reviews section of a PDP](media/rnr-eCommerce-buy-box-rating-summary.png)

## Configure the link for the privacy and policy page

To configure the link for the privacy and policy page, follow these steps.

1. Go to **Home \> Sites**.
1. Select the name of your site. 
1. Go to **Site management \> Extensibility**
1. On the **Routes** tab, under **RNR Privacy and Policy**, select **Add a link**. If a link is already entered, and you want to replace it, select the link. 
1. In the **Add a link** dialog box, select the link for the privacy and policy page, and then select **OK**. 
1. Select **Save and Publish**. 

The following illustration shows what this configuration looks like in Dynamics 365 Commerce.

![Configuring the link for the privacy and policy page](media/rnr-eCommerce-rnr-privacy-policy-link.png)

## Additional resources

[Ratings and reviews overview](ratings-reviews-overview.md)

[Opt in to use ratings and reviews](opt-in-ratings-reviews.md)

[Manage ratings and reviews](manage-reviews.md)

[Sync product ratings in Dynamics 365 Retail](sync-product-ratings.md)
