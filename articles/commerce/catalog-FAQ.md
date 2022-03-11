---
  
# required metadata

title: Commerce catalogs for B2B FAQ
description: This topic provides answer to frequently asked questions about Microsoft Dynamics 365 Commerce catalogs.
author: ashishmsft
ms.date: 03/08/2022
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

Make sure that the **Enable use of multiple catalogs on retails channels** feature is enabled in the Commerce headquarters **Feature management** workspace and that your environment is the Commerce version 10.0.26 or later release. 

#### Can you select a catalog and view the catalog-specific hierarchy in Commerce site builder? 

Yes, site builder users who can access the **Products** tab are able to select a catalog and view the catalog-specific hierarchy. Also, users can enrich the category page for a specific category in the catalog. If you want to have enrichment specific to a catalog, it is recommended to have a distinct and unique navigation hierarchy for that catalog. 
 
#### Can a B2B shopper purchase from multiple catalogs in a single checkout?

Yes, purchasing from multiple catalogs in a single checkout is allowed. B2B shoppers can view the catalog indicator in the cart view to understand what items were added from which catalogs. 

#### If a B2B shopper purchases the same item from different catalogs, what is the expected behavior? 

First & foremost - our recommendation is that for  - 

while a given user may have access to multiple catalogs at any point in time, it is expected that products in those catalogs will be mutually exclusive. In other words, ideally a product shouldn't be part of more than catalog for a given user. 

However, should the situation arise where a product belongs to multiple catalogs, then the system would maintain two cart lines specific to each catalog for the same product. The same product from two different catalogs will not be merged at checkout.  

#### When a B2B shopper is shopping is there be any validation for catalog availability? 

Yes, a B2B shopper will only be allowed to proceed to checkout if all items in the cart are from valid catalogs. If any cart items are from expired or retracted catalogs. they will be removed and the user will be notified. 

#### During the shopping experience is search and product discovery (including related and recommended product collections) catalog-specific? 

Yes, as soon as a user selects a specific catalog the entire shopping journey is catalog-specific, including product discovery experiences like search suggestions, search results, category results, refiners, pricing, attributes, and recommended products (such as new, best-selling, trending, frequently bought together, and related products). 

#### Can a B2B shopper purchase from the default assortment (catalogID=0)?

No, a B2B shopper is not allowed to purchase from the default assortment, which is only intended for anonymous browsing. In other words, if a B2B shopper is missing any catalog assignment (pending updates from their administration) then they aren't able to see any catalogs to choose from, and no category hierarchy will be visible. 

#### Is it allowed to curate marketing content for a product specific to a catalog?

Currently, product enrichment is supported at the site and channel level. In other words, if a product is enriched it is shared across multiple catalogs and a corresponding product details page (PDP) for that product would be rendered the same way across all catalogs for a given site. 

#### Is catalog support available for both B2B & business-to-consumer (B2C) online channels? 

Currently, Commerce catalogs are intended to work only with B2B channels. 

#### Can we set up catalog-specific upsell/cross-sell items? 

Currently, only related products functionality is supported. However, upsell and cross-sell item configurations are available for call centers. 

In addition, the following features are only supported for call centers: 
- Catalog source codes.
- Use of source IDs to track costs and response rates.
- Catalog-specific order and item scripts.
- Catalog page analysis.
- Catalog requests.
- Payment schedules.
- Free products based on source codes.

#### Can we use catalog source codes for B2B orders through the e-commerce portal? 

Catalog source codes are only supported for call center channels.

#### As a developer, what's the critical change I must be watchful with introduction of this feature as well as if I were to be interested in extending catalog-context to my custom-scenarios? 

> <p> Please note - this is the standard process the customer need to follow as upon upgrade their customization may not auto-support latest features, and if your customization indeed were to want any new feature or bug fix to be included in their experiences, we recommend to update their customization code accordingly, similar to the changes Microsoft may have done for the core code. Review further below if indeed your customizations must be updated. 

All merchandising APIs have been attempted to be 'catalog-aware' for which passing in 'CatalogID' parameter is critical. 

As discussed earlier that catalog 0 is not a valid catalog for B2B users when they are signed in. Thus all API calls that pass 0 or use a default value will fail since the user won’t have access to catalog 0. In order to get the right experience, the API calls that customer does need to be updated to pass the catalog id that was selected from the catalog picker. Even if you use some default value, if the user switches the catalog, the website should provide the data accordingly to the selected catalog, so the APIs from customization should pass the selected catalog as well to match the APIs that are executed from core eCommerce code.



These are the cases that are possible 
1.	A customer introduced their own data action that calls a product-related API or calls a product related data action. For more information, see [Data actions](e-commerce-extensibility/data-actions.md). Required steps from the customer:
    1. If it uses a direct API call, update data action to pass catalog id, e.g.: 
![Customization1_a](./media/customization1_a.png)

    1. If it calls a different product-related data action inside the customization, the code needs to be updated to pass some new parameters such as requestContext (which is used to retrieve the current catalog id):
![Customization1_b](./media/customization1_b.png)

2. A customer has an overridden data action. For more information, see [Data action overrides](e-commerce-extensibility/data-action-overrides.md). 
Required steps: update the data action similar to #1.

3. A customer has module ejection, view extension, or created a new module, which includes calls to APIs or calls to data actions. For more information, see [Clone a module library module](e-commerce-extensibility/modules-overview.md#clone-a-module-library-module).
Required steps: update similar to #1, e.g.:
![Customization3](./media/customization3.png)

4. If a customer uses getById API call, they need to switch to getByIds instead since getById has some limitations and it won’t support catalog awareness.
5. If a customer has any data action that retrieves info for multiple products that could be from different catalogs, they need to split the API calls by catalog id. E.g. for the APIs in the cart, the cart may have products from different catalogs, so in order to receive product info, they need to group the products in the cart lines by catalog id, and call API for each catalog separately. E.g.
![Customization5](./media/customization5.png)
