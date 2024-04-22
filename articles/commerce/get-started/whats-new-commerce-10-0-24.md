---
# required metadata

title: What's new or changed in Dynamics 365 Commerce 10.0.24 (February 2022)
description: This article describes features that are either new or changed in Dynamics 365 Commerce 10.0.24. 
author: josaw1
ms.date: 04/12/2024
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.custom:
  - bap-template
  - evergreen
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2021-12-31 
ms.dyn365.ops.version: 10.0.24

---

# What's new or changed in Dynamics 365 Commerce 10.0.24 (February 2022)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.24. This version has a build number of 10.0.1084 and is available on the following schedule:

- **Preview of release:** December 2021
- **General availability of release (self-update):** January 2022
- **General availability of release (auto-update):** February 2022

## Features included in this release

The following table lists the features that are included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/planned-features), where you can see the official release dates for each feature. The *More information* column provides more details and/or links to related documentation. To determine how to turn on a feature, see the *Enabled by* column. For more information about how to use feature management, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). We might update this article to include features that made it into the build after this article was initially published.

| Feature area   | Feature                                                  | More information                                          |  Enabled by             |
|----------------|----------------------------------------------------------|-----------------------------------------------------------|-------------------------|
|  B2B         | Support for matrixed view of product variants on the PDP and quick order entry page.        | [Set up a B2B e-commerce site](../b2b/set-up-b2b-site.md)            | Site builder |
|  Inventory   |  [Improved stock count operation in POS](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/improved-stock-count-operation-pos)  | This feature introduces several functional and experience enhancements to the stock count operation in the POS app.  | Feature management<p>*Improved stock count operation in POS*  |
| Payments | [Improvements to payment flows for pick-up order processing in POS](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/improvements-payment-flows-pick-up-order-processing-pos) | [Multiple available payment methods for in-store pickup](../dev-itpro/multiple-payments-pickup.md) | Feature management<p>*Omni-channel payments* |

## Feature enhancements included in this release

The following table lists the feature enhancements that are new for this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/planned-features). However, to ensure that these enhancements won't conflict with your existing customizations or preferences, each of them is turned off by default (unless otherwise noted).

If you want to turn any of these features on or off, you must do so in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), where they are listed using the names shown in the *Feature name in feature management* column of the following table.

| Module | Feature name in feature management | More information |
|---|---|---|
| Customer management  | Enable enhanced async customer creation  | This feature enables capturing title, affiliations, and second contact information while creating a customer in asynchronous mode.  Refer to [Asynchronous customer creation mode](../async-customer-mode.md) for more details. |
| Headquarters setup   |  Run "Initialize commerce scheduler" after Headquarters is updated |  [Commerce Data Exchange best practices](../dev-itpro/cdx-best-practices.md) |


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Commerce 10.0.24 includes platform updates. To learn more, see [Platform updates for version 10.0.24 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-24.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=641306&dbType=3&qc=5b1d5e49c96b8a5cfb5601889a413e6f3773ba6500f9bc47310dcc5c54fff42f).

For Commerce-specific breaking changes, view the [Dynamics 365 Commerce online SDK FAQ](../e-commerce-extensibility/sdk-faq.md).

### Dynamics 365: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

