---
title: Apply display settings for product dimensions
description: Learn about the display settings for product dimensions and how to apply them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Apply display settings for product dimensions

[!include [banner](includes/banner.md)]

This article explains the display settings for product dimensions and describes how to apply them in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce supports size, style, and color dimensions to distinguish product variants. Dimensions typically appear as text values, such as "Small," "Medium," and "Large" for sizes, and "Black" and "Brown" for colors. However, if a product supports many variations, it can be difficult to browse product variants, because multiple selections are required to view the image for each variant. To make it easier to browse product variants, the version 10.0.20 release of Commerce can use images and hexadecimal (hex) codes to show dimensions as swatches.

In Commerce site builder, you define dimension settings at **Site Settings \> Extensions \> Dimension Settings**. The following illustration shows an example of dimension settings in site builder.

:::image type="content" source="./dev-itpro/media/swatch_site_settings.PNG" alt-text="Screenshot of site settings for dimensions in Commerce site builder.":::

Two dimension settings are available:

- **Dimensions to display as image** – Specify which dimensions should appear as swatches on e-commerce site pages such as product details pages (PDPs) and search result list pages. Any combination of color, size, and style dimensions can be shown as a swatch. If you select a dimension for display as a swatch, Commerce module rendering looks for an available configuration of a hex code swatch. If no hex code is configured, system logic looks for a configuration of an image URL swatch. If neither a hex code nor an image URL is configured, text is shown.

    The following illustration shows an example where a PDP on an e-commerce site includes color and size swatches. In this example, a hex code is configured for the color dimension. Therefore, swatches appear as colors. However, neither a hex code nor an image URL is configured for the size dimension. Therefore, text appears.

    :::image type="content" source="./dev-itpro/media/swatch_pdp.png" alt-text="Screenshot of the color dimension shown as swatches on an e-commerce product details page.":::

- **Dimensions to display in product card** – Specify which dimensions should appear on product cards that are shown in lists and on list pages. Before a dimension can appear on a product card, enable this setting for that dimension. Also enable the **Dimensions to display as image** setting. The swatch selection behavior on product cards is optimized for the color dimension. For other dimensions, a view extension might be required to customize swatch selection behavior.

    The following illustration shows an example where a list page on an e-commerce site contains product cards that include color swatches.

    :::image type="content" source="./dev-itpro/media/swatch_searchresults.PNG" alt-text="Screenshot of the color dimension shown as swatches on an e-commerce list page.":::

For information about how to configure product dimensions so that they appear as swatches on site pages, see [Configure product dimension values to appear as swatches](./dev-itpro/dimensions-swatch.md).

## Additional resources

[Module library overview](starter-kit-overview.md)

[Search results module](search-result-module.md)

[Buy box module](add-buy-box.md)

[Configure product dimension values to appear as swatches](./dev-itpro/dimensions-swatch.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
