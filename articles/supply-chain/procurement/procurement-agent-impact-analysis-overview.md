---
title: Impact analysis overview (production-ready preview)
description: Impact analysis streamlines how purchasing teams evaluate supplier change requests, ensuring fast decisions and uninterrupted supply chain operations.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 04/24/2026
ms.custom:
  - bap-template
---

# Impact analysis overview (production-ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Procurement Agent in Dynamics 365 Supply Chain Management works with procurement teams to manage supplier changes that affect purchase orders and supply commitments. Impact analysis evaluates whether and how supplier changes affect inventory levels, production schedules, and customer deliveries. It helps teams react faster and with higher confidence by clearly indicating when purchase order changes proposed by suppliers have downstream impact.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

Instead of spending a lot of time manually tracing pegging, reservations, or planning dependencies across the system for each change communicated by suppliers, teams can quickly determine which changes they can safely accept and which require further action. This process helps prioritize time spent on changes with impact, ultimately protecting service levels and production continuity.

When a supplier proposes a change to a purchase order through a configured source, or when it's manually initiated, impact analysis looks for downstream impact on sales orders, production orders, transfer orders, and inventory levels. It does this by tracing the changed supply across the system to identify orders that are linked to the purchase order through markings and peggings (if available), and checking this tracing against confirmed incoming supply and projected on-hand inventory.

## Review the impact of purchase order changes from vendors

Purchasing teams regularly receive change requests from suppliers, including delivery delays, quantity reductions, and cancellations. Each change to a purchase order can potentially affect safety stock, production schedules, internal transfers, and customer commitments. In most cases, purchasers don't want to spend time on changes to purchase orders with no downstream impact. Impact analysis gives purchasers the confidence, visibility, and ability to quickly identify those changes that can be safely accepted, apply them right away, and move on.

For changes with downstream impact on orders, or changes that cause inventory levels to go below certain thresholds, purchasers need to quickly understand the details and consequences, and decide how to respond. Purchasers often follow up with a supplier to request alternatives, such as expediting production or transportation, resulting in an earlier delivery date, increased quantity delivered, or a split delivery, while also looking for other alternatives such as alternative vendors.

If purchasers must accept a change with impact, they now know straight away which internal stakeholders to inform.

Impact analysis automatically analyzes the downstream impact of changes that arrive through emails (if you're using the supplier communication feature of the Procurement Agent) and through the vendor collaboration interface of Supply Chain Management.

Learn more in [Review impact of purchase order changes from vendors](procurement-agent-impact-analysis-review-changes.md).

## Simulate whether purchase order changes have impact

The impact simulation capability allows purchasers and planners to test the impact of proposed changes that aren't directly communicated through emails or the vendor collaboration interface. Some key use cases for this simulation include:

- Testing and getting a feel for the impact analysis feature before using it on live supplier change requests.
- Proactively testing potential scenarios for at-risk or high-priority purchase orders. This scenario could be purchase orders for which you didn't receive a reply yet.
- Evaluating whether supplier proposals for expediting or setting new dates or quantities solve the impact. These proposals can be alternatives that result from follow-up conversations with the supplier for changes with impact.
- Evaluating changes received and reviewed in channels that don't automatically trigger an impact analysis.

Learn more in [Simulate whether purchase order changes have impact](procurement-agent-impact-analysis-simulation.md).

## Cost

Impact analysis incurs charges based on the number of Microsoft Copilot Studio credits you use when running it. It has a fixed cost per run and a variable cost that depends on the resources it consumes. The agent management configurations control this cost.

Impact analysis runs on changes that vendors communicate through the configured sources. If you set up and configure impact analysis to run for changes coming through emails via supplier communications, you pay credits when the conditions in the configuration of supplier communications are met. For example, if you configure supplier communications to run on incoming emails from all vendors in a shared mailbox, and you configure impact analysis to run on vendor emails, impact analysis consumes credits when any vendor sends an email about purchase order changes.

The fixed cost applies each time the agent runs, and the variable cost depends on the number of line changes communicated.

Learn about the billing rates and management for Copilot Studio in [Billing rates and management](/microsoft-copilot-studio/requirements-messages-management).
