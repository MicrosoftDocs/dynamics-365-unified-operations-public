# Procurement Agent #

The Procurement Agent in Dynamics 365 Supply Chain Management works with procurement teams to manage supplier changes that affect purchase orders and supply commitments. By streamlining routine supplier communication and automating impact evaluation, the Procurement Agent enables purchasers to spend less time on manual updates and analysis, and more time on informed decision‑making and exception handling.

It consists of multiple capabilities that work together in the procurement workflow.

## Capabilities ##

### Supplier communications ###

Supplier communications manages inbound and outbound updates tied to purchase orders. With it, teams can quickly coordinate with vendors and keep purchase records aligned with supplier commitments.

The inbound functionality within supplier communications monitors and classfies emails from vendors. For those related to purchase orders, it identifies which are confirmations and which are change requests. For change requests, it identifies the changed field(s). Purchasers can confirm and apply changes directly from the same user interface without having to navigate to the purchase orders in Dynamics 365 Supply Chain Management, ensuring purchase orders are up-to-date.

Supplier communications also supports outbound communication, enabling teams to automate outgoing or follow-up communication.

See [Supplier communications](https://learn.microsoft.com/en-us/dynamics365/supply-chain/procurement/supplier-com-agent-overview). 

### Impact analysis ###

Impact analysis evaluates how supplier changes affect inventory, production schedules, and customer deliveries. When a supplier change is received, impact analysis assesses the potential effects on inventory availability, production schedules, and customer deliveries. This allows procurement teams to understand the consequences of a change before deciding whether to accept it or take further action.

Vendors may send confirmations and change requests through various channels. Impact analysis supports these coming in through emails and the Vendor Collaboration Module. The impact analysis can also be manually initiated or simulated.

In addition to automatically analyzing changes communicated by suppliers, impact analysis can also be used to manually simulate changes. 

## How the Procurement Agent capabilities work together ##

The following conceptual flow shows how supplier communications and impact analysis interact within the Procurement Agent.
<Diagram>

**High‑level purchaser workflow with the Procurement Agent**:

1. Send purchase order to vendor
2. Supplier communications sends follows up emails to vendors for confirmation if response is missing or delayed.
3. Supplier communications receives and processes email purchase order responses.
  4. For purchase order confirmations, supplier communications automatically applies these to the purchase order
  5. For purchase order changes, supplier communications highlights the changed field(s) and impact analysis automatically identifies if the change has downstream impact on orders and inventory levels.
6. If using Vendor Collaboration Module, impact analysis is also automatically run for any change requests received
7. For changes without downstream impact, purchasers can apply changes
8. For changes with downstream impact, purchasers can choose to apply the change or follow up with the supplier, as well as determine further action to mitigate impact. If impact cannot be avoided, they know who to inform based on what the impact will be.
