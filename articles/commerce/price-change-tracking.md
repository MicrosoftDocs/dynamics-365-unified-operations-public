---
# required metadata

title: Price change tracking
description: This article describes the price change tracking feature in Microsoft Dynamics 365 Commerce.
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

This article describes the price change tracking feature in Microsoft Dynamics 365 Commerce.

A product's active sales price is influenced by multiple factors (for example, seasonal adjustments and promotions) and may go up and down over a period of time. Many Commerce scenarios rely on price change signals to trigger specific business workflows. Examples of triggered business workflows include a retail store needing to update shelf labels with changed prices, or an e-commerce website alerting shoppers about a price drop for items in their shopping bags. The Commerce price change tracking feature provides a mechanism to monitor products with changed prices and generate data feeds to surface that information.

## Configure price change tracking

Price change tracking can be enabled at the legal entity level. 

To configure the price change tracking feature in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **Prices and discounts** tab, add the legal entities for which you want to enable price change tracking, then select **Save**.
1. Run the **1110 (Global configuration)** distribution schedule job.

For organizations that use [cloud-powered product search](cloud-powered-search-overview.md) in Commerce, after upgrading to Commerce version 10.0.32 or later for the first time, the price change tracking feature is enabled by default on all legal entities where cloud-powered product search is enabled. This helps improve the efficiency of pricing data publishing in the search index by only monitoring incremental updates for products with changed prices, instead of relying on a full product data sync. To take advantage of this enhancement, ensure that the [environment initialization process](enable-configure-retail-functionality.md) has been completed, and execute the **1020 (Prices and discounts)** distribution schedule job after your environment upgrade. 

To disable price change tracking for a specific legal entity, in headquarters remove the legal entity from the price change tracking setting in Commerce shared parameters (**Retail and Commerce \> Headquarters setup > Parameters \> Commerce shared parameters**). The removed legal entities won't automatically be added again, even if cloud-powered product search is enabled for them. Removing all legal entities effectively disables the entire price change tracking feature.

## How price change tracking works

Determining whether a product's price has changed must be based on a comparison baseline. The comparison baseline is set or refreshed when any of the following events occur:

- A price change tracking company list is updated.
- Pricing related data is imported into headquarters via the [data management framework](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages).
- The discount concurrency control setting is updated in Commerce parameters.

On top of the baseline, the price change tracking feature monitors the following system change scenarios that might affect a product's effective sales price:

- A new product is added and released to a legal entity.
- A product category is added, updated, or removed.
- A product variant is added or removed.
- The base sales price or sales unit of a released product is updated.
- A trade agreement is added, updated, removed, or expired.
- A price adjustment is added, updated, removed, or expired.
- A simple discount is added, updated, removed or expired.

> [!NOTE]
> To determine price changes, currently the price change tracking feature only monitors trade agreements, price adjustments, and simple discounts that are linked to channel-specific price groups or catalog-specific price groups. Pricing rules linked to affiliation-specific price groups or loyalty program-specific price groups are not in the tracking scope. 

The price change tracking feature depends on the following two batch jobs to detect and record price changes:

- **Check price and discount valid period for change tracking** – A recurrent job that records price changes by checking the validity period of trade agreements, price adjustments, and discounts. This batch job can be found on the **Batch jobs** form in headquarters and runs daily by default. Organizations can adjust its recurrence as needed.
-	**Price change tracking** – A job that is executed at runtime when pricing master data or pricing rules are updated in headquarters. This job isn't discoverable on the **Batch jobs** form in headquarters.

Price changes are recorded in the **RetailPriceChangeTracking** table, as described below.

| **Field**           | **Type**    | **Description**                                                                                                                          |
|---------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------|
| ProductId           | BigInt      | Unique identifier of the product record that has the price change. Special value of **0** indicates a timestamp when the price change tracking baseline is reset. |
| UpdatedDatetime     | Datetime    | Date and time when the price change was detected. |
| UpdatedDatetimeTZId | Int         | Time zone of the date and time when the price change was detected. |
| DataAreaId          | Nvarchar(4) | Legal entity where the price change occurred.  |

## Other considerations

For customer environments where pricing or product data is updated very frequently (for example, more than one line per second), Microsoft recommends that you extensively test the price change feature to assess performance implications before enabling it in your production environment.

When performing large-scale changes (for example, bulk data migration), Microsoft recommends that you temporarily remove all legal entities from the price change tracking setting prior to the changes, and then add them back after the changes are done. The system then mitigates the performance impact by making a one-time full refresh, instead of tracking every single line change.

## Additional resources

[Cloud-powered search overview](cloud-powered-search-overview.md)

[Initialize seed data in new Commerce environments](enable-configure-retail-functionality.md)

[Data management overview](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
