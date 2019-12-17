---
# required metadata

title: Alert module 
description: This topic covers alert modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 10/31/2019
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

# Alert module

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers Promo banner module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A Promo banner module is used to show inline informational messages on a page. It can be used to show site-wide promotions that appear on all pages of an e-Commerce site. 

Promo banner supports a text message and a link. If multiple messages are added to the promo banner, it turns into a carousel view and allows user to cycle through all the mesages. 

Promo banner module is driven by data from the content management system (CMS) and can be put on any page.

## Usage examples of promo banner in e-Commerce

Promo banner can be used in the site header to indicate site-wide promotions or messages. Here are some examples:

"Annual sale ends in 10 days"

"Save big with back to school sale. Shop Now."

## Promo banner module properties

| Property name  | Value                              | Description |
|----------------|------------------------------------|-------------|
| Banner Messages           | Array of text and links                               | An array of text an links can be added to the banner|
|Autoplay| **True** or **False**| It automatically cycles through the messages if there are multiple messages configured|
|Slide transition interval| Number in ms| An interval can be provided to cycle through each message|
| Allow dismiss  | **True** or **False**              | If the value is set to **True**, the customer can dismiss the alert. |
|Show carousel flipper| **True** or **False**| Shows the carousel flippers for a user to manually cycle through multiple items in the banner|
| Text alignment | **Right**, **Left**, or **Center** | A value that defines how text is aligned in the alert module. |

| Link           | URL                                | The URL for an optional link. |

## Add a promo banner to a page 

To add an promo banner module to a page and set the required properties, follow these steps.

1. Create a page template that is named **Promo banner template**.
1. In the **Main** slot of the default page, add a promo banner module.
1. Check in the template, and publish it. 
1. Use the alert template that you just created to create a page that is named **Promo banner page**. 
1. In the **Main** slot of the new page, add a promo banner module.
1. In the settings for the module, add one or many banner messages. Each message can have a text with a link. You can edit the other properties if you want to customize the module further.
1. Save and preview the page. At the top of the page, you should see an alert that has the text that you added.
1. Check in the page, and publish it. 

Note: A promo banner is typically used in the page Header slot or Sub-header slot.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Carousel module](add-carousel.md)

[Content rich block module](add-content-rich-block.md)

[Content placement module](add-content-placement-modules.md)

[Feature module](add-feature-module.md)

[Hero module](add-hero-module.md)

[Video player module](add-video-player.md)
