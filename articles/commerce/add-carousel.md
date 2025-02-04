---
title: Carousel module
description: This article covers carousel modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 08/01/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Carousel module

[!include [banner](includes/banner.md)]

This article covers carousel modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

A carousel module is used to put multiple promotional items (including rich images) in a rotating carousel banner that customers can browse. For example, a retailer can use a carousel module on a home page to showcase multiple new products or promotions.

You can add content block modules inside a carousel module. The properties of the carousel module then define how those modules are rendered.

## Examples of carousel modules in e-Commerce

- A carousel that has multiple promotional modules inside it can be used on a home page.
- A carousel that has multiple promotional modules inside it can be used on a product details page.
- A carousel can be used on any marketing page to promote multiple promotions or products.

The following image shows an example of a carousel module that is used on a home page. This carousel module contains multiple content block items.

![Example of a carousel module.](./media/Hero.PNG)

## Carousel module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Autoplay                  | **True** or **False** | If the value is set to **True**, the transition between items inside the carousel occurs automatically. If the value is set to **False**, no transition occurs unless the customer uses the keyboard or mouse to move from one item to the next item. |
| Slide transition interval | A value in seconds    | The interval for transitions between items. |
| Transition type           | **Slide** or **Fade** | The transition effect between items. |
| Hide carousel flipper     | **True** or **False** | If the value is set to **True**, the carousel flipper and sequence indicator are hidden. |
| Allow carousel dismiss    | **True** or **False** | If the value is set to **True**, users can dismiss the carousel. |

## Add a carousel module to a page

To add a carousel module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New Template** dialog box, under **Template Name**, enter **Carousel template**, and then select **OK**.
1. In the **Body** slot, add a **Default page** module.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it.  
1. Use the carousel template that you just created to create a page that is named **Carousel page**.
1. In the **Main** slot of the new page, add a container module. 
1. In the pane on the right, set the **Width** value to **Fill Screen**.
1. Under **Page Outline**, add a carousel module to the container module.
1. Add a content block module to the carousel module. Set the properties of the content block module by providing **Heading**, **Link**, **Layout**, and other properties.
1. Add and configure another content block module.
1. Set additional properties for the carousel module as you require.
1. Select **Save**, and then select **Preview** to preview the page. The page should show a carousel that has two modules inside it (a hero module and a feature module). You can change additional properties for the carousel, hero, and feature modules to achieve the desired effect.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Promo banner module](add-alert.md)

[Text block module](add-content-rich-block.md)

[Content block module](add-hero-module.md)

[Video player module](add-video-player.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
