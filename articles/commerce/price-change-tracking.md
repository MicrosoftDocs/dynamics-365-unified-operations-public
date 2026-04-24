---
title: Price change tracking
description: Learn about the price change tracking feature in Microsoft Dynamics 365 Commerce.
author: boycez
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2023-06-01
ms.custom: 
  - bap-template
---

# Price change tracking

[!include [banner](../includes/banner.md)]

This article describes the price change tracking feature in Microsoft Dynamics 365 Commerce.

Multiple factors, such as seasonal adjustments and promotions, influence a product's active sales price. The price might go up and down over time. Many Commerce scenarios rely on price change signals to trigger specific business workflows. Here are some examples of these triggered business workflows. (These two examples aren't out-of-box features.)

- A retail store must update shelf labels so that they reflect changed prices.
- An e-commerce website alerts shoppers about a price drop for items in their shopping carts.

The Commerce price change tracking feature provides a mechanism for monitoring products that change prices and generating data feeds to surface that information.

## How price change tracking works

To determine whether a product's price changed, the price change tracking feature needs a comparison baseline. The feature sets or refreshes the comparison baseline when any of the following events occur:

- Update a price change tracking company list.
- Import pricing-related data into headquarters through the [data management framework](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages).
- Update the setting for discount concurrency control in Commerce parameters.

On top of the baseline, the price change tracking feature monitors the following system change scenarios that might affect a product's effective sales price:

- Add and release a new product to a legal entity.
- Add, update, or remove a product category.
- Add or remove a product variant.
- Update the base sales price or sales unit of a released product.
- Add, update, remove, or expire a trade agreement.
- Add, update, remove, or expire a price adjustment.
- Add, update, remove, or expire a simple discount.

> [!NOTE]
> To determine price changes, the price change tracking feature currently monitors only trade agreements, price adjustments, and simple discounts that are linked to channel-specific price groups or catalog-specific price groups. Pricing rules that are linked to affiliation-specific price groups or loyalty program–specific price groups aren't in the tracking scope.

The price change tracking feature relies on the following two batch jobs to detect and record price changes:

- **Check price and discount valid period for change tracking** – A recurrent job that records price changes by checking the validity period of trade agreements, price adjustments, and discounts. You can find this batch job on the **Batch jobs** page in headquarters. By default, it runs daily. However, organizations can adjust its recurrence as they require.
-	**Price change tracking** – A job that runs at runtime when you update pricing master data or pricing rules in headquarters. This job isn't discoverable on the **Batch jobs** page in headquarters.

You record price changes in the **RetailPriceChangeTracking** table, as described in the following table.

| Field               | Type        | Description |
|---------------------|-------------|-------------|
| ProductId           | BigInt      | The unique identifier of the product record that has the price change. The special value **0** (zero) indicates a timestamp when the price change tracking baseline is reset. |
| UpdatedDatetime     | Datetime    | The date and time when the price change was detected. |
| UpdatedDatetimeTZId | Int         | The time zone of the date and time when the price change was detected. |
| DataAreaId          | Nvarchar(4) | The legal entity where the price change occurred. |

## Configure price change tracking

Enable price change tracking at the legal entity level.

To configure the price change tracking feature in Commerce headquarters, follow these steps:

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **Prices and discounts** tab, add the legal entities that you want to enable price change tracking for, and then select **Save**.
1. Run the **1110 (Global configuration)** distribution schedule job.

After organizations that use Commerce [cloud-powered product search](cloud-powered-search-overview.md) upgrade to Commerce version 10.0.32 or later for the first time, the price change tracking feature is enabled by default for all legal entities where cloud-powered product search is enabled. This enhancement helps improve efficiency when pricing data is published in the search index, because only incremental updates for products that change prices are monitored. A full synchronization of product data isn't required. To take advantage of this enhancement, ensure that you [initialize the base configuration data for Commerce scheduler](dev-itpro/CDX-Best-Practices.md#update-configurations), and then run the **1020 (Prices and discounts)** distribution schedule job after you upgrade your environment.

To disable price change tracking in headquarters for a specific legal entity, remove the legal entity from the price change tracking setting in Commerce shared parameters (**Retail and Commerce \> Headquarters setup > Parameters \> Commerce shared parameters**). The removed legal entities aren't automatically added again, even if cloud-powered product search is enabled for them. If you remove all legal entities, you disable the price change tracking feature.

### Specify a batch group for price change tracking batch jobs

The price change tracking feature triggers batch jobs that run in the background. To prevent the batch jobs from blocking other critical jobs, specify a batch group for price change tracking batch jobs.

To specify a batch group for price change tracking batch jobs in headquarters, follow these steps:

1. Reuse an existing batch group or [create a batch group](/dynamicsax-2012/appuser-itpro/create-a-batch-group).
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters \> Prices and discounts**.
1. Under **Backend tasks**, specify the batch group to use to run pricing batch jobs. Dedicate a few Application Object Server (AOS) instances to that batch group, separate from other instances dedicated to processing of backbone operations.

For information about the availability of batch group support, see [LCS Issue 830636](https://fix.lcs.dynamics.com/Issue/Details/?bugId=830636&dbType=3).

### Usage patterns not suitable for feature enablement

The price change tracking feature is enabled by default for Azure Search configured legal entities. The feature is efficient when tracking occasional changes based on stable settings, so the following usage patterns aren't recommended for feature enablement.

- Large-scale changes (for example, bulk data migration).
- Highly frequent update of pricing or product data (for example, more than one line per second).

For such cases, temporarily disable the price change tracking feature by removing all legal entities from the **Price change tracking** grid in **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters \> Prices and discounts**, and then restarting AOS. After the data changes are complete, to re-enable the feature for desired legal entities, add the legal entity back to the grid, and then restart AOS. If restarting AOS isn't practical, ensure that the batch group for pricing processing is set up correctly so that the pricing jobs generated don't affect processing of other system batch tasks.

### Cross-company entity change tracking

The following tables are cross-company entities that trigger change tracking when modified, even if the legal entity where the changes are made isn't set up for change tracking.

- RetailGroupMemberLine
- RetailChannelTable
- RetailCatalogPriceGroup
- RetailChannelPriceGroup
- EcoResProductCategory

## Other considerations

For customer environments where pricing or product data is updated frequently (for example, more than one line per second), extensively test the price change feature to assess performance implications before you enable it in your production environment.

When you make large-scale changes (for example, bulk data migration), temporarily remove all legal entities from the price change tracking setting before the changes. Then add them back after the changes are completed. By using this approach, the system mitigates the performance impact by making a one-time full refresh instead of tracking every single line change.

## Troubleshooting

For information on troubleshooting price change tracking issues, see [Price change tracking issues](/troubleshoot/dynamics-365/commerce/pricing-discounts-taxes/price-track-issues).

## Additional resources

[Cloud-powered search overview](cloud-powered-search-overview.md)

[Commerce Data Exchange best practices](dev-itpro/cdx-best-practices.md)

[Data management overview](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages)

[Price change tracking troubleshooting](/troubleshoot/dynamics-365/commerce/pricing-discounts-taxes/price-track-issues)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
