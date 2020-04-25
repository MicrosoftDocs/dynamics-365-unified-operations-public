---
# required metadata

title: Breadcrumb module 
description: This topic covers breadcrumb module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 04/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Breadcrumb module


[!include [banner](includes/banner.md)]

This topic covers  Breadcrumb module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview
Breadcrumb module is used as secondary navigation on site pages. It provides a quick way to navigate to relevant site pages. Its most commonly used on product details page to show the product category heirarchy. This helps a user quickly navigate and find relevant products within the category heirarchy of the product or category they are viewing. It can also be used to show a Back to results option when the the user navigated to a product details page from a search or a list page. This helps the user go quickly go back to their fitlered list page to continue their shopping journey.

The breadcrumb can also be used on any other page with a curated list of breadcrumb links, e.g. on an Account management page.

Below is an example of breadcrumb on product details page showing the category heirarchy
![Example of a breadcrumb module](./media/ecommerce-breadcrumb1.PNG)

Below is an example of breadcrumb on product details page showing the back to results.
![Example of a breadcrumb module](./media/ecommerce-breadcrumb2.PNG)

Below is an example of breadcrumb on the Account management page showing the curated set of links.
![Example of a breadcrumb module](./media/ecommerce-breadcrumb3.PNG)

## Module overview
Breadcrumb is a module that can be added to any page. Its typically showcased on the top of the page below the header.

On pages that have product category context such as PDP and Category page, breadcrumb can show the category heirarchy. If a page does not have category context, it wil default to show "<Root>\<Current page>".  In addtion, the breadcrumb can be manually configured to show links to specific pages within the site.

On Product details page, there are some behavior variations that breadcrumb supports. In some cases retailers may want to show a **back to results** link instead of product heirarchy, e.g. if a user navigated to a pdp from a search or category page.  This can be acheived using this breadcrumb module.

The module relies on a site setting called **Breadcrumb display type on PDP** which is defined in **Site Settings\Extensions** in Site Builder. There are 3 settings defined,

**Show category heirarchy only** - When this setting is applied, breadcrumb will show the full category heirarchy of the viewed product on the product details page.

**Show back to results only** - When this setting is applied, breadcrumb will show a back to results link on the PDP if the user navigated to the PDP from a module that allows back to results. Typically when a user navigates from a Category page or a Search page to a PDP, some retailers show back to results instead of category heirarchy. However, this could be applicable for list pages and recommendation lists as well. To support this scenario, **Product collection** and **Search results** modules have a module property called **Allow back to results on PDP**. This provides the flexibiltiy to define which scenarios should support the back to results on the PDP.  E.g. If this site setting is turned ON and search results module for Search page has "Allow back to results on PDP" turned ON. When these two settings are on, if a user navigates from search page to a PDP, the back to results is shown.  If a user navigates to a PDP from a recommendation list in this case, back to results will not be shown, instead it will fallback to category heirarchy. By providing this additional flexibility in the module, the site author can decide which scenarios should support back to results on the PDP.

**Show category heirarchy and back to results** - This setting is a combination of the above two. When this setting is applied, breadcrumb will show the full category heirarchy and back to results on the PDP. 


## Breadcrumb module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Root          | Link| A root can be defined for the breadcrumb, E.g. Home, Storefront etc. Its an optional field, if not configured the root will be the category heirarchy or none|
| Breadcrumb link  | Link | If a page needs a manually configured breadcrumb, the links can defined via this link property. The links appear in the order they are added.|


## Add a breadcrumb module to a new page

To add a breadcrumb module to a PDP and set the required properties, follow these steps.

1. Go to Site settings/Extension and choose a **Breadcrumb style for PDP**. In this e.g. lets choose "Category heirarchy only" type
1. Go to **Templates**, and choose the PDP template 
1. In the Container for the Buy Box, add the Breadcrumb module. 
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. If you have a page for PDP, open the page or create a new page for PDP
1. In the **Container** for the BuyBox, add a module
1. In the **Add Module** dialog box, under **Select Modules**, select the Breadcrumb module, and then select **OK**.
1. In the outline tree on the left, select the Breadcrumb module
1. In the properties pane on the right, select a Root, define root as the **Home** page
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 


## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Search results](category-search-page-overview.mdt.md)

[Product collection](product-collection-module-overview.md)

[Buy box](add-buy-box.md)

