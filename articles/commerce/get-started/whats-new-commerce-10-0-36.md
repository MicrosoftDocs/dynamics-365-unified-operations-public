---
title: Preview of Dynamics 365 Commerce 10.0.36 (October 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.36. 
author: josaw1
ms.date: 08/01/2023
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-07-31
ms.dyn365.ops.version: 10.0.36
---

# Preview of Dynamics 365 Commerce 10.0.36 (October 2023)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.36. This version has a build number of 10.0.1695 and is available on the following schedule:

- **Preview of release:** July 2023
- **General availability of release (self-update):** September 2023
- **General availability of release (auto-update):** October 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Inventory management | [Enable real-time inventory with Inventory Visibility](/dynamics365/release-plan/2023wave2/commerce/dynamics365-commerce/enable-real-time-inventory-commerce-inventory-visibility) |  This feature enables native integration between Commerce and Inventory Visibility (IV), a Dynamics 365 Supply Chain Management microservice. Customers who are licensed for both Supply Chain Management and Commerce will have the option to enable Inventory Visibility as the inventory data provider to serve commerce scenarios. On-hand inventory can be queried, reserved, and adjusted in real-time. Organizations can also configure additional inventory data sources and define custom on-hand inventory calculation formulas to fit specific business needs. | IT Pro opt-in |
| Loyalty  |  Define loyalty cards   |  [Define loyalty cards](../tasks/define-loyalty-cards.md)  |  |
|  Orders  | Prompt customer contact details during asynchronous order cancellation  |  If the asynchronous order cancellation feature is enabled, the store associates can be prompted to verify the customer contact information when canceling an order. This verification ensures that if there are any problems in canceling the order, the customer can be reached using the verified contact details.<p>[Customer orders in point of sale (POS)](../customer-orders-overview.md#enable-customer-orders-to-be-created-in-asynchronous-mode)  |  IT Pro opt-in   |
|   Payments   |   Google Pay on Adyen (Fix with Standard Google Pay Button)  |  Commerce now offers a dedicated "Google Pay" module to offer an alternate Google Pay solution for regular (non-express) payment in the online cart checkout process. This module uses the direct Google Pay API approach, differing from the Iframe structure used by the common payment module. This new module addresses browser limitations from Google and will support direct express checkout experiences in future iterations.<p>[Configure Google Pay with Adyen](../dev-itpro/google-pay-adyen.md)  |  Developer opt-in   |
| Point of sale (POS) |  Organizations that have strict requirements for unique receipt IDs can enable automatic synchronization of number sequence data. When enabled, the latest number sequence data is retrieved from the Commerce Scale Unit (CSU) whenever POS is initialized. This action guarantees that the POS will always have the most current number sequence before any transactions are executed.   |  [Reset receipt numbers](../reset_receipt_number_sequence.md)  |  Admin/maker    |



## Additional resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.36 includes platform updates. To learn more, see [Platform updates for version 10.0.36 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-36.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.35, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=831854&dbType=3&qc=bffd63612a8f998d04f4f14d6d456f17d1f6038819d1225f612e2fd0f5c59e17).

### Dynamics 365 and industry clouds: 2023 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 2 plan](/dynamics365/release-plan/2023wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.


For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
