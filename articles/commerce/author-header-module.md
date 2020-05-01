---
# required metadata

title: Header module
description: This topic covers header modules and describes how to create page headers in Microsoft Dynamics 365 Commerce.
author: anupamar
manager: annbe
ms.date: 05/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar-ms
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Header module

[!include [banner](includes/banner.md)]

This topic covers header modules and describes how to create page headers in Microsoft Dynamics 365 Commerce.

## Overview

In Dynamics 365 Commerce, a page header comprises multiple modules, such as the header, navigation menu, search, promo banner, and cookie consent modules. 

The header module includes a site logo, links to the navigation hierarchy, links to other pages on the site, a cart symbol, a wishlist symbol, sign-in options, and the search bar. A header module is automatically optimized for the device that the site is being viewed on (in other words, for a desktop device or a mobile device). For example, on a mobile device, the navigation bar is collapsed into a **Menu** button (which is sometimes referred to as a *hamburger menu*).

The following image shows an example of a header module on a home page.

![Example of header module](./media/ecommerce-header.png)

## Properties of a header module

A header module supports **Logo image**, **Logo link**, and **My account links** properties. 

The **Logo image** and **Logo link** properties are used to define a logo on the page. For more information, see [Add a logo](add-logo.md). 

The **My account links** property can be used to define account pages that the site owner wants to show quick links for in the header.

## Modules that are available in a header module

The following modules can be used in a header module:

- **Navigation menu** – The navigation menu represents the channel navigation hierarchy and other static navigation links. The channel navigation hierarchy can be configured in Dynamics 365 Commerce. The navigation menu has a **Navigation Source** property that is used to specify Retail Server navigation menu items and static menu items as a source. If static menu items are specified as a source, relative links to other pages on the site can be provided. Configured items then appear as header navigation. 

- **Search** – The search module lets users enter search terms to search for products. The URL of the default search page and the search query parameters must be provided at **Site Settings \> Extensions**. The search module has properties that let you suppress the search button or label as you require. The search module also supports auto-suggest options, such as product, keyword, and category search results.

- **Cart icon** - The cart icon module represents the cart icon, which shows the number of items in the cart at any given time. For more information, see [Cart icon module](cart-icon-module.md).

## Create a header module for a page

To create a header module, follow these steps.

1. Go to **Page Fragments** and select **+New** to create a new fragment.
1. In the **New Page Fragment** dialog box, select the **Container** module, enter a name for the page fragment, and then select **OK**.
1. Select the **Default container** slot, then in the properties pane on the right, set the **Width** property to **Fill container**.
1. In the **Default container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Promo banner** and **Cookie consent** modules, and then select **OK**.
1. In the **Default container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. Select the **Container** slot, then in the properties pane on the right, set the **Width** property to **Fill container**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Header** module, and then select **OK**.
1. In the **Navigation menu** slot of the header module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Navigation menu** module, and then select **OK**.
1. In the property pane for the navigation menu module, configure the properties as needed.
1. In the **Search** slot of the header module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Search** module, and then select **OK**.
1. In the property pane for the search module, configure the properties as needed.
1. In the **Cart icon** slot of the header module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Cart icon** module, and then select **OK**.
1. In the property pane for the cart icon module, configure the properties as needed. If you want the cart icon to display a mini cart when hovered over, select **Show mini cart**.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

To help guarantee that a header appears on every page, follow these steps on every page template that is created for the site.

1. In the **Header** slot of the **Default page** module, add the footer fragment that you created.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
