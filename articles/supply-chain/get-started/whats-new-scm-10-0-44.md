---
title: What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)
description: Learn about features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management 10.0.44 with a table outlining feature areas. 
author: kamaybac
ms.author: kamaybac
ms.reviewer: kamaybac
ms.search.form:
ms.topic: whats-new
ms.date: 08/05/2025
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# What's new or changed in Dynamics 365 Supply Chain Management 10.0.44 (June 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Supply Chain Management version 10.0.44. This version has a build number of 10.0.2263 and is available on the following schedule:

- **Preview of release:** April 2025
- **General availability of release (self-update):** June 2025
- **General availability of release (auto-update):** July 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Procurement and sourcing | [Automate procure-to-pay tasks with supplier communications agent](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/automate-procure-to-pay-tasks-copilot) | [Supplier Communications Agent overview (production ready preview)](../procurement/supplier-com-agent-overview.md) | Feature management:<ul><li>*(Preview) Immersive Home*</li><li>*(Production ready preview) Agent management*</li><li>*(Production ready preview) Supplier Communications Agent*</li><li>*(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails*</li></ul> |
| Production control and Accounts receivable | [Achieve regulatory compliance and quality excellence](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-supply-chain-management/achieve-regulatory-compliance-quality-excellence) | [Advanced quality management overview](../inventory/advanced-quality-management-overview.md) | Feature management:<ul><li>*Approved customer list*</li><li>*Dispense management*</li><li>*Electronic signature improvements*</li><li>*Advanced quality management*</li></ul> |
| Production control | Select color themes on production floor execution interface | [How workers use the production floor execution interface](../production-control/production-floor-execution-use.md)<br><br>[Configure the production floor execution interface](../production-control/production-floor-execution-configure.md) | Feature management:<br>*Select color themes on production floor execution interface* |

## <a name="enhancements"></a>Feature enhancements added in this release

The following table lists the feature enhancements that were added in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they're only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2024wave2/finance-supply-chain/dynamics365-supply-chain-management/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

Some of these features aren't visible on your system until you turn them on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) using the name listed here for the *Feature management name* (additional configuration may also be needed). Features that don't show a feature management name are visible by default as of this version of Supply Chain Management, but typically add a new configuration option that you need to set to use the new functionality.

| Feature enhancement | Description |
|---|---|
| **Module:** Asset management<br><br>**Feature management name:** *Aggregated material availability check* | Aggregates supply and demand per item, providing a comprehensive view of potential material shortages.<br><br>Learn more in [Material availability check for work orders](../asset-management/work-orders/material-availability-check-work-orders.md). |
| **Module:** Asset management<br><br>**Feature management name:** *Credit limit check on work order dispatch.* | Issues a warning or error if a work order forecast exceeds the customer's remaining credit limit.<br><br>Learn more in [Bill for maintenance on customer-owned assets](../asset-management/integration-to-project-management-and-accounting/customer-billing.md). |
| **Module:** Cost management<br><br>**Feature management name:** *Large Volume Historical Inventory Value Report Generation* | Adds the capability to run a historical inventory value report storage, which can prevent time-out errors from occurring when generating an inventory value report. It works by separating the items into multiple bundles and then processing each bundle list continuously. You can configure the number of items processed within each bundle on the **Inventory and warehouse management parameters** page. For example, when dealing with a large item volume, such as 800K, a bundle size of 30K might be appropriate. This feature should only be used when generating historical reports for a significantly large number of items because it takes longer to run than the standard inventory value report.<br><br>Learn more in [Inventory value reports](../cost-management/inventory-value-report-storage.md). |
| **Module:** Master planning<br><br>**Feature management name:** *Allow pegging of demand against multiple shelf life batches for Planning Optimization.* | Enhances coverage groups to to add an option that allows Planning Optimization to peg a single demand against multiple batches with different expiration dates. |
| **Module:** Master planning<br><br>**Feature management name:** *Cosider batch disposition code in available to promise (ATP) calculation.* | Enables the system to calculate available to promise (ATP) for items tracked using inventory batches. The feature adds a new parameter to the sales settings that lets you choose whether the batch disposition code is considered when calculating ATP. |
| **Module:** Master planning<br><br>**Feature management name:** *Plan for a single site or warehouse in Planning Optimization* | Lets you plan for a single site or warehouse in Planning Optimization. Enterprises and companies operating in different sites can operate independently by running different master plans for their respective ownership. The feature adds a new filter on the master plan level, which lets you specify the scope for the given master plan by choosing the required inventory dimensions. |
| **Module:** Procurement and sourcing<br><br>**Feature management name:** *Copy Prices include sales tax setting from vendor* | Adds the option to copy the vendor's **Prices include sales tax** setting when you create a purchase order from a purchase requisition. If you turn this option off, the **Prices include sales tax** setting isn't copied and is disabled by default. To set this option, go to the **Accounts payable parameters** page, open the **General** tab, expand the **Vendor** FastTab, and adjust the **Copy Prices include sales tax setting from vendor** slider. This feature is already mandatory and can't be turned off. |
| **Module:** Product information management<br><br>**Feature management name:** *Enable foreign trade parameters for all countries* | Adds foreign trade parameters for all previously unsupported countries/regions, including Hong Kong SAR, China, Thailand, Japan, Korea, Malaysia, Russia, and Türkiye. The new settings are available on **Foreign trade** FastTab for released products. |
| **Module:** Production control<br><br>**Feature management name:** *Add lines to the adjust materials dialog* | Lets you add and delete material lines in the **Adjust materials** dialog on the production floor execution interface. |
| **Module:** Production control<br><br>**Feature management name:** *Enhanced user experienced for tracked components management* | Enhances the production floor execution interface to provide a more efficient and user-friendly experience for registering tracked component information. Workers can now use the scan option instead of toggle buttons to register serial or batch numbers for finished goods. You can now choose between multiple scan modes (*product* or *component*), which allows for greater flexibility and accuracy. The interface for editing product and component associations has been improved, making it easier to manage and update these associations. |
| **Module:** Production control<br><br>**Feature management name:** *List view for reporting job scrap from the production floor execution interface* | Workers reporting job scrap from the production floor execution interface can now choose to work from a list view that shows several jobs at once, or from a detail view that shows more information about one job at a time. Previously, only the detail view was available. |
| **Module:** Warehouse management<br><br>**Enhancement:** *Display tracking dimension control for last on-hand*<br><br>**Feature management name:** *(None)* | Lets you choose how the Warehouse Management mobile app shows the *tracking dimension below location* control, including *batch below number* and *serial below number*. The setting has no impact on the display of *tracking dimension above location*, such as *batch above number* or *serial above number*.<br><br>Learn more in [Global mobile device parameters](../warehousing/mobile-device-parameters.md). |
| **Module:** Warehouse management<br><br>**Enhancement:** *Transfer order receiving ASN cleanup*<br><br>**Feature management name:** *(None)* | Adds a setting that lets you choose when advance shipping notice (ASN) data is deleted during the transfer order receiving process. It covers scenarios where ASN data is required beyond default settings on the receiving process, for example when partially receiving a transfer order with multiple license plates using both the Warehouse Management mobile app and the web client.<br><br>Learn more in [Configure the transfer order receiving process](../warehousing/configure-transfer-order-receiving-process.md). |

## Features becoming mandatory in this release

The following table lists the features that became mandatory in version 10.0.44. These features can still be seen in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) but can no longer be turned off.

| Module | Feature name | More information |
|---|---|---|
| Procurement and sourcing | *Copy Prices include sales tax setting from vendor* | [Feature enhancements included in this release](#enhancements) |

## Features removed from Feature management

The following table lists features that were removed from Feature management in version 10.0.44. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Supply Chain Management.

| Module | Feature name | More information |
|---|---|---|
| Cost management | *Enable user-defined batch number setup for inventory closing reverse* | [Preview features in Dynamics 365 Finance 10.0.20 (August 2021)](../../finance/dev-itpro/whats-new-changed-10-0-20.md) |
| Cost management | *Inventory aging report storage* | [Inventory aging report storage](../cost-management/inventory-aging-report-storage.md) |
| Cost management | *Inventory value report storage* | [Inventory value reports](../cost-management/inventory-value-report-storage.md) |

## Related information

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Supply Chain Management 10.0.44 includes platform updates. Learn more in [Platform updates for version 10.0.44 of Finance and Operations apps (June 2024)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-44.md).

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.44, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1026442).

### Dynamics 365: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Microsoft Dynamics 365: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Supply Chain Management features

The [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article describes features that have been or are scheduled to be removed or deprecated for Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Supply Chain Management](removed-deprecated-features-scm-updates.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
