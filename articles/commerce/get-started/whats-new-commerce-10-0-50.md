---
title: What's new or changed in Dynamics 365 Commerce 10.0.50 (October 2026)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.50. 
author: miraoms
ms.author: mirao
ms.reviewer: mirao
ms.date: 11/15/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ai-usage: ai-assisted
ms.custom: 
  - bap-template
  - evergreen
ms.search.region: Global
ms.search.validFrom: 2026-08-01
ms.dyn365.ops.version: 10.0.50

---

# What's new or changed in Dynamics 365 Commerce 10.0.50 (October 2026)

> [!IMPORTANT]
> Release plans won't be published starting in September 2026. New Dynamics 365, Power Platform, and Dataverse capabilities will be published to the AI at Work roadmap beginning in September 2026. Existing release plans remain available for historical reference until further notice. For more information, see [Dynamics 365 and Power Platform: Release Plans retirement](/dynamics365/release-plans/).

This article lists features that are new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.50. This version has a build number of 10.0.2919 and is available on the following schedule:

- **Preview of release**: October 2026
- **General availability of release (self-update)**: December 2026
- **General availability of release (auto-update)**: January and February, 2027

## Features included in this release

The following table lists the features that are included in this release. Microsoft might update this article to include features that are added to the build after this article is originally published.

| Feature area | Feature | More information | Enabled by |
| ------------ | ------- | ---------------- | ---------- |
| Point of sale | Find and add products or customers from **Quick Add** | Associates can enter a full or partial value in the transaction numpad to open a native **Quick Add** pane. The pane provides separate **Products** and **Customers** tabs so associates can find and add products, identify variants and serial-numbered items, or attach a customer without leaving the transaction page. Quick Add is available by default in Commerce version 10.0.50. For more information about the modern transaction experience, see [Modernized transaction grid in Store Commerce](../pos-modern-transaction-grid.md). | Enabled by default |
| Point of sale | Configure sales order attributes in **Quick Operations** | Transaction (sales order header) attributes configured in Commerce headquarters are available in the **Attributes** panel for the **Quick Operations** control, alongside the built-in transaction fields. Associates can view and edit the selected attributes directly on the transaction page instead of opening the transaction attributes dialog. Configure the control and its fields in Screen Layout Designer. For more information, see [Modernized transaction grid in Store Commerce](../pos-modern-transaction-grid.md). | Admins |
| Point of sale | Filter transaction lines by errors or warnings | The modern transaction grid can filter the current transaction to show all lines, lines with errors, or lines with warnings. Each option includes a line count, which helps associates focus on exceptions without changing cart contents, totals, validation, or available actions. Turn on **Show transaction line filter** in the screen layout configuration. For more information, see [Modernized transaction grid in Store Commerce](../pos-modern-transaction-grid.md). | Admins |
| Point of sale extensibility | Extend compact Store Commerce layouts | Extensions can add custom commands to the mobile cart app bar and its overflow menu. The modernized customer details page also reserves space for extension content in compact layouts. These additions make partner workflows available on mobile devices without requiring a separate application surface. For more information, see [Cart view handlers and commands](../dev-itpro/cart-view-handlers.md) and [Modernized customer details page in Store Commerce](../pos-modern-customer-details.md). | Developers |
| Point of sale | Configure additional sales-line information in full layouts | Full desktop layouts can show configured subfields beneath a sales line, matching the established Compact layout pattern. Administrators can select and order built-in or extension fields under **Additional information** independently of the primary receipt-panel columns, which reduces layout clutter while keeping relevant line details visible. For more information, see [POS user interface visual configurations](../pos-screen-layouts.md). | Admins |
| Point of sale | Print product and shelf labels in Store Commerce (preview) | Store associates can print product and shelf labels on demand by scanning or searching for products, or from label print requests created and released by Commerce headquarters. Associates can review request lines, adjust label types and copy counts, and print to a configured label printer. Administrators configure label formats and printers in Commerce headquarters. For more information, see [Label printing in Store Commerce (preview)](../label-printing.md). | Admins |
| Point of sale | Edit call center orders in POS when omni-channel order payments is enabled | You can now edit call center orders in POS even when **omni-channel order payments** is turned on. This removes a key blocker for merchants that need modern payment enhancements and still need in-store order editing workflows, including partially invoiced order scenarios. | Admins |
| Point of sale | Improve pickup workflows for multiple orders and additional in-store items | Store associates can complete pickup tasks more efficiently across one or more orders for the same customer, with improved pick and scan flows and pickup controls. For checkout-based pickup scenarios, associates can also add carry-out items during the pickup transaction, which helps reduce split-payment friction for in-store customers. | Admins |
| Point of sale | Pin and resume suspended transactions in POS | Store associates can pin suspended transactions and quickly resume them from a POS-local list. This update helps cashiers manage interrupted checkouts and return to in-progress transactions faster without changing the existing suspended-cart storage model. | Admins |
| Point of sale | Print finance and operations-based invoices from POS on A4 paper | POS now supports printing finance and operations backed **invoices** on A4 paper for B2B and distributor scenarios. It helps stores standardize invoice print handling at pickup and fulfillment touchpoints. | Admins |
| Self-checkout | Assign a functionality profile to a self-checkout register | Each self-checkout (SCO) register can inherit the store functionality profile or use a selected SCO-specific profile. The register-level profile can isolate checkout-specific device settings, transaction reason codes, receipt numbering, and fiscal settings without changing staffed registers. For more information, see [Enable self-checkout in the Store Commerce app](../store-commerce-self-check-out.md). | Admins |
| Receipt designer | Author tables and rich text in modern receipts | The modern receipt designer supports fixed-row and data-driven repeating tables, borders, alignment, font family, 11–96-pixel font sizes, font weight, italic, underline, and strikethrough. The structured content is supported in POS previews and modern email receipts. For physical printing, tables and document typography require the Windows printer path through Windows Hardware Station. OPOS, Epson, Star, and Adyen printer paths don't support these layouts. You first have to deploy aligned Commerce headquarters, Commerce Scale Unit, Store Commerce, proxy, and Hardware Station components before using these capabilities. For more information, see [Modern receipt designer in Commerce headquarters](../modern-receipt-designer.md). | Feature management |
| Payments | Preserve original transaction references when returning items from exchange scenarios | Return flows for transactions that include exchanges now retain and reference original transaction details more reliably. This change improves payment-method handling and helps avoid return completion issues in zero-sum and exchange-linked return scenarios. | Admins |
| Payments | Enable **Tap to Pay** on Android by using the Adyen companion app | Store Commerce on Android can use Adyen Tap to Pay so compatible NFC-capable devices can accept tap card payments without separate payment hardware. This support expands mobile checkout options on commodity and ruggedized Android devices. | Admins |

## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.50 includes platform updates. For information about the release schedule and service update process, see [Service update availability](../../fin-ops-core/dev-itpro/get-started/public-preview-releases.md).
  
### Bug fixes

For information about the bug fixes included in each update that's part of version 10.0.50, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1156136).

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before Microsoft removes any feature from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that you need to make to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
