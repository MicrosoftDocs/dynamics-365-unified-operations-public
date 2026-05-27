---
title: Modernized transaction grid in Store Commerce
description: Learn about the modernized transaction grid in Store Commerce POS, including inline line actions, contextual discount visibility, loyalty prompts, and notifications.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 05/13/2026
ms.reviewer: mirao
ms.custom:
  - bap-template
---

# Modernized transaction grid in Store Commerce

[!include [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.42 and later

The modernized transaction grid replaces the legacy cart view on the Store Commerce transaction page with a React-based, Fluent UI experience. The grid introduces inline cart line interactions, contextual discount visibility, a loyalty upsell prompt, and an extensible notification framework - all without requiring associates to navigate away from the transaction.

This article describes the capabilities of the modernized transaction grid and how to enable them.

## Prerequisites

- Store Commerce app version 10.0.42 or later
- Enable the following feature flag in Commerce headquarters: **Enable Modern Transaction Grid in POS Transaction View**

> [!NOTE]
> Individual capabilities within the transaction grid have their own minimum versions, noted in each of the following sections.

## Enable the modernized transaction grid

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration** > **Workspaces** > **Feature management**).
1. Search for **Enable Modern Transaction Grid in POS Transaction View** and select **Enable now**.
1. Go to **POS visual profiles** (**Retail and Commerce** > **Channel setup** > **POS setup** > **POS profiles** > **POS visual profiles**).
1. For each visual profile, set the **Modern transaction grid** value to **Yes**.
1. Enable any optional per-capability toggles described in later sections.
1. Run the **Registers (1090)** distribution schedule job to push changes to channels.
1. Restart the Store Commerce app.

> [!TIP]
> The **Modern transaction grid** toggle in POS visual profiles lets you roll out the change to specific registers before enabling it broadly.

## Cart line interactions

### Inline line actions

You can perform common cart line operations as inline actions directly on each cart line, so you don't need nested button navigation. Available actions include void product, return item, line discount, price override, coupon, line comment, and change unit of measure.

- **Desktop**: Hover over a line and select the ellipsis (…) to open the inline actions list.
- **Mobile/touch**: Long-press a line to open the inline actions list.

To expose a broader set of line operations, enable **Enable advanced inline actions** in the **Feature management** workspace.

#### Configure inline actions per screen layout

Retailers and implementation partners can configure which operations appear as inline actions, their display order, and custom operations per screen layout by using the screen layout designer in headquarters.

Here's what you can configure:

- **Which actions appear**: Select any eligible out-of-the-box POS operation or custom operation registered in headquarters to include as an inline action on transaction line item.
- **Display order**: Control the sequence in which inline actions appear so the most relevant operations for a given store format or associate role surface first.
- **Custom operations**: Add operations built through the POS extension framework as inline actions alongside out-of-the-box operations, giving retailers a unified configuration surface for both standard and customized workflows.

By default, no configuration is required to preserve the current experience. If you don't configure any inline actions for a screen layout, Store Commerce continues to display the existing default set of inline operations for that layout. After you configure inline actions for a specific layout, the configured list replaces the defaults for that layout only. Other layouts remain unaffected.

To configure inline actions, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Screen layouts**.
1. Open the screen layout to configure and launch **Screen layout designer**.
1. Select the transaction grid component and open the inline actions configuration.
1. Add operations from the available list, remove operations that aren't needed, and set the display order.
1. Save the layout and run the **Channel configuration (1090)** distribution schedule job to push changes to stores.

Changes take effect in Store Commerce after the updated layout is downloaded at the register.

#### Localization

The system automatically localizes out-of-the-box operation names by using existing POS resource strings, so you don't need to provide extra configuration. For custom operations, display names fall back to the operation name configured in headquarters. To provide localized display names for custom operations, use resource files and operation mappings in your extension code.

#### Security and permissions

Inline actions respect the same POS security roles and permission model as button grid operations. Use role-based access controls to restrict sensitive operations (such as price override or void) line to managers, while presenting a simplified action set to cashiers.

### Inline quantity updates

Associates can update the quantity of a cart line by selecting or tapping the quantity value directly within the grid. This feature doesn't require any nested buttons or dialogs.

### Product images on cart lines

Product images display on each cart line, helping associates visually confirm items at a glance. Make sure you correctly configure product images in headquarters before enabling this capability. For more information, see [Set up and manage images for Store Commerce](set-up-manage-images-retail-mpos.md).

To enable product images on the transaction grid:

1. In **Feature management**, search for **Enable product images on modern transaction grid** and select **Enable now**.
2. Run the **Registers (1090)** job.

## Contextual discount visibility

### Quantity discount captions

An inline caption appears on a cart line when a quantity-based discount is available, giving associates a natural prompt to inform customers about potential savings.

To enable this feature:

1. In **POS visual profiles**, set **Show inline quantity discount messages** to **Yes**.
2. Run the **Registers (1090)** job.

### Threshold discount bar

A discount bar appears above the cart when the cart total approaches a threshold-based discount tier, giving associates a clear cue to encourage customers to add more items.

To enable this feature:

1. In **POS visual profiles**, set **Show threshold discount bar** to **Yes**.
2. Run the **Registers (1090)** job.

## Cart suggestions

The cart suggestions panel provides a modernized layout for displaying product recommendation cards with add-to-sale actions directly from the transaction page. Headquarters users curate the default recommendations. The component exposes an extensibility API that allows partners and ISVs to supply their own recommendation logic, including AI-curated suggestions.

To enable this feature:

1. In **POS visual profiles**, set **Show product suggestions** to **Yes**.
2. Run the **Registers (1090)** job.

## Loyalty upsell prompt

When a customer is attached to the transaction, the loyalty upsell prompt surfaces how close the customer is to their next loyalty tier. This feature gives associates a data-backed moment to encourage more purchases.

For more information, see [Loyalty upsell prompt feature in POS](loyalty-upsell-prompt.md).

## Notifications

The toast notification framework delivers real-time, nonblocking alerts on the transaction page. Built-in scenarios include policy updates for associates, low-stock item alerts, and kiosk assistance requests.

The framework is fully extensible. Partners and ISVs can implement custom notification types by extending the toast notification model.

For more information, see [Offline reliability toast notifications in the Store Commerce app](dev-itpro/retail-sdk/offline-reliability-toast-notifications.md).

## Transaction page workflow improvements

### Streamlined add-to-cart workflow

When an associate adds a product to the cart from the product details page or search results, the following two workflows are available:

- **Confirmation dialog (default)**: A dialog confirms the item was added and returns the associate to the browser experience. This behavior is suited for assisted-selling scenarios where associates add multiple items before processing.
- **Go directly to transaction**: The associate is taken immediately to the transaction page after adding an item, with no confirmation dialog. This behavior is suited for single-item transaction scenarios.

To configure this feature:

1. In **POS visual profiles**, under **General** > **Product details page**, set **Bypass Item added dialog** to **Yes** (go directly to transaction) or **No** (show confirmation dialog).
2. Run the **Registers (1090)** job after each change.

### Reset button grids at end of transaction

When a transaction is completed, suspended, or voided, the default button grid assigned to the first tab automatically restores. This behavior reduces the number of clicks required when associates handle consecutive transactions.

## Version history

| Version | Enhancements |
| ------- | ------------ |
| 10.0.48 | Inline actions extensibility: Configure operations, display order, and custom operations per screen layout |
| 10.0.47 | Quantity discount captions, threshold discount bar, refreshed and extensible cart suggestions |
| 10.0.44 | Inline line actions, inline quantity update, loyalty upsell prompt |
| 10.0.43 | Toast notification framework |
| 10.0.42 | Product images on cart lines |
| 10.0.40 | Streamlined add-to-cart workflow, reset button grids, payment capture improvements. For more information, see [Check out faster with optimized payment flows](dev-itpro/faster-checkout-pos.md). |
| 10.0.39 | Enhanced date picker, persist zoom level |

## More resources

- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Loyalty upsell prompt feature in POS](loyalty-upsell-prompt.md)
- [Offline reliability toast notifications in the Store Commerce app](dev-itpro/retail-sdk/offline-reliability-toast-notifications.md)
- [Check out faster with optimized payment flows](dev-itpro/faster-checkout-pos.md)
- [Set up and manage images for Store Commerce](set-up-manage-images-retail-mpos.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
