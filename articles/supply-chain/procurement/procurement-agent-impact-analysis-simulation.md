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

The impact simulation capability enables purchasers and planners to test the impact of changes that aren't directly or explicitly communicated through emails or the vendor collaboration interface. This functionality is useful when proactively testing potential changes to critical or at-risk purchase orders, seeing whether changes received through external channels have an impact, or evaluating whether supplier follow-up proposals to increase quantities or deliver earlier solves the impact.

To run an impact simulation, follow these steps:

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All Purchase orders** and select a purchase order.
2. On the Action Pane, open the **Purchase Order** tab and, from the **Impact simulation** group, select **Simulate purchase order changes**.
1. Modify the purchase order details for the simulation by completing any or all of the following steps:
    - In the **Purchase order heading** section, select a new **Confirmed receipt date** to change the date for all purchase order lines.
    - In the **Purchase order lines** section, select a new **Confirmed receipt date** to change the date for one or more specific purchase order lines.
    - In the **Purchase order lines** section, select a new **Quantity** to change the quantity for one or more specific purchase order lines.
1. Select **Simulate impact**.
1. The result is displayed as described in [Review impact of purchase order changes from vendors](procurement-agent-impact-analysis-review-changes.md).

> [!IMPORTANT]
> Impact simulations *don't* change the actual purchase order or affect planning calculations. Simulations use the current planning data at the time of simulation and are for analysis only.
