---
# required metadata

title: Add a feature module to a page 
description: This topic covers feature modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
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

This topic covers feature modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A feature module is used to market products or promotions through a combination of images and text. For example, a retailer can add a feature module to a product details page to highlight the features of the product.

A feature module is driven by data from the content management system (CMS). It's a stand-alone module that doesn't depend on any other modules on the page. A feature module can be put on any site page where a retailer wants to market or promote something (for example products, sales, or features).

## Examples of feature modules in e-Commerce

A feature module can used on the following pages:

- A product details page, to showcase product features
- The home page, to promote products
- A category page, to highlight a category of products

## Feature module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Image             | Image file | An image can be used to market the product or promotion. An image can be uploaded to the image gallery, or an existing image can be used. |
| Heading           | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Every feature module can have a heading. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |
| Paragraph         | Paragraph text | Feature modules support paragraph text in rich text format. Some basic rich text capabilities are supported, such as bold, underlined, and italic text, and hyperlinks. Some of these capabilities can be overridden by the page theme that is applied to the module. |
| Link              | Link text, link URL, Accessible Rich Internet Applications (ARIA) label, and **Open link in new tab** | Feature modules support one or more "call to action" links. If a link is added, link text, a URL, and an ARIA label are required. ARIA labels should be descriptive to meet accessibility requirements. Links can be configured so that they are opened on a new tab. |
| Image placement   | **Right**, **Left**, **Top**, or **Bottom** | This property defines the position of the image relative to the text. For example, if **Right** is selected, the image appears to the right of the text. |
| Image column size | A value from **1** through **12** | This property defines the size of the image relative to the text. Size is expressed as a number of columns on the page. There are 12 columns on a page. By default, the image and text have equal size (six columns each). However, the size can be adjusted as required. |

## Add a feature module to a new page 

To add a feature module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and create a page template that is named **feature template**.
1. In the **Main** slot of the default page, add a feature module.
1. Check in the template, and publish it.
1. Use the feature template that you just created to create a page that is named **feature page**.
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, under **Select Modules**, select a feature module, and then select **OK**.
1. In the outline tree on the left, select the feature module.
1. In the properties pane on the right, select **Add an image**. Then either select an existing image or upload a new image.
1. Select **Heading**.
1. In the **Heading** dialog box, add the heading text, select the heading level, and then select **OK**.
1. Under **Rich Text**, add text as you require.
1. Select **Add Action Link**.
1. In the **Action Link** dialog box, add link text, a link URL, and an ARIA label for the link, and then select **OK**.
1. Save the page, and preview your changes.
1. Check in the page, and publish it.
