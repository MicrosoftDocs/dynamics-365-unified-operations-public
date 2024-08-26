---
title: Preview features in Dynamics 365 Commerce 10.0.40 (June 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.40. 
author: johnmichalak
ms.date: 04/12/2024
ms.topic: article
audience: Application User
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.40

---

# What's new or changed in Dynamics 365 Commerce 10.0.40 (June 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.40. This version has a build number of 10.0.1935.5 and is available on the following schedule:

- **Preview of release:** April 2024
- **General availability of release (self-update):** May 2024
- **General availability of release (auto-update):** June 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Point of sale (POS)| Native bar code scanning for mobile apps | The Store Commerce app can now scan bar codes and QR codes with the rear-facing camera on an Android or iOS mobile device without requiring the licensing of a third party app. Workflows where bar code scanning is enabled include adding items to a transaction, processing a return, price checks, and inventory operations. | Admins |
| Point of sale (POS)| Streamlined workflow for adding items to a transaction from the product page. | When you add an item to the cart from the product description page or search results, a confirmation dialog is now displays with the list of products being added. Navigation options to go to the transaction or stay on the product or search page are added. Additionally, a new configuration option in the Visual profile in Headquarters can be used to bypass the confirmation dialog and take the user directly to the transaction when an item is added to the sale. | Automatically / Admins | 
| Point of sale (POS)| Display the store phone number on the store location page in point of sale (POS) | Store associates can now view a store’s phone number on the store location page in POS. The store’s phone number is useful for store associates in their daily tasks for contacting the store or providing the phone number to a customer. The store phone number was already available in e-Commerce and Call Center. Now it's available in POS, including a mobile view and an offline mode. | Automatically |
| Point of sale (POS)| Reset button grids at the end of a transaction | To reduce confusion and provide a consistent experience for point of sale users, the default button grid assigned to the first tab is restored when a transaction is completed, suspended, or voided. | Automatically |
| Point of sale (POS)| Configure display of search results | The default view for displaying search results can now be configured in the Visual profile in Headquarters. Before this release, the default view for search results was list view, but we received feedback from customers that they prefer card view, especially on mobile devices. | Admins |
| Point of sale (POS)| Store commerce self-checkout | POS customers can turn on kiosk based self-checkout for their shoppers to be able to scan and pay for items by credit card. | Admins |
| Point of sale (POS)| Check out faster with optimized payment flows | An updated user interface for cash and credit card POS payment flows saves time at checkout using modern, redesigned single-window interactions to accept payments. These flows also bring 'Exact payment' options to quickly send the checkout to the payment terminal or process an exact-change payment. The cash payment flow also introduces "Smart denominations," that offer logical cash grouping payment options a shopper is likely to use for the transaction.  | Admins |
| Payments | Support for nonrecurring payment tokens in Commerce | Commerce now supports payment operations without the need to store a card token for payment processing. Online store, Call Center, and POS Customer Orders are updated to process payments within a single authorization request. Sales Order adjustments uses 'authorization adjustment' actions to increase or decrease the original authorization instance. System authorization expiry parameters can now be set at the card type level. Expired authorizations can also be monitored in the Credit card authorization management form in Headquarters.  | Admins |
| Digital commerce | Provide multiple shipping address, notes, and delivery date | Consumer and business buyers can now choose multiple shipping addresses for the items within a single order and add notes such as delivery instructions and optionally add a delivery date for the items. | Admins |
| Point of sale (POS)| Customer insights by Copilot^ | Enhance customer interactions and create personalized shopping experiences with Copilot, empowering store associates through data-driven insights. [Learn more](https://learn.microsoft.com/en-us/dynamics365/commerce/copilot-pos-customer-insights)| IT administrators |
| Point of sale (POS) | Report insights by Copilot^| Enhance efficiency, accuracy, and real-time sales analysis with Copilot’s narrative summaries for store reports in the Store Commerce app. [Learn more](https://learn.microsoft.com/en-us/dynamics365/commerce/copilot-pos-report-insights)| IT administrators |
| Point of sale (POS) | Product insights by Copilot^| Copilot empowers store associates to efficiently share product details and promotions, enhancing cross-selling and customer experience. | IT administrators |

^ 10.0.40, PQU-1 onwards (CSU : 9.50.24184.2, Store Comm. App 9.50.24189.1)

## Additional resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.40 includes platform updates. To learn more, see [Platform updates for version 10.0.40 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-40.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.39, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=932660).

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
