---
title: Modernized product details page in Store Commerce
description: Learn about the modernized product details page in Store Commerce POS, including the mobile-first layout, inventory preview, related products, and how to enable it.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 04/13/2026
ms.reviewer: v-griffinc
ms.custom:
  - bap-template
---

# Modernized product details page in Store Commerce

[!include [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.47 and later

The modernized product details page is a mobile-first, vertical layout rebuilt on React that consolidates every product detail and action into one focused view. Associates can select dimensions, check inventory in nearby stores, view related products with add-to-sale actions, and add items to the cart — all without switching screens.

This article describes the capabilities of the modernized product details page and how to enable them.

## Prerequisites

- Store Commerce app version 10.0.47 or later
- The following feature flag must be enabled in Commerce headquarters:
  - **Enable modernized product details page**

## Enable the modernized product details page

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration \> Workspaces \> Feature management**).
2. Search for **Enable modernized product details page** and select **Enable now**.
3. Enable any optional per-capability toggles described in the sections below.
4. Run the **Registers (1090)** distribution schedule job to push changes to channels.
5. Restart the Store Commerce app.

---

## Page layout


The product details page uses a sticky vertical layout that keeps primary product information and key actions visible at all times while associates scroll through details.

- **Sticky layout** — keeps primary info and actions visible while scrolling.
- **Always-visible key actions** — keeps **Add to sale** and other primary actions within reach at all times.
- **Accordion sections** — organizes long product details into collapsible sections for faster scanning.

---

## Product imagery


The improved image gallery provides clearer product visuals and faster recognition with better swipe interactions, helping associates confirm products for customers more confidently.

---

## Dimension and quantity selection


Dimension controls (size, color, style) and quantity entry are presented inline on the page, streamlining variant and quantity selection for quicker, error-free entry.

---

## Related products carousel


A related products carousel is displayed on the product details page, enabling quick cross-sell opportunities. Each card in the carousel includes an **Add to sale** button so associates can add related items to the cart without navigating away.

---

## Inventory preview


Associates can check real-time availability for the current store and nearby stores directly from the product details page. The inventory preview opens in a side drawer and supports choosing pickup or ship-from-store options.

To enable: In **POS visual profiles**, set **Show nearby store inventory** to **Yes**, then run the **Registers (1090)** job.

---

## Contextual discount visibility


A quantity discount indicator is displayed on the product details page when quantity-based discounts are available for the product, helping associates explain pricing benefits to customers.

To enable: In **POS visual profiles**, set **Show quantity discount on modern PDP** to **Yes**, then run the **Registers (1090)** job.

---

## Version history

| Version | Enhancements |
|---|---|
| 10.0.47 | React-based mobile-first layout, improved image gallery, dimension and quantity controls, related products carousel, inventory preview, quantity discount indicator |

---

## Additional resources

- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Modernized search results view in Store Commerce](pos-modern-search-view.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
