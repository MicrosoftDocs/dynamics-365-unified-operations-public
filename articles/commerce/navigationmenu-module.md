---
# required metadata

title: Navigation menu module 
description: This topic covers Navigation menu module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 05/28/2020
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

# Navigation menu module

[!include [banner](includes/banner.md)]

This topic covers Navigation menu module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Navigation menu module allows the users to browse the channel navigation heirarchy as defined in HQ. In addition, it also allows menu items to be added on Site builder and linked to pages within the site.

The module can be added to the Header module and authored to show on all page headers. In Fabrikam theme, the navigation menu shows 2-levels by default. In Starter theme, the navigation menu shows 3-levels by default. 

![Example of a navigation meu module](./media/ecommerce_navigationmenu.PNG)

## Navigation menu module properties
| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Source                  | Retail, Manual authoring, Retail and manual authoring |Retail source allows the channel navigaiton heirarchy from HQ to be displayed on the navigation menu. Manaul authoring allows static menu items to be curated|
| Show category images |True or False    | This property was added in 10.0.14 and displays category images defined in HQ for a category on the navigation menu|
| Static menu item| Array of values| Static menu items take a menu item name and link to a static page. Recursively, you can create menu items below each other. By default static menu appear on the root level and appended to channel navigation heirarchy if it exists |

## Add a social share module to a buy box module

The Social share module can be added to the buy box module within the **Social share slot**.  

1. In Fabrikam, open the the **DefaultPDP** page which is the product details page 
1. To the Buy box module, **Social share slot** add the **Social share module**. Set caption if needed. Set Orientation=Horizontal
1. To the **Social share** add a **Social share item** module.
1. On the **Social share item** module, select Social Media = Facebook. Set Icon to the Facebook icon.
1. Conitnue adding more **Social share item**s.
1. Select **Save**, and then select **Preview** to preview the page. The page will show the social share module.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy Box](add-buy-box.md)

[Cookie compliance](cookie-compliance.md)

[Header]
