---
# required metadata

title: Text block module
description: This topic covers text block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 05/25/2020
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


[!include [banner](includes/banner.md)]

This topic covers text block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A text block module is a module that is used to add textual content. This content can be informational or promotional.

Text block modules are driven by data from the content management system (CMS) and can be put on any page. They are stand-alone modules that don't depend on page context or any other modules.

## Examples of text block modules in e-Commerce

Text block modules can be used in the following ways:

* To showcase product features on a product details page.
* For informational purposes on any page. For example, they can explain the benefits of loyalty programs, describe shipping and return policies, answer frequently asked questions, or provide "about us" content.
* To add custom messages on a product details page. (for example, "Free shipping for orders over $50").
* For disclaimers and contact details on product details pages, cart pages, checkout pages, and other pages (for example, "Shipping and returns are subject to store policies").

The following image shows an example of a text block module used on a home page.

![Example of a text block module](./media/ecommerce-textblock.PNG)

## Text block module properties

| Property name     | Value                                            | Description |
|-------------------|--------------------------------------------------|-------------|
| Rich text         | Rich text                                        | Paragraph text. Some basic rich text capabilities are supported, such as bold, underlined, and italic text. |
| Custom class name | A Cascading Style Sheets (CSS) class name        | The name of a custom CSS class that a developer provides to format this module. The class name should be defined in the theme pack. |
| Font size         | **Small**, **Medium**, **Large**, or **X-Large** | The font size of the content. |

## Add a text block module to a page

To add a text block module to a new page and set the required properties, follow these steps.

1. Create a page template that is named **Content template**. 
1. In the **Body** slot, add a **Default page** module.
1. Finish editing the template, and publish it.
1. Use the content template that you just created to create a page that is named **Content page**.
1. In the **Main** slot of the new page, add a container module.
1. In the property pane for the container module, set the **Width** property to **Fill container**.
1. Add a text block module to the container module. 
1. In the property pane of the text block module, add text to the **Rich text** field.
1. Finish editing the page, and publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Promo banner module](add-alert.md)

[Carousel module](add-carousel.md)

[Content block module](add-hero-module.md)

[Video player module](add-video-player.md)

