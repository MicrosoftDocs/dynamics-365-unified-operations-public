---
# required metadata

title: Customize site navigation
description: This article describes how to create a customized online navigation hierarchy to organize your products for browsing on your Dynamics 365 Commerce site.
author: bicyclingfool
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
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: StuHarg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---
# Customize site navigation

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This article describes how to create a customized online navigation hierarchy to organize your products for browsing on your Dynamics 365 Commerce site.

## Overview

Most online storefronts provide the ability for customers to discover and browse products by navigating through product categories. This capability is typically provided using tabs at the top of the page or a left navigation bar. 

In Commerce, you can create and manage the hierarchal structure of your category navigation and the products contained within those categories. 

## Create a retail channel navigation hierarchy

To create a retail channel navigation hierarchy, do the following.

1. Go to **Retail > Products and categories > Category and product management**.
1. Click **Category hierarchies**, then click **New**.
1. Name the hierarchy.
    - The topmost category you create is the root category node and will not be displayed on your site. If you wish to create a category hierarchy that has a single top-level node on your site, create and name that category as a child of the root category. 
1. Click **New category node** and name the category. 
1. Continue creating sibling and child categories as needed.

You can now assign products to each category you created under the top-level category. 

## Customize the order of categories

By default, the categories you define will be displayed in alphabetical order on your site. However, you can also customize the display order of categories.

## Assign a category hierarchy type

1. Go to **Retail > Products and categories > Category and product management > Category hierarchies**.
1. Under **SET UP** in the top menu, click **Associate hierarchy type**.
1. Click **New**.
1. In the dropdown in the **Category hierarchy type** column, select **Retail channel navigation hierarchy**.
1. In the dropdown in the **Category hierarchy** column, select the channel navigation hierarchy you just created.

## Publish new or updated navigation hierarchies

To make your navigation hierarchy available to your online storefront, do the following:

1. Go to **Retail > Channel setup > Channel categories and product attributes**.
1. In the tree, select your online store.
1. Click **Publish channel updates**.
1. Go to **Retail > Retail IT > Distribution schedule**.
1. In the list, find and select **Job 1040**.
1. Click **Run now**.
1. Repeat steps 6 and 7 for jobs 1070 and 1150.

## Display categories on your site

To display your category hierarchy on your online storefront, you must add the navigation menu module in the appropriate location within a template or fragment. See [Creating templates](http://) and [Creating fragments](http://) for more information. Provided that you have published your retail navigation hierarchy to the channel that your site is bound to, the Navigation menu module will display your navigation hierarchy. 

[!NOTE]
The navigation menu module that comes with the store starter kit will only allow users to navigate to categories that do not have subcategories. If you would like your customers to be able to navigate to categories that contain subcategories, you will need to customize the navigation menu module. 

## Customizing navigation options

You can also add navigation options to your navigation menu that aren't part of your product category hierarchy. For example, you can add a Contact Us menu item at the end of the list of product categories which can point to a specific page on your site that you have built for this purpose. 

To add custom navigation options to your navigation menu, do the following.

1. Select the navigation menu module within the template or fragment that you wish to customize.
1. In the property panel, click the **Data** tab.
1. Click **+Add item** to create a new CMS navigation item.
1. Enter link text and a URL.
1. Repeat steps 3 and 4 to add more custom menu items.
1. When finished, save and check in the fragment. 

 

 

 

 

 
