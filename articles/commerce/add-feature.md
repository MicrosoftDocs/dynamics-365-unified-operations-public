---
# required metadata

title: Add a feature module to a page 
description: This topic covers feature module modules and how to add them to site pages in Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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

# Add a feature module to a page 

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers feature module modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

The Feature module is used for marketing products or promotions using a combination of image and text. For example, on the product details page a retailer can add a Feature module that uses both image and text to highlight the capabilities of the product. 

Feature module is driven by CMS data which can authored in the tooling. It’s a standalone module and does not have dependency on page context on any other modules in the page. Technically this allows Feature to be placed on any page where a C1 wants to promote content.

## e-Commerce scenarios


- Feature is used on the product details page to showcase the product features
- Feature can be used on the home page to promote products
- Feature can be used on a category page to highlight the category of products

## Feature module properties

|   Property name   | Values                                                       | Property Description                                         |
| :---------------: | :----------------------------------------------------------- | :----------------------------------------------------------- |
|       Image       | Image file                                                   | This is the image that will be used for marketing the product or   promotion. An image can uploaded to the image gallery or an existing   image can be used. |
|      Heading      | Heading text<br /><br />Heading tag = H1, H2, H3, H4, H5, H6 | A Feature has a heading. Heading supports heading tag which defaults   to H2 but can be changed to meet accessibility requirements. |
|     Paragraph     | Paragraph text                                               | Feature supports paragraph in rich text format. Some basic rich text   functionality is supported such a Bold, Underline, Italics, hyperlinks etc. Some of these capabilities may be overridden by the page theme applied on the module. |
|       Link        | Link text<br />Link url<br />Aria label<br />Open link in new tab | A Feature can have one or more call to   actions. E.g. “Shop Now” which redirects the shopper to the link. If a link   is added, link text, url and aria label must be provided.<br />Aria-label should be descriptive for   accessibilty.<br />If user wants to open the link in a new   tab, that can be configured. |
|  Image Placement  | Right<br />Left<br />Top<br />Bottom                         | Image placement defines the position of the image relative to the text. If Right is chosen, image will be on right of the text. Four different settings are available to configure. |
| Image Column size | Values from 1-12                                             | This defines the size of the image relative to the text. In the   default experience image and text will have equal size i.e value = 6  (i.e.12 columns total on the page). This can   be configured as needed. |



## Creating a page with a Feature module

This section explains how to add a Feature module to a new page and set the required properties. Refer to Templates and Pages for more details on these actions.

1. We need to first create a template. In tooling, create a new page template “Feature template”.

2. In the **Main** slot the Default Page,, add a Feature module. A Feature can be placed directly on the page or within a container <link>. Multiple Feature modules can be placed within a Carousel<link>.

3. Check-in and Publish. 

4. Now create a new page with the “Feature template” and call it “Feature page”

5. In the page outline, add Default page. To the Main slot, add Feature module.

6. Expand the Feature properties and add Image. rom the image picker, choose an existing image or upload a new asset. 

7. Add a Heading, change the default text, size and Heading tag as needed

8. Add a Paragraph, change the default text as needed

9. Add a Link, set the link text to “Shop Now” and add a link url to the page you want to redirect. Set the Aria label to be description “Shop now for Surface Laptop sale”

10. Save the page and preview the changes.

11. Other properties can be changed to achieve a more customized Feature – Image placement, Image column size etc.

12. Check-in and Publish.

    

See Enriching a product details page for details on how to use Feature to enrich a product details page.

See Enriching a category page for details on how use Feature to enrich a category page. 
