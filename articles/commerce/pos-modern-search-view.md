---
title: Modernized search results view in Store Commerce
description: Learn about the modernized search results view in Store Commerce POS, including refreshed product tiles, inventory visibility, discount cues, and how to enable it.
author: anush6121
ms.author: anvenkat
ms.topic: article
ms.date: 04/13/2026
ms.reviewer: v-griffinc
ms.custom:
  - bap-template
---

# Modernized search results view in Store Commerce

[!include [banner](../includes/banner.md)]

**Applies to:** Dynamics 365 Commerce version 10.0.47 and later

The modernized search results view introduces a streamlined, React-based experience designed for efficient, insight-driven product discovery. Refreshed product tiles, larger imagery, and contextual discount and inventory cues help associates find the right product and explain pricing benefits — without leaving the search results.

This article describes the capabilities of the modernized search results view and how to enable them.

## Prerequisites

- Store Commerce app version 10.0.47 or later
- The following feature flag must be enabled in Commerce headquarters:
  - **Enable modernized search view results**

## Enable the modernized search results view

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration \> Workspaces \> Feature management**).
2. Search for **Enable modernized search view results** and select **Enable now**.
3. Enable any optional per-capability toggles described in the sections below.
4. Run the **Registers (1090)** distribution schedule job to push changes to channels.
5. Restart the Store Commerce app.

---

## Search results layout

*Available from version 10.0.47*

The search results page has been rebuilt on React with a refreshed card-based layout that reduces visual clutter and improves scan speed.

- **Refreshed product tiles** — a cleaner layout that improves scan speed and reduces visual clutter.
- **Larger imagery** — supports quicker visual recognition, helping associates verify products at a glance.
- **Compact/tile view toggle** — lets associates switch between showing more cards per row (compact) or larger, more detailed cards (tile).
- **Add to sale button on each card** — shortens the path to starting a transaction by eliminating extra taps.
- **Filter and sort at the top** — makes it easier to refine results without scrolling.

---

## Contextual discount visibility

*Available from version 10.0.47*

Quantity discount captions appear directly on search result cards when quantity-based discounts are available, allowing associates to proactively inform customers about potential savings.

To enable: In **POS visual profiles**, set **Show quantity discount captions** to **Yes**, then run the **Registers (1090)** job.

---

## Inventory visibility

*Available from version 10.0.47*

Store and nearby store availability is displayed directly on each product card, allowing associates to confirm stock without navigating to the product details page.

To enable: In **POS visual profiles**, set **Show stock count and availability across stores** to **Yes**, then run the **Registers (1090)** job.

---

## Version history

| Version | Enhancements |
|---|---|
| 10.0.47 | React-based search results layout, quantity discount captions, inventory visibility on cards |

---

## Additional resources

- [Modern workflows in Store Commerce POS](POS-UX-modernization.md)
- [Modernized product details page in Store Commerce](pos-modern-product-details.md)
- [Store Commerce extensibility overview](dev-itpro/pos-extension/pos-extension-overview.md)
