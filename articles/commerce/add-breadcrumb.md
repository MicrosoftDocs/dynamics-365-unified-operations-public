---
# required metadata

title: Breadcrumb module 
description: This topic covers breadcrumb modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 05/25/2020
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

This topic covers breadcrumb modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Breadcrumb modules are used to provide secondary navigation on site pages, and are typically displayed on the top of a page below the header. Breadcrumb modules can be added to any page, but are most commonly used on product details pages (PDPs) to show the product category hierarchy and provide a quick way to navigate around a site. A breadcrumb module can also be used to show a "Back to results" link when a user navigates to a product details page from a search or list page, which helps the user quickly return to their filtered list page to continue their shopping journey.

On pages that have product category context such as PDP and category pages, breadcrumb modules show the category hierarchy. If a page does not have category context, the breadcrumb it will default to displaying **&lt;Site root&gt; / &lt;Current page&gt;**. The breadcrumb module can also be manually configured on other types of site pages to display links to specific pages within the site.

On PDPs, there are some behavior variations that breadcrumb supports. In some cases, retailers may want to show a "Back to results" link instead of a product category hierarchy, for example if a user has navigated to a PDP from a search or category page. 

The following image shows an example of a breadcrumb displaying the category hierarchy on a product details page.

![Example of a breadcrumb module](./media/ecommerce-breadcrumb.PNG)

## Breadcrumb module settings

The module relies on the **Breadcrumb display type on PDP** feature, which is defined in site builder under **Site Settings \> Extensions**. The feature has three possible settings:

**Show category hierarchy only** - When this setting is applied, breadcrumb will show the full category hierarchy of the viewed product on the product details page.

**Show back to results only** - When this setting is applied, breadcrumb will show a back to results link on the PDP if the user navigated to the PDP from a module that allows back to results. When a user navigates from a Category page or a Search page to a PDP, some retailers show back to results instead of category hierarchy. However, this could be applicable for list pages and recommendation lists as well. To support this scenario, **Product collection** and **Search results** modules have a module property called **Allow back to results on PDP**. This provides the flexibiltiy to define which scenarios should support the back to results on the PDP.  E.g. When this site setting is turned ON AND search results module for Search page has "Allow back to results on PDP" turned ON - if a user navigates from search page to a PDP, the back to results is shown.  If a user navigates to a PDP from a recommendation list in this case, back to results will not be shown, instead it will fallback to category hierarchy. By providing this additional flexibility in the module, the site author can decide which scenarios should support back to results on the PDP.

**Show category hierarchy and back to results** - This setting is a combination of the above two. When this setting is applied, breadcrumb will show the full category hierarchy and back to results on the PDP. 

## Breadcrumb module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Root          | Link| An optional property that defines a site root for the breadcrumb, for example "Home," "Storefront," etc. If not configured, no root will be defined|
| Breadcrumb link  | Link | An optional property that defines links for a manually configured breadcrumb, if needed. Links appear in the order they are listed.|

## Add a breadcrumb module to a new page

To add a breadcrumb module to a PDP and set the required properties, follow these steps.

1. Go to **Site Settings /> Extensions** and under **Breadcrumb display type on PDP**, select "Show category hierarchy" from the drop down menu.
1. Go to **Templates**, and select the PDP template.
1. In the **Container** slot that contains the buy box module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Breadcrumb** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages** and open a PDP page that uses the PDP template. If a PDP page doesn't yet exist, create one. 
1. In the **Container** slot that contains the buy box module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Breadcrumb** module, and then select **OK**.
1. In the properties pane of the **Breadcrumb** slot, select **Link text** under **Root**.
1. In the **Link text** dialog box, enter "Home", and then select **+Add a link** under **Link target**.
1. In the **Add a link** dialog box, select a link for the breadcrumb root, and then select **OK**. 
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Search results](category-search-page-overview.mdt.md)

[Product collection](product-collection-module-overview.md)

[Buy box](add-buy-box.md)

