---
# required metadata

title: Add a content rich block module to a page
description: This topic covers content rich block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
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

This topic covers content rich block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A content rich block module is a special container that one or more content rich block items can be put inside. Content rich block modules are used for textual content on a page. This content can be either informational or promotional.

Content rich block modules are driven by data from the content management system (CMS) and can be put on any page. They are stand-alone modules that don't depend on page context or any other modules.

## Examples of content rich block modules in e-Commerce

Content rich block modules can be used in the following ways:

* To showcase product features on a product details page.
* For informational purposes on any page. For example, they can explain the benefits of loyalty programs, describe shipping and return policies, answer frequently asked questions, or provide "about us" content.
* To add custom messages on a product details page. (for example, "Free shipping for orders over $50").
* For disclaimers and contact details on product details pages, cart pages, checkout pages, and other pages (for example, "Shipping and returns are subject to store policies").

## Content rich block module properties

| Property name     | Value                                 | Property |
|-------------------|---------------------------------------|----------|
| Number of columns | A number from **1** through **4**     | The number of columns in the content rich block. There can be up to four columns. |
| Width             | **Fill container** or **Fill screen** | If the value is set to **Fill container**, the items inside the container are restricted to the width of the container. If the value is set to **Fill screen**, the items aren't restricted to the container width but can go into full-screen mode. You can change the value to achieve the desired layout. |

## Content rich block item module properties

| Property name | Value          | Description |
|---------------|----------------|-------------|
| Paragraph     | Paragraph text | The text that accompanies each content rich block item. Some basic rich text capabilities are supported, such as bold, underlined, and italic text. |

## Add a content rich block module to a page

To add a content rich block module to a new page and set the required properties, follow these steps.

1. Create a page template that is named **Content template**.
1. In the **Main** slot of the default page, add a content rich block module.
1. Check in the template, and publish it.
1. Use the content template that you just created to create a page that is named **Content page**.
1. In the **Main** slot of the new page, add a content rich block module.
1. In the properties of the content rich block module, set number of columns to **2**.
1. In the content rich block module, select **Add a module**, and add a content rich block item (for example, **item1**).
1. In the new content rich block item, add paragraph text.
1. In the content rich block module, select **Add a module**, and add a content rich block item (for example, **item2**).
1. In the new content rich block item, add paragraph text.
1. Save the page, and preview the changes. You should see two rich text blocks in a two-column view.
1. Check in the page, and publish it.

> [!NOTE]
> If you add a third content rich block item, it will be stacked below the two items that you previously added. By changing the number of columns and items in the container, you can achieve different layouts for textual content.
