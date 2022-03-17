---
  
# required metadata

title: Commerce catalogs for B2B FAQ
description: This topic provides answer to frequently asked questions about Microsoft Dynamics 365 Commerce catalogs.
author: ashishmsft
ms.date: 03/16/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-02-28
---

  
# Commerce catalogs for B2B FAQ 

[!include [banner](includes/banner.md)]

This topic provides answer to frequently asked questions about Microsoft Dynamics 365 Commerce business-to-business (B2B) catalogs.

#### Why am I unable to configure a catalog-specific navigation hierarchy or see an option to associate a customer hierarchy? 

Ensure that the **Enable use of multiple catalogs on retails channels** feature is enabled in the Commerce headquarters **Feature management** workspace and that your environment is the Commerce version 10.0.26 or later release. 

#### Can you view catalog-specific hierarchy and enrich category pages in Commerce site builder? 

Yes, site builder users who have access to the **Products** page in site builder are able to select a catalog and view the catalog-specific hierarchy. Users can also enrich a category page for a specific category in the catalog from the **Products** page. For more information, see [Enrich a category landing page](enrich-category-page.md). If you want to have enrichment specific to a catalog, it is recommended to have a distinct and unique navigation hierarchy for that catalog. 
 
#### Can a B2B shopper purchase from multiple catalogs in a single checkout?

Yes, purchasing from multiple catalogs in a single checkout is allowed. B2B shoppers can view the catalog indicator in the cart view to determine what items were added from which catalogs. 

#### If a B2B shopper purchases the same item from different catalogs, what is the expected behavior? 

While a given user may have access to multiple catalogs at any point in time, the expectation is that products in those catalogs will be mutually exclusive. In other words, ideally a product shouldn't be part of more than one catalog for a given user. 

However, should the situation arise where a product belongs to multiple catalogs, then the system would maintain two cart lines specific to each catalog for the same product. The same product from two different catalogs will not be merged at checkout.  

#### When a B2B shopper is shopping is there any validation for catalog availability? 

Yes, a B2B shopper will only be allowed to proceed to checkout if all items in the cart are from valid catalogs. If any cart items are from expired or retracted catalogs they will be removed and the user will be notified. 

#### During the shopping experience is search and product discovery (including related and recommended product collections) catalog-specific? 

Yes, as soon as a user selects a specific catalog the entire shopping journey is catalog-specific, including product discovery experiences like search suggestions, search results, category results, refiners, pricing, attributes, and recommended products (such as new, best-selling, trending, frequently bought together, and related products). 

#### Can a B2B shopper purchase from the default assortment (catalogID=0)?

No, a B2B shopper is not allowed to purchase from the default assortment, which is only intended for anonymous browsing. If a B2B shopper is missing catalog assignments (pending updates from their administration), then they won't be able to see any catalogs to choose from, and no category hierarchy will be visible. 

#### Is it allowed to curate marketing content for a product specific to a catalog?

Currently, product enrichment is only supported at the site and channel level. In other words, if a product is enriched it is shared across multiple catalogs and the corresponding product details page (PDP) for that product would be rendered the same way across all catalogs for a given site. 

#### Is catalog support available for both B2B & business-to-consumer (B2C) online channels? 

Currently, Commerce catalogs are intended to work only with B2B channels. 

#### Can we set up catalog-specific upsell/cross-sell items? 

Currently, only related products functionality is supported. However, upsell and cross-sell item configurations are available for call centers. 

The following features are also only supported for call centers: 
- Catalog source codes.
- Use of source IDs to track costs and response rates.
- Catalog-specific order and item scripts.
- Catalog page analysis.
- Catalog requests.
- Payment schedules.
- Free products based on source codes.

#### Can we use catalog source codes for B2B orders through the e-commerce portal? 

No, catalog source codes are supported only for call center channels.
