---
title: Apply unit of measure settings
description: Learn about unit of measure settings and how to apply them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/30/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Apply unit of measure settings

[!include [banner](includes/banner.md)]

This article explains unit of measure settings and describes how to apply them in Microsoft Dynamics 365 Commerce.

You can sell a product in different units, such as "each," "pair," and "dozen." In Commerce headquarters, you can define the sell-by unit of measure for a product and show it on an e-commerce site. For example, if a retailer sells a product both individually and in dozens, you can show the available units of measure together with other product information.

In the example in the following illustration, a sell-by unit of measure of **ea** (each) is configured for a product in Commerce headquarters.

:::image type="content" source="./media/Productunit-headquarters.PNG" alt-text="Screenshot of a product that is configured with a unit of measure in Commerce headquarters.":::

> [!NOTE]
> Support for applying and showing the unit of measure is available as of the Commerce version 10.0.19 release.

## Unit of measure settings

Define unit of measure display settings in Commerce site builder, at **Site settings \> Extensions \> Display unit of measure for products**. Three settings are available:

- **Do not display** – When you select this setting, the e-commerce site doesn't show the unit of measure for the product. This behavior is the default behavior.
- **Display in the product buying experience** – When you select this setting, the unit of measure shows on product details, cart, checkout, order history, and order details pages.
- **Display in the product browsing and buying experience** – When you select this setting, the unit of measure shows on the product buying experience pages and also during the product browsing experience. As part of this behavior, units of measure show in search results and product collection modules.

> [!IMPORTANT]
> Unit of measure display settings are available as of the Commerce version 10.0.19 release. If you're updating from an older version of Commerce, you must manually update the appsettings.json file. For instructions, see [SDK and module library updates](e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file).

## Modules that use unit of measure settings

Modules that use the unit of measure settings include the buy box, wishlist, cart, cart icon, search results container, product collection, checkout, and order details modules.

In the example in the following illustration, a product details page (PDP) shows the unit of measure (**ea**) for a product.

:::image type="content" source="./media/Productunit-PDP.png" alt-text="Screenshot of a PDP that shows the unit of measure.":::

In the example in the following illustration, a product collection module shows the unit of measure (**ea**) for a product.

:::image type="content" source="./media/Productunit-productcollection.png" alt-text="Screenshot of a product collection module that shows the unit of measure.":::

## Additional resources

[Module library overview](starter-kit-overview.md)

[Cart module](add-cart-module.md)

[Buy box module](add-buy-box.md)

[Account management pages and modules](account-management.md)

[SDK and module library updates](e-commerce-extensibility/sdk-updates.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
