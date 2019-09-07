---
# required metadata

title: Add a content placement module to a page
description: This topic covers content placement and content placement item modules and how to add them to site pages in Dynamics 365 Commerce.
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
# Add a content placement module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers content placement and content placement item modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

A content placement module is a special container that allows modules to be placed within it in a specific layout. Content placement modules supports content placement item, account welcome item, account order item, account wish list item, and account profile item modules. A content placement module is a container of other modules and derives data from the child modules that it supports. Its usage varies based on which modules are added to it.

A content placement item module is used to showcase promotions, policies, and product features using both image and text. For example, it can be used on a home page to display store policies or shipping information. 

Content placement item modules are driven by CMS data and can be placed on any page. However, a content placement item module can only be used within a content placement module container. 

## Examples of content placement module uses in e-Commerce

* Content placement modules containing content placement item modules can be used on home or marketing pages to showcase product features, promotions, store policies, shipping information, and other informational messages using both images and text.

* Content placement modules containing content placement item modules can be used on product details pages to showcase product features.

* Content placement modules containing account welcome item or account order item modules can be used on account management pages.

## Content placement module properties

| Property name | Values                                                    | Property description                                         |
| :-----------: | :-------------------------------------------------------- | ------------------------------------------------------------ |
|     Width     | Fit container<br />Fill screen                            | The "Fill container" value restricts the items inside the content placement to fit within the content placement width.<br/>The "Fill screen" value allows the items to go full-bleed and does not restrict within carousel width. |

## Content placement item module properties

| Property name | Values                                                       | Property description                                         |
| :-----------: | :----------------------------------------------------------- | ------------------------------------------------------------ |
|    Heading    | Heading text<br /><br />Heading tag = H1, H2, H3, H4, H5, H6 | Each content placement item module can have a heading. Heading   supports heading tag which defaults to H2 but can be changed to meet   accessibility requirements. |
|   Paragraph   | Paragraph text                                               | Content placement item supports paragraph in rich text format. Some   basic rich text functionality is supported such as bold, underline, italics, hyperlinks, etc. Some of these capabilities may be overridden by the page theme applied on the module. |
|     Image     | Image                                                        | An image can be associated to the text.                      |
|     Link      | Link URL <br />Link text                                     | A link can be added to the text to redirect the user to a specific page. |
|   Tile size   | 1-12                                                         | Tile size on each content placement item defines the number of slots each item should take within the content placement container. Max size of the container is 12. If tile size for first *n* items in the content placement is over 12, it will wrap to the next row. |

 

## Add a content placement module containing a content placement item module to a page  

To add a content placement module with a content placement item module to a new page and set the required properties, do the following. 

1. Create a new template named 'content placement template."

1. In the **Main** slot of the default page, add a content placement module. 

1. In the content placement module, add a content placement item module.

1. Check in and publish the template. 

1. Create a new page named "Content placement page" with the content placement template.

1. In the **Main** slot of the Default page, add a content placement module.

1. In the content placement module, add a content placement item module.

1. In the content placement item module property pane, select an image, add a heading, add a paragraph, add a link, set the link URL, and set the tile size  to **6**.

1. In the content placement module, add another content placement item module and repeat step 8.

1. Save and preview the page. Preview will show two content placement items placed side by side. You can further alter the tile size property of each content placement item module or add more modules to achieve the desired layout. 

1. Check in and publish the page. 
