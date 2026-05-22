---
title: Ratings and reviews modules
description: Learn about ratings and reviews modules used on product details pages in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 01/28/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-10-31
ms.custom: 
  - bap-template
---

# Ratings and reviews modules

[!include [banner](includes/banner.md)]

This article covers ratings and reviews modules used on product details pages (PDPs) in Microsoft Dynamics 365 Commerce.

Ratings and reviews on e-commerce websites help customers learn about products before they make a purchase decision. They're also a mechanism for collecting customer feedback about products.

You see ratings on product list pages, category list pages, search results pages, and other site pages.

You see ratings histograms and product reviews on PDPs. A **Write a review** button lets customers submit ratings and reviews for a product. Ratings and review modules control these PDP features.

## Ratings and reviews modules on PDPs

Three modules show the ratings and reviews summary on PDPs:
- Write review module
- Product reviews list module
- Ratings histogram module

The following illustration shows what the ratings and reviews modules look like on a PDP.

:::image type="content" source="media/rnr-eCommerce-pdp-reviews-modules_design.png" alt-text="Screenshot of ratings and reviews modules on a PDP.":::

> [!TIP]
> For information about how to optimize PDP templates and layouts so that you can share the configurations for ratings and reviews modules among multiple PDPs on your e-Commerce site, see [Templates and layouts overview](templates-layouts-overview.md).

The following illustration shows how the **Add module** dialog box presents ratings and reviews modules in Dynamics 365 Commerce.
:::image type="content" source="media/rnr-eCommerce-pdp-adding-rnr-modules.png" alt-text="Screenshot of the Add module dialog box.":::

### Write review module

The write review module includes a **Write a review** button that users can use to sign in, assign a rating, and write a review of a product. This module also lets users edit a rating or review that they previously submitted. This module typically appears above the ratings histogram and product reviews list modules on a PDP.
The following illustration shows the **Write a review** dialog box that appears when a customer selects **Write a review**. The customer can use this dialog box to submit a rating and a review.

:::image type="content" source="media/rnr-eCommerce-write-review-module.png" alt-text="Screenshot of the Write a review dialog box.":::

The following table shows the write review module property that you need to configure in the authoring tool.

| Property name | Value        | Property description                 |
|---------------|--------------|--------------------------------------|
| Name          | Write review | The name of the write review module. |

### Ratings histogram module

The ratings histogram module shows a ratings histogram. This module typically appears between the write review module and the product reviews list module on a PDP.
The ratings histogram module requires no configuration. You just have to add the module in the PDP template.
The following illustration shows what a PDP template looks like in Dynamics 365 Commerce when ratings and reviews modules are configured for display on PDPs.

:::image type="content" source="media/rnr-eCommerce-pdp-reviews-modules.png" alt-text="Screenshot of a PDP template when ratings and reviews are configured for display on PDPs.":::

### Product reviews list module

The product reviews list module shows a list of product reviews together with sort, filter, and pagination options. This module typically appears after the ratings histogram module on a PDP.
The following table shows the product reviews list module properties that you need to configure in the authoring tool.

| Property name              | Value | Property description |
|----------------------------|-------| ---------------------|
| Reviews shown on each page | 10    | The number of reviews that show at a time on a PDP. **Next** and **Previous** buttons are included, so that users can move through the pages of reviews. |

#### Ratings histogram – Summary view

The product reviews list module includes a slot where you can add a ratings histogram module. The following illustration shows how you can add a ratings histogram module in the product reviews list module in Dynamics 365 Commerce.

:::image type="content" source="media/rnr-eCommerce-pdp-rating-histogram-summary.png" alt-text="Screenshot of adding a ratings histogram module in a product reviews list module.":::

## Additional resources

[Module library overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
