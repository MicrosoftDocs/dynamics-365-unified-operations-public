---
# required metadata

title: Price change tracking
description: This article describes the price change tracking feature provided by Dynamics 365 Commerce.
author: boycez
ms.date: 06/01/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2023-06-01

---

# Price change tracking

[!include [banner](../includes/banner.md)]

This article describes the price change tracking feature provided by Dynamics 365 Commerce.

A product’s active sales price is influenced by multiple factors (seasonal adjustments, promotions, etc.) and may go up and down over a period. Many commerce scenarios rely on the price change signals to trigger specific business workflows. For example, a retail store needs to update the shelf labels with changed prices, an e-commerce website wants to alert shoppers about price drop of items in their shopping bags. The price change tracking feature provides a mechanism to detect products with changed prices and generate data feeds to surface the information.

## Configure price change tracking

Price change tracking can be enabled at legal entity level. To use this feature, follow these configuration steps in Commerce headquarters:

1. Go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce shared parameters**.
1. On the **Prices and discounts** tab, add the legal entities you want to enable price change tracking into the data grids, then click **Save**.
1. Run the **1110 (Global configuration)** distribution schedule.

For customers who use [cloud-powered product search](https://learn.microsoft.com/dynamics365/commerce/cloud-powered-search-overview) in Commerce, after first time upgrading to version **10.0.32** and later, the price change tracking is enabled by default on all legal entities where the cloud-powered product search is enabled. This helps improve the efficiency of pricing data publishing in the search index by leveraging incremental updates only for products with changed prices rather than relying on full product data sync. Please ensure the [environment initialization process](https://learn.microsoft.com/dynamics365/commerce/enable-configure-retail-functionality) is done and the **1020 (Prices and discounts)** distribution schedule job is executed after environment upgrade to take advantage of this enhancement. 

To disable price change tracking on a specific legal entity, simply remove that legal entity from the price change tracking setting in Commerce shared parameters. The removed legal entities won’t be automatically added back even cloud-powered product search is enabled for them. Removing all legal entities effectively disables the entire price change tracking feature.

## How price change tracking works

The statement of “a product’s price has changed” must be based on a comparison baseline. For example, product X’s sales price has changed since two weeks ago. In price change tracking feature, that baseline is set or refreshed when any of the following occurs:

- Price change tracking company list is updated.
- Pricing related data is imported into Commerce headquarters via [Data management framework](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages).
- Discount concurrency control setting is updated in Commerce parameters.

On top of the baseline, the following changes in the system that might affect a product’s effective sales price are monitored by the price change tracking feature:

-	A new product is added and released to a legal entity.
-	A product category is added, updated or removed.
-	A product variant is added or removed.
-	The base sales price or sales unit of a released product is updated.
-	A trade agreement is added, updated, removed, or expired.
-	A price adjustment is added, updated, removed, or expired.
-	A simple discount is added, updated, removed or expired.

> [!NOTE]
> Currently, the price change tracking feature only monitors trade agreements, price adjustments and simple discounts that are linked to channel-specific price groups or catalog-specific price groups to determine price changes. Pricing rules linked to affiliation-specific price groups or loyalty-program-specific price groups are not in the tracking scope. 

The price change tracking feature relies on two batch jobs to detect and record price changes:

- **Check price and discount valid period for change tracking** – A recurrent job that records price changes by checking validity period of trade agreements, price adjustments and discounts. This batch job can be found in the Batch jobs form and runs daily by default. Organizations can adjust its recurrence as needed.
-	**Price change tracking** – A job that is executed at runtime when pricing master data or pricing rule is updated in Commerce headquarters. This job cannot be found in the Batch jobs form.

Price changes are recorded in the **RetailPriceChangeTracking** table.

| **Field**           | **Type**    | **Description**                                                                                                                          |
|---------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------|
| ProductId           | BigInt      | RecordId of the product that has price change. Special value *0* indicates a timestamp when the price change tracking baseline is reset. |
| UpdatedDatetime     | Datetime    | Datetime when the price change is detected.                                                                                              |
| UpdatedDatetimeTZId | Int         | Timezone of the datetime when the price change is detected.                                                                              |
| DataAreaId          | Nvarchar(4) | Legal entity where this price change occurs.                                                                                             |

## Other considerations

For customer environments where pricing or product data is updated very frequently (e.g., >1 line / second), it’s recommended to test this feature extensively to assess performance implications before enabling it on production.

When performing large-scale changes, for example, bulk data migration, it’s recommended to temporarily remove all legal entities from the price change tracking setting prior to the changes and add them back after the changes are done. This way, the system will mark a one-time full refresh instead of tracking every single line change, to mitigate the performance impact.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
