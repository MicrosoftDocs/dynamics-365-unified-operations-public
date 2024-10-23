---
title: Preview features in Dynamics 365 Commerce 10.0.42 (December 2024)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.42. 
author: johnmichalak
ms.date: 10/25/2024
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.40

---

# What's new or changed in Dynamics 365 Commerce 10.0.42 (December 2024)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.42. This version has a build number of 10.0.NNNNNNNN and is available on the following schedule:

- **Preview of release:** October 2024
- **General availability of release (self-update):** December 2024
- **General availability of release (auto-update):** ?????????????

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Point of sale  | Boost efficiency with modern Store Commerce workflows  | You can now set the new flag **modern transaction grid** to yes on POS visual profiles configuration in addition to turning on the feature **Enable modern transaction grid in POS transaction view** to benefit from the refreshed transaction grid, numpad and the button grids. These updates also enable retailers to show product image in cart view  | Admins  |
| Payments  | Check out faster with optimized payment flows  | Adding to the payment methods released with 10.0.40 that support the new user interface, additional payment methods now support the new optimized and unified payment experience. These payment methods include, Gift cards (internal and external), Payment voucher, Customer account and Currency. | Admins  |
| Payments  | Support for new wallet payment methods  | Wallet payments usage is growing across the brick and mortar stores as customers find them as convenient and secure. Businesses can now offer Alipay, WeChat Pay and Affirm payment methods with the out of the box Adyen payment connector using the QR code displayed on the PIN Pad terminals. | Admins  |
| Payments | Support for routing debit cards through local US debit networks  | The debit cards in USA support local debit networks such as PULSE, STAR, NYCE etc. along with global networks such as Visa, Mastercard etc. Merchants can now enable the intelligent routing of debit transactions through these local debit networks using the out of box Adyen connector for In Person Payments and save on transaction fees. | Admins  |
| Orders | Purge Commerce transactions | Some businesses do not have the need to save the Commerce transactions for a long time and thus they want the capability to purge the older transactions to save storage and associated costs. The users with appropriate privileges can now purge old Commerce transactions. | Admins  |


## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.42 includes platform updates. To learn more, see [Platform updates for version 10.0.42 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-42.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.42, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=NNNNNNN).

### Dynamics 365 and industry clouds: 2024 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave2/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
