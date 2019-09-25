---
# required metadata

title: Add content placement modules to a page
description: This topic covers content placement and content placement item modules, and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Add content placement modules to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers content placement and content placement item modules, and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A content placement module is a special container that other modules can be put inside in a specific layout. Content placement modules support the following types of modules as child modules: content placement item, account welcome item, account order item, account wish list item, and account profile item.

Content placement modules derive data from the child modules that they support. Therefore, content placement modules can be used in various ways, depending on the modules that are added to it.

Content placement item modules use both images and text to showcase promotions, policies, and product features. For example, a content placement item module can be used on a home page to show store policies or shipping information. Content placement item modules are driven by data from the content management system (CMS) and can be put on any page. However, they can be used only inside a content placement module.

## Examples of content placement modules in e-Commerce

* Content placement modules that contain content placement item modules can be used on a home page or marketing pages to showcase product features, promotions, store policies, shipping information, and other information through both images and text.
* Content placement modules that contain content placement item modules can be used on product details pages to showcase product features.
* Content placement modules that contain account welcome item or account order item modules can be used on account management pages.

## Content placement module properties

| Property name | Value | Description |
|---------------|-------|-------------|
| Width         | **Fit container** or **Fill screen** | If the value is set to **Fit container**, the items inside the content placement module are restricted to the width of the content placement module. If the value is set to **Fill screen**, the items aren't restricted to the width of the content placement module but can go into full-screen mode. |

## Content placement item module properties

| Property name | Value | Description |
|---------------|-------|-------------|
| Heading       | Heading text and heading tags (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Every content placement item module can have a heading. The **Heading** property supports heading tags. By default, the **H2** heading tag is used, but the heading tag can be changed to meet accessibility requirements. |
| Paragraph     | Paragraph text | Content placement item modules support paragraph text in rich text format. Some basic rich text capabilities are supported, such as bold, underlined, and italic text, and hyperlinks. Some of these capabilities can be overridden by the page theme that is applied to the module. |
| Image         | Image file | An image can be associated with the text. |
| Link          | Link URL and link text | A link can be added to the text to redirect users to a specific page. |
| Tile size     | A number from **1** through **12** | For each content placement item, this property defines the number of slots that the item should fill in the content placement module. The maximum size of the content placement module is 12 slots. If the total tile size for the first *n* items in the content placement module exceeds 12 slots, the items are wrapped to the next row. |

## Add a content placement module that contains a content placement item module to a page

To add a content placement module that contains a content placement item module to a new page and set the required properties, follow these steps.

1. Create a template that is named **content placement template**.
1. In the **Main** slot of the default page, add a content placement module.
1. In the content placement module, add a content placement item module.
1. Check in the template, and publish it.
1. Use the content placement template that you just created to create a page that is named **Content placement page**.
1. In the **Main** slot of the new page, add a content placement module.
1. In the content placement module, add a content placement item module.
1. In the property pane for the content placement item module, select an image, add a heading, add a paragraph, add a link, set the link URL, and set the tile size to **6**.
1. Repeat steps 7 and 8 to add another content placement item module that has the same tile size.
1. Save and preview the page. You should see two content placement items that appear side by side. You can adjust the **Tile size** property of each content placement item module or add more modules to achieve the desired layout.
1. Check in the page, and publish it.
