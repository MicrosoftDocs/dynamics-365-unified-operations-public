---
# required metadata

title: Promo banner module
description: This topic covers promo banner modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 04/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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

# Promo banner module


[!include [banner](includes/banner.md)]

This topic covers promo banner modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Promo banner modules are used to show inline informational messages on a page. They can be used to show site-wide promotions that appear on all pages of an e-Commerce site. 

Promo banner modules support a text message and a link. If multiple messages are added to a promo banner module, it becomes a rotating carousel banner that lets customers cycle through all the messages. 

Promo banner modules are driven by data from the content management system (CMS) and can be put on any page.

## Usage examples of promo banners in e-Commerce

Promo banners can be used in the site header to show site-wide promotions or messages, as in the following examples.

"Annual sale ends in 10 days"

"Save big with back to school sale. Shop Now."

## Promo banner module properties

| Property name             | Value                              | Description |
|---------------------------|------------------------------------|-------------|
| Banner messages           | Text and links                     | An array of text and links. |
| Autoplay                  | **True** or **False**              | A value that indicates whether messages are automatically cycled through, if multiple messages are configured. |
| Slide transition interval | A number of milliseconds (ms)      | The interval that is used to cycle through messages. |
| Allow dismiss             | **True** or **False**              | If the value is set to **True**, customers can dismiss the alert. |
| Show carousel flipper     | **True** or **False**              | A value that indicates whether the carousel flippers should be shown, so that customers can manually cycle through multiple banner items. |
| Text alignment            | **Right**, **Left**, or **Center** | The text alignment in the promo banner module. |
| Link                      | A URL                              | The URL for an optional link. |

## Add a promo banner module to a page 

To add a promo banner module to a page and set the required properties, follow these steps.

1. Create a page template that is named **Promo banner template**.
1. Under **Page Outline**, add a **Default page** module to the **Body** slot. 
1. Check in the template, and publish it. 
1. Use the template that you just created to create a page that is named **Promo banner page**. 
1. In the **Main** slot of the new page, add a container module. 
1. In the pane on the right, set the **Width** value to **Fill Container**.
1. Under **Page Outline**, add a promo banner module to the container module.
1. In the settings for the banner module, add one or more banner messages. Each message can have text together with a link. You can edit the other properties to customize the module further.
1. Save and preview the page. At the top of the page, you should see an alert that shows the text that you added.
1. Finish editing the page, and publish it. 

> [!NOTE]
> A promo banner is typically used in the page header slot or a subheader slot.


## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Carousel module](add-carousel.md)

[Text block module](add-content-rich-block.md)

[Content block module](add-hero-module.md)

[Video player module](add-video-player.md)
