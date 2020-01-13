---
# required metadata

title: Text block module
description: This topic covers text block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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
# Text block module

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers text block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A text block module is a module used for adding textual content that can be informational or promotional.

Text block modules are driven by data from the content management system (CMS) and can be put on any page. They are stand-alone modules that don't depend on page context or any other modules.

## Examples of text block modules in e-Commerce

Text block modules can be used in the following ways:

* To showcase product features on a product details page.
* For informational purposes on any page. For example, they can explain the benefits of loyalty programs, describe shipping and return policies, answer frequently asked questions, or provide "about us" content.
* To add custom messages on a product details page. (for example, "Free shipping for orders over $50").
* For disclaimers and contact details on product details pages, cart pages, checkout pages, and other pages (for example, "Shipping and returns are subject to store policies").

## Text block module properties

| Property name | Value          | Description |
|---------------|----------------|-------------|
| Rich text     | Rich text | Paragraph text. Some basic rich text capabilities are supported, such as bold, underlined, and italic text. |
|Custom class name| CSS class name| The name of a custom CSS class provided by a developer to format this module. The class name should be defined in the theme pack.|
|Font size| Small, Medium, Large, X-Large| This property specifies the font size for the content. |

## Add a text block module to a page

To add a text block module to a new page and set the required properties, follow these steps.

1. Create a page template that is named **Content template**. 
1. In the **Body** slot, add a **Default page** module.
1. Finish editing and publish the template.
1. Use the content template that you just created to create a page that is named **Content page**.
1. In the **Main** slot of the new page, add a container module.
1. In the **Container** property pane, set the **Width** property to **Fill container**.
1. Add a **Text block** module to the container module. 
1. In the text block module property pane, add text to the **Rich text** field.
1. Finish editing and publish the page.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Promo banner module](add-alert.md)

[Carousel module](add-carousel.md)

[Content block module](add-feature-module.md)

[Hero module](add-hero-module.md)

[Video player module](add-video-player.md)

