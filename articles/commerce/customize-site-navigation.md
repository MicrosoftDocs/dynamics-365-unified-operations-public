---
# required metadata

title: Customize site navigation
description: This topic describes how to create a customized online navigation hierarchy to organize your products for browsing on your Microsoft Dynamics 365 Commerce site.
author: bicyclingfool
manager: annbe
ms.date: 12/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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


[!include [banner](includes/banner.md)]

This topic describes how to create a customized online navigation hierarchy to organize your products for browsing on your Microsoft Dynamics 365 Commerce site.

## Overview

Online storefronts typically let customers discover and browse products by navigating through product categories. This capability is usually provided by tabs at the top of the page or by a navigation bar on the left. In Dynamics 365 Commerce, you can create and manage the hierarchal structure of your category navigation and the products that are included in the various categories.

## Create a channel navigation hierarchy

To create a channel navigation hierarchy, follow these steps.

1. Go to **Retail and Commerce \> Products and categories \> Category and product management**.
1. Select **Category hierarchies**, and then select **New**.
1. Name the hierarchy.

    > [!NOTE]
    > The topmost category that you create is the root category node. It won't be shown on your site. To create a category hierarchy where a single top-level node is shown on your site, create and name the category as a child of the root category.

1. Select **New category node**, and name the category.
1. Continue to create sibling and child categories as you require.

You can now assign products to each category that you created under the top-level category.

## Customize the order of categories

By default, the categories that you define will appear in alphabetical order on your site. However, you can also customize the display order of categories.

## Assign a category hierarchy type

1. Go to **Retail and Commerce \> Products and categories \> Category and product management**.
1. Select **Category hierarchies**.
1. On the Action Pane, on the **Category hierarchy** tab, in the **Set up** group, select **Associate hierarchy type**.
1. Select **New**.
1. In the **Category hierarchy type** field, select **Channel navigation hierarchy**.
1. In the **Category hierarchy** field, select the channel navigation hierarchy that you created earlier.

## Publish new or updated navigation hierarchies

To make your navigation hierarchy available to your online storefront, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. In the tree on the left, select your online store.
1. Select **Publish channel updates**.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. In the list, find and select **Job 1040**.
1. Select **Run now**.
1. Repeat steps 5 and 6 for jobs 1070 and 1150.

## Show categories on your site

To show your category hierarchy on your online storefront, you must add the navigation menu module in the appropriate location in a template or fragment. The navigation menu module will then show your navigation hierarchy, provided that you've published your navigation hierarchy to the channel that your site is bound to.

> [!NOTE]
> The navigation menu module that is included in the store starter kit lets users navigate only to categories that don't have subcategories. If your customers should be able to navigate to categories that have subcategories, you must customize the navigation menu module.

## Add custom navigation options

On your navigation menu, you can add navigation options that aren't part of your product category hierarchy. For example, at the end of the list of product categories, you can add a **Contact Us** item that points to a contact page that you've built for your site.

To add custom navigation options to your navigation menu, follow these steps.

1. In the template or fragment that you want to customize, select the navigation menu module.
1. In the property pane, on the **Data** tab, select **Add item** to create a new content management system (CMS) navigation item.
1. Enter link text and a URL.
1. Repeat steps 2 and 3 to add more custom navigation options.
1. When you've finished, save the template or fragment, and check it in.

## Additional resources

[Templates and layouts overview](templates-layouts-overview.md)

[Work with templates](work-with-templates.md)

[Work with preset layouts](work-with-layouts.md)

[Work with fragments](work-with-fragments.md)

[Work with modules](work-with-modules.md)

[Create a page URL](create-page-url.md)

[Work with publish groups](publish-groups.md)
