---

# required metadata

title: Commerce catalogs for B2B FAQ
description: This article provides answers to frequently asked questions about Microsoft Dynamics 365 Commerce catalogs.
author: ashishmsft
ms.date: 06/27/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2022-02-28

---

# Commerce catalogs for B2B FAQ

[!include [banner](includes/banner.md)]

This article provides answers to frequently asked questions about Microsoft Dynamics 365 Commerce [business-to-business (B2B) catalogs](catalogs-b2b-sites.md).

### Why can't I configure a catalog-specific navigation hierarchy or see an option to associate a customer hierarchy?

Ensure that the **Enable use of multiple catalogs on retails channels** feature is enabled in the Commerce headquarters **Feature management** workspace and that your environment is the Commerce version 10.0.27 or later release. Ensure that you've selected **B2B** under **Catalog type**.

### Can I view the catalog-specific hierarchy and enrich category pages in Commerce site builder?

Yes, Commerce site builder users who have access to the **Products** page in site builder can select a catalog and view the catalog-specific hierarchy. From the **Products** page, users can also enrich a category page for a specific category in the catalog. For more information, see [Enrich a category landing page](enrich-category-page.md). If you want to have enrichment that is specific to a catalog, we recommend that you have a distinct and unique navigation hierarchy for that catalog.

### Can a B2B shopper purchase from multiple catalogs in a single checkout?

Yes, purchases from multiple catalogs in a single checkout are allowed. B2B shoppers can use the catalog indicator in the cart view to determine which items were added from which catalogs.

### If a B2B shopper purchases the same item from different catalogs, what is the expected behavior?

Although a given user might have access to multiple catalogs at a given time, the expectation is that products in those catalogs will be mutually exclusive. In other words, ideally, the same product should not be part of more than one catalog for a given user.

However, if a situation arises where the same product belongs to multiple catalogs, the system will maintain multiple cart lines for that product. There will be a separate line for each catalog. The same product from two different catalogs won't be merged at checkout.

### When a B2B shopper is shopping, is there any validation for catalog availability?

Yes. A B2B shopper will be allowed to proceed to checkout only if all items in the cart are from valid catalogs. If any cart items are from expired or retracted catalogs, they will be removed, and the user will be notified.

### During the shopping experience, are search and product discovery (including related and recommended product collections) catalog-specific?

Yes. As soon as a user selects a specific catalog, the whole shopping journey becomes catalog-specific. This journey includes product discovery experiences such as search suggestions, search results, category results, refiners, pricing, attributes, and recommended products (such as new, best-selling, trending, frequently bought together, and related products).

### Can a B2B shopper purchase from the default assortment (catalogID=0)?

No, a B2B shopper isn't allowed to purchase from the default assortment. That assortment is intended only for anonymous browsing. If a B2B shopper is missing catalog assignments (pending updates from their administration), they won't be able to see any catalogs that they can choose from, and no category hierarchy will be visible.

### Why is a B2B shopper getting 404 errors and no longer able to access categories or products pages?

If the **Enable use of multiple catalogs on retails channels** feature is enabled in headquarters, then it's required that at least one catalog is associated with every customer hierarchy. If a B2B shopper is trying to access a B2B catalog that was previously accessible, confirm that the catalog is still valid and hasn't expired or been retracted by your organization. 

### After getting a 404 error for an expired or invalid catalog, why isn't a B2B shopper being redirected to the catalog picker page? 

Ensure that your site administrator has selected your catalog picker page in site builder at **Extensions \> Catalog Picker Route**, and has selected **Save & Publish** to publish the change. 

### Can marketing content be curated for a product that is specific to a catalog?

Currently, product enrichment is supported only at the site and channel level. In other words, if a product is enriched and is shared across multiple catalogs, the corresponding enriched product details page (PDP) for that product will be rendered in the same way across all catalogs for a given site. 

### Is catalog support available for both B2B and business-to-consumer (B2C) online channels?

Currently, Commerce catalogs are intended to work with B2B Online channels only.

### A new customer was added to the customer hierarchy or a new hierarchy was associated with the catalog, but the catalog is not available to the user. Why?

Ensure that you ran **1010** jobs after you associated the new customer to an existing customer hierarchy, and when you created the new customer hierarchy. The catalogs associated with the customer hierarchy will only be visible after the **1010** job is completed successfully. If the catalog is also new, ensure that you ran the **1150** (catalog) job as well as  the **1010** jobs. As with any new catalog, allow some time for the data to sync to the channel and the search index. If a job has the status "Applied", that means that the data is being synced to channel database, but additional time is required for the data to sync to the search index. 

### Can we set up catalog-specific upsell/cross-sell items?

Currently, only related products functionality is supported. However, upsell and cross-sell item configurations are available for call centers.

The following features are also supported only for call centers:

- Catalog source codes
- Use of source IDs to track costs and response rates
- Catalog-specific order and item scripts
- Catalog page analysis
- Catalog requests
- Payment schedules
- Free products based on source codes

### Can we use catalog source codes for B2B orders through the e-commerce portal?

No. Catalog source codes are supported only for call center channels.

### When the B2B catalogs feature is enabled, do order templates show only items from the currently selected catalog? 

Currently, order templates aren't catalog-aware. Therefore, when you access order templates, if the **B2B catalog** feature is enabled, only partial lines from the order template that are also part of the currently selected catalog are shown. To check for progress on the ability of catalogs and order templates to work together correctly, we recommend that you check the release notes for future updates. 

### When the B2B catalogs feature is enabled, is the Buy it again option available for the order lines in the order history? 

Because the same customer can buy products from both B2B and B2C channels, the order history shows the customer's order history from all channels. Catalog support is available only for B2B channels, and catalog information is required to purchase in a B2B channel. Order lines from B2C channels shouldn't have any catalog information. For this initial phase, the **Buy it again** option was removed from the order history view. To learn whether the **Buy it again** option becomes available in the order history in a B2B channel, we recommend that you check the release notes for future updates. 

## Additional resources

[Create Commerce catalogs for B2B sites](catalogs-b2b-sites.md)

[Catalog picker module](catalog-picker.md)

[Extensibility impact of Commerce catalogs for B2B customizations](catalogs-b2b-sites-dev.md)
