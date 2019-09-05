---
# required metadata

title: Add a carousel module to a page 
description: This topic covers carousel modules and how to add them to site pages in Dynamics 365 Commerce.
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

# Add a carousel module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers carousel modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

A carousel module is used to place multiple promotional items within a carousel that customers can browse. It's a special container module that hosts other modules inside of it. For example, a retailer can use a carousel module on a home page to showcase multiple new products or promotions.

You can add hero and feature modules inside a carousel module and the properties of the carousel define how these items will be rendered. 

## Examples of carousel module uses in e-Commerce

- A carousel can be placed on a home page with multiple promotional modules inside it.
- A carousel can be used on product details page with multiple promotional modules inside it.
- A carousel can be used on any marketing page to promote multiple promotions or products.

## Carousel module properties

| Property name             | Values                         | Property Description                                         |
| :------------------------ | :----------------------------- | :----------------------------------------------------------- |
| Autoplay                 | True or False                  | When the autoplay property is set to True, items inside the carousel will automatically transition.<br />When the autoplay property is set False, the items will not transition unless the customer uses the keyboard or mouse. |
| Slide transition interval | In seconds                        | Defines the interval to transition from one item to the next     |
| Transition animation      | Slide<br />Fade                | Defines if the transition effect should be slide or fade         |
| Width                     | Fit container<br />Fill screen | The fit container value restricts the items inside the carousel to fit within the carousel width. The fill screen value allows items to go full-bleed and does not restrict them within carousel width.<br />The values can be changed to achieve the layout desired. |

## Add a carousel module to a page

To add a carousel module to a new page and set the required properties, do the following. 

1. Create a new page template named "Carousel template."

1. In the **Main** slot of the default page, add a carousel module. 

1. Add a hero module to the carousel module.

1. Add a feature module to the carousel module.

1. Check in and publish the template. 

1. Create a new page named "carousel page" with the carousel template you created.

1.In the **Main** slot of the new page, add a carousel module.

1. Set the carousel module property **Width** to **Fill screen**. 

1. Set the carousel module property **Transition animation* to **Slide**.

1. Add a hero module to the carousel module. In the hero module, add an image and a heading and click **Save**. 

1. Add a feature module to the carousel module. In the feature module, add an image, a heading, and a paragraph of test.

1. Save and preview the page. The page should show a carousel with two modules inside of it (hero and feature). Additional properties for carousel, hero, or feature modules can be modified to achieve the desired effect.

1. Check in and publish the page.

