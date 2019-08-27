---
# required metadata

title: Carousel module 
description: This topic explains how to use a Carousel module in ecommerce pages
author:  anupamar 
manager: BrendanS
ms.date: 07/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: 
ms.search.industry: 
ms.author: jeffbl
ms.search.validFrom: 2019-10-01
ms.dyn365.ops.version: 
---

# Carousel

A Carousel is used to place multiple promotional items within a carousel view. It’s a special container module that hosts other modules inside it and provides a carousel for the user to browse the content. For example, on the home page a retailer can showcase multiple new products or promotions within a carousel.

You can add Hero and Feature modules inside a carousel and the properties of the carousel define how these items will be rendered. 

## Usage examples in ecommerce:

* Carousel can be placed on the home page with multiple promotional modules inside it

- Carousel can be used on product details page with multiple promotional modules inside it

- Carousel can be used on any marketing page to promote multiple promotions or products

## Carousel module properties

| Property name             | Values                         | Property Description                                         |
| :------------------------ | :----------------------------- | :----------------------------------------------------------- |
| Auto play                 | True or False                  | When auto play is true, items inside the carousel will automatically   transition.<br />When auto play is false, the items will not transition unless the user   interacts with keyboard or mouse. |
| Slide transition interval | In secs                        | Defines the interval to transition from one item to next     |
| Transition animation      | Slide<br />Fade                | Defines if transition effect should be slide or fade         |
| Width                     | Fit container<br />Fill screen | Fill container restricts the items inside the carousel to fit within   the carousel width. Fill screen allows the items to go full-bleed and does   not restrict within carousel width.<br />The values can be changed to achieve   the layout that we want. |

 

## Creating a page with a Carousel module

This section explains how to add a Carousel module to a new page and set the required properties. Refer to Templates and Pages for more details.

 

1. We need to first create a template. In tooling, create a new page template “Carousel template”.

2. In the Main slot of the Default Page, add a Carousel module. 

3. Add a Hero module to the carousel.

4. Add a Feature module to the carousel.

5. Check-in and Publish. 

6. Now create a new page with the “Carousel template” and call it “Carousel page”.

7. In the page outline, add Default Page. To the Main slot,  add Carousel module.

8. Set Carousel module property Width to Fill screen. 

9. Set Carousel module property Transition animation to Slide.

10. To the Carousel module, add a Hero module. On the Hero module, add an Image and a Heading and save. See Hero module for more details.

11. To the Carousel module, add a Feature module.  On the Feature module, add an Image, Heading and Paragraph. See Feature module for more details

12. Save and Preview.  Preview will show a carousel with 2 modules inside it -Hero, Feature. Additional propertis for Carousel, Hero or Feature can be changed to achieve the desired effect.

13. Check-in and Publish the page.

