# Procurement Agent #

The Procurement Agent in Dynamics 365 Supply Chain Management works with procurement teams to manage supplier changes that affect purchase orders and supply commitments. By streamlining routine supplier communication and automating impact evaluation, the Procurement Agent enables purchasers to spend less time on manual updates and analysis, and more time on informed decision‑making and exception handling.

It consists of multiple capabilities that work together in the procurement workflow.

## Capabilities ##

### Supplier communications ###

Supplier communications manages inbound and outbound updates tied to purchase orders. With it, teams can quickly coordinate with vendors and keep purchase records aligned with supplier commitments.

The inbound functionality within supplier communications monitors and classfies emails from vendors. For those related to purchase orders, it identifies which are confirmations and which are change requests. For change requests, it identifies the changed field(s). Purchasers can confirm and apply changes directly from the same user interface without having to navigate to the purchase orders in Dynamics 365 Supply Chain Management, ensuring purchase orders are up-to-date.

Supplier communications also supports outbound communication, enabling teams to automate outgoing or follow-up communication.

See [Supplier communications overview](https://learn.microsoft.com/en-us/dynamics365/supply-chain/procurement/supplier-com-agent-overview). 

### Impact analysis ###

Impact analysis evaluates how supplier changes affect inventory, production schedules, and customer deliveries. When a supplier change is received through configured sources, impact analysis automatically assesses the downstream effects on orders and inventory. This allows procurement teams to understand the consequences of a change before deciding whether to accept it or take further action.

Vendors may send change requests through various channels. Impact analysis supports these coming in through emails via supplier communications as well as the Vendor Collaboration Module. 

The impact analysis can also be manually initiated on any open purchase order.

See [Impact analysis overview](). 

## How the Procurement Agent capabilities work together ##

This section describes how the Procurement Agent capabilities fit into the procurement workflow based on whether supplier communications or the Vendor Collaboration Module is used to communicate with suppliers around purchase order confirmations and changes. 

### If using emails through supplier communications to communicate with suppliers: ###

<Diagram>
  
1. Send purchase order to vendor
2. Follow up with vendor for confirmation (supplier communications)
3. Receive purchase order confirmation and update purchase order (supplier communications)
4. Receive purchase order change request and view changed field(s) in the **Emails from vendors** workspace (supplier communications)
5. Analyze downstream impact of the change and view result in the **Emails from vendors** workspace (impact analysis)
6. Decision based on impact analysis result (supplier communications + impact analysis)
  7. *No impact*: The purchaser can accept the change and update the purchase order (supplier communications)
  8. *Has impact*: The purchaser can view more details about the impact (impact analysis) and determine how to proceed. This can be to follow up with the supplier, accept the change and update the PO if nothing can be done (supplier communications), cancel the PO, as well as informing stakeholders. 

### If using Vendor Collaboration Module to communcate with suppliers: ###

<Diagram>

1. Send purchase order to vendor
2. Receive purchase order change request via the Vendor Collaboration Module's *In external review requires action* tab in the **Purchase order preparation** workspace
5. Analyze downstream impact of the change (impact analysis)
6. Decision based on impact analysis result (impact analysis)
  7. *No impact*: The purchaser can accept the change and update the purchase order 
  8. *Has impact*: The purchaser can view more details about the impact (impact analysis) and determine how to proceed. This can be to follow up with the supplier, accept the change and update the PO if nothing can be done, cancel the PO, as well as informing stakeholders. 

## Cost ##

The Procurement Agent incurs charges based on the number of Microsoft Copilot Studio credits you use when running it. The agent has a fixed cost per run and a variable cost that depends on the resources it consumes.

Learn about the billing rates and management for Copilot Studio in [Billing rates and management[(https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management).

For information about how charges apply to each capability, refer to: [Cost for supplier communications](https://learn.microsoft.com/en-us/dynamics365/supply-chain/procurement/supplier-com-agent-overview#cost) and [Cost for impact analysis](insert link).

Learn about the billing rates and management for Copilot Studio in (Billing rates and management)[https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management].
