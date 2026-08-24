---
title: Preview features in Dynamics 365 Commerce 10.0.49 (July 2026)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.49. 
author: miraoms
ms.author: mirao
ms.reviewer: mirao
ms.date: 08/24/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.search.region: Global
ms.search.validFrom: 2026-08-01
ms.dyn365.ops.version: 10.0.49

---

# What's new or changed in Dynamics 365 Commerce 10.0.49 (July 2026)

This article lists features that are new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.49. This version has a build number of 10.0.2790 and is available on the following schedule:

- **Preview of release**: July 2026
- **General availability of release (self-update)**: September 2026
- **General availability of release (auto-update)**: October 2026

## Features included in this release

The following table lists the features that are included in this release. Microsoft might update this article to include features that are added to the build after this article is originally published.

| Feature area | Feature | More information | Enabled by |
| ------------ | ------- | ---------------- | ---------- |
| Point of sale | Expansion of the modernized customer details page in Store Commerce | Version 10.0.49 significantly expands the modernized Customer details page in Store Commerce, which was introduced in version 10.0.48. This release adds full address management - Associates can add, edit, set as primary, and remove shipping addresses directly from the **Account details** tab's **Shipping addresses** tile, with an in-place tile refresh and no full page reload. A functional **Timeline** tab lets associates view customer purchases and activities in a single chronological view and add or delete note activities. The **Account details** tab also offers a modern affiliations and wishlist management, loyalty card addition, and customer attribute editing, and a modern React-based view replaces the legacy affiliations experience. Customer creation and editing workflows now use the same React-based add and edit view consistent with the rest of the modernized experience. Starting in 10.0.49, administrators can turn Customer details page sections on or off and reorder them from Commerce headquarters using **POS visual profiles**, with no code required. You can show, hide, or reorder both whole sections and the individual items within composite sections. The extensibility surface also expands with app bar command support on the compact (phone) layout, an extension surface on the standalone address add and edit view, and safer extension-host lifecycle handling. All the capabilities are gated by the `StoreCommerce.EnableModernCustomerDetailsPage` feature flag introduced in 10.0.48. For more information, see [Modernized customer details page in Store Commerce (preview)](../pos-modern-customer-details.md). | Admins |
| Point of sale | Design A4 and thermal receipts in a modern designer | Commerce headquarters now embeds a new React-based receipt designer under **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Receipt formats** > **Designer**, replacing the legacy standalone desktop designer that required a separate installation and login. The new designer runs entirely in the browser with predefined templates, drag-and-drop element placement, inline line adding, a live preview pane, and the ability to save receipt formats end-to-end, including support for custom fields. A new structured receipt schema (Header, Footer, and Lines) is stored in Commerce headquarters, synchronized to the channel database, and consumed end-to-end by Commerce Scale Unit (ReceiptService V2), Store Commerce, and Hardware station. Hardware station is updated to support both A4 paper and thermal printer paths - OPOS, network printer, and Windows print paths all convert from the structured format to the platform-specific output, enabling B2B and trade-counter scenarios where invoices and order receipts must print on A4 paper directly from the point of sale. The feature is controlled by a feature flag; existing receipt formats, Hardware station extensions, and print integrations continue to work unchanged until a retailer chooses to opt in. For more information, see [Modern receipt designer in Commerce headquarters](../modern-receipt-designer.md). | Admins |
| Point of sale | Transaction line search in Store Commerce | Transaction line search lets associates filter the **Lines** tab on the transaction page by item name, item number, or SKU to quickly locate a specific line in large carts. This capability is especially useful in B2B and trade-counter scenarios where carts can have many lines. To enable transaction line search, open the screen layout in Screen Layout Designer in Commerce headquarters, select the transaction grid component, and select **Show transaction line search** on the **Lines** tab. Run the **Channel configuration (1090)** distribution schedule job after saving. For more information, see [Configure transaction line search](../pos-modern-transaction-grid.md#configure-transaction-line-search). | Admins |
| Point of sale | Multi-select cart line updates in Store Commerce | Multi-select cart line updates let associates select multiple transaction lines and apply supported bulk actions together in a single step. Supported bulk actions include void item, ship, pick up, carry out, line discount percentage, line discount amount, and line comment. Button grid operations for void and line discount also operate on all selected lines when multi-select is active. To enable multi-select, open the screen layout in Screen Layout Designer, select the transaction grid component, and select **Show transaction line multi-select** on the **Lines** tab. Run the **Channel configuration (1090)** distribution schedule job after saving. For more information, see [Configure multiselect cart line updates](../pos-modern-transaction-grid.md#configure-multiselect-cart-line-updates). | Admins |
| Point of sale | Bulk item add in Store Commerce | Bulk item add lets associates add many items to a transaction from a single entry panel by entering or pasting a list of item IDs and quantities. This capability is designed for B2B and trade-counter scenarios where associates receive a list of items to fulfill. To expose bulk item add, add the bulk item add operation to the appropriate button grid or action panel for the screen layout in Screen Layout Designer. For more information, see [Use bulk item add](../pos-modern-transaction-grid.md#use-bulk-item-add). | Admins |
| Point of sale | Quick Operations panel in Store Commerce | The **Quick Operations** panel surfaces frequently used transaction-level fields directly on the transaction page, so associates can complete common tasks without opening the button grid. Supported fields include total discount percentage, total discount amount, notes, and customer purchase order (PO) number. Each field uses the same runtime validation as the corresponding button grid operation. To configure the **Quick Operations** panel, add the **Quick Operations** control to the transaction page layout in Screen Layout Designer and select the operations to show. Run the **Channel configuration (1090)** distribution schedule job after saving. For more information, see [Configure the Quick Operations panel](../pos-modern-transaction-grid.md#configure-the-quick-operations-panel). | Admins |
| Point of sale | Button grid keyboard shortcuts in Store Commerce | Keyboard shortcuts let associates trigger **CartView** button grid operations by pressing a configured function key (F2, F3, F4, F6, F7, F8, F9, or F10) directly on the transaction page, without navigating menus. If a key maps to a single visible enabled button, Store Commerce runs that operation immediately. If a key maps to multiple buttons, a selector displays. To assign a keyboard shortcut, open the button grid in **Button Grid Designer** in Commerce headquarters, right-click the button, select **Button properties**, and set the **Keyboard shortcut** field. Run the **Channel configuration (1090)** distribution schedule job after saving. For more information, see [Configure keyboard shortcuts for button grids](../pos-modern-transaction-grid.md#configure-keyboard-shortcuts-for-button-grids). | Admins |
| Point of sale | Contextual switching of POS with external apps on iOS | Contextual switching in Store Commerce is now available on iOS, extending the capability introduced for Windows, Android, and browsers in version 10.0.48. External applications can pass product, customer, and transaction context directly into POS. This capability helps reduce friction by enabling external applications to pass product, customer, and transaction context directly into POS. For more information, see [Enable contextual switching of the Store Commerce app](../dev-itpro/store-commerce-contextual-switch.md). | |
| Payments | Print Commerce receipts on Adyen payment terminals | Stores that use supported Adyen handheld payment terminals with printing capabilities can now print receipts designed in Dynamics 365 Commerce directly from the terminal. This capability improves store associate mobility and productivity and can reduce the need for dedicated receipt printers. For more information, see [Dynamics 365 Payment Connector for Adyen overview](../dev-itpro/adyen-connector.md). | Admins |
| Point of sale | Mark orders as expedited and release them for fulfillment | Counter sales associates can mark an order as expedited, which automatically releases it to the warehouse for priority picking. This capability helps reduce customer wait times and improves counter sales efficiency. It's available only for stores that use a warehouse configured for advanced warehouse management. | Admins |
| Point of sale | Manage organization buyers as contacts in POS | Store associates can manage an organization's buyers as contacts and add the buyer to a POS transaction. Recording the specific buyer improves auditability for purchases and returns, especially when transactions use credit. To use this capability, admins must enable the modern customer details page feature. | Admins |
| Point of sale | Improve the order capture experience in POS | Store associates can add notes to capture important details from customer interactions, default the current store as the pickup location, and override deposit within the payment capture flow. These improvements reduce the number of steps required to capture an order and provide capabilities that previously needed customization. | Admins |
| Payments | Compress payment tokens independent of transaction archiving | Administrators can compress stored payment-token data independent of the **Archive credit card transaction data** batch job. This capability helps reduce storage usage which can improve performance and reduce storage costs. Enable the feature in the **Feature management** workspace. For more information, see [Further storage management with token compression](../dev-itpro/archive-cc-data.md#further-storage-management-with-token-compression). | Admins |
| E-commerce | E-commerce platform modernization | Dynamics 365 Commerce continues to modernize its E-commerce platform with updated support for Node.js 22, the recommended Node.js 24 runtime, and TypeScript 4.2.4. These enhancements provide a more secure, performant, and future-ready development environment for building and extending Commerce experiences. For more information, see [E-commerce platform modernization](../e-commerce-extensibility/ecommerce-platform-modernization.md). | Admins, Developers |
| E-commerce | On-behalf-of (OBO) support in Microsoft Entra External ID | B2B E-commerce now provides comprehensive setup guidance for on-behalf-of (OBO) authentication with Microsoft Entra External ID. The feature enables secure account manager sign-in, customer impersonation permissions, identity provider integration, and streamlined B2B customer-management experiences. This feature is backported and available from release 10.90.46 onwards. For more information, see [Create and configure a Microsoft Entra application for account manager sign-in](../dev-itpro/obo-create-aad-application.md?tabs=eeid). | Admins, Developers |
| B2B E-commerce | B2B multi-outlet | Commerce version 10.0.49 expands B2B multioutlet ordering with configurable roles and permissions, enhanced storefront user management, cross-channel invoice access for administrators, invoice delivery to additional email addresses, and improved on-behalf-of (OBO) experiences with Microsoft Entra. Together with capabilities introduced in earlier releases, one contact can use a single sign-in to switch between multiple outlets while Commerce applies the selected organization's pricing, catalogs, inventory, credit limits, and fulfillment rules. Contact-aware order history, templates, invoices, wishlists, distributor scenarios, and OBO ordering provide a consistent experience across storefront and assisted-sales channels. For more information, see [B2B multioutlet capabilities (preview)](../b2b/b2b-multi-outlet.md). | Admins |

## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.49 includes platform updates. For more information, see [Platform updates for version 10.0.49 of finance and operations apps (July 2026)](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-49.md).
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.49, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1156136).

### Dynamics 365: 2026 release wave 1 plan

Want to know about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). It captures all the details, end-to-end, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before Microsoft removes any feature from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that you need to make to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
