---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.26 (May 2022)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.26 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.topic: article
ms.date: 04/19/2024
ms.custom: evergreen
ms.reviewer: kamaybac
ms.search.form:
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.26 (May 2022)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.26. This version has a build number of 10.0.1192 and is available as follows:

- **Preview of release:** March 2022
- **General availability of release (self-update):** April 2022
- **General availability of release (auto-update):** May 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory and logistics | [Inventory Visibility on-hand query to support advanced warehouse management items](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/inventory-visibility-support-advanced-warehouse-management) | [Inventory Visibility support for WMS items](../inventory/inventory-visibility-whs-support.md) | Feature management:<br>*Enable warehouse items in Inventory Visibility* |
| Inventory and logistics | [Available-to-promise for the Inventory Visibility Add-in](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/available-to-promise-inventory-visibility-add-in) | [Inventory Visibility on-hand change schedules and available to promise](../inventory/inventory-visibility-available-to-promise.md) | Enabled by service configuration |
| Manufacturing | [Catch weight items for the production floor execution interface](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/catch-weight-items-production-floor-execution-interface) | [How workers use the production floor execution interface](../production-control/production-floor-execution-use.md) | Feature management:<br>*Report on catch weight items from the production floor execution interface* |
| Manufacturing | My jobs tab on the production floor execution interface | [How workers use the production floor execution interface](../production-control/production-floor-execution-use.md) | Feature management:<br>*My jobs tab on the production floor execution interface* |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do that in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Module | Feature name in feature management | More information |
|---|---|---|
| Procurement and sourcing | Post registered quantities of stocked products and remainders of not-stocked products for receipts and vendor invoices | This feature changes how quantities of not-stocked products (such as services) are posted when processing vendor invoices and inbound shipments against purchase orders. The feature modifies the behavior of the *Registered quantity and services* quantity option for posting receipts and vendor invoices by changing it to match the behavior of the *Registered quantity and not-stocked products* option already provided when posting quantities for sales packing slips.<br><br>When you post a product receipt or vendor invoice using the *Registered quantity and services* quantity option, the system posts the registered quantity of stocked products and posts the remainder quantity of not-stocked products (including both services and non-services). Without this feature, the system still posts the registered quantity of stocked products (including services configured as stocked items) but always posts the full ordered quantity of not-stocked service products (and ignores not-stocked products that are not of type *Service*). |
| Procurement and sourcing | Synchronize tracking dimensions on intercompany sales and purchase order lines | This feature lets you control whether the serial and batch number tracking dimensions are synchronized across intercompany sales and purchase order lines. It adds new settings to both the **Purchase order policies** and **Sales order policies** tabs of the **Intercompany** setup page for customers and vendors. It also updates the names of a few related, nearby settings for clarity.<br><br>If you are using warehouse management processes (WMS), then be aware that this feature will only synchronize batch and serial numbers when those dimensions are above location in the target destination reservation hierarchy. |
| Product information management | Clean up product attribute values | This feature adds a periodic task called **Clean up product attribute values**, which cleans up product attribute value records that are no longer associated with any product via a product category. |
| Inventory and warehouse management | (Russia) Prevent discrepancies when issuing GTDs for purchase orders that include WMS-enabled items | This feature is for Russian localization only. It prevents discrepancies that occur when issuing Russian customs declaration numbers (GTDs) for import purchase orders that include items enabled for warehouse management processes (WMS). The GTD-issuing process changes some inventory dimension values on the related inventory transactions for invoices included in the custom journal, which leads to discrepancies between the work records for the purchase order and the inventory transactions for the purchase. When this feature is enabled, the GTD-issuing process generates adjustment work that eliminates such discrepancies. |
| Warehouse management | Enhanced parser for GS1 barcodes | This feature adds an enhanced parser for GS1 symbol data. The new parser implements the GS1 General Specification algorithm for parsing GS1 symbols and provides stronger data validation. Learn more in [GS1 bar code scanning](../warehousing/gs1-barcodes.md). |
| Warehouse management | Warehouse management application - blank GTD | This feature is for Russian localization only. It allows workers using the Warehouse Management mobile app to leave Russian customs declaration numbers (GTDs) blank when needed. If the GTD tracking dimension is set up to allow blank values, the system will accept blank values for GTD for inventory operations provided on-hand inventory is available. |

## New and updated documentation resources

We have recently added or significantly updated the following help articles. These articles aren't necessarily related to the new features that were added for this release, as listed in the previous sections. However, they might help you to get more out of existing features.

| Feature area | New or updated articles |
|---|---|
| Cost management | Updated examples and diagrams were added to each of the following articles:<ul><li>[FIFO with physical value and marking](../cost-management/fifo-physical-value-marking.md)</li><li>[LIFO with physical value and marking](../cost-management/lifo-physical-value-marking.md)</li><li>[LIFO Date with physical value and marking](../cost-management/lifo-date-physical-value-marking.md)</li><li>[Running average cost price](../cost-management/running-average-cost-price.md)</li><li>[Weighted average with physical value and marking](../cost-management/weighted-average-physical-value-marking.md)</li></ul> |

## Related information

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.26 includes platform updates. Learn more in [Platform updates for version 10.0.26 of finance and operations apps (May 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-26.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of 10.0.26, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=662864).

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

