---
title: What's new and changed in Dynamics 365 Commerce 10.0.31 (February 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.31. 
author: josaw1
ms.date: 01/10/2023
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-10-01
ms.dyn365.ops.version: 10.0.31
---

# What's new and changed in Dynamics 365 Commerce 10.0.31 (February 2023)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.31. This version has a build number of 10.0.1406 and is available on the following schedule:

- **Preview of release:** October 2022
- **General availability of release (self-update):** January 2023
- **General availability of release (auto-update):** February 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Error codes | Commerce introduced standardized error references to be included in online channel checkout errors presented to online shoppers.| [Checkout module error codes](../checkout-module-error-codes.md)  | On by default |
| Languages | Four additional languages are available | Four new languages are available for user selection in the preferred language list: Korean, Portuguese (Portugal), Vietnamese, and Chinese (Traditional). To select this option, go to **User options \> Preferences \> Language and country/region preference**. | Localized preferences |  
| Payments | [Enable Apple Pay with Dynamics 365 Payment Connector for Adyen](/dynamics365-release-plan/2022wave2/commerce/dynamics365-commerce/enable-apple-pay-dynamics-365-payment-connector-adyen)  | E-commerce customers can use Apple Pay on cart and checkout pages when using supported devices or browsers. | Developer opt-in |
| Payments  |  Commerce added the capability to limit how users interact with recurring payment tokens throughout the Commerce headquarters user interface. Payment forms, such as the **Call Center Sales Order** page, no longer display a customer's previously utilized recurring payment token for use in a new transaction. Only a determined "card on file" input into the Commerce **Customer Payments** screen, or with agreement with a customer while paying through a sales order, will be presented to the call center or Commerce headquarters users when processing a payment for a new transaction. | [Limit payment token usage](../dev-itpro/limit-token-usage.md)  |  Feature management<p>*Restrict Payment Token usage to Order context*  |
| POS | [Create purchase orders from POS](/dynamics365-release-plan/2022wave2/commerce/dynamics365-commerce/create-purchase-orders-pos)  |  Improved inbound inventory operation in point of sale (POS) app to allow users to create, edit, and confirm purchase order requests. |  Feature management<p>*Ability to create purchase order request in POS*   |
| POS | <p>The [Store Commerce app](../dev-itpro/store-commerce.md) is now available for iOS and can be installed directly from the Apple App store.<p>The Store Commerce app for iOS supports an integrated hardware station. You can connect directly to networked payment terminals, receipt printers, and cash drawers without having to deploy a shared hardware station. | <p>[Store Commerce for mobile platforms](../dev-itpro/store-commerce-mobile.md)<p>[Store Commerce app in the Apple App store](https://apps.apple.com/app/store-commerce/id1630004521)  | <p>On by default<p>When creating a new device in Commerce headquarters, use the existing "Modern POS - iOS" device type.  |



## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Commerce 10.0.31 includes platform updates. To learn more, see [Platform updates for version 10.0.31 of finance and operations apps (February 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-31.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.31, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=758525).

### Dynamics 365 and industry clouds: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.


For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
