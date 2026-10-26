---
title: Rental management overview (preview)
description: Learn about rental management capabilities for tracking fleet item rental contracts, shipping, invoicing, and returns.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Rental management overview (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Rental management in Dynamics 365 Supply Chain Management and Dynamics 365 Finance provides a comprehensive solution for managing the full lifecycle of rental operations. Rental management helps you track fleet item availability, create and manage contracts, ship and receive fleet items, invoice customers, and handle common rental scenarios such as swaps, stand-down credits, and dynamic pricing.

## Rental industry concepts

The rental management module is built around concepts that are common across rental industries, though terminology might vary depending on your specific business.

### Fleet item types

Rental fleets include three kinds of fleet items. You set the kind with **Fleet item type** on the released product, which has the values *Fleet item*, *Attachment fleet item*, and *Bulk fleet item*:

- **Prime fleet items** – The main serialized fleet item that you rent out to the customer, such as an excavator, skid steer, or generator. A prime fleet item typically has a service meter unit (SMU) or hour meter that tracks usage, similar to the odometer on a vehicle.
- **Attachments** – Serialized accessories that connect to prime fleet items to extend their capabilities. For example, buckets, forks, and mulching heads are common attachments for a skid steer. You can pre-attach attachments to prime fleet items or add them individually to a contract.
- **Bulk fleet items** – Non-serialized fleet items that you rent out alongside prime fleet items, such as hoses, strainers, or cables. You track these fleet items by quantity rather than by serial number.

### Fleet types

Every fleet item belongs to a *fleet type*. The fleet type shows where the fleet item is in its ownership and rental lifecycle. Each fleet type has a *value tracking method* that determines how the system tracks the fleet items in it, such as inventory (stock) or fixed assets. You maintain fleet types and their value tracking methods as setup data. The following table shows an example configuration.

| Fleet type | Description | Value tracking method |
|---|---|---|
| *New* | New fleet items. | *Inventory* |
| *Rental* | Active rental fleet. | *Fixed asset* |
| *Lease* | Long-term rental fleet for fleet items that you rent out on lease contracts. Your company keeps ownership of the fleet item. | *Fixed asset* |
| *Used* | Fleet items that left the active rental or lease fleet and are being marketed for sale. | *Inventory* |
| *Re-rent* | Fleet items sourced from another rental business to help cover customer demand. | *Manual* |
| *Customer* | Customer-owned fleet items that the rental business tracks and services. Sold fleet items are automatically transferred to the *Customer* fleet as part of the sales process. | *Customer* |
| *Canceled* | Fleet items that are retired from the fleet. | *Canceled* |

The system tracks fleet items in a fleet type whose value tracking method is *Inventory* as stock, while fleet items in a fleet type whose value tracking method is *Fixed asset* have an associated fixed asset. Only one fleet type can use the *Customer* value tracking method, and only one can use *Canceled*. Moving a fleet item between fleet types is a fleet transfer. Some transfers happen automatically, such as the move to the *Customer* fleet when a fleet item is sold.

### Fleet item lifecycle

Over its life, an individual fleet item moves through several fleet types. A typical journey looks like this:

1. **Acquired** – A purchased fleet item enters the fleet type that you select when you create its fleet item on the purchase order line, typically *New*, or *Used* if you purchase it used. A fleet item sourced from another rental business enters the *Re-rent* fleet. A re-rent fleet item is only temporarily part of the fleet and, because you don't own it, it isn't backed by inventory or a fixed asset.
1. **In the rental fleet** – You transfer the fleet item into the *Rental* fleet (or *Lease* for lease contracts) so you can rent it. This transfer creates a fixed asset that the system tracks the fleet item against.
1. **On rent and maintained** – You rent out the fleet item on contracts, ship and receive it through fleet item movements, and service it as needed. Between rentals, it stays in the *Rental* (or *Lease*) fleet.
1. **Marketed for sale** – When the fleet item leaves the active rental or lease fleet to be sold, you transfer it to the *Used* fleet. This transfer disposes the fixed asset and returns the fleet item to inventory.
1. **Sold** – When you sell the fleet item, the sales process automatically transfers it to the *Customer* fleet. The fleet item is now customer-owned, though the rental business can continue to track and service it.
1. **Bought back** – If a sold fleet item is later bought back, purchasing it creates a new fleet item with a new number, and the same serial number, in the *New* fleet. The original record stays in the *Customer* fleet as inactive, so the fleet item's history is preserved.
1. **Retired** – A fleet item that leaves the fleet without being sold, for example a canceled purchase, moves to the *Canceled* fleet.

Not every fleet item follows every step, and some transfers happen automatically as part of another process (for example, the move to the *Customer* fleet on sale). Learn more about how fleet transfers work and which transfers the system triggers automatically in [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md).

### Job sites

A *job site* represents a physical location where fleet items are delivered and used, such as a construction project or a data center build. More than one customer can share a single job site. This arrangement is common on large projects where several subcontractors work at the same location. Each customer's link to the job site keeps its own contact and delivery notes, so fleet items reach the right person with the right instructions (for example, *deliver at gate D*). The job site carries a delivery address, and it drives the fleet item's location while the fleet item is deployed there.

Learn more about how to create and manage job sites in [Manage customer and prospect records for rental](manage-customer-prospect-records.md) and [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md).

### Key personas

The rental process involves several roles:

- *Rental coordinator* – Manages day-to-day rental operations from the counter, including creating quotes and contracts, coordinating fleet items, invoicing customers, and handling call-offs.
- *Rental representative* – A sales role that works with customers to secure rental deals and earns commission on contracts in their territory.
- *Rental manager* – Oversees rental operations, monitors utilization, and handles approvals.
- *Operations staff* – Prepares fleet items for shipping, performs inspections and checklists, documents hours and fuel, and receives returning fleet items, at the counter<!-- or on a mobile device-->.
- *Service department* – Handles scheduled and unscheduled maintenance on fleet items, both in the shop and through field service calls.

## Rental lifecycle

### Typical rental flow

A rental typically follows these stages from initial customer contact through final invoicing. Not every contract requires all the stages.

1. **Quote** – *(Optional)* A rental coordinator or representative creates a quotation for the customer based on the requested fleet item and rental period. Create quotations for prospects (customers without an established account) or existing customers.
1. **Reserve** – *(Optional)* Reserve fleet item availability for the customer, either as a reservation request (class, model, or individual fleet item level) or a reservation (a specific fleet item). A reservation can stand on its own, or be connected to a quotation or contract. When you link it, it can be configured to update automatically as the lifecycle state of the linked quotation or contract moves forward. For example, the system marks it as converted when the quotation becomes a contract, or as canceled if you mark the quotation as lost (provided your setup is configured to cancel reservations).
1. **Contract** – Rental contracts define the fleet item, rates, rental period, billing, and more. You can create a contract directly or by confirming a quote.
1. **Activate** – The coordinator activates the contract. You must activate the contract before you can invoice fleet items.
1. **Ship** – Create an outbound fleet item movement. This step is typically automated through a configuration on the rental template. The operations staff prepares the fleet item, completes inspection checklists, documents hours and fuel, takes photos, and logs any pre-existing damage before shipping.
1. **Service** – While the fleet item is on rent, the service department might perform scheduled preventive maintenance or respond to unscheduled service calls in the field. The integration with Dynamics 365 Field Service handles maintenance. Learn more in [Maintenance with Field Service](#maintenance-with-field-service).
1. **Invoice** – The system generates rental invoices periodically based on the billing scenario defined in the rental template (for example, a 28-day monthly cycle). The system supports full and partial credit notes for corrections.
1. **Call off** – When the customer is finished with the fleet item, the rental coordinator creates a call-off to stop rental charges from accruing. Based on the configured call-off action, the system can create and optionally schedule an inbound fleet item movement for receiving.
1. **Receive** – The operations staff receives the fleet item, inspects it, documents the ending hours and fuel level, and notes any damage. The system supports partial receives for situations where not all fleet items are returned at once. This step is typically followed by a return-to-ready process to get the fleet item ready for the next rental.
1. **Close** – The rental coordinator uses the contract closing wizard to review final charges. The best rate calculation (BRC) determines the optimal rate for the customer based on the rental duration. The system calculates any fuel charges, overtime, or other ancillary fees. It generates a final invoice and closes the contract. If you need corrections or additional charges later, you can reopen a closed contract to add supplemental charges before closing it again.

### Contract lifecycle

The rental contract header moves through the following statuses:

| Contract status | Description |
|---|---|
| *Created* | Initial draft state. The contract can be reviewed, edited, and printed before activation. |
| *Approved* | The contract is approved, for example after being put on hold because a discount exceeds a predefined limit. |
| *Active* | The contract is activated and is ready for shipping and invoicing. |
| *On hold* | The contract is on hold, for example when a discount exceeds a predefined limit or when the rental purchase option maximum term date has passed. While a contract is on hold, you can still create proforma invoice schedules and add miscellaneous charges, but you can't create or post invoice schedules, and you can't run the contract closing wizard. |
| *Reopened* | A previously closed contract that is reopened for corrections or additional charges. |
| *Closed* | All contract lines are processed and the contract is fully closed. |

Each contract line also has its own status that tracks the billing state independently of the contract header:

| Contract line status | Description |
|---|---|
| *Active* | The line is active and generating invoice schedule entries on the configured billing cycle. |
| *Call-offs* | A call-off is recorded on the line, stopping rental charges for that line. |
| *Best rate calculation* | The system processes the line through best rate calculation as part of contract closing. |
| *Closed* | The line is fully closed and invoiced. |

### Fleet item movement lifecycle

Fleet item movements track the physical movement of fleet items.

#### Outbound fleet item movement

Outbound fleet item movement tracks fleet items leaving the warehouse. The following table outlines the possible statuses for outbound fleet item movements.

| Status | Description |
|---|---|
| *Request* | The movement is requested but not scheduled. |
| *To be shipped* | The fleet item movement is scheduled. |
| *In transit* | The fleet item is on the way to the job site. This stage is optional. |
| *On job site* | The fleet item is delivered and at the customer's job site. |
| *Canceled* | The outbound movement is no longer needed and is therefore canceled. |

#### Inbound fleet item movement

Inbound fleet item movement tracks fleet items returning to the warehouse. The following table outlines the possible statuses for inbound fleet item movements.

| Status | Description |
|---|---|
| *Request* | The inbound movement is created, typically when a call-off is processed. |
| *To be picked* | The fleet item movement is scheduled. |
| *In transit* | The fleet item is on the way back. This stage is optional. |
| *Received* | The fleet item is received. |
| *Canceled* | The inbound movement is no longer needed and is therefore canceled. |

## Key capabilities

Rental management includes the following key capabilities:

- **Rental management workspace** – A centralized dashboard for rental coordinators and managers that provides tiles for your active contracts, contracts on hold, called-off contracts that aren't returned, contracts due to ship, and more. Learn more in [Use the Rental management workspace](rental-management-workspace.md).
- **Fleet item availability** – A real-time view of all fleet items with agreement status, physical status, and service status. Learn more in [Check fleet item availability and select fleet items](check-equipment-availability.md).
- **Rental cart** – A guided wizard that walks users through creating a quotation or contract, making it easy for new rental coordinators to get started quickly. Learn more in [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md).
- **Fleet item movements** – Shipping and receiving documents track every movement of fleet items between warehouses, job sites, and customers. Fleet item movements support damage tracking, photo attachments, and customizable inspection checklists. Learn more in [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md).
<!-- - **The Dynamics 365 Supply Chain Management mobile app** – On a mobile device, operations staff list the fleet item movements that are scheduled to ship or return. They inspect each fleet item, record service meter and fuel readings, report damage, set the service status, and ship or receive the fleet items. Learn more in [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md). -->
- **Best rate calculation (BRC)** – Automatically calculate the optimal rate for the customer based on the rental duration, promoting from daily to weekly to monthly rates as appropriate.
- **Dynamic pricing** – Automatically adjust suggested rental rates based on inventory levels, utilization, reservations, and customer history.
- **Stand-down credits** – Provide customer concessions for weather, venue closures, holidays, or service issues, with support for full-day and partial-day (hourly) credits.
- **Fleet item swaps and substitutions** – Swap fleet items before shipping, exchange fleet items on site during a rental, and log substitutions when you provide a different-sized fleet item.
- **Job sites** – Track delivery locations with support for multiple customers sharing the same job site.
- **Insurance validation** – Check customers' insurance coverage when a fleet item is added to a rental contract. A periodic job monitors insurance expiration dates and produces follow-up lists. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md).
- **Financial integration** – Integrate with the general ledger, fixed assets, and accounts receivable through standard inventory, fixed asset, and sales category posting. The system splits revenue for a main rental line across the fleet items on it, and revenue-based depreciation posts automatically when you post invoices. Learn more in [Understand rental management financial integration](understand-rental-financial-integration.md).
- **Periodic batch jobs** – Automate routine tasks including invoice schedule generation and posting, insurance expiry monitoring, reservation cleanup, utilization calculations, and overtime processing. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md).
- **Rental rates and discounts** – Apply book rates, customer-specific rates, rental rate group rates, application-based rates (such as salt water environments), shift-based rates, and rental packages. Discount override limits protect margins. Learn more in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).
- **Fleet item master** – Keep a comprehensive record for each fleet item that tracks financial summaries, damage history, service meter usage, GPS location, rental history, and attachment history. Learn more in [Manage fleet item master data](manage-equipment-master-data.md).
- **Fleet utilization tracking** – Track time and financial utilization of your fleet down to the individual fleet item level, with configurable reporting periods. Learn more in [Track rental fleet utilization](track-rental-fleet-utilization.md).
- **Fleet item sales** – Sell fleet items from the rental fleet by using sales orders. Learn more in [Sell fleet items from the rental fleet](sell-equipment-from-rental-fleet.md).
- **Rental purchase option (RPO)** – Create rent-to-own contracts, where a customer rents a fleet item with the option to buy it with part of the rent credited toward the purchase price. You enable the option on the contract, and the rental template supplies the interest terms, the minimum and maximum term, and the fleet types you can use. The rental purchase option report shows the remaining balance and the pay-off amount. When all the invoice schedules of the contract are invoiced and the customer buys the fleet item, you start the buy-out from the contract and complete it as a fleet transfer. A rental purchase option isn't the same as the *Lease* fleet type. A lease keeps ownership of the fleet item with your company, while a rental purchase option leads to the customer owning it. A contract can combine the two. The rental purchase option isn't supported in hourly billing scenarios. Learn more in [The Rental purchase option parameters FastTab](set-up-rental-templates.md#the-rental-purchase-option-parameters-fasttab).
- **Re-rents** – Source fleet items from another rental business to cover customer demand when your own fleet is short. The system tracks re-rent fleet items in a dedicated Re-rent fleet, and you rent them out like owned fleet items. Learn more in [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md).
- **Bulk fleet items** – Rent non-serialized fleet items by quantity alongside prime fleet items, such as hoses, cables, or strainers. The system can suggest bulk fleet items automatically based on the rental class.
- **Sales of accessories and consumables** – Sell accessory and consumable items—such as blades, fuel, or safety gear—to rental customers on a standard sales order, separate from the rental contract. Learn more in [Sell accessories and consumables](sell-accessories-consumables.md).
- **Fleet management** – Purchase new fleet items, transfer fleet items between fleet types, and manage attachment compatibility. Learn more in [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md).

### Maintenance with Field Service

The system handles maintenance of rental fleet items through an integration with Dynamics 365 Field Service. Fleet items that you mark **Eligible for service** appear in Field Service as serviceable assets. The service team uses Field Service to plan and perform maintenance work.

The two systems split responsibilities. Users in Field Service cover preventive and incident-related maintenance, including planning and execution. Users on the rental side file work order requests for reactive maintenance and for work that requires a work order, such as mounting a complex attachment to a prime fleet item before it ships.

To set up the integration, follow the steps in [Set up the rentals integration](/dynamics365/field-service/rentals-setup). Learn more in [Rental operations in Dynamics 365 Field Service](/dynamics365/field-service/rentals-overview).

#### Create a work order request

When you create a *work order request*, the system creates it directly in Field Service to drive the maintenance work order. A work order request captures the incident type, priority, due date and time, and service account, and it tracks a status. The service account defaults from **Customer** on the fleet item, if set. Use the fleet item's service status (for example, *In shop* or *Hard down*) to reflect where the fleet item is in the maintenance process.

You can create a work order request for a fleet item from any of these pages:

- **Fleet items** (the fleet item master)
- **Fleet item availability**
- **Fleet item movements**
- **Rental contracts and quotations** (from the contract or quotation line)
- **Damage history**

To review the work order requests that were already raised for a fleet item, select **View work order requests** from the **Service** group. On the **Fleet items** page, the command is on the **Functions** tab of the Action Pane. On the **Fleet item availability** page, it's on the **Fleet items** tab of the Action Pane. The **Work order requests** page lists the requests from Field Service, newest first.

## Related information

- [Understand rental management financial integration](understand-rental-financial-integration.md)
- [Run rental management periodic jobs](run-rental-periodic-jobs.md)
- [Use the Rental management workspace](rental-management-workspace.md)
- [Check fleet item availability and select fleet items](check-equipment-availability.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
- [Reserve fleet items](reserve-rental-equipment.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
<!-- - [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md) -->
- [Invoice rental contracts](invoice-rental-contracts.md)
- [Call off and close rental contracts](call-off-close-rental-contracts.md)
- [Manage fleet item swaps, substitutions, and transfers](manage-equipment-swaps-substitutions-transfers.md)
- [Handle stand-down credits and concessions](handle-stand-down-credits-concessions.md)
- [Manage fleet item master data](manage-equipment-master-data.md)
- [Track rental fleet utilization](track-rental-fleet-utilization.md)
- [Manage customer and prospect records for rental](manage-customer-prospect-records.md)
- [Set up rental rates and discounts](set-up-rental-rates-discounts.md)
- [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md)
- [Sell fleet items from the rental fleet](sell-equipment-from-rental-fleet.md)
- [Set up rental reference data](set-up-rental-reference-data.md)
- [Configure rental parameters](configure-rental-parameters.md)
