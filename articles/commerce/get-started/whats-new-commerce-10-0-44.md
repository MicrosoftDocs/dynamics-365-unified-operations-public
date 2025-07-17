---
title: Preview features in Dynamics 365 Commerce 10.0.44 (April 2025)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.44. 
author: johnmichalak
ms.date: 06/20/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.44

---

# What's new or changed in Dynamics 365 Commerce 10.0.44 (April 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.44. This version has a build number of 10.0.2263.11 and is available on the following schedule:

- **Preview of release:** April 2025
- **General availability of release (self-update):** June 2025
- **General availability of release (auto-update):** July 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Payments | Klarna support for physical stores via Store Commerce app |  Supporting buy now, pay later (BNPL) payment methods like Klarna helps merchants boost sales by offering customers flexible, interest-free financing options. BNPL can drive higher average order values and enhances customer satisfaction and loyalty by making purchases more accessible.  | Admins  |
| Payments | Optimized payment flow now available for loyalty payments  |  Like other payment methods, the loyalty payment method now supports the optimized and unified payment user interface (UI). Other capabilities include the ability to initiate customer search and view all loyalty cards associated with a customer. This functionality helps cashiers easily find the required information to complete the transaction. | Admins  |
| Point of Sale | Loyalty upsell prompt | The loyalty upsell prompt feature is designed to prompt store associates to inform customers about their loyalty program status and tier qualifying points. This feature aims to enhance customer engagement and satisfaction, resulting in increased loyalty, repeat purchases, and overall sales. To enable this feature in Commerce headquarters, go to the feature management workspace and enable **Retail Loyalty Upsell Prompt**. Learn more in [Loyalty upsell prompt feature in POS](../loyalty-upsell-prompt.md). | Admins |
| Point of Sale | Health check view for offline readiness | This feature performs various checks to verify the status and readiness of the offline database, ensuring a smooth switching experience by creating awareness of any issues. This feature is enabled by default. Learn more in [Health check view for offline readiness](/dynamics365/commerce/health-check-view-offline). | Admins |
| Point of Sale | Enable toast notifications for data sync failures and unsuccessful offline installation | The toast notifications provide more visibility to issues that may be preventing offline switching such as data sync failures and unsuccessful offline installations during the app upgrades. Learn more in [Offline reliability toast notifications in the Store Commerce app](/dynamics365/commerce/dev-itpro/retail-sdk/offline-reliability-toast-notifications). | Admins |
| Point of Sale | Toast notifications extensibility | This release also features the API availability for extending toast notifications and provides the schema and samples for the same. Learn more in [How to consume APIs in your extension](/dynamics365/commerce/dev-itpro/pos-apis#how-to-consume-apis-in-your-extension). | Admins |
| Point of Sale | Modern workflows in POS | Boost efficiency with modern workflows in Store Commerce enabled by React-based controls and Fluent Design on the transaction page. The transaction page includes new capabilities such as inline actions, inline change quantity on the transaction grid, and product images in cart view. To enable this feature, turn on the **Enable modern transaction grid in POS transaction view** in the headquarters **Feature management workspace**, and set the **Flag modern transaction grid** option to **Yes** on the POS visual profiles configuration. Learn more in [Modern workflows in POS](../POS-UX-modernization.md). | Admins |
| Point of Sale | Support for iOS hardware station extensibility | iOS hardware station extensibility enables greater flexibility in hardware integration while reducing your in-store hardware footprint. You can build extensions to support custom hardware station requirements such as fiscal printers or other custom peripheral devices on iOS devices. Learn more in [Store Commerce Hardware station extensibility for Android and iOS devices](/dynamics365/commerce/dev-itpro/store-comm-android-ios-ext).| Admin |
| Point of Sale | Extensibility in POS self-checkout | This feature enables an extension point for cart level lines that can allow customers to override and add custom business rules. | Admins |
| Payments |  Pay by Link on Point of Sale using Adyen connector |  This feature adds the support for asynchronous notifications to the out-of-the-box Adyen payment connector. A new payment method named Pay by Link (and QR code) is also available that enables all the modern payment methods without the need of dedicated payment terminals. This feature is in **preview** and will be **available to a limited number of customers** until it's marked as Generally Available.  | Admins  |

## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.44 includes platform updates. To learn more, see [Platform updates for version 10.0.44 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-44.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.44, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1026442).

### Dynamics 365 and industry clouds: 2024 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
