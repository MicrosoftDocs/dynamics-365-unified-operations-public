---

# required metadata

title: Commerce catalogs for B2B FAQ
description: This topic provides answer to frequently asked questions about Microsoft Dynamics 365 Commerce catalogs.
author: ashishmsft
ms.date: 04/28/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-02-28
---

# Commerce catalogs for B2B FAQ

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic provides answer to frequently asked questions about Microsoft Dynamics 365 Commerce [business-to-business (B2B) catalogs](catalogs-b2b-sites.md).

## Why can't I configure a catalog-specific navigation hierarchy or see an option to associate a customer hierarchy?

Make sure that the **Enable use of multiple catalogs on retails channels** feature is enabled in the **Feature management** workspace in Commerce headquarters. Additionally, make sure that your environment is using the Commerce version 10.0.26 or later release.

## Can I view the catalog-specific hierarchy and enrich category pages in Commerce site builder?

Yes, Commerce site builder users who have access to the **Products** page in site builder can select a catalog and view the catalog-specific hierarchy. From the **Products** page, users can also enrich a category page for a specific category in the catalog. For more information, see [Enrich a category landing page](enrich-category-page.md). If you want to have enrichment that is specific to a catalog, we recommend that you have a distinct and unique navigation hierarchy for that catalog.

## Can a B2B shopper purchase from multiple catalogs in a single checkout?

Yes, purchases from multiple catalogs in a single checkout are allowed. B2B shoppers can use the catalog indicator in the cart view to determine which items were added from which catalogs.

## If a B2B shopper purchases the same item from different catalogs, what is the expected behavior?

Although a given user might have access to multiple catalogs at a given time, the expectation is that products in those catalogs will be mutually exclusive. In other words, ideally, the same product should not be part of more than one catalog for a given user.

However, if a situation arises where the same product belongs to multiple catalogs, the system will maintain multiple cart lines for that product. There will be a separate line for each catalog. The same product from two different catalogs won't be merged at checkout.

## When a B2B shopper is shopping, is there any validation for catalog availability?

Yes. A B2B shopper will be allowed to proceed to checkout only if all items in the cart are from valid catalogs. If any cart items are from expired or retracted catalogs, they will be removed, and the user will be notified.

## During the shopping experience, are search and product discovery (including related and recommended product collections) catalog-specific?

Yes. As soon as a user selects a specific catalog, the whole shopping journey becomes catalog-specific. This journey includes product discovery experiences such as search suggestions, search results, category results, refiners, pricing, attributes, and recommended products (such as new, best-selling, trending, frequently bought together, and related products).

## Can a B2B shopper purchase from the default assortment (catalogID=0)?

No, a B2B shopper isn't allowed to purchase from the default assortment. That assortment is intended only for anonymous browsing. If a B2B shopper is missing catalog assignments (pending updates from their administration), they won't be able to see any catalogs that they can choose from, and no category hierarchy will be visible.

## Can marketing content be curated for a product that is specific to a catalog?

Currently, product enrichment is supported only at the site and channel levels. In other words, if a product is enriched, it's shared across multiple catalogs, and the corresponding product details page (PDP) for that product will be rendered in the same way across all catalogs for a given site.

## Is catalog support available for both B2B and business-to-consumer (B2C) online channels?

Currently, Commerce catalogs are intended to work with B2B channels only.

## Can we set up catalog-specific upsell/cross-sell items?

Currently, only related products functionality is supported. However, upsell and cross-sell item configurations are available for call centers.

The following features are also supported only for call centers:

- Catalog source codes
- Use of source IDs to track costs and response rates
- Catalog-specific order and item scripts
- Catalog page analysis
- Catalog requests
- Payment schedules
- Free products based on source codes

## Can we use catalog source codes for B2B orders through the e-commerce portal?

No. Catalog source codes are supported only for call center channels.

## Additional resources

[Create Commerce catalogs for B2B sites](catalogs-b2b-sites.md)

[Extensibility impact of Commerce catalogs for B2B customizations](catalogs-b2b-sites-dev.md)
