---
# required metadata

title: Add a content rich block module to a page
description: This topic covers content rich block modules and how to add them to site pages in Dynamics 365 Commerce.
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
# Add a content rich block module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers content rich block modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

A content rich block module is a special container that allows one or more content rich block items to be placed within it. This container allows one or more content rich block items to be placed within it. Content rich block modules are used for textual content on a page, which can be informational or promotional.

Content rich block modules are driven by CMS data and can be placed on any page. They are standalone modules that do not depend on page context or on any other modulese. 

## Examples of content rich block module uses in e-Commerce

Content rich block can be used:

* To showcase product features on a product details page.
* On any page for informational purposes (for example, benefits of loyalty programs, shipping and return policies, frequently asked questions, about us content, etc.).
* To add custom messages on a product details page (for example, "Free shipping for orders over $50"). 
* For disclaimers and contact details on product details pages, cart pages, checkout pages, etc. (for example, "Shipping and returns are subject to store policies").
 
## Content rich block module properties

|   Property name   | Values                         | Property description                                         |
| :---------------: | :----------------------------- | ------------------------------------------------------------ |
| Number of columns | 1 to 4                     | Number of columns in a content rich block, up to 4 columns      |
|       Width       | Fill container<br />Fill screen | The "fill container" value restricts items inside the container to fit within the container width. The "fill screen" property allows items inside the container to go full-bleed and does not restrict them to fit within container width.<br />The values can be changed to achieve the layout desired. |

 

## Content rich block item module properties

| Property name | Values         | Property description                                         |
| :-----------: | :--------------: | ------------------------------------------------------------ |
|   Paragraph   | Paragraph text | The text that accompanies each content rich block item. Some basic rich text capabilities such as bold, underline, and italics are supported. |

 
## Add a content rich block module

To add a content rich block module to a new page and set the required properties, do the following.

1. Create a new page template named "Content template."

1. In the **Main** slot of the default page, add a content rich block module. 

1. Check in and publish the template.

1. Create a new page named "Content page" using the content template you created.

1. In the **Main** slot of the new page, add a content rich block module.

1. Expand the content rich block module properties and set number of columns to **2**.

1. In the content rich block module, select **Add a module**, then add a content rich block item (for example, "item1"). 

1. In content rich block item 1, add paragraph text.

1. In the content rich block module, select **Add a module**, then add a content rich block item (for example, "item2"). 

1. In content rich block item 2, add paragraph text.

1. Save the page and preview the changes. You should see two rich text blocks placed in two column view. 

1. Check in and publish the page.

>[!NOTE] 
> If a third content rich block item is added, it will stack below the two items added previously. By changing the number of columns and items in the container, different layouts can be achieved for textual content.

