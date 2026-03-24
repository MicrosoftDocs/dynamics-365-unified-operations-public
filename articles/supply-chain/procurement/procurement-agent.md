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

High‑level flow:

- Vendors send confirmations or change requests through supported channels such as email or the Vendor Collaboration module.
- Supplier communications receives, extracts, and structures these supplier updates and links them to the relevant purchase orders.
- Supplier change requests are passed to impact analysis for evaluation.
- Impact analysis assesses the downstream impact on inventory, production, and customer deliveries.
- Procurement teams review the results and decide whether to accept the change, negotiate with the vendor, or take further action.
- Impact analysis can also be triggered at any time through manual simulation, allowing procurement teams to evaluate the impact of hypothetical or internally proposed changes—even when no supplier request has been received yet.
