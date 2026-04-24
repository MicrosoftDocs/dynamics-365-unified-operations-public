---
title: Simulate whether purchase order changes have impact (production ready preview)
description: Simulate purchase order changes and review their impact in real time. Take control of your procurement process and make data-driven decisions with confidence.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/24/2026
ms.custom:
  - bap-template
---

# Simulate whether purchase order changes have impact (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The impact simulation capability allows purchasers and planners to test the impact of changes not directly or explicitly communicated through e-mails via configured channels. This could be proactively testing potential changes to critical or at-risk purchase orders, seeing if changes received through external channels have an impact, or evaluating if supplier follow-up proposals to increase quantities or deliver earlier solves the impact.

## How to use impact simulation

1. From the **Procurement and sourcing** > **All Purchase Orders** page, select a purchase order. 
2. In the **Purchase Order** menu item in the top navigation pane, click **Simulate purchase order changes** in the **Impact simulation** section.
3. Either
    - Select a new **Confirmed receipt date** on the purchase order header to change the date for all purchase order lines.
    - Select a new **Confirmed receipt date** on a specific purchase order line.
    - Select a new **Confirmed receipt date** and/or quantity on a specific purchase order line.
4. Select **Simulate impact**.
5. The result will show the same as described in [Review impact of purchase order changes from vendors](procurement-agent-impact-analysis-review-changes.md).

> [!IMPORTANT]
> Impact simulations do **not** change the actual purchase order or affect planning calculations. Simulations use the current planning data at the time of simulation and are for analysis only.
