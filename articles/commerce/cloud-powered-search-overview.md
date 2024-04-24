---
title: Cloud-powered search overview
description: This article gives an overview of cloud-powered search in Microsoft Dynamics 365 Commerce.
author: ashishmsft
ms.date: 02/08/2024
ms.topic: overview
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
ms.assetid:

---

# Cloud-powered search overview

[!include [banner](includes/banner.md)]

This article gives an overview of cloud-powered search in Microsoft Dynamics 365 Commerce.

Product discoverability helps guarantee that customers can quickly and easily find products by browsing categories, searching, and filtering. Retailers consider product discovery a primary tool for customer interaction across channels powered by Cloud Scale Unit (CSU), such as e-commerce and point of sale (POS).

Customers are used to the nearly instantaneous response times of search engines, e-commerce websites, social apps, search autosuggestions, faceted navigation, and highlighting. If customers can't quickly find the product that they're looking for in one e-commerce store, they don't hesitate to go to a different e-commerce store.

The cloud-powered product discoverability in Commerce helps retailers continue to increase consumer retention and conversion rates across channels powered by CSU.

The Commerce search experience has advanced capabilities to help retailers achieve better product discoverability. At the same time, these capabilities deliver the scalability and performance that are required for e-commerce traffic.

## Configure cloud-powered search capabilities

Cloud-powered search capabilities are available starting in Commerce version 10.0.8.

To configure cloud-powered search capabilities, follow these steps.

1. In Commerce headquarters, go to **Commerce Parameters \> Configuration Parameters**.
1. Under **Set up the configuration parameters**, check that an entry exists for **ProductSearch.UseAzureSearch**, and that its value is set to **true**, as shown in the following example image.

    ![Configuration parameters for cloud-powered search.](./media/CloudPoweredSearchConfigurationParameters.png)

    1. If the **ProductSearch.UseAzureSearch** configuration parameter exists and is set to **true**, cloud-powered search capabilities are already configured.
    1. If the **ProductSearch.UseAzureSearch** configuration parameter exists but isn't set to **true**, set it to **true**.
    1. If the **ProductSearch.UseAzureSearch** configuration parameter isn't present, continue to the next step.

1. Select **New** to add the **ProductSearch.UseAzureSearch** configuration parameter.
1. Set the value of the **ProductSearch.UseAzureSearch** configuration parameter to **true**.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1110 (Global configuration)** job.

## Browse and search

Search relevance and performance are key factors in the omnichannel experience, because product discovery relies primarily on search functionality for information retrieval and content navigation. An effective and efficient browse and search experience helps increase conversion.

The following illustration shows an example of typical browse and search functionality.

![Search landing page.](./media/SearchLanding.png)

> [!NOTE]
> Product information is regularly published to the Azure Cognitive Search index, but the prices associated with specific customers through trade agreements, price adjustments, or discounts aren't reflected in product search refiners. If you enable **Show affiliation prices** for the **Search results** container in site builder, customer-specific prices will load dynamically when products are shown.

## Faceted navigation and choice summary

Faceted navigation helps customers more easily browse for content by letting them filter on refiners that are linked to terms in a term set. After a customer selects and applies refiners, a summary of their choices is shown.

By using faceted navigation, you can configure different refiners for different terms in a term set without having to create additional pages.

The following illustration shows an example where faceted navigation is used in a search.

![Choice summary.](./media/ChoiceSummary.png)

## Immersive autosuggest

Current autosuggest functionality shows keywords that trigger a search for the matching keyword. Because of new enhancements in Commerce, customers can often discover links to products before they finish typing.

Commerce also supports functionality for keyword matches in various categories. This functionality lets customers see the number of matching keywords across categories and trigger a search for a keyword in other categories.

The following illustration shows an example where immersive autosuggest is being used.

![immersive autosuggest.](./media/ImmersiveAutoSuggestUX.png)

## Sort

Sort functionality enables customers to sort, search, and browse category results, and refine them by criteria such as price, product name, and product number. If you enable [Product recommendations](product-recommendations.md) in your environment, customers can also sort results based on advanced sorting criteria such as new, best-selling, and trending.

> [!NOTE]
> Advanced sorting options like "new", "best-selling", and "trending" are available with Commerce SDK version version 9.35 and Dynamics 365 Commerce version 10.0.20.

## Additional resources

[Default category landing page and search results page overview](category-search-page-overview.md)

[Manage SEO metadata](manage-seo-metadata.md)


[!INCLUDE [footer-include](../includes/footer-banner.md)]
