---
# required metadata

title: Add a hero module to a page 
description: This topic covers hero modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
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

# Add a hero module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers hero modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A hero module is used to market products or promotions through a combination of images and text. For example, a retailer can add a hero module to the home page of an e-Commerce site to promote a new product and attract the attention of customers.

A hero module is driven by data from the content management system (CMS). It's a stand-alone module that doesn't depend on any other modules on the page. A hero module can be put on any site page where a retailer wants to market or promote something (for example, products, sales, or features).

## Examples of hero module in e-Commerce

- A hero module can be used on the home page of an e-Commerce site to highlight promotions and new products.
- A hero module can be used on a product details page to showcase product information.
- Multiple hero modules can be put inside a carousel module to highlight multiple products or promotions.

## Hero module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Image          | Image file | An image can be used to showcase a product or a promotion. An image can be uploaded to the image gallery, or an existing image can be used. |
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Every hero module can have a heading. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |
| Paragraph      | Paragraph text | Hero modules support paragraph text in rich text format. Some basic rich text capabilities are supported, such as bold, underlined, and italic text, and hyperlinks. Some of these capabilities can be overridden by the page theme that is applied to the module. |
| Link           | Link text, link URL, Accessible Rich Internet Applications (ARIA) label, and **Open link in new tab** | Hero modules support one or more "call to action" links. If a link is added, link text, a URL, and an ARIA label are required. ARIA labels should be descriptive to meet accessibility requirements. Links can be configured so that they are opened on a new tab. |
| Text placement | **Top Left**, **Top Right**, **Top Center**, **Bottom Left**, **Bottom Right**, **Bottom Center**, **Center Left**, **Center Right**, or **Center Center** | This property defines the position of the image relative to the text. For example, if **Right** is selected, the image appears to the right of the text. |
| Text theme     | **Light** or **Dark** | A color scheme can be defined for the text, based on the background image. For example, if the image has a dark background, a light theme can be applied to make the text more visible and to meet color contrast ratios for accessibility purposes. |
| Gradient       | **True** or **False** | A gradient can be applied to the image to meet color contrast ratios for accessibility purposes. |

## Add a hero module to a new page

To add a hero module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and create a page template that is named **hero template**.
1. In the **Main** slot of the default page, add a hero module.
1. Check in the template, and publish it.
1. Use the hero template that you just created to create a page that is named **hero page**.
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, under **Select Modules**, select the hero module, and then select **OK**.
1. In the outline tree on the left, select the hero module.
1. In the properties pane on the right, select **Add an image**. Then either select an existing image or upload a new image.
1. Select **Heading**.
1. In the **Heading** dialog box, add the heading text, select the heading level, and then select **OK**.
1. Under **Rich Text**, add text as you require.
1. Select **Add Action Link**.
1. In the **Action Link** dialog box, add link text, a link URL, and an ARIA label for the link, and then select **OK**.
1. Save the page, and preview your changes.
1. Check in the page, and publish it.
