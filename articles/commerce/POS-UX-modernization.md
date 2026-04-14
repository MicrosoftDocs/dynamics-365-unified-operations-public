---
title: Modern workflows in POS
description: This article provides an overview of the modernized views in Microsoft Dynamics 365 Commerce Store Commerce POS, with links to enable and configure each view.
author: anush6121
ms.author: anvenkat
ms.topic: overview
ms.date: 04/13/2026
ms.reviewer: v-griffinc
ms.custom:
  - bap-template
---

# Modern workflows in Store Commerce POS

[!include [banner](../includes/banner.md)]

This article provides an overview of the modernized views in Microsoft Dynamics 365 Commerce Store Commerce. Use the links in this article to learn how to enable each view and explore what's available in each release.

Store Commerce POS features are continuously enhanced with modern, mobile-optimized experiences built on a React-based foundation and Fluent UI. These enhancements bring a more consistent, faster, and accessible interface across devices — helping associates find products faster, understand product details more clearly, and surface contextual insights at the right moment.

The React framework enables mobile-optimized workflows, simplifies extensibility, and meets accessibility requirements across browsers and all Store Commerce applications. Fluent Design complements the React framework by providing visual clarity and consistency.

## Modernized views

| Modernized view | First available | Latest enhancements | Status |
|---|---|---|---|
| [Transaction grid](pos-modern-transaction-grid.md) | 10.0.39 | 10.0.47 | Generally available |
| [Search results view](pos-modern-search-view.md) | 10.0.47 | 10.0.47 | Generally available |
| [Product details page](pos-modern-product-details.md) | 10.0.47 | 10.0.47 | Generally available |
| [Customer details page](pos-modern-customer-details.md) | 10.0.48 | 10.0.48 | Preview |
| [Customer create and edit workflows](pos-modern-customer-create-edit.md) | 10.0.48 | 10.0.48 | Preview |

## Modern transaction grid

The modernized transaction grid brings a cleaner, more intuitive cart that surfaces discount opportunities inline. Associates can edit cart lines quickly, see how close a cart is to a threshold discount tier, and take action without navigating away from the transaction. The transaction grid has been continuously enhanced since its introduction in version 10.0.39, with enhancements spanning inline line actions, loyalty upsell prompts, product images, and toast notifications.

[Learn more about the modern transaction grid](pos-modern-transaction-grid.md)

## Modern search results view

The modernized search results view introduces a streamlined, React-based experience for efficient, insight-driven product discovery. Refreshed product tiles, larger imagery, and contextual discount and inventory cues help associates find the right product faster — and explain pricing benefits without leaving the search results.

[Learn more about the modern search results view](pos-modern-search-view.md)

## Modern product details page

The modernized product details page is a mobile-first, vertical layout rebuilt on React that consolidates every detail and action into one focused view. Associates can select dimensions, check inventory in nearby stores, view related products with add-to-sale actions, and complete the transaction without switching screens.

[Learn more about the modern product details page](pos-modern-product-details.md)

## Modern customer details page

The modernized customer details page replaces the legacy customer details view with a React-based, responsive experience organized into four content tabs: Account summary, Timeline, Account details, and Transactions. The page surfaces Copilot customer insights and recommended products within the Account summary tab, and introduces a richer extensibility model for partners and ISVs.

[Learn more about the modern customer details page](pos-modern-customer-details.md)

## Modern customer create and edit workflows

The modernized customer create and edit workflows rebuild the legacy add/edit view on React and Fluent UI. The address section is now part of the create form — associates complete customer information and address entry in a single save. Optional mandatory address validation is available as a CSU flight, ensuring customer records always have an associated address at the time of creation.

[Learn more about the modern customer create and edit workflows](pos-modern-customer-create-edit.md)

## Additional resources

- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
- [Store Commerce app overview](dev-itpro/store-commerce.md)
- [Copilot in Dynamics 365 Commerce overview](copilot-overview.md)
