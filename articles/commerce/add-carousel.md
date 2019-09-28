---
# required metadata

title: Add a carousel module to a page 
description: This topic covers carousel modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
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

This topic covers carousel modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A carousel module is used to put multiple promotional items in a carousel that customers can browse. It's a special container module that hosts other modules. For example, a retailer can use a carousel module on a home page to showcase multiple new products or promotions.

You can add hero and feature modules inside a carousel module. The properties of the carousel module then define how those modules are rendered.

## Examples of carousel modules in e-Commerce

- A carousel that has multiple promotional modules inside it can be used on a home page.
- A carousel that has multiple promotional modules inside it can be used on a product details page.
- A carousel can be used on any marketing page to promote multiple promotions or products.

## Carousel module properties

| Property name             | Value                                | Description |
|---------------------------|--------------------------------------|-------------|
| Autoplay                  | **True** or **False**                | If the value is set to **True**, the transition between items inside the carousel occurs automatically. If the value is set to **False**, no transition occurs unless the customer uses the keyboard or mouse to move from one item to the next item. |
| Slide transition interval | A value in seconds                   | The interval for transitions between items. |
| Transition animation      | **Slide** or **Fade**                | The transition effect. |
| Width                     | **Fit container** or **Fill screen** | If the value is set to **Fit container**, the items inside the carousel are restricted to the width of the carousel. If the value is set to **Fill screen**, the items aren't restricted to the carousel width but can go into full-screen mode. You can change the value to achieve the desired layout. |

## Add a carousel module to a page

To add a carousel module to a new page and set the required properties, follow these steps.

1. Create a page template that is named **carousel template**.
1. In the **Main** slot of the default page, add a carousel module.
1. Add a hero module to the carousel module.
1. Add a feature module to the carousel module.
1. Check in the template, and publish it. 
1. Use the carousel template that you just created to create a page that is named **carousel page**.
1. In the **Main** slot of the new page, add a carousel module.
1. Set the **Width** property of the carousel module to **Fill screen**. 
1. Set the **Transition animation** property to **Slide**.
1. Add a hero module to the carousel module.
1. In the hero module, add an image and a heading, and then select **Save**.
1. Add a feature module to the carousel module.
1. In the feature module, add an image, a heading, and a paragraph of text.
1. Save and preview the page. The page should show a carousel that has two modules inside it (a hero module and a feature module). You can change additional properties for the carousel, hero, and feature modules to achieve the desired effect.
1. Check in the page, and publish it.
