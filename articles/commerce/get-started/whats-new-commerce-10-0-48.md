---
title: Preview features in Dynamics 365 Commerce 10.0.48 (June 2026)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.48. 
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 04/24/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.search.region: Global
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.48

---

# What's new or changed in Dynamics 365 Commerce 10.0.48 (June 2026)

[!include [banner](../includes/banner.md)]

This article lists features that are new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.48. This version has a build number of 10.0.2645 and is available on the following schedule:

- **Preview of release:** April 2026
- **General availability of release (self-update):** June 2026
- **General availability of release (auto-update):** July 2026

## Features included in this release

The following table lists the features that are included in this release. Microsoft might update this article to include features that are added to the build after this article is originally published.

| Feature area | Feature | More information | Enabled by |
| --- | --- | --- | --- |
| E-commerce | Customize the default branding of EEID sign-in page | In addition to replacing Azure AD B2C for new deployments, Microsoft Entra External ID as next-gen CIAM introduces enhanced support for customizing the sign‑in and sign‑up experience, allowing sellers to brand and tailor authentication pages to match their storefront identity and customer journeys. | --- |
| E-commerce | Prevent indexing of internal URLs | The E-commerce platform now supports preventing search engines from indexing internal or nonpublic URLs. This feature helps ensure that only intended, customer‑facing pages appear in search results. It reduces the risk of exposing internal flows (such as preview, authoring, testing, or system-generated URLs), improves SEO quality, and avoids duplicate or low‑value pages being indexed by search engines. This capability helps you maintain clean search visibility, protect internal site structures, and improve overall search ranking signals by indexing only relevant, production‑ready content. | --- |
| Store Commerce | Distance units display (KM or miles) for store locator and inventory lookup based on the legal entity's country/region | This feature is on by default. Distances are automatically displayed in kilometers for metric-region legal entities and miles for others. | Admins |
| Fulfillment | Cross-legal entity order fulfillment | Commerce orders can now be sourced and fulfilled across multiple legal entities. Retailers can define cross-legal entity fulfillment groups, access inventory across legal entities, automate intercompany order creation, and fulfill cross-legal entity orders from Point of Sale (POS). DOM profiles and rules are updated to support cross-LE strategies. | Admins |
| Point of sale | Modernized customer details page in Store Commerce | The modernized Customer details page replaces the legacy customer details view with a React-based, responsive Fluent UI experience. The redesigned page adapts to desktop and mobile form factors and organizes customer information into four tabs: Account summary, Timeline, Account details, and Transactions. Copilot customer insights and recommended products are surfaced on the Account summary tab. The Transactions tab lets associates view a customer's purchase history and quickly add previously purchased items back to the cart using the new **Buy again** capability. To enable this feature, turn on **Modern customer details page** in the Feature management workspace in Commerce headquarters, then run the **1110 (Global configuration)** distribution schedule job and restart Store Commerce. | Admins |
| Point of sale | Modernized customer create and edit workflows in Store Commerce | Customer creation and editing workflows in Store Commerce are rebuilt on React with a streamlined single-save experience. Associates can now capture customer information and a primary address in one form and save the complete record in a single action, eliminating the previous multistep flow where the customer record could be saved without an address. Mandatory address field validation is controlled by a channel-level setting in Commerce headquarters (**Retail and Commerce \> Channels \> Stores \> All stores**), allowing retailers to enforce this requirement only for markets where a complete primary address is legally required on customer records. The edit workflow follows the same consolidated pattern, keeping associates in a single context rather than navigating between separate screens. | Admins |
| Point of sale | Configure inline actions on transaction line items in Store Commerce | Inline actions extensibility lets retailers and implementation partners configure the set of actions displayed per line item in the modern transaction grid in Store Commerce, using Screen Layout Designer in Dynamics 365 Commerce headquarters. Retailers can select any eligible out-of-the-box POS operation or custom operation to include as an inline action, control the display order, and add custom operations built through the POS extension framework. If no inline actions are configured for a layout, Store Commerce continues to display the existing default set of inline operations. This feature requires the modern transaction grid (**Enable modern transaction grid in POS transaction view** in Feature management). | Admins |
| Point of sale | Dynamic payment terminal selection in point of sale | This feature improves the hardware station and payment terminal selection experience when a hardware station is selected dynamically at the start of a transaction or at the time of tendering. When an associate selects a hardware station, Store Commerce now correctly uses the hardware profile and all peripheral information, including the payment terminal, from the selected hardware station. Associates can also pair a new payment terminal mid-transaction by using the new **Pair a payment terminal** operation, enabling assisted selling scenarios where associates walk to a customer and use the nearest terminal to complete the payment. | Admins |
| Point of sale | Contextual switching of POS with external apps | Today, integrating external systems with POS requires significant development effort, and sales associates must manually re-enter information when moving between applications. Contextual switching eliminates these friction points by enabling external applications to pass product, customer, and transaction context directly into POS. This leads to faster transactions, fewer errors, and a streamlined workflow for store employees, unlocking a flexible, low-friction way to extend POS without replacing existing investments in specialized systems. | --- |
| Point of sale | Prevent the return of specific items in point of sale | This feature enables merchandising managers to define specific products or entire product hierarchies as non-returnable. This can be done by enabling a new property on released products either individually, or in bulk via the category view. Once configured, POS blocks the return of such items to enforce compliance and reduce unauthorized returns. | Admins |
| Point of sale | Set payment method display order and visibility in POS | The feature introduces payment profiles that can be associated with POS registers. These payment profiles provide retailers with a flexible and centralized way to manage how payment methods appear across their POS registers. Store administrators can create reusable profiles and assign them to individual registers or groups of registers, ensuring that each station only displays relevant payment methods. | Admins |
| Omni-channel | Enable credit management support for Commerce orders |Credit limit management is essential for business-to-business (B2B) organizations because most transactions occur on accounts, often involving large orders, long fulfillment cycles, and repeat purchasing. This feature enhancement extends the standard credit management framework to all Commerce orders across channels, ensuring the consistent application of credit policies between Commerce and Supply Chain Management. | Admins |
| Call center | Prevent editing of authorizations from call center |Some merchants enable the automatic capture of authorizations with their payment processors; however, Commerce system is unaware of the capture and voids or adjusts the authorization based on order actions. This can result in captured payments being refunded to the customer and new payments shown on the customer’s account. However, the refunds can take some time to show up and customers being unaware of this and assume that they have been charged multiple times. With this feature, the existing authorizations can't be edited either systematically, partial or full cancellation, or manually from call center. Such modifications need to happen in the payment processor’s portal. | Admins |


## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.48 includes platform updates. For more information, see [Platform updates for version 10.0.48 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-48.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.48, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1125352).

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). It captures all the details, end-to-end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before Microsoft removes any feature from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that you need to make to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
