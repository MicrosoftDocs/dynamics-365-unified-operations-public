---
title: Procurement Agent overview
description: The Procurement Agent in Dynamics 365 Supply Chain Management works with procurement teams to manage supplier changes that affect purchase orders and supply commitments.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 04/24/2026
ms.custom: 
  - bap-template
---

# Procurement Agent overview (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Procurement Agent in Dynamics 365 Supply Chain Management works with procurement teams to manage supplier changes that affect purchase orders and supply commitments. By streamlining routine supplier communication and automating impact evaluation, the Procurement Agent enables purchasers to spend less time on manual updates and analysis, and more time on informed decision‑making and exception handling.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

The Procurement Agent is made up of the following capabilities that work together in the procurement workflow:

- Supplier communications
- Impact analysis

You can choose to enable and use both or just one. This means that you can use supplier communications to handle inbound and/or outbound supplier email communication without the automatic analysis of downstream impact, and you can use impact analysis on sources other and emails through supplier communications.

## Capabilities

### Supplier communications

Supplier communications manages inbound and outbound updates tied to purchase orders. With it, teams can quickly coordinate with vendors and keep purchase records aligned with supplier commitments.

The inbound functionality within supplier communications monitors and classifies emails from vendors. For those related to purchase orders, it identifies which are confirmations and which are change requests. For change requests, it identifies the changed field(s). Purchasers can confirm and apply changes directly from the same user interface without having to navigate to the purchase orders in Dynamics 365 Supply Chain Management, ensuring purchase orders are up-to-date.

Supplier communications also supports outbound communication, enabling teams to automate outgoing or follow-up communication.

Learn more in [Supplier communications features of the Procurement Agent](procurement-agent-supplier-com-overview.md).

### Impact analysis

Impact analysis evaluates how supplier changes affect inventory, production schedules, and customer deliveries. When a supplier change is received through configured sources, impact analysis automatically assesses the downstream effects on orders and inventory. This allows procurement teams to understand the consequences of a change before deciding whether to accept it or take further action.

Vendors may send change requests through various channels. Impact analysis supports these coming in through emails via supplier communications as well as the vendor collaboration interface by classifying changes as "Has impact" and "No impact". See [Review the impact of purchase order changes from vendors](procurement-agent-impact-analysis-review-changes.md)

The impact analysis can also be manually initiated on a purchase order. See [Impact simulation](procurement-agent-impact-analysis-simulation.md)

See [Impact analysis overview](procurement-agent-impact-analysis-overview.md).

## How the Procurement Agent capabilities work together

This section describes how the Procurement Agent capabilities fit into the procurement workflow based on whether supplier communications or the vendor collaboration interface is used to communicate with suppliers on purchase order changes.

### If using emails through supplier communications together with impact analysis

:::image type="content" source="media/procurement-agent-supplier-communications-impact-analysis-workflow.png" alt-text="Diagram of the procurement agent workflow showing supplier communications, impact analysis, and decision steps for purchase order changes." lightbox="media/procurement-agent-supplier-communications-impact-analysis-workflow.png":::
  
1. Send purchase order to vendor
2. Follow up with vendor for confirmation (supplier communications)
3. Receive purchase order confirmation and update purchase order (supplier communications)
4. Receive purchase order change request and view changed field(s) in the **Emails from vendors** workspace (supplier communications)
5. Analyze downstream impact of the change and view result in the **Emails from vendors** workspace (impact analysis)
6. Decision based on impact analysis result (supplier communications + impact analysis)
7. *No impact*: The purchaser can accept the change and update the purchase order (supplier communications)
8. *Has impact*: The purchaser can view more details about the impact (impact analysis) and determine how to proceed. This can be to follow up with the supplier, accept the change and update the PO if nothing can be done (supplier communications), cancel the PO, as well as informing stakeholders.

### If using vendor collaboration interface together with impact analysis

:::image type="content" source="media/procurement-agent-vendor-collaboration-impact-analysis.png" alt-text="Diagram of the vendor collaboration workflow showing PO change request, impact analysis, and decision steps." lightbox="media/procurement-agent-vendor-collaboration-impact-analysis.png":::

1. Send purchase order to vendor
2. Receive purchase order change request via the vendor collaboration interface's *In external review requires action* tab in the **Purchase order preparation** workspace
3. Analyze downstream impact of the change (impact analysis)
4. Decision based on impact analysis result (impact analysis)
5. *No impact*: The purchaser can accept the change and update the purchase order
6. *Has impact*: The purchaser can view more details about the impact (impact analysis) and determine how to proceed. This can be to follow up with the supplier, accept the change and update the PO if nothing can be done, cancel the PO, as well as informing stakeholders.

## Cost

The Procurement Agent incurs charges based on the number of Microsoft Copilot Studio credits you use when running it. The agent has a fixed cost per run and a variable cost that depends on the resources it consumes. This is controlled by the agent management configurations.

For information about how charges apply to each capability, refer to: [Cost for supplier communications](procurement-agent-supplier-com-overview.md#cost) and [Cost for impact analysis](procurement-agent-impact-analysis-overview.md#cost).

Learn about the billing rates and management for Copilot Studio in [Billing rates and management](/microsoft-copilot-studio/requirements-messages-management).
