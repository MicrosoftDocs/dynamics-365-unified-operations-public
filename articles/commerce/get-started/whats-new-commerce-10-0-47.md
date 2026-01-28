---
title: Preview features in Dynamics 365 Commerce 10.0.47 (January 2026)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.47. 
author: johnmichalak
ms.date: 01/28/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.47

---

# What's new or changed in Dynamics 365 Commerce 10.0.47 (January 2026)

[!include [banner](../includes/banner.md)]

This article lists features that are new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.47. This version has a build number of 10.0.2527.17 and is available on the following schedule:

- **Preview of release:** January 2026
- **General availability of release (self-update):** March 2026
- **General availability of release (auto-update):** April 2026

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that are added to the build after this article is originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
|E-commerce | Show QR code and payment link as a payment method using Adyen connector | Merchants using the Adyen connector can use a new module to display the Payment link and a corresponding quick response (QR) code in Dynamics 365 Commerce e-commerce. Customers can scan the QR code or select the payment link to see a list of available payment methods. Once the payment is completed, Adyen sends a payment notification to the Commerce Scale Unit (CSU). CSU triggers the automatic checkout of the cart and creates the order. If the payment notification is received but the order can't be created, the CSU logs this information in Commerce headquarters for monitoring. | Admins |
|B2B E-commerce | B2B multioutlet support using contacts | This feature enables a single authenticated business-to-business (B2B) buyer to seamlessly place orders on behalf of multiple outlets associated with their organization. Buyers can switch outlets within the same session, view outlet‑specific catalog entitlements and pricing, and complete purchases without needing separate sign-ins for each outlet. Additionally, this feature modernizes B2B user account management by shifting user access to Contacts instead of the legacy Customer (Person) account type. This provides cleaner administration and clearer governance for users who need to buy on behalf of multiple outlets. | Admins |
|Omnichannel | Purge commerce transactions | This feature is now Generally Available. Businesses that don't need to save the Commerce transactions for a long time can use this capability to purge older transactions and save storage associated costs. [Learn more](/dynamics365/commerce/purge-transactions) | Admins |
|Omnichannel | Archive commerce transactions | This feature is now Generally Available. Businesses that don't want to delete the transactions and rather archive them for any compliance or analytical needs, can use the Archive commerce transactions feature to archive commerce transactions. [Learn more](/dynamics365/commerce/archive-transactions) | Admins |
|Point of Sale | Cross legal entity inventory lookup on POS | This feature enables store clerks to view inventory across legal entities directly in point of sale (POS). Supports cross store, franchise, and cross border availability checks when local store is out of stock. CSU APIs now support multiorg inventory visibility powered by Inventory Visibility Service (IVS). Integration is configured by admins. | Admins |
|Point of Sale| Enable language selection at self-checkout | This feature adds multilanguage support to self-checkout, allowing shoppers to switch languages directly on the self-checkout welcome screen or via the **Change language** operation on the transaction screen. All UI labels, prompts, messages, and receipts update instantly based on the selected language, using the channel's configured language list. This capability delivers a more inclusive and intuitive self‑checkout experience for customers in multilingual environments. | Admins |
|Point of Sale| Localization support for POS button grids and tabs | This feature enables full localization of POS button grids and tabs directly within the layout designer, allowing users to enter translated text once when creating the screen layout. Store Commerce renders the appropriate localized labels at runtime based on the user’s preferred language, eliminating the need to duplicate screen layouts for each language and simplifying global deployment.| Admins |
|Point of Sale | Modernize POS journeys with React and Fluent UI | This feature modernizes product listing (search results), product detail, and transaction page views in Store Commerce POS by migrating these experiences to React and Fluent UI. The updated interface delivers a consistent, responsive design across desktop and mobile, introduces streamlined selling workflows, and surfaces proactive insights for inventory availability and discount opportunities to help associates serve customers more effectively.| Admins|

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.47. You can still disable these features in **Feature management**, if necessary.

| Module | Feature name | More information |
|--|--|--|
| Retail and commerce |Improved user experience for POS returns | This feature simplifies the return experience on Point of Sale. It introduces a multiselect grid where users can select and clear the selection of returnable products.[Learn more about the feature](/dynamics365/commerce/pos-returns#user-experience-enhancements)|

## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.47 includes platform updates. For more information, see [Platform updates for version 10.0.47 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-47.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.47, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1093817).

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2026 release wave 1 plan](/dynamics365/release-plan/2025wave2/). It captures all the details, end-to-end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before Microsoft removes any feature from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that you need to make to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
