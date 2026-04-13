---
title: Modernized transaction grid in Store Commerce
description: Learn about the modernized transaction grid in Store Commerce POS, including inline line actions, contextual discount visibility, loyalty prompts, and notifications.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 04/13/2026
ms.reviewer: v-griffinc
ms.custom:
  - bap-template
---

# Modernized transaction grid in Store Commerce

[!include [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.42 and later

The modernized transaction grid replaces the legacy cart view on the Store Commerce transaction page with a React-based, Fluent UI experience. The grid introduces inline cart line interactions, contextual discount visibility, a loyalty upsell prompt, and an extensible notification framework — all without requiring associates to navigate away from the transaction.

This article describes the capabilities of the modernized transaction grid and how to enable them.

## Prerequisites

- Store Commerce app version 10.0.42 or later
- The following feature flag must be enabled in Commerce headquarters:
  - **Enable Modern Transaction Grid in POS Transaction View**

> [!NOTE]
> Individual capabilities within the transaction grid have their own minimum versions, noted in each section below.

## Enable the modernized transaction grid

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration \> Workspaces \> Feature management**).
2. Search for **Enable Modern Transaction Grid in POS Transaction View** and select **Enable now**.
3. Go to **POS visual profiles** (**Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> POS visual profiles**).
4. For each visual profile, set **Modern transaction grid** to **Yes**.
5. Enable any optional per-capability toggles described in the sections below.
6. Run the **Registers (1090)** distribution schedule job to push changes to channels.
7. Restart the Store Commerce app.

> [!TIP]
> The **Modern transaction grid** toggle in POS visual profiles lets you roll out the change to specific registers before enabling it broadly.

---

## Cart line interactions

### Inline line actions


Common cart line operations are available as inline actions directly on each cart line, removing the need for nested button navigation. Available actions include void product, return item, line discount, price override, coupon, line comment, and change unit of measure. The display order of inline actions is ranked automatically by frequency of use per register.

- **Desktop:** Hover over a line and select the ellipsis (**…**) to open the inline actions list.
- **Mobile/touch:** Long-press a line to open the inline actions list.

To expose a broader set of line operations, enable **Enable advanced inline actions** in the **Feature management** workspace.

### Inline quantity update


Associates can update the quantity of a cart line by selecting or tapping the quantity value directly within the grid — no nested buttons or dialogs required.

### Product images on cart lines


Product images are displayed on each cart line, helping associates visually confirm items at a glance. Ensure product images are correctly configured in headquarters before enabling this capability. Learn more in [Set up and manage images for Store Commerce](set-up-manage-images-retail-mpos.md).

To enable product images on the transaction grid:

1. In **Feature management**, search for **Enable product images on modern transaction grid** and select **Enable now**.
2. Run the **Registers (1090)** job.

---

## Contextual discount visibility

### Quantity discount captions


An inline caption appears on a cart line when a quantity-based discount is available, giving associates a natural prompt to inform customers about potential savings.

To enable: In **POS visual profiles**, set **Show inline quantity discount messages** to **Yes**, then run the **Registers (1090)** job.

### Threshold discount bar


A discount bar appears above the cart when the cart total is approaching a threshold-based discount tier, giving associates a clear cue to encourage customers to add more items.

To enable: In **POS visual profiles**, set **Show threshold discount bar** to **Yes**, then run the **Registers (1090)** job.

---

## Cart suggestions


The cart suggestions panel displays AI-curated product recommendation cards with add-to-sale actions directly from the transaction page. Cards use a modernized Fluent UI layout with larger imagery. Default recommendations are curated by headquarters users.

The suggestions component is extensible — partners and ISVs can provide custom recommendation logic by extending the suggestions panel.

To enable: In **POS visual profiles**, set **Show product suggestions** to **Yes**, then run the **Registers (1090)** job.

---

## Loyalty upsell prompt


When a customer is attached to the transaction, the loyalty upsell prompt surfaces how close the customer is to their next loyalty tier — giving associates a data-backed moment to encourage additional purchases.

Learn more in [Loyalty upsell prompt feature in POS](loyalty-upsell-prompt.md).

---

## Notifications


The toast notification framework delivers real-time, non-blocking alerts on the transaction page. Built-in scenarios include policy updates for associates, low-stock item alerts, and kiosk assistance requests.

The framework is fully extensible — partners and ISVs can implement custom notification types by extending the toast notification model.

Learn more in [Offline reliability toast notifications in the Store Commerce app](dev-itpro/retail-sdk/offline-reliability-toast-notifications.md).

---

## Transaction page workflow improvements

### Streamlined add-to-cart workflow


Two workflows are available when an associate adds a product to the cart from the product details page or search results:

- **Confirmation dialog (default):** A dialog confirms the item was added and returns the associate to the browse experience. Suited to assisted-selling scenarios where associates add multiple items before processing.
- **Go directly to transaction:** The associate is taken immediately to the transaction page after adding an item, with no confirmation dialog. Suited to single-item transaction scenarios.

To configure: In **POS visual profiles**, under **General \> Product details page**, set **Bypass Item added dialog** to **Yes** (go directly to transaction) or **No** (show confirmation dialog). Run the **Registers (1090)** job after each change.

### Reset button grids at end of transaction


When a transaction is completed, suspended, or voided, the default button grid assigned to the first tab is automatically restored. This reduces the number of clicks required when associates handle consecutive transactions.

---

## Version history

| Version | Enhancements |
|---|---|
| 10.0.47 | Quantity discount captions, threshold discount bar, refreshed and extensible cart suggestions |
| 10.0.44 | Inline line actions, inline quantity update, loyalty upsell prompt |
| 10.0.43 | Toast notification framework |
| 10.0.42 | Product images on cart lines |
| 10.0.40 | Streamlined add-to-cart workflow, reset button grids, payment capture improvements ([learn more](dev-itpro/faster-checkout-pos.md)) |
| 10.0.39 | Enhanced date picker, persist zoom level |

---

## Additional resources

- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Loyalty upsell prompt feature in POS](loyalty-upsell-prompt.md)
- [Offline reliability toast notifications in the Store Commerce app](dev-itpro/retail-sdk/offline-reliability-toast-notifications.md)
- [Check out faster with optimized payment flows](dev-itpro/faster-checkout-pos.md)
- [Set up and manage images for Store Commerce](set-up-manage-images-retail-mpos.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
