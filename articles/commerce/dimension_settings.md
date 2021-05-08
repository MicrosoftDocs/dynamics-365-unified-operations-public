---
# required metadata

title: Apply display settings for product dimensions
description: This topic covers the display settings for product dimensions and describes how to apply them in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 04/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Apply display settings for product dimensions

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers the display settings for product dimensions and describes how to apply them in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce supports dimensions Size, Style and Color for representing product variants. These dimensions are typically displayed as text value E.g Size = Small, Large, Medium or Color = Black, Brown. However, for a product that supports many variations, browsing through these variants requires multiple selections to view each product variant image. This makes the selection process slow and tedious for a shopper. Refer to [Configure product dimension to be represented as swatch](./dev_itpro/media/dimensions_ swatch.md) to setup the dimension values to be represented as a swatch. 

In e-Commerce, dimensions settings are defined at Site Settings > Extensions > Dimension Settings in site builder. There are two settings available:

- **Dimensions to display as swatch**: This setting defines which dimensions should appear as a swatch on e-commerce experiences such as product details page, refiners, quick view module etc. Any combination of Color, Size, Style can be displayed as a swatch. If a dimension is selected to be displayed as a swatch, e-commerce module rendering will look-up for available hexcode configuration. If there is no hexcode configured, it will fallback and check for an image url configuration. If both are missing, text will be displayed. Below is an example where Color and Size are selected to be swatch. Color shows hexcode but Size fallsback to Text.

![Example of displaying color as swatch on e-commerce product details page](../dev-itpro/media/swatch_pdp.png)

- **Dimensions to display in Product card**  This setting allows dimensions to be displayed on the product cards i.e on list pages and lists. If a dimension needs to be displayed on product card, this setting must be enabled for that dimension and it should also be enabled as a swatch. For example, to display Color on the product cards, the following should be configured. In addition, the swatch selection behavior on product cards along with the refiner experience is most optimized for Color dimension. For other dimensions, a view extension may be needed to provide an optimal experience. 

![Example of site settings on Site Builder](../dev-itpro/swatch_site_settings.PNG)
![Example of displaying color as swatch on e-commerce list page](../dev-itpro/media/swatch_searchresults.PNG)

## Additional resources

[Module library overview](starter-kit-overview.md)

[Search results module](search-result-module.md)

[Buy box module](add-buy-box.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
