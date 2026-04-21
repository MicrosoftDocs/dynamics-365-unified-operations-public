---
title: procurement-agent-impact-analysis-overview.md
description: Impact analysis streamlines how purchasing teams evaluate supplier change requests, ensuring fast decisions and uninterrupted supply chain operations.
#customer intent: As a procurement specialist, I want to use impact analysis to trace the effects of supplier changes across sales, production, and transfer orders so that I can make informed decisions.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: lisascholz
ms.date: 04/24/2026
ms.topic: overview
---

# Impact analysis overview

The Procurement Agent in Dynamics 365 Supply Chain Management works with procurement teams to manage supplier changes that affect purchase orders and supply commitments. Impact analysis evaluates if and how supplier changes affect inventory levels, production schedules, and customer deliveries. It helps teams react faster and with higher confidence when suppliers propose changes to purchase orders by clearly indicating whether they have a downstream impact.

Instead of spending a lot of time manually tracing pegging, reservations, or planning dependencies across the system for each change communicated by suppliers, teams are able to quickly determine which can be safely accepted, and which require further action. This helps prioritize time spent on changes with impact, ultimately protecting service levels and production continuity.

When a supplier proposes a change to a purchase order through a configured source or when it is manually initiated, impact analysis looks for downstream impact on sales, production, and transfer orders, as well as on inventory levels. It does this by tracing the changed supply across the system to identify orders that are linked to it through markings and peggings (if available), and checking this against confirmed incoming supply as well as projected on-hand inventory.

## Review the impact of purchase order changes from vendors

Purchasing teams regularly receive change requests from suppliers, including delivery delays, quantity reductions, and cancellations. Each change to a purchase order can potentially affect safety stock, production schedules, internal transfers, and customer commitments. In most cases, purchasers will not want to spend time on changes to purchase orders with no downstream impact. Impact analysis gives purchasers the confidence, visibility, and ability to quickly identify these changes that can be safely accepted, apply them right away, and move on.

For changes with downstream impact on orders, or ones that cause inventory levels to go below certain thresholds, purchasers need to quickly understand the details, consequences, and decide how to respond. Purchasers often follow up with the supplier to request alternatives such as expediting production or transportation, resulting in an earlier delivery date, increased quantity delivered, or a split delivery, while also looking for other alternatives such as different vendors.

If purchasers must accept a change with impact, they now know straight away which internal stakeholders to be informed.

Impact analysis automatically analyzes the downstream impact of changes that arrive through e-mails (Procurement Agent - Supplier communications) and through the Vendor Collaboration Module of Supply Chain Management if configured and enabled.

See [Review impact of purchase order changes from vendors](procurement-agent-impact-analysis-review-changes.md).

## Simulate if purchase order changes have impact

The impact simulation capability allows purchasers and planners to test the impact of changes not directly communicated through e-mails via the Procurement Agent - Supplier communications features or the Vendor Collaboration Module.

Some key use cases for this simulation include:

- Testing and getting a feel for the impact analysis feature before using it on live supplier change requests.
- Proactively testing potential scenarios for at-risk or high-priority purchase orders. This could be purchase orders for which no reply has been received yet.
- Evaluating if supplier proposals for expediting, new dates and/or quantities solve the impact. This can be alternatives that come out of follow-up conversations with the supplier for changes with impact.
- Evaluating changes received and reviewed in channels that do not automatically trigger an impact analysis.

Learn more in [Simulate if purchase order changes have impact](procurement-agent-impact-analysis-simulation.md).

## Cost

Impact analysis incurs charges based on the number of Microsoft Copilot Studio credits you use when running it. It has a fixed cost per run and a variable cost that depends on the resources it consumes. This is controlled by the agent management configurations.

Impact analysis runs on changes communicated by vendors through the configured sources(s). If impact analysis has been set up and configured to run for changes coming through emails via supplier communications, then credits will be charged when the conditions in the configuration of supplier communications are met. For example, if supplier communications has been configured to run on incoming emails from all vendors in a shared mailbox, and impact analysis is configured to run on vendor emails, then impact analysis will consume credits when any vendor sends an email about purchase order changes.

The fixed cost applies each time the agent runs, and the variable cost depends on the number of line changes communicated.

Learn about the billing rates and management for Copilot Studio in [Billing rates and management](/microsoft-copilot-studio/requirements-messages-management).
