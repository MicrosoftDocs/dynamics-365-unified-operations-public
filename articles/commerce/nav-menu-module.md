---
title: Navigation menu module
description: Learn about navigation menu modules and how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Navigation menu module

[!include [banner](includes/banner.md)]

This article describes navigation menu modules and explains how to add them to site pages in Microsoft Dynamics 365 Commerce.

The primary purpose of navigation menu modules is to allow site users to browse products and site pages according to the channel navigation hierarchy defined in Dynamics 365 Commerce headquarters. Items that you configure in a navigation menu module appear as site header navigation. Navigation menu modules also support static menu items that link to other pages on an e-commerce site.

Add the navigation menu module to the header module of a page. In the Fabrikam theme, the navigation menu shows two levels by default. In the Starter theme, the navigation menu shows three levels by default. To change the number of levels, you need a view extension on the theme.

The following illustration shows an example of a navigation menu for the Fabrikam site with two levels of category hierarchy and some static menu items.
:::image type="content" source="./media/ecommerce-header.png" alt-text="Screenshot of a navigation menu module example.":::

## Navigation menu module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Source                  | **Retail**, **Manual authoring**, **Retail and manual authoring** | The **Retail** value displays the channel navigation hierarchy from Commerce headquarters on the navigation menu. The **Manual authoring** value allows you to curate static menu items. The **Retail and manual authoring** value allows a mix of both. |
| Show category images | **True** or **False**    | When enabled, this property displays category images on the navigation menu as defined in Commerce headquarters for each category. Added in Commerce release 10.0.14. |
| Show promotional images | **True** or **False** | When this property is enabled, you configure promotions by using images, links, and text. This property was added in the Commerce version 10.0.17 release. |
|Add category promotional content | Text, image, or link | When the **Show promotional images** property is enabled, you can add text, an image, or a link as promotional content on the navigation menu. |
| Enable multi-level navigation menu | **True** or **False** | When this property is enabled, the navigation menu can show multiple levels of the navigation hierarchy. This feature is available in the Commerce version 10.0.15 release. |
| Number of levels | integer | This property defines the numbers of levels that show if the **Enable multilevel navigation menu** property is set to **True**. |
| Static menu item| Array of values| Static menu items that associate a menu item name with a link to a static site page. You can create menu items under other menu items. By default, static menus appear at the root level and are appended to the channel navigation hierarchy if it exists. |
| Show root menu | **True** or **False** | When this property is enabled, the navigation menu can be defined under a custom root (for example, **Shop now**). This feature is available in the Dynamics 365 Commerce 10.0.15 release. |
| Root menu | string | This property defines text for a custom root if the **Show root menu** property is set to **True**. |

The following illustration shows an example of a category image displayed on the navigation menu for the Fabrikam site.
:::image type="content" source="./media/ecommerce-categoryimages.PNG" alt-text="Screenshot of a navigation menu module with category images.":::

## Add a navigation menu module to a header module

For more information about how to add a navigation menu module to a header module, see [Header module](author-header-module.md).

## Additional resources

[Module library overview](starter-kit-overview.md)

[Breadcrumb module](add-breadcrumb.md)

[Site picker module](site-selector.md)

[Buy box module](add-buy-box.md)

[Cookie compliance](cookie-compliance.md)

[Header module](author-header-module.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
